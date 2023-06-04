# Working with Tables

:octicons-tag-24: **0.8.1.9**

## Description

Item **properties** and **descriptions** aren't defined on gameobjects themselves but in **tables** that both look and work similarly to the [CSV format](https://simple.wikipedia.org/wiki/Comma-separated_values).

Tables usually begin with `gml_globalscript_table` in their name and are located in the "**CODE**" block.

!!! Warning
    It is HEAVILY recommended to save your data.win changes before messing with tables, as those are very prone to crash UMT and could cause the loss of any unsaved changes.

---

## Reading & Writing Tables

To read and edit the tables, using **UMT isn't practical** as it's both laggy with big files, and doesn't provide a clear interface to know which column you're trying to modify.

As such, you should use the [GML to CSV Converter](../tools/gmltocsv.md).  
A detailed guide of how to use it is available on its page, but here's a quick rundown :
??? abstract "GML to CSV Converter Guide"
    - Make sure you have the [.Net Core 3.1](https://dotnet.microsoft.com/en-us/download/dotnet/3.1) installed.
    - Download and extract CSV_GML_Converter.
    - Extract the GML tables in the same folder with `UMT > Scripts > Resource Unpacker > Dump Specific Code` and specify the names of the files containing the tables you want to extract.
    - Once done, open up `CSV_GML_converter_and_editor.exe`, and press the key corresponding to the name of the file to be converted.
    - Your .csv file will be generated, you can open it in several applications, including **Google Docs** or **Excel**.

---

## Content

Usually, all properties of an object **won't necessarily be in a single table**.  
A clear example of this are consumables :

Their **properties** are stored in `gml_GlobalScript_table_Consumable_Parameters` while their **description and translations** are stored in `gml_GlobalScript_table_consumables`.

A list of more or less documented tables can be found [here](../references/tables.md).

---

!!! Warning
    **Missing** or **misplaced** elements in tables or **corrupted** tables can cause **game crashes** or **unintended behaviours**.
