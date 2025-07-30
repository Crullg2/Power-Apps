# 🧭 Problem Decision Tool

![Decision Tool UI](images/Screenshot%202025-05-08%20155534.png)

**The Problem Decision Tool** is a Power Platform-based triage app that helps users categorize problems and determine the appropriate level of intervention. Whether an issue is best suited for a `Just Do It`, `RPIW`, `Yellow Belt`, or `Green Belt` project, this app guides users through a consistent, structured decision-making process.

---

## 🔍 Purpose

- Quickly assess the scale and complexity of a problem  
- Reduce ambiguity when deciding whether to escalate an issue  
- Align problems with appropriate Lean or PI tools  
- Does not require a datasource but can add one for tracking  

---

## ⚙️ Features

- Dynamic questions based on selected issue type  
- Built-in logic that evaluates scope, risk, urgency, and control  
- Recommends a decision path (e.g., Yellow Belt or Green Belt)  
- Allows saving/exporting of decisions  
- Works on both mobile and desktop  

---

## 📊 Decision Logic

- Is the root cause known?  
- Is it isolated to one area or cross-functional?  
- Does it involve safety, compliance, or major impact?  
- How much effort would it take to address?  

**Possible outcomes:**  
- 🛠️ **Just Do It**
- 🟡 **Yellow Belt**
- 🚀 **RPIW**
- 🟢 **Green Belt**

---

## 📈 ROI & Impact

- 5 unnecessary RPIW requests avoided per year  
- 10 employees × 40 hours = **2,000 labor hours saved**  
- Estimated savings per facility: **$480,000/year**  
- App cost to build: **$2,040** (40 hours × 2 developers)  
- **ROI: 23,429%**  
- Org-wide potential savings: **$22M+ in unrealized value**

![ROI Summary](images/ROI-Screenshot.png)

---

## 🧠 Tech Stack

- Power Apps Canvas App  
- SharePoint or Dataverse backend if desired to record decisions/track ROI from use  
- Logic via `Switch()`, `If()`, `Patch()`, and collections  

---

## ✅ Other Suggested Add-ons

- Add a list that dynamically tracks ROI based on final selections

---

## 📲 How to Install the Problem Decision Tool in Power Apps

1. **Download the App Package**  
   Get the `.msapp` file or export package (may be a `.zip`) from your team or download link.

2. **Open Power Apps Studio**  
   Go to [Power Apps](https://make.powerapps.com/) and sign in.

3. **Import the App**  
   - Click **Apps** on the left menu.  
   - Select **Import canvas app** (top of the page or under "+ New app" dropdown).  
   - Upload your `.msapp` file or exported package.

4. **Name & Review**  
   - Give the app a name (or keep default).  
   - Review details and set up any needed data connections (SharePoint, Dataverse, etc.).

5. **(Optional) Connect Data Sources**  
   - If you want to save decisions or track ROI, connect to a SharePoint list or Dataverse table when prompted.

6. **Save & Publish**  
   - Click **Save**.  
   - Click **Publish** to make the app available to users.

7. **Share the App**  
   - Click **Share** in Power Apps.  
   - Add users or groups who need access.  
   - Set permissions (User, Co-owner, etc.) as needed.  
   - Click **Share** to send invites.

8. **Access on Any Device**  
   - Users can launch the app from [Power Apps](https://make.powerapps.com/) or the Power Apps mobile app (iOS/Android).  
   - For easy access, pin the app to your Home screen or Teams.

**Tip:**  
The app works out-of-the-box for triage and decision support. Add a data source if you want to track decisions or ROI.

---

### Example: Connecting to SharePoint

1. In Power Apps Studio, go to **Data** > **Add data**.  
2. Find your SharePoint site.  
3. Select or create the list you’ll use for tracking.

---

**Need screenshots or a quick how-to video? Just ask.**

