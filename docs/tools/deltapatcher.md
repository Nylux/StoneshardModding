# DeltaPatcher

## Description

---

**DeltaPatcher** is the 2nd most used tool for Stoneshard modding.  
Currently, it's the way we both **distribute** and have **users install mods**.

It works by checking the differences between 2 files, and generating a **.xdelta file** which contains only the difference (or *delta* :material-delta:) between the 2 files.  
This is important because this allows us to **share our mods without sending the entire game files**, as that would imply much **bigger file sizes** as well as technically being **piracy**.

The other use of **DeltaPatcher** as mentionned above is to actually **install the mods for users**.  
All they have to do is install **DeltaPatcher**, download your **.xdelta file** and apply it on their **data.win**.

???+ Question "Limitations"
    Obviously this method has **limitations**.  
    Since in the end we are essentially **replacing** the user's data.win with our own, this means the following :

    - Mods only work for **1 specific version** : **the one they were made on**. Any update, regardless of how insignificant will break mod compatibility because of how this works.
    - It's **impossible to install multiple mods at once**, unless they have been **manually merged** in the data.win.

    Though this is no fault of DeltaPatcher, we are currently **looking for better options**.  
    Let us know if you know of any on the [Stoneshard Mod Hub :fontawesome-brands-discord:](https://discord.gg/YxfRKYUuht).

## Download

---

You can grab **DeltaPatcher** directly on Github.  
Make sure to grab the version for your OS and ^^not the Source Code^^ !

[DeltaPatcher on Github :octicons-link-external-16:](https://github.com/marco-calautti/DeltaPatcher/releases){ .md-button .md-button--primary}

## Usage

---

### Creating Mods
???+ abstract "Creating .xdelta files"
    - Make sure you have both a **vanilla** data.win, and a **modded** data.win, and that they're both from the **same game version**.
    - Open `DeltaPatcher.exe`.
    - Click on the blue button with 2 arrows at the bottom of the window.
    - You should now have 2 more fields.
    - In the `Original file` field, browse to your **vanilla** data.win.
    - In the `Modified file` field, browse to your **modified** data.win.
    - in the `XDelta patch` field, browse to the place where you want to save the **.xdelta file**.
    - You can enter a description in the `Description (optional)` field if you wish.
    - When done, click on the `Create patch` button.
    - Wait for it to be done, it can take a bit of time.
    - When done you should have a .xdelta file in the folder you specified.
    - You can distribute this to anyone, **this .xdelta file is your mod**.

### Installing Mods
???+ abstract "Applying .xdelta files"
    - Make sure your data.win and the .xdelta of the mod you downloaded are for the **same game version**.
    - Open `DeltaPatcher.exe`.
    - In the `Original file` field, browse to your **vanilla** data.win.
    - In the `XDelta patch` field, browse to the .xdelta mod you want to apply to your game.
    - Click on the `Apply patch` button.
    - Wait for it to be done, it can take a bit of time.
    - When done, your game is now modded.

## Relevant Guides

---

!!! info "WIP"
    Come back later !

## Screenshots

---

!!! info "WIP"
    Come back later !
