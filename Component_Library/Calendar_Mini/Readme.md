# 📆 Mini Calendar Date Picker Component for Power Apps

![Mini Calendar Preview](Image/Screenshot%202025-05-12 114630.png)

---

## Overview

This lightweight **Mini Calendar** component for Power Apps provides a simple, quick way for users to pick a date.  
It supports month navigation, highlights selected dates, and exposes key properties for easy customization like colors, start/end dates, and style settings.

Perfect for compact apps like desk booking, event scheduling, and time-off requests.

---

## ✨ Key Features

- Fast month navigation
- Easy date selection
- Customizable start and end date limits
- Styling options for selected date and calendar appearance
- Slim and responsive design
- Supports single date selection or range mode

---

## 🔧 Custom Properties (Inputs)

| Property | Description |
|:---------|:------------|
| `BorderRadius` | Sets corner roundness for the calendar box. |
| `ChildTabPriority` | Used for keyboard/tab ordering inside the app. |
| `Color` | Main calendar text color. |
| `ContentLanguage` | Language setting (if localization is needed). |
| `DaysAheadRestriction` | Limits future selectable days from today's date. |
| `DefaultEndDate` | Predefined end date when the calendar loads. |
| `DefaultStartDate` | Predefined start date when the calendar loads. |
| `EnableChildFocus` | Allows focus inside the calendar fields. |
| `EndDate` | Max date allowed to be selected. |
| `Fill` | Background color of the calendar. |
| `Height` | Total height of the calendar control. |
| `OnReset` | Custom behavior when the calendar is reset. |
| `SelectedDateColor` | Font color of the selected date. |
| `SelectedDateFill` | Background fill color for the selected date. |
| `SelectRange` | Enables selecting a range instead of a single date. |
| `StartDate` | Min date allowed to be selected. |
| `Styles` | Applies additional style settings (optional). |
| `Width` | Total width of the calendar control. |

---

## 📤 Custom Properties (Outputs)

| Property | Description |
|:---------|:------------|
| `SelectedDate` | Captures the date selected by the user. |
| `SelectedRange` | Captures the range if `SelectRange` is enabled. |

---

## 🔥 How It Works

- Dates are displayed in a **7-column grid** (Sunday–Saturday).
- Users can move month-by-month using the left/right arrows.
- Only valid dates (within `StartDate` and `EndDate`) are selectable.
- Clicking a date stores it in the `SelectedDate` output property.
- In range mode, users can select two dates to define a start and end range.

---

## 📚 How to Use

1. Import the mini-calendar component `.msapp` file into your Power Apps project.
2. Place the control wherever needed on your screen.
3. Configure input properties (colors, default dates, etc.).
4. Capture selected date using `SelectedDate` output.
5. Optionally, listen for `OnReset` if you add reset logic.

---

## 🙏 Credits

Created to bring **simple**, **elegant**, and **fast** date selection to your Power Apps solutions.  
Feel free to use it, modify it, and adapt it for your projects!

---


