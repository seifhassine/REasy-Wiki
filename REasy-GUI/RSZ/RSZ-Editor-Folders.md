[⬅️ Back to RSZ Editor](./RSZ-Editor.md)

# Folders

## Table of Contents

- [Folder Types](#folder-types)
- [REasy Folder Operations](#reasy-folder-operations)
  - [Create A Folder](#create-a-folder)
  - [Delete A Folder](#delete-a-folder)
  - [Create A Child GameObject](#create-a-child-gameobject)
  - [Paste GameObject into Folder](#paste-gameobject-into-folder)
  - [Translate Folder Name](#translate-folder-name)
  - [Enable/Disable Folders](#enabledisable-folders)

---

<details>
<summary><strong>Folder Types</strong></summary>

In RSZ files, Folders may:

- Be empty. 

    <img src="../../media/empty_folder.png" alt="Empty folder" width="300"/>

    <br>
- Reference an external .scn file. 

    <img src="../../media/folder_external_reference.png" alt="External Reference folder" height="190"/>

    <br>

- Contain other Folders/GameObjects.

    <img src="../../media/populated_folder.png" alt="Populated folder" height="160"/>

</details>

---

<br>

## REasy Folder Operations

<details>
<summary><strong>Create A Folder</strong></summary>

You can create a Folder either:

- By right-clicking the main "Folders" node and creating a normal Folder:

    <img src="../../media/create_folder_from_root.png" alt="Create folder" />

<br>

- By right-clicking any Folder and creating a sub-Folder:

    <img src="../../media/create_subfolder.png" alt="Create sub-folder" />
    
<br>
</details>

---

<details>
<summary><strong>Delete A Folder</strong></summary>

<br>

When deleting a Folder, all of its children will be deleted (nested sub-Folders and GameObjects). 

Right click the Folder then choose **Delete Folder**:

<img src="../../media/create_subfolder.png" alt="Create sub-folder" />
    
</details>

---

<details>
<summary><strong>Create A Child GameObject</strong></summary>

<br>

To create a GameObject under a Folder, first right click the Folder and choose **Create GameObject**:

<img src="../../media/folder_create_gameobject_1.png" alt="Create GameObject in Folder 1" />

<br>

Then choose a name for the new GameObject, and click **OK**:

<img src="../../media/folder_create_gameobject_2.png" alt="Create GameObject in Folder 2" />

<br>

You will see the new GameObject in the **children** node of your Folder:

<img src="../../media/folder_create_gameobject_3.png" alt="Create GameObject in Folder 3" />

<br>
</details>

--- 

<details>
<summary><strong>Paste GameObject into Folder</strong></summary>

If you have previously copied a GameObject, you can paste it as a child in your Folder.
It will then appear in the **children** node.

<br>
</details>

---

<details>
<summary><strong>Translate Folder Name</strong></summary>

You can translate names of Folders (make sure to choose your preferred language in **File**>**Settings**).

First, right click the Folder and choose **Translate Name**:

<img src="../../media/translate_folder_1.png" alt="Create GameObject in Folder 3" />

<br>

You will then see the name in your chosen language (English here):

<img src="../../media/translate_folder_2.png" alt="Create GameObject in Folder 3" />

<br>
</details>

---

<details>
<summary><strong>Enable/Disable Folders</strong></summary>

There are usually 3 toggles (**Update**, **Draw** and **Standby**).

When a Folder is disabled, it will not be used and none of its children will be active.

Make sure to have all three toggles enabled if you want a folder to be active:

<img src="../../media/folder_toggle.png" alt="Create GameObject in Folder 3" height="220"/>
</details>


