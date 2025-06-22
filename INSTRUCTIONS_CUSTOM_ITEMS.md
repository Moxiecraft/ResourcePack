## 🧪 How to Add a Custom Item Model

This guide walks you through adding new models.

---

### ✅ Step 1: Add Your Texture

Save your PNG texture here:
```
assets/moxiecraft/textures/item/<your_texture_name>.png
```

> Example:  
> `assets/moxiecraft/textures/item/ruby_cookie.png`

---

### ✅ Step 2: Create a Model File

Create a model JSON file for your item:
```
assets/moxiecraft/models/item/<your_texture_name>.json
```

Example:
```json
{
  "parent": "minecraft:item/generated",
  "textures": {
    "layer0": "moxiecraft:item/ruby_cookie",
  }
}
```

> Use `"minecraft:item/handheld"` as the parent for tools or weapons.

---

### ✅ Step 3: Link It to a Vanilla Item

Open or create the override file for a base item:
```
assets/minecraft/items/<vanilla_item>.json
```

Example: `cookie.json`

Use this format:
```json
{
  "model": {
    "type": "minecraft:select",
    "property": "minecraft:custom_model_data",
    "cases": [
      {
        "when": "<your_custom_key>",
        "model": {
          "type": "minecraft:model",
          "model": "moxiecraft:item/<your_texture_name>"
        }
      }
    ],
    "fallback": {
      "type": "minecraft:model",
      "model": "minecraft:item/<vanilla_item>"
    }
  }
}
```

> Replace `<your_custom_key>` and `<your_texture_name>` with your item’s name.  
> Example: `"when": "ruby_cookie"`

---

### ✅ Step 4: Testing the item in-game

Use the following `/give` command:
```mcfunction
/give @p <vanilla_item>[minecraft:custom_model_data={strings:["<your_custom_key>"]}] 1
```

> Example:
```mcfunction
/give @p cookie[minecraft:custom_model_data={strings:["diamond_cookie"]}] 1
/give @p shears[minecraft:custom_model_data={strings:["netherite_shears"]}] 1
```

---