## ![Start Page](Images/Screenshot%202025-05-12%20092442.png)

## ![Step 1](Images/Screenshot%202025-05-12%20092500.png)

## ![Step 2](Images/Screenshot%202025-05-12%20092509.png)

## ![Step 3](Images/Screenshot%202025-05-12%20092530.png)

## ![Repetitive Occurrences Check 1](Images/Screenshot%202025-05-12%20092542.png)

## ![Repetitive Occurrences Check 2](Images/Screenshot%202025-05-12%20092550.png)

## ![Final Recommendation](Images/Screenshot%202025-05-12%20092557.png)

---

# Just Culture Decision Support App

A **Power Apps** tool designed to guide leaders through a structured and fair employee incident review process using "Just Culture" principles. This tool helps leadership teams distinguish between human error, at-risk behavior, and reckless behavior — ensuring responses are consistent, fair, and focused on system improvement when needed.

---

## 📂 SharePoint Lists

### 1. `JustCultureDecisionToolResults` — Stores the full decision flow and responses

| Column Name | Type | Purpose |
|:------------|:-----|:--------|
| ELT | Single line of text | Executive Leadership Team Member name |
| Service | Single line of text | Employee’s Service name |
| Step1 | Single line of text | Step 1 behavior classification (e.g., Human Error, At-Risk Behavior, Reckless Behavior, Impaired Judgment) |
| Step2 | Single line of text | Step 2 substitution test response (e.g., System Issue, Employee Responsible) |
| Step3 | Single line of text | Step 3 evaluation of repetitive occurrences |
| Behavior | Single line of text | Summarized behavior type if selected separately |
| Are there behavior choices that are causing the repetitive occurrences? | Single line of text | Captures Yes/No response |
| Willemployeemakebetterchoices | Single line of text | Coaching action needed? |
| ConsiderDisciplinaryAction | Single line of text | Disciplinary action recommended? |
| Coach employee to make better choices. | Single line of text | Coaching plan for behavior improvement |
| Are there system performance shaping factors? | Single line of text | System factors identified (Yes/No) |
| Consider System Re-design. | Single line of text | System redesign recommended? |
| Are there personal performance shaping factors? | Single line of text | Personal factors contributing (Yes/No) |
| Consider Re-assignment or disciplinary action. | Single line of text | Additional action needed |
| Will employee address these factors? | Single line of text | Employee willingness to address issues |
| Coach employee to remedy personal performance shaping factors. | Single line of text | Additional coaching needed for personal factors |
| Did this tool help you in Just Culture decision making? | Single line of text | Final feedback on tool effectiveness (Yes/No) |
| Created | Date and Time | Record creation timestamp |
| Modified | Date and Time | Record last modification timestamp |
| Created By | Person or Group | Creator account |
| Modified By | Person or Group | Last modifier account |
---

### 2. `ELTServices` — Dropdown for ELT Member & Service selection

| Column Name | Type | Purpose |
|:------------|:-----|:--------|
| ELT | Single line of text | Name of ELT member |
| Service | Single line of text | Name of service |
| PartOfMedCenter | Single line of text | Site if needed |
| ELTAbbrev | Single line of text | Abbreviation |
| SvCabbrev | Single line of text | Service abbreviation |
| POC | Person or Group | Point of contact |

---

### 3. `JustCultureQuestions` — Predefined Step-by-Step Behavior Guides

| Column Name | Type | Purpose |
|:------------|:-----|:--------|
| Title | Single line of text | Question set title |
| Step1 | Single line of text | Initial behavior description |
| Step2 | Single line of text | System or culture context explanation |
| Step3 | Single line of text | Final "Yes/No" recommendation guide |
| Created | Date and Time | Created timestamp |
| Modified | Date and Time | Last modified timestamp |
| Created By | Person or Group | Creator |
| Modified By | Person or Group | Last modifier |

**Explanation:**
- **Step1** = Defines the *initial behavior* you are reviewing (example: "Employee impaired by substances").
- **Step2** = Provides *context* about system design or leadership expectations related to that behavior.
- **Step3** = Guides if there is an immediate "Yes" or "No" recommendation to move forward based on system findings.
---

## 🔧 App Workflow Explained

### 1. **Home Screen**
- `Set()` variables to reset all system factor flags to `false`.
- Clears old response collections.
- Prepares user session for new decision flow.

```powerfx
Set(varCurrentUserEmail, User().Email);
Set(varWillemployeemakebetterchoices, false);
Set(varAretheresystemperformanceshapingfactors, false);
Clear(colResponse);
Set(varContainerStep1, false);
```

### 2. **Start Button**
- Prepares navigation to the first decision step.

```powerfx
Set(vargalleryStep1, true);
Set(vargalleryStep2, false);
Set(vargalleryStep3, false);
Navigate('Just Culture Decision Support Tool');
```

### 3. **Behavior Selection (Step 1 Buttons)**
- Depending on the selected behavior, it patches Step 1 info into `JustCultureDecisionToolResults`.
- Saves Behavior classification.
- Moves to Step 2 (system checks).

```powerfx
If(
    ThisItem.ID = 1 || ThisItem.ID = 23 || ThisItem.ID = 26 || ThisItem.ID = 25 || ThisItem.ID = 24,
    Set(varContainerStep1,true);
    Set(VarStep3bt,false),

    Patch(JustCultureDecisionToolResults,
    {
        ELT: ELTdd.Selected.Value,
        Service: Servicedd.SelectedText.Value,
        Step1: ThisItem.Step1,
        Behavior: If(
            ThisItem.ID = 25, "AT RISK Behavior",
            If(ThisItem.ID = 24,"Human Error",
            If(ThisItem.ID = 26,"RECKLESS Behavior",
            If(ThisItem.ID = 1,"IMPAIRED JUDGEMENT"))))
    });

    Refresh(JustCultureDecisionToolResults);
    Set(varID, Last(JustCultureDecisionToolResults).ID);
    Set(varContainerStep1,true);
    Set(vargalleryStep1, false);
    Set(vargalleryStep3, false)
)
```

### 4. **Substitution Test (Step 2 Yes Button)**
- Records Step 2 response.
- Advances to Step 3.

```powerfx
Patch(
    JustCultureDecisionToolResults,
    {
        ELT: ELTdd.Selected.Value,
        Service: Servicedd.SelectedText.Value,
        Step1: Step1bt.Text,
        Step2:  Button6.Text,
        Behavior: Behaviortxt_1.Text 
    }
);
Refresh(JustCultureDecisionToolResults);
Set(varID, Last(JustCultureDecisionToolResults).ID);
Set(vargalleryStep1, false);
Set(vargalleryStep3, true);
Set(varContainerStep1,false);
```

### 5. **Repetitive Behavior (Step 3 Yes Button)**
- Updates Step 3 response.
- Navigates based on Step 3 outcome.

```powerfx
Patch(
    JustCultureDecisionToolResults,
    LookUp(JustCultureDecisionToolResults, ThisRecord.ID = varID),
    {Step3: ThisItem.Step3}
);

Set(
    varTargetScreen,
    If(
        Step3bt.Text = "Yes",
        'Repetitive Occurrences of: Human Error / At Risk Behavior / Reckless Behavior',
        SuccessSc_1
    )
);
Navigate(varTargetScreen);
```

### 6. **Final Save and PDF Generation**
- At the end, final choices are updated.
- PDF is generated summarizing the session.

```powerfx
Patch(
    JustCultureDecisionToolResults,
    LookUp(JustCultureDecisionToolResults, ThisRecord.ID = varID),
    {
        'Are there behavior choices that are causing the repetitive occurrences?': "No",
        'Consider System Re-design.': "Yes",
        'Are there system performance shaping factors?': "Yes",
        'Did this tool help you in Just Culture decision making?': "Yes"
    }
);

Set(varWorkOrderPDF, PDF('Repetitive Occurrences of: Human Error / At Risk Behavior / Reckless Behavior', {ExpandContainers: true}));
DownloadPDFFromPowerApps.Run(varID, {
    file: {
        name: $"Results_{Text(Now(), "yyyymmddhhmmss")}.pdf",
        contentBytes: varWorkOrderPDF
    }
});
Navigate(Home);
```

---

## 🧑‍💻 Maintainer

**Gary Crull**  
Program Analyst | Citizen Developer | Power Platform Champion

---

## 🔄 How to Run
1. Import the app `.msapp` file into Power Apps.
2. Ensure SharePoint lists are created exactly as shown above.
3. Upload all screenshots under `/Images/` folder.
4. Update `DownloadPDFFromPowerApps` flow connection if needed.
5. Publish and share with ELT Leadership and QI staff!

---
