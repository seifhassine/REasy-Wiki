[⬅️ Back to RSZ Editor](./RSZ-Editor.md)

# GameObjects

## Table of Contents

- [What are GameObjects?](#what-are-gameobjects)
- [GameObject Types](#gameobject-types)
- [GameObject Operations](#gameobject-operations)
  - [Add a New Component](#add-a-new-component)
  - [Paste a Previously Copied Component](#paste-a-previously-copied-component)
  - [Copy Component](#copy-component)
  - [Delete Component](#delete-component)
  - [Create a Child GameObject](#create-a-child-gameobject)
  - [Copy the GameObject](#copy-the-gameobject)
  - [Paste Another GameObject from Clipboard as a Child](#paste-another-gameobject-from-clipboard-as-a-child)
  - [Export the GameObject as a Template to Template Manager](#export-the-gameobject-as-a-template-to-template-manager)
  - [Translate the Name of the GameObject](#translate-the-name-of-the-gameobject)
  - [Associate a Prefab to the GameObject (or Modify Existing Prefab Path)](#associate-a-prefab-to-the-gameobject-or-modify-existing-prefab-path)
  - [Enable/Disable GameObject](#enabledisable-gameobject)
  - [Delete the GameObject](#delete-the-gameobject)

---

## What are GameObjects?

<details>
<summary>Show/Hide</summary>

GameObjects are the fundamental building blocks in both `.pfb` (Prefab) and `.scn` (Scene) files.

- In **.pfb files**, a GameObject never has a prefab attached, because it defines the prefab itself.  
    <sub>A prefab is a template for creating objects with predefined properties and components. It allows for easy reuse and instantiation of complex objects.</sub>

- In **.scn files**, GameObjects can represent a wide variety of entities, such as:
  - Enemies
  - Map objects
  - Controllers (e.g., spawn controllers that define conditions for enemy spawning)
  - Other interactive or static elements in the scene

Each GameObject should have a unique **GUID** assigned to it in its `settings` node. This ensures proper identification and referencing by the game.

GameObjects are used to structure and organize the data and logic within both prefabs and scenes.
</details>

---

## GameObject Types

<details>
<summary>Show/Hide</summary>

GameObjects in RSZ files can be:

- **Root GameObjects**  
  - Located directly under the Data Block or inside a Folder.
  - Serve as main entities in the Scene.

- **Child GameObjects**  
  - Part of another GameObject, listed under its `children` node.
  - Can represent:
    - Physical objects attached to the main object.
    - Before/After patterns (e.g., a child GameObject named "before" and another named "after" to represent states such as pre- and post-explosion).
    - Param GameObjects that control the behavior or properties of the parent GameObject.
    - Other specialized roles depending on the context/game.

</details>

---

## GameObject Operations

<img src="../../media/gameobject_operations.png" alt="GameObject Operations" height="220"/>

### Add a New Component

<details>
<summary>Show/Hide</summary>
Add a new component to the selected GameObject to extend its functionality.
</details>

---

### Paste a Previously Copied Component

<details>
<summary>Show/Hide</summary>

Insert a component from the clipboard into the current GameObject.

</details>

---

### Copy Component

<details>
<summary>Show/Hide</summary>

To copy a component, navigate to the **Components** node under the GameObject and right-click the component you want to copy.  
Select **Copy Component** from the context menu.

<img src="../../media/copy_component.png" alt="Copy Component"/>

</details>

---

### Delete Component

<details>
<summary>Show/Hide</summary>

To delete a component, navigate to the **Components** node under the GameObject and right-click the component you want to delete.  
Select **Delete Component** from the context menu.

<img src="../../media/delete_component.png" alt="Delete Component"/>

</details>

---

### Create a Child GameObject

<details>
<summary>Show/Hide</summary>

Add a new GameObject as a child under the selected GameObject.

</details>

---

### Copy the GameObject

<details>
<summary>Show/Hide</summary>

Copy the selected GameObject to the clipboard for duplication or transfer.

</details>

---

### Paste Another GameObject from Clipboard as a Child

<details>
<summary>Show/Hide</summary>

Insert a copied GameObject as a child under the current GameObject.

</details>

---

### Export the GameObject as a Template to Template Manager

<details>
<summary>Show/Hide</summary>

Save the GameObject as a reusable template for future use.

</details>

---

### Translate the Name of the GameObject

<details>
<summary>Show/Hide</summary>

Automatically translate the GameObject's name to your preferred language.

</details>

---

### Associate a Prefab to the GameObject (or Modify Existing Prefab Path)

<details>
<summary>Show/Hide</summary>

Link a prefab to the GameObject or change the path of an existing prefab association.

</details>

---

### Enable/Disable GameObject

<details>
<summary>Show/Hide</summary>

To enable a GameObject, make sure both **UpdateSelf** and **DrawSelf** are toggled on under its `settings` node.  
Disabling a GameObject will deactivate it and its children.

<img src="../../media/toggle_gameobject.png" alt="Toggle GameObject"/>

</details>

---

### Delete the GameObject

<details>
<summary>Show/Hide</summary>

Remove the GameObject and all its children from the file.

</details>

---

[⬅️ Back](RSZ-Editor.md) | [⬆️ Top](#gameobjects)