# Sample Workout Data

This file contains sample workouts in the correct format to populate your fitness tracker database.

## Format Reference

```
#Category
-Exercise Name
-Sets X Reps
-Weight (kg)
-Duration (min)
```

---

## Sample Workouts Collection

### LEG DAY

```
#Legs
-Back Squat
-5 setsX15 reps
-30 kg
-10 min

#Legs
-Leg Press
-4 setsX12 reps
-80 kg
-8 min

#Legs
-Leg Curls
-3 setsX15 reps
-25 kg
-6 min

#Legs
-Calf Raises
-4 setsX20 reps
-15 kg
-5 min

#Legs
-Lunges
-3 setsX10 reps
-20 kg
-8 min
```

### CHEST DAY

```
#Chest
-Bench Press
-5 setsX8 reps
-80 kg
-12 min

#Chest
-Incline Dumbbell Press
-4 setsX10 reps
-30 kg
-10 min

#Chest
-Cable Flyes
-3 setsX12 reps
-15 kg
-7 min

#Chest
-Push-ups
-3 setsX15 reps
-0 kg
-8 min

#Chest
-Chest Dips
-3 setsX10 reps
-25 kg
-6 min
```

### BACK DAY

```
#Back
-Deadlifts
-5 setsX5 reps
-100 kg
-15 min

#Back
-Bent Over Rows
-4 setsX8 reps
-70 kg
-10 min

#Back
-Pull-ups
-4 setsX8 reps
-10 kg
-10 min

#Back
-Lat Pulldowns
-3 setsX12 reps
-50 kg
-8 min

#Back
-Barbell Rows
-4 setsX6 reps
-90 kg
-12 min
```

### SHOULDER DAY

```
#Shoulders
-Overhead Press
-4 setsX8 reps
-40 kg
-10 min

#Shoulders
-Lateral Raises
-3 setsX12 reps
-12 kg
-6 min

#Shoulders
-Reverse Pec Deck
-3 setsX15 reps
-20 kg
-7 min

#Shoulders
-Dumbbell Shoulder Press
-4 setsX10 reps
-25 kg
-9 min

#Shoulders
-Face Pulls
-3 setsX15 reps
-8 kg
-6 min
```

### ARM DAY

```
#Arms
-Barbell Curls
-4 setsX8 reps
-30 kg
-8 min

#Arms
-Tricep Dips
-3 setsX10 reps
-20 kg
-7 min

#Arms
-Hammer Curls
-3 setsX12 reps
-20 kg
-7 min

#Arms
-Rope Pushdowns
-3 setsX15 reps
-15 kg
-6 min

#Arms
-EZ Bar Curls
-4 setsX10 reps
-25 kg
-8 min
```

### CARDIO DAY

```
#Cardio
-Running
-1 setsX1 reps
-0 kg
-30 min

#Cardio
-Cycling
-1 setsX1 reps
-0 kg
-45 min

#Cardio
-Jump Rope
-5 setsX100 reps
-0 kg
-15 min

#Cardio
-Treadmill Sprint
-10 setsX1 reps
-0 kg
-20 min

#Cardio
-Elliptical Machine
-1 setsX1 reps
-0 kg
-30 min
```

### FULL BODY WORKOUT

```
#Full Body
-Squats
-4 setsX10 reps
-60 kg
-10 min

#Full Body
-Bench Press
-4 setsX8 reps
-70 kg
-10 min

#Full Body
-Rows
-4 setsX8 reps
-65 kg
-10 min

#Full Body
-Overhead Press
-3 setsX8 reps
-35 kg
-8 min

#Full Body
-Deadlifts
-3 setsX5 reps
-80 kg
-10 min
```

### ABS & CORE

```
#Core
-Crunches
-3 setsX20 reps
-0 kg
-5 min

#Core
-Planks
-3 setsX1 reps
-0 kg
-5 min

#Core
-Leg Raises
-3 setsX15 reps
-0 kg
-5 min

#Core
-Russian Twists
-3 setsX20 reps
-10 kg
-5 min

#Core
-Mountain Climbers
-3 setsX30 reps
-0 kg
-5 min
```

---

## How to Use

### Option 1: Manual Entry via UI
Copy and paste individual workouts into the "Add Workout" form on the dashboard.

### Option 2: Database Seed Script
Create a `server/seeds.js` file to bulk insert:

```javascript
import mongoose from "mongoose";
import dotenv from "dotenv";
import Workout from "./models/Workout.js";

dotenv.config();

const sampleWorkouts = [
  {
    user: "USER_ID_HERE",  // Replace with actual user ID
    workoutName: "Back Squat",
    category: "Legs",
    sets: 5,
    reps: 15,
    weight: 30,
    duration: 10,
    date: new Date(),
    caloriesBurned: 750,
  },
  // Add more workouts...
];

mongoose.connect(process.env.MONGODB_URL).then(async () => {
  await Workout.insertMany(sampleWorkouts);
  console.log("Workouts seeded!");
  process.exit(0);
});
```

Run with: `node server/seeds.js`

### Option 3: API Request via Postman
Use the format provided in the add workout endpoint:

```
POST /api/user/workout
Authorization: Bearer YOUR_JWT_TOKEN

Body (raw JSON or form data):
{
  "workoutString": "#Legs\n-Back Squat\n-5 setsX15 reps\n-30 kg\n-10 min"
}
```

---

## Categories Available

- **Legs** — Lower body exercises
- **Chest** — Chest exercises
- **Back** — Back exercises
- **Shoulders** — Shoulder exercises
- **Arms** — Biceps, triceps, forearms
- **Cardio** — Running, cycling, jump rope
- **Full Body** — Compound movements
- **Core** — Abs and core stability

---

## Calorie Burn Reference

The app calculates calories as: `duration × 5 × weight`

Examples:
- Back Squat (10 min × 5 × 30 kg) = 1,500 calories
- Running (30 min × 5 × 0 kg) = 0 calories (adjust formula for cardio)
- Bench Press (12 min × 5 × 80 kg) = 4,800 calories

**Note:** These are sample calculations. Real calorie burn depends on intensity, body weight, fitness level, and exercise type.

---

## Tips

✅ Mix different categories for balanced training  
✅ Start with lighter weights and progress gradually  
✅ Adjust reps/sets based on your fitness level  
✅ Use these as templates and customize for your goals
