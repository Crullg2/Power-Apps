# Nurse Hospital Rescue

![Game Screenshot 1](./Images/Image/Screenshot%202025-05-20%20074850.png)
![Game Screenshot 2](./Images/Image/Screenshot%202025-05-20%20074858.png)
![Game Screenshot 3](./Images/Image/Screenshot%202025-05-20%20074909.png)

---

**Nurse Hospital Rescue** is an interactive Power Apps game where you score points by clicking on hero nurses and lose points by clicking on the wrong character. This is a fun game for healthcare-themed events, nurse appreciation, or just some friendly competition.

---

## How It Works

- The game runs for 60 seconds.
- Nurse and doctor icons appear randomly on the map.
- Click hero nurses to earn points.
- Avoid the "dofey" doctor—he’ll deduct points if clicked.
- You can easily swap backgrounds and images for your own theme.

---

## Game Logic

### Timer & Random Appearance

- The game uses a timer to control how often icons appear.
- Each timer tick, a state variable is set to a random value, controlling when and where icons show up.

```powerapps
Set(Row_4_State, Round(Rand() * 10, 0))
```

- Each character icon uses a formula in its **Visible** property to decide when to show up:

```powerapps
Row_2_State = 2
```

---

### Scoring

#### Add Points (Hero Nurse Example)

```powerapps
Set(Score, Score + 50);
Set(Row_2_State, Row_2_State * -1)
```
- Clicking a hero nurse increases the score and hides the nurse until the next random appearance.

#### Deduct Points (Dofey Doctor Example)

```powerapps
Set(Score, Score - 50);
Set(Row_3_State, Row_3_State * -2)
```
- Clicking the dofey doctor decreases your score and resets the doctor icon.

---

### Game Variables

- `Score`: Tracks the player's current score.
- `Row_X_State`: Controls the visibility of each icon (nurses, doctor).

---

## Customization

- **Icons:** Swap in your own nurse or doctor images.
- **Background:** Change the background to any map or setting you like.
- **Scoring:** Adjust point values as needed in the icon formulas.

---

## Quick Start

1. Import the app into Power Apps Studio.
2. Add your own backgrounds and character images.
3. Set up each icon’s **Visible** and **OnSelect** properties using the formulas above.
4. Start the timer and play!

---

## Tips

- This game is easy to re-theme for any hospital, clinic, or health education activity.
- All logic is managed with Power Apps variables and formulas—no complicated code required.
- Great for boosting engagement at health fairs, education days, or team-building events.

---

**Have fun—let the best nurse win!**
