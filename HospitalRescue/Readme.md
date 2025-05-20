# Nurse Hospital Rescue

![Game Screenshot 1](./Images/Screenshot_1.png)
![Game Screenshot 2](./Images/Screenshot_2.png)
![Game Screenshot 3](./Images/Screenshot_3.png)

---

**Nurse Hospital Rescue** is a Power Apps game where you rack up points by clicking on hero nurses and lose points if you click the wrong character. Great for health-themed events, nurse appreciation, or just some lighthearted fun.

## How It Works

- The game runs for 60 seconds.
- Nurse (and doctor) icons pop up at random locations.
- Click on hero nurses for points.
- Avoid the "dofey" doctor (he’ll deduct points).
- Swap in any background or character images you like.

---

## Game Logic

### Timer & Random Icon Appearance

- Uses a timer to update state variables with random values.
- This makes characters appear/disappear.

```powerapps
Set(Row_4_State, Round(Rand() * 10, 0))

Each icon’s Visible property is set by a condition:

powerapps
Copy
Edit
Row_2_State = 2
Scoring
Add Points (Hero Nurses):

powerapps
Copy
Edit
Set(Score, Score + 50);
Set(Row_2_State, Row_2_State * -1)
Deduct Points (Dofey Doctor):

powerapps
Copy
Edit
Set(Score, Score - 50);
Set(Row_3_State, Row_3_State * -2)
Game Variables
Score: Tracks the player’s current score.

Row_X_State: Controls each icon’s visibility.

Customization
Icons: Replace with your own nurse/doctor images.

Background: Swap the background for any location or theme.

Points: Adjust scoring as you wish in the icon formulas.

Quick Start
Import the app into Power Apps Studio.

Add your backgrounds and character images.

Set up icons’ Visible and OnSelect formulas as above.

Start the timer and play!

Tips
Great for hospital or clinic events, education, or recognition.

All logic is handled with Power Apps variables—easy to adapt for other scenarios.

Have fun—let the best nurse win!

yaml
Copy
Edit

**How it looks on GitHub:**  
- Screenshots will display at the top.  
- All sections are clearly labeled and easy to read.  
- You can add or change the image paths to match your repository folder (e.g., `/images/` or `/assets/`).

---

**If you want YAML for documentation tools, let me know—but Markdown is the standard for GitHub READMEs.**







