---
publish: true
---

```powershell
regedit
```

1. Open registry path `HKEY_CLASSES_ROOT\Directory\shell\`
2. Right click on `shell` and select `New > Key`
3. Type in name of action (can be anything)
4. Right Click on your new Key and add another new Key
5. Name new Key `command` (mandantory)
6. Click on command and right click on `(Default)`, then click Modify...
7. Set Value Data to your Intellij IDEA program location plus `%1` 
   - e.g: `"C:\Program Files\JetBrains\IntelliJ IDEA 2021.2.1\bin\idea64.exe" "%V"`
8. Click on the Key you made in step 3 and set `(Default)` value to the text you want to see
9. Go to your folder and Enjoy!
10. Also, if you want an icon, do this:
    - Go to the Key you made in step 3
    - Right Click and choose `New > String Value`
    - Name it `Icon` (mandantory)
    - Right Click > Modify...
    - Set Data Value to Intellij IDEA exe file


---
Sources:
- 2022-05-02: [Open a project in IntelliJ from folder - Stack Overflow](https://stackoverflow.com/questions/49733733/open-a-project-in-intellij-from-folder)

Related:
[Registry - Read and write to the registry](./Registry%20-%20Read%20and%20write%20to%20the%20registry.md)

Tags:
[Windows](./Windows.md)
