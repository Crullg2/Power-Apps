## ![Phone Number Input Mask](Image/inputmask.gif)

---

# Power Apps - Phone Number Input Mask Component

This **Power Apps** component provides a smart text input box that automatically formats a phone number as the user types —  
keeping data entry clean, readable, and consistent.

---

## ✨ Features

- Automatically formats phone numbers during typing
- Only allows numeric input (no accidental characters)
- Works with **single** or **multiple** phone number formats
- Supports different country formats (Canada, US, UK, Japan, India, etc.)
- Easy to customize and deploy
- Provides both **formatted** and **raw** output

---

## ⚙️ Exposed Properties

| Property Name | Type | Description |
|:--------------|:-----|:------------|
| `InputMask` | Text (Input) | Defines a single phone number format. Example: `(###) ###-####` |
| `InputMaskMultipleFormats` | Table (Input) | Defines multiple formats based on prefixes (for countries like UK). `InputMask` must be blank to use this. |
| `PhoneNumber` | Text (Output) | The unformatted phone number (digits only). |
| `Text` | Text (Output) | The formatted phone number shown in the input box. |

---

## 📱 Example — Single Phone Number Format

| Country | Example | InputMask |
|:--------|:--------|:----------|
| Canada | `204-998-8344` | `"###-###-####"` |
| US | `(204) 998-8344` | `"(###) ###-####"` |
| United Kingdom | `+44 1234 567890` | `"+## #### ######"` |
| Japan | `(03)-4567-1234` | `"(##)-####-####"` |
| India | `+91 0123 456789` | `"+## ####-######"` |

---

## 📚 Example — Multiple Phone Number Formats (United Kingdom)

```powerfx
Table(
    { Prefix: "01", Format: "##### ######" },
    { Prefix: "02", Format: "### #### ####" },
    { Prefix: "03", Format: "#### ### ####" },
    { Prefix: "07", Format: "##### ######" },
    { Prefix: "08", Format: "#### ### ####" },
    { Prefix: "", Format: "##### ######" }
)
Important:
To use InputMaskMultipleFormats, leave InputMask blank.

🧠 How It Works
User types a phone number (ex: 2049876543)

Input field dynamically formats it according to your mask

Both formatted text and raw phone number are available to the app

🚧 Limitations
Cannot be used inside Galleries or Edit Forms (Power Apps limitation).

You must create a custom form and submit data using Patch() instead of the built-in form controls.

For a guide on how to recreate this functionality in an Edit Form, see:
👉 Phone Number Formatting in a Form (Matthew Devaney)

👍 Give It a Try
If you find this component useful:

⭐ Star this project

🛠 Modify it to fit your app’s needs
