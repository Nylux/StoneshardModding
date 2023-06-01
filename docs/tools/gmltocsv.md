# GML to CSV Converter

## Description

---

In Stoneshard, some data is stored in **tables**.  
The best way to describe what those are is a **spreadsheet**.  
Unfortunately, you can't import GML tables into **Excel** or **Google Docs** as they are.

This tool fixes this by converting them to the [**.csv** format](https://simple.wikipedia.org/wiki/Comma-separated_values), which is commonly used for spreadsheets, and as such lets you import them in most software to both **read** and **edit tables**.

## Download

---

You can grab the **GML to CSV Converter** from the [Stoneshard Mod Hub :fontawesome-brands-discord:](https://discord.gg/YxfRKYUuht) or below.

Make sure you have installed the **.Net Core 3.1** as this is a **requirement** for the **GML to CSV Converter** to work.
</br></br>

[.Net Core 3.1 :octicons-link-external-16:](https://dotnet.microsoft.com/en-us/download/dotnet/3.1){ .md-button .md-button--primary}&emsp;
[GML To CSV Converter :octicons-download-16:](../downloads/CSV_GML_Converter.zip){ .md-button .md-button--primary}

## Usage

---

### 1. Extracting the table
???+ abstract "Extracting the table"
    - Open UMT.
    - Locate the file containing the table you want to convert into .csv and note down its name. (exemple : `gml_GlobalScript_table_all_attribute`)
    - Click on `Scripts`, `Resource Unpackers` and finally `DumpSpecificCode.csx`.
    - Select the folder where the file containing your table will be extracted.
    - Enter the name of the file you want to extract.
    - A `Code` folder should have appeared where you extracted the file, and it should contain a `.gml` file.

### 2. Converting the table
???+ abstract "Converting to .csv"
    - Move the .gml file in the `CSV_GML_Converter` folder you installed earlier.
    - Your .gml file should be in the same folder as the `PUT_CSV_OR_GML_FILES_HERE` file.
    - Run the `CSV_GML_converter_and_editor.exe` file.
    - Read the instructions on screen, and press the key corresponding to the file you're trying to convert.
    - The converter will create the .csv file in the same folder.
    - Once it prompts you to chose a file again, you can close it.

!!! Tip
    To avoid bloating this folder I strongly recommend moving both the .gml and .csv files out of the folder when you're done with converting them.

## Relevant Guides

---

!!! info "WIP"
    Come back later !

## Screenshots

---

!!! info "WIP"
    Come back later !
