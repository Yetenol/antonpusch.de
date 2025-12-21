---
date: "2025-07-17T08:13:58.720+02:00"
title: "SWTPP Haskell Übungsblätter"
description: "-"
dg-publish: true
---

# 1.3) Funktionen

In diesem Casino wird mit Chips gespielt, die an der Kasse gekauft werden, wo selbstverständlich Transaktionsgebühren anfallen. Alle Chips haben den gleichen Wert. Im ersten Schritt setzen wir die Grundrechenarten als Funktionen mit Integer-Werten um. Es kann davon ausgegangen werden, dass die Integer-Werte nie negativ sind.

- Eine konstante Funktion `fee` soll die Transaktionsgebühr festsetzen. Sie soll vorerst einen Chip betragen.
- Die Funktion `charge val` zieht die Gebühr von einem gegebenen Wert ab. Das Ergebnis kann aber nicht negativ werden, d.h. von null Chips wird auch nichts abgezogen
- Die Funktion `putChips owned added` soll zwei Chip-Anzahlen zusammenrechnen. Sie funktioniert wie die Addition, auf das Ergebnis wird aber die Transaktionsgebühr fällig.
- Die Funktion `takeChips owned taken` zieht einen Chipstapel taken von owned ab, z.B. wenn man einen Einsatz macht. Da man aber nicht mehr einsetzen kann als man hat, kann das Ergebnis der Operation nicht kleiner als 0 werden - entsprechend einem All-In.

```run-haskell
-- Constant that defines the transaction fee
fee :: Int
fee = 1

-- Reduce the number of chips passed on by the transaction fee
charge :: Int -> Int
charge a = if a > fee then a - fee else 0

-- Increase the number of chips passed on by the amount passed on. A fee is due.
putChips :: Int -> Int -> Int
putChips owned bought = charge (owned + bought)

-- Reduce the number of chips passed on by the amount passed on.
takeChips :: Int -> Int -> Int
takeChips owned taken =
    let result = owned - taken in 
            if result >= 0 then result else 0
-- fee = 1 -- Transaktionsgebühr beträgt 1 Euro
-- charge 10 = 9 -- Kauft man 10 Chips, erhält man nur 9
-- putChips 10 2 = 11 -- Kaufen wir 2 neue Chips und haben wir danach 11 Chips
-- takeChips 11 5 = 7 -- Spielen wir 5 unserer 11 Chips, bleiben noch 7
```

# 1.4) Rekursion

Euer Casino-Rechner beherrscht nun einige Grundfunktionen, im Casino gibt es aber noch Spezial-Gewinne. Die Funktion `win :: Int -> Int -> Int` ist ein spezieller Gewinn-Modus für die Spielautomaten, bei dem zwei Chipstapel multipliziert werden. Es gibt aber in den AGBs eine gestaffelte Gebühr, mit der auch verhindert werden soll, dass man einen zu großen Gewinn mit einem zu kleinen Einsatz holt. Sei a der größere der beiden Operanden a und b. Dann gibt es a Iterationen, in denen b auf das Ergebnis addiert wird (Multiplikation durch Addition). Jedes Mal wenn die Anzahl der übrigen Iterationen durch 10 teilbar ist, wird b für die nachfolgenden Iterationen um 1 verringert (bis b=0 erreicht ist).

```run-haskell
win :: Int -> Int -> Int
win a b = if a > b then recurse a b else recurse b a
    where
    recurse :: Int -> Int -> Int
    recurse a b = if a > 0 && b > 0 then 
        if a `mod` 10 == 0 then 
            b + recurse (a-1) (b-1)
        else 
            b + recurse (a-1) b
    else 0
```

---

# 2.1 Rekursion II

Variante mit pattern matching

```run-haskell
win2 :: Int -> Int -> Int
win2 a b = if a > b then recurse a b else recurse b a
    where 
    recurse a 0 = 0
    recurse 0 b = 0
    recurse a b = 
        let b' = if a `mod` 10 == 0 then b-1 else b
        in b + recurse (a-1) b'
-- win2 20 0 = 0
-- win2 20 5 = 72
-- win2 5 20 = 72
-- win2 20 2 = 12
-- win2 100000000 10000000 = *** Exception: stack overflow
```

Variante mit tail recursion

```run-haskell
win3 :: Int -> Int -> Int
win3 a b = if a > b then recurse a b 0 else recurse b a 0
    where
    recurse _ 0 p = p
    recurse 0 _ p = p
    recurse a b p = 
        let b' = if a `mod` 10 == 0 then b-1 else b 
        in recurse (a - 1) b' $! (b + p)
-- win3 20 0 = 0
-- win3 20 5 = 72
-- win3 5 20 = 72
-- win3 20 2 = 12
-- win3 100000000 10000000 = 499999960000000
```

## 2.1* Fibonaccily

Langsame Variante mit top-down

```run-haskell
fib :: Int -> Int
fib 0 = 0
fib 1 = 1
fib a = fib (a - 1) + fib (a - 2)
-- fib 7 = 13
-- fib 30 = 832040 -- langsam
-- fib 70 = 190392490709135 -- braucht ewig
```

Schnelle Variante mit tail call optimization (bottom-up)

```run-haskell
fib2 :: Int -> Int
fib2 a = let n = if a < 0 then 0 else a in fibHelper 0 1 n

fibHelper :: Int -> Int -> Int -> Int
fibHelper curr prev 0 = curr
fibHelper curr prev n = fibHelper (curr + prev) curr $! n - 1
-- fib2 7 = 13
-- fib2 30 = 832040
-- fib2 70 = 190392490709135 -- immer noch extrem schnell
```

# 2.2 Eigene Datentypen

```run-haskell
data CommandS = Put | Take | Win deriving Show -- Summentyp/Aufzaehlungstyp
evalS :: CommandS -> Int -> Int -> Int
evalS c a b = case c of -- alternative zum pattern matching
    Put -> putChips a b
    Take -> takeChips a b
    Win -> win a b

-- | 2b) Commands with parameters
data CommandP = PutP Int Int | TakeP Int Int | WinP Int Int deriving Show
evalP :: CommandP -> Int
evalP (PutP a b) = putChips a b
evalP (TakeP a b) = takeChips a b
evalP (WinP a b) = win a b

-- | 3c) Oh the recursiveness!
data CommandR = PutR CommandR CommandR
              | TakeR CommandR CommandR
              | WinR CommandR CommandR
              | ValR Int
              deriving Show
evalR :: CommandR -> Int
evalR (PutR c1 c2) = putChips (evalR c1) (evalR c2)
evalR (TakeR c1 c2) = takeChips (evalR c1) (evalR c2)
evalR (WinR c1 c2) = win (evalR c1) (evalR c2)
evalR (ValR v) = v

-- Blatt 1
fee = 1 :: Int
charge :: Int -> Int
charge a = if a > fee then a - fee else 0
putChips, takeChips, win :: Int -> Int -> Int
putChips owned bought = charge (owned + bought)
takeChips owned taken = let result = owned - taken in 
            if result >= 0 then result else 0
win a b = if a > b then recurse a b 0 else recurse b a 0
    where
    recurse _ 0 p = p
    recurse 0 _ p = p
    recurse a b p = 
        let b' = if a `mod` 10 == 0 then b-1 else b 
        in recurse (a - 1) b' $! (b + p)
```

# 2.3 Arbeiten mit Strings

```run-haskell
ascii = ['\0'..'\127'] -- Liste aller ASCII Zeichen
```

```run-haskell
isVowel ('a') = True
isVowel ('e') = True
isVowel ('i') = True
isVowel ('o') = True
isVowel ('u') = True
isVowel _ = False
-- isVowel 'a' = True
-- isVowel '\0' = False
```

```run-haskell
hasVowel [] = False
hasVowel ('a':xs) = True
hasVowel ('e':xs) = True
hasVowel ('i':xs) = True
hasVowel ('o':xs) = True
hasVowel ('u':xs) = True
hasVowel (_:xs) = hasVowel xs
-- hasVowel "cake" = True
-- hasVowel "rhythm" = False
```

```run-haskell
toString :: CommandR -> String
toString command = case command of
    ValR x    -> show x
    PutR x y  -> "(" ++ toString x ++ " + " ++ toString y ++ ")"
    TakeR x y -> "(" ++ toString x ++ " - " ++ toString y ++ ")"
    WinR x y  -> "(" ++ toString x ++ " * " ++ toString y ++ ")"
data CommandR = PutR CommandR CommandR
              | TakeR CommandR CommandR
              | WinR CommandR CommandR
              | ValR Int
              deriving Show
-- toString (WinR (ValR 4) (PutR (WinR (ValR 2) (ValR 3)) (ValR 5))) = "(4 * ((2 * 3) + 5))"
```

---

# 3.1 Parametrisierte Datentypen

`rep <list> <num_repetitions>` => `<list>`

```run-haskell
rep :: [Int] -> Int -> [Int]
rep x 0 = []
rep x n = x `mappend` rep x (n-1)
l :: [Int]
l = [1,2,3]
-- rep l 3 = [1,2,3,1,2,3,1,2,3]
-- rep l 0 = []
-- rep [] 2 = []
```

`mirror <list>` => `<list>`

```run-haskell
mirror :: [Int] -> [Int]
mirror x = x `mappend` reverse x
l :: [Int]
l = [1,2,3]
-- mirror l = [1,2,3,3,2,1]
-- mirror [] = []
```

`drop2 <list>` => `<list>`

```run-haskell
drop2 :: [Int] -> [Int]
drop2 [] = []
drop2 (_:[]) = []
drop2 (_:_:xs) = xs
l :: [Int]
l = [1,2,3,4]
-- drop2 l = [3,4]
-- drop 2 [1,2] = []
-- drop2 [1] = []
-- drop2 [] = []
```

# 3.3 Listenfunktionale I

```run-haskell
nvcls :: String -> String
nvcls = filter (not.is_vocal)
is_vocal :: Char -> Bool
is_vocal c = c `elem` "aeiouAEIOU"
t = "Today is the first day of the month."
-- nvcls t = "Tdy s th frst dy f th mnth."
```

```run-haskell
sqr, pot :: Int -> Int
sqr = (^ 2)
pot = (2 ^)
-- map sqr [0..10] = [0,1,4,9,16,25,36,49,64,81,100]
-- map pot [0..10] = [1,2,4,8,16,32,64,128,256,512,1024]
```

```run-haskell
data CommandR = PutR CommandR CommandR | TakeR CommandR CommandR | WinR CommandR CommandR | ValR Int deriving Show
-- am besten listen wir erstmal die Blattwerte von einzelnen CommandR
values (ValR v) = [v]
values (PutR a b) = (values a) ++ (values b)
values (TakeR a b) = (values a) ++ (values b)
values (WinR a b) = (values a) ++ (values b)
-- Dann können wir für eine Liste alle zusammenfügen
listValues = (foldr (++) []) . (map values)
-- listValues [ValR 0, TakeR (ValR 5) (ValR 10)] = [0,5,10]
```

# 4.1 Listenfunktionale II

```run-haskell
data CommandR = PutR CommandR CommandR | TakeR CommandR CommandR | WinR CommandR CommandR | ValR Int deriving Show
badluck :: CommandR -> [CommandR] -> CommandR
badluck start bets = foldl TakeR start bets
badluckr :: CommandR -> [CommandR] -> CommandR
badluckr start bets = foldr (flip TakeR) start bets
-- badluck (ValR 10) [ValR 4, ValR 2] = TakeR (TakeR (ValR 10) (ValR 4)) (ValR 2)
-- badluckr (ValR 10) [ValR 4, ValR 2] = TakeR (TakeR (ValR 10) (ValR 2)) (ValR 4)
```

```run-haskell
import Prelude hiding (any)
any :: (a -> Bool) -> [a] -> Bool
any pred [] = False
any pred (x:xs) = if pred x then True else any pred xs

-- | Funktioniert genauso wie any!
any' pred = foldr (||) False . map pred
-- any (>= 5) [1..4] = False
-- any (>= 5) [1..10] = True
-- any (>= 5) [1..] = True -- funktioniert mit unendlichen Listen!
-- any (< 5) [5…] = …… -- aber nur wenn das Ergebnis True ist 
```

```run-haskell
import Prelude hiding (elem)
elem y = any (==y)
-- elem 'a' "Hallo" = True
```

```run-haskell
hasVowel :: String -> Bool
hasVowel = any isVowel
isVowel = (`elem` "aeiou") :: Char -> Bool
-- hasVowel "rhythm" = False
-- hasVowel "cake" = True
```

# 4.2 List Comprehensions

```run-haskell
-- ersten 20 Vielfachen von 7
a = [i * 7 | i <- [2..21]]

-- jede Zahl bis 100, die nicht durch fünf teilbar ist
b = [i | i <- [1..100],
         mod i 5 /= 0]

-- Alle Primzalhen bis 100
c = [i | i <- [2..100],
         let l2 = [j | j <- [2..(div i 2)],
                  (mod i j) == 0],
         length l2 == 0]

-- Alle Dreierkombinationen von Vornamen für den Perso
d = [ name | i <- einzelnamen, 
             j <- einzelnamen, 
             i /= j,    -- "Jon-Jon-Bran" wollen wir nicht
             k <- einzelnamen,
             j /= k,    -- "Theon-Jon-Jon" wollen wir nicht
             i /= k,    -- "Jon-Samwell-Jon" wollen wir nicht
             let name = i ++ "-" ++ j ++ "-" ++ k ++ " Schubert",
             length name < 27  -- muss auf dem Perso passen
    ]
  where einzelnamen = ["Jon", "Theon", "Samwell", "Joffrey", "Bran"]
```

# 4.3 Typklassen

```run-haskell
-- Aus Blatt 1
fee = 1 :: Int
charge :: Int -> Int
charge a = if a > fee then a - fee else 0
putChips, takeChips, win :: Int -> Int -> Int
putChips owned bought = charge (owned + bought)
takeChips owned taken = let result = owned - taken in 
            if result >= 0 then result else 0
win a b = if a > b then recurse a b 0 else recurse b a 0
    where
    recurse _ 0 p = p
    recurse 0 _ p = p
    recurse a b p = 
        let b' = if a `mod` 10 == 0 then b-1 else b 
        in recurse (a - 1) b' $! (b + p)
data Command = Put Command Command | Take Command Command | Win Command Command | Val Int | Sig Command
eval :: Command -> Int
eval (Put c1 c2)  = putChips (eval c1) (eval c2)
eval (Take c1 c2) = takeChips (eval c1) (eval c2)
eval (Val v)      = v
eval (Win c1 c2)  = win (eval c1) (eval c2)
eval (Sig v)      = signum (eval v)
-- 
toString :: Command -> String
toString command = case command of
    Val x    -> show x
    Sig x    -> "signum " ++ toString x
    Put x y  -> "(" ++ toString x ++ " + " ++ toString y ++ ")"
    Take x y -> "(" ++ toString x ++ " - " ++ toString y ++ ")"
    Win x y  -> "(" ++ toString x ++ " * " ++ toString y ++ ")"
instance Show Command where
    show = toString
instance Num Command where
    c1 + c2  =  Put  c1 c2
    c1 - c2  =  Take c1 c2
    c1 * c2  =  Win  c1 c2
    abs c1 = c1
    signum c1 =  Sig c1
    fromInteger x
        | x >= 0 = Val (fromInteger x)  
instance Eq Command where
    c1 == c2 = eval c1 == eval c2
instance Ord Command where
    c1 <= c2 = eval c1 <= eval c2
-- show (Put (Win (Val 2) (Val 3)) (Val 5)) = "((2 * 3) + 5)"
-- abs (2 * 3) + 5 :: Command = ((2 * 3) + 5)
-- 2 * 3 + 5 == (17 - 6 :: Command) = False
-- 2 * 3 + 5 == Val 10 = True
-- 2 * 3 + 5 < Val 9 = False
-- 2 * 3 + 5 > Val 9 = True
-- :t max = max :: Ord a => a -> a -> a
-- max (2 * 3 + 5) (Val 9) = ((2 * 3) + 5)
```

---
Sources:

Related:

Tags:
Softwaretechnik und Programmierparadigmen
