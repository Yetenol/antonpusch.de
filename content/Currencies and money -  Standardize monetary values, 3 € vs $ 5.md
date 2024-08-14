---  
dg-publish: true  
---  
  
# Usage  
  
| Command      | Rendering |  
| ------------ | --------- |  
| `\cEUR{}`    | €         |  
| `\cUSD{}`    | $         |  
| `\cJPY{}`    | ¥         |  
| `\cGBP{}`    | £         |  
| `\dEUR{1.5}` | 1.50 €    |  
| `\dUSD{1.5}` | $ 1.50    |  
| `\dJPY{1.5}` | 2 ¥       |  
| `\dGBP{1.5}` | £ 1.50    |  
  
# Setup  
  
## Dependency  
  
The [currency](https://texdoc.org/serve/currency/0) package provide a convenient, standardized way to print monetary units and values. It ensures consistency and global style changes.  
  
**Use package** in the preamble    
```latex  
\usepackage{currency} % Normalized way to print and format monetary unit  
```  
  
## Define currencies  
  
**Define currencies** in the preamble    
```latex  
\DefineCurrency{EUR}{  
    name={euro},  
    plural={euros},  
    symbol={\euro},  
    iso={EUR}  
}  
\DefineCurrency{USD}{  
    name={dollar},  
    plural={dollars},  
    symbol={\$},  
    iso={USD},  
    pre=true  
}  
\DefineCurrency{JPY}{  
    name={yen},   
    plural={yens},   
    symbol={\yen},   
    iso={JPY},   
    cents=false  
}  
\DefineCurrency{GBP}{  
    name={pound},   
    plural={pounds},   
    symbol={\pounds},   
    iso={GBP},   
    pre=true  
}  
  
\CurrencySetup{  
    kind=symbol   % Representation of the monetary unit  
}  
```  
  
## Format monetary quantities  
  
**Format money** using key-value pairs in the preamble    
  - First option is the default value.    
  - Supports all [siunitx](https://texdoc.org/serve/siunitx/0) key-value pairs.  
```latex  
\CurrencySetup{  
    kind = iso|plural|name|symbol,   % Representation of the monetary unit  
    pre = false|true,   % Force currency before the value?  
    cents = true|false|always   % Force allow cents to be printed?  
}  
```  
  
Inherit **decimal marker** from [siunitx](https://texdoc.org/serve/siunitx/0)'s configuration  
```latex  
\sisetup{  
    locale = DE   % Use culture's decimal marker  
}  
```  
  
  
---  
Sources:  
  
Related:  
[LaTeX Symbols - Lookup mathematical symbols, operations, relations, and arrows](./LaTeX%20Symbols%20-%20Lookup%20mathematical%20symbols,%20operations,%20relations,%20and%20arrows.md)  
  
Tags:  
[Values  - Standardize math, numbers, symbols, quantities, money](./Values%20%20-%20Standardize%20math,%20numbers,%20symbols,%20quantities,%20money.md)  
