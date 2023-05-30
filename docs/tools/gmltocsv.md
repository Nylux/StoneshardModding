# GML to CSV Converter

## Description

---

In Stoneshard, some info is stored in **tables**.  
The best way to describe what those are is a **spreadsheet**.  
Unfortunately, you can't import GML's tables into **Excel** or **Google Docs** as they are.

This tool fixes this by converting them to the **.csv** format, which is commonly used for spreadsheets, and as such lets you import them in most software to both **read** and **edit tables**.

## Download

---

You can grab the **GML to CSV Converter** from the [Stoneshard Mod Hub Discord](https://discord.gg/YxfRKYUuht) or [here](../downloads/CSV_GML_Converter.zip){:download}.

Make sure you have installed the **[.Net Core 3.1](https://dotnet.microsoft.com/en-us/download/dotnet/3.1)** as this is a **requirement** for the **GML to CSV Converter** to work.

## Usage

---

### 1/ Extracting the table

- Open UMT.
- Locate the file containing the table you want to convert into .csv and note down its name. (exemple : `gml_GlobalScript_table_all_attribute`)
- Click on `Scripts`, `Resource Unpackers` and finally `DumpSpecificCode.csx`.
- Select the folder where the file containing your table will be extracted.
- Enter the name of the file you want to extract.
- A `Code` folder should have appeared where you extracted the file, and it should contain a `.gml` file.

### 2/ Converting the table

- Move the .gml file in the `CSV_GML_Converter` folder you installed earlier.
- Your .gml file should be in the same folder as the `PUT_CSV_OR_GML_FILES_HERE` file.
- Run the `CSV_GML_converter_and_editor.exe` file.
- Read the instructions on screen, and press the key corresponding to the file you're trying to convert.
- The converter will create the .csv file in the same folder.
- Once it prompts you to chose a file again, you can close it.

To avoid bloating this folder I strongly recommend moving both the .gml and .csv files out of the folder when you're done with converting them.

## Relevant Guides

---

WIP. Come back later !

## Screenshots

---

WIP. Come back later !
