---
title: "Alte Unihefter archivieren"
dg-publish: true
---

# How to Export a OneNote Notebook from OneDrive

In some cases (for example, to add your notebook to Outline without using OneDrive) you may have to export it.

First of all, let's clarify what a OneNote notebook is. Or, in other words, what the result of an export would be:

1.  A OneNote notebook is stored on a local file system as a folder with files that have .one and .onetoc2 extensions (and may contain sub folders). 
2.  Also, OneNote can export an entire notebook as a OneNote Package - a file with .onepkg extension. A OneNote Package is an archive with all notebook files. You can open it in Outline or in OneNote. Please note that .onepkg file is just a snapshot/copy of your notebook and when you open it, it is always opened as a local Notebook, not connected to any storage (i. e. not synchronized).
3.  Finally, that may be a zip archive of a folder with files described in point 1.

When your OneNote notebook resides in OneDrive, it is not stored as files and folders in it like other office files. So, you cannot use OneDrive synchronization client to download your OneNote notebook files to your local hard drive. Your data is accessible via API and you need client app to download it. You can use OneNote 2016 on Windows or Outline for Mac to do that. Another option is to export your notebook from OneDrive web site as a zip archive, but that will not work under some certain conditions. Lets review these options in details:

# Export a notebook using OneNote 2016/2021 on Windows

There are two options of how you can export your data. You can use both of them. The only difference is as follows: When you export your notebook as OneNote Package your original notebook in OneNote stays connected to OneDrive, so you can continue using it.

## Export as a OneNote Package

1.  Open your notebook in OneNote. Use OneNote's Open Notebook feature to open your notebook from OneDrive and wait while it fully syncs.
2.  Use File menu to export your notebook. Select File -> Export -> Notebook -> OneNote Package (*.onepkg) and click Export.

![Export OneNote package.png](./attachments/export%20onenote%20package.png)

Now you should have .onepkg file that contains all data from your notebook. You can open this file in OneNote 2016/2021 on Windows or in Outline for Mac.

## Export by changing a notebook location to a local hard drive

1.  Open your notebook in OneNote first. Use OneNote's Open Notebook feature to open your notebook from OneDrive and wait while it fully syncs.
2.  Right-click on a notebook and open Notebook Properties window.
3.  Click on Change Location button and select some folder on your local hard drive.
4.  Close the notebook in OneDrive.

![Move OneNote location.png](./attachments/move%20onenote%20location.png)

Now you should have a folder with .one files and subfolders (if you have section groups). This folder itself is your notebook that contains all your data. 

# Export a notebook using OneDrive Web app

OneDrive allows you to export your notebook as a zip archive using only a web browser. But, unfortunately, this doesn't seems to work with all subscription types. Also it doesn't work in some web browsers (feature is not accessible in Safari 15 at the moment). Nevertheless, this is the easiest option as you need just a web browser, so it's worth a try.

Please follow [this instruction](https://support.microsoft.com/en-us/office/export-and-import-onenote-notebooks-a4b60da5-8f33-464e-b1ba-b95ce540f309) from Microsoft. 

---
Sources:
- 2022-06-15: [How to Export a OneNote Notebook from OneDrive - Outline](https://help.outline.app/article/150-how-to-export-notebook-from-onedrive)

Related:

Tags:
[Microsoft OneNote](./microsoft%20onenote.md)