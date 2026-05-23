# Swipe Out! — Final Game Design Document & Project README

**Project Code:** SWIPE-OUT-2026

---

## PART 1: GENERAL INFORMATION

* **Game Name:** Swipe Out!
* **Engine Version:** Unity 6.4 (6000.4.0f1)
* **Genre:** Mobile Sliding Block Puzzle
* **Platform:** Mobile (Android `.apk` / iOS Xcode Project)
* **Art Style:** Fully 2D minimalist aesthetic featuring 100% AI-generated visual assets, optimized for crisp mobile screen presentation.
* **Elevator Pitch:** Clear the path, slide the obstacles, and get the red block to the green finish line. *Swipe Out!* brings classic spatial puzzle mechanics to mobile devices with juicy feedback, completely AI-crafted 2D graphics, and buttery-smooth layout transitions.

---

## PART 2: GAMEPLAY MECHANICS & CORE LOOP

### 2.1. Core Gameplay Loop

```
LAUNCH GAME → MAIN MENU → PLAY → SLIDE 2D BLOCKS → REACH GREEN GOAL → LEVEL WIN → RESTART / NEXT LEVEL

```

### 2.2. Primary Mechanics

* **Axis-Locked Block Sliding:** Players tap and drag 2D blocks across a grid. Vertical blocks can only slide up and down, while horizontal blocks can only slide left and right.
* **Target Objective:** The primary objective is to maneuver a uniquely designated **Red Block** across the grid layout to cross a **Green End Line**.
* **Level Reset:** A dedicated, instantly responsive **Restart Button** allows players to reset the board if they miscalculate their moves.

### 2.3. Mobile UI & Optimization Must-Haves

* **Canvas Scaler Setup:** The Canvas Scaler is strictly configured to **Scale With Screen Size** utilizing a target reference resolution of **1080x1920**.
* **Anchoring & Layouts:** All UI elements, score counters, and buttons use explicit anchoring to adapt flawlessly across varying smartphone aspect ratios (e.g., 16:9, 19.5:9).
* **Safe Area Implementation:** A dedicated runtime script dynamically shifts the UI panels inward to ensure that device notches, hole-punch cameras, and bottom navigation bars never overlay interactable buttons.

---

## PART 3: UI, SCENE MANAGEMENT, & JUICE

### 3.1. Menu & State Architecture

The game runs on a robust scene management system executing a clean loop without crashing:

* **Main Menu:** Displays the game title and an interactive **Play Button** that manages the scene transition into the active puzzle space.
* **Gameplay HUD:** Includes a real-time move tracker, a Restart button, and a **Pause Button**.
* **Pause & Settings Panel:** Toggling pause freezes gameplay interactions and introduces options to return to the main menu or adjust configurations.

### 3.2. DOTween Animations & Juicy Feedback

To elevate player satisfaction, three distinct, intentional DOTween animations are integrated:

1. **Main Menu Entrance (3-Step Sequence):**
* Step 1: The game logo scales down from the top using `Ease.OutBounce`.
* Step 2: The Play Button punches upward slightly later via a delayed vector scale.
* Step 3: Background UI elements smoothly fade in their alpha values simultaneously.


2. **Panel Transition Hook (`OnComplete`):** When the level victory or pause panel animates onto the screen, the underlying interaction scripts use an `.OnComplete()` callback. This ensures buttons only become clickable once the visual animation completes, completely stopping accidental double-clicks during screen changes.
3. **Action Juice Effect:** Guiding the Red Block across the green finish line fires off an instant **Punch Scale** effect on the victory banner, alongside a quick, satisfying UI screen shake to reward puzzle completion.

---

## PART 4: TECHNICAL WORKFLOW & KNOWN ISSUES

### 4.1. Known Issues

While the core loop operates consistently from start to finish, the following limitations are present in this final build:

* **Visual UI Desync:** Under rapid, continuous panel switching, canvas sorting layers can occasionally desync momentarily, causing minor visual overlapping bugs before snapping back into place.
* **Level Softlocks:** Certain complex board layouts can occasionally trap blocks in unpassable configurations due to input timing anomalies, requiring the user to manually trigger a level restart.

---

## PART 5: WHAT CHANGED AND WHY

### 5.1. Scope Reduction & The Strategic Pivot

The development pipeline underwent an absolute structural shift from the midterm concept, *Static Signal: The VHS Haunting*. The original layout relied heavily on a 3D first-person survival horror loop, complex "Static Phantom" stalker AI behaviors, real-time vertex shaders, and immersive spatial sound designs.

As a solo developer handling full implementation, keeping that original scope proved unmanageable within the academic timeline. The technical overhead of optimizing 3D tracking systems, retro post-processing filters, and reliable navigation loops for mobile hardware risked breaking final performance standards.

To guarantee a fully functional, bug-free standalone build that achieves a perfect game loop (Start → Play → Win/Lose → Restart) without crashing, the project pivoted to a **fully 2D puzzle architecture** under *Swipe Out!*. Dropping the third dimension entirely and moving the project to **Unity 6.4 (6000.4.0f1)** allowed for total optimization of mobile-centric touch mechanics, asset weight management, and UI micro-interactions.

### 5.2. Mechanics Matrix: Implemented vs. Cut

| Mechanic / Feature | Status | Justification |
| --- | --- | --- |
| **Touch-to-Drag Translation** | **Implemented** | Core control input needed to manipulate block navigation on touchscreens. |
| **Canvas Scaling & Safe Area** | **Implemented** | Essential for compliance with professional mobile delivery standards across multiple devices. |
| **DOTween Feedback Loops** | **Implemented** | Mandatory criteria to establish weight, juice, and professional UI polish. |
| **Fully 2D Asset Pipeline (Added)** | **New Add** | Replaced all intended 3D assets with AI-generated 2D textures to ensure a lightweight, visually consistent package. |
| **3D First-Person Navigation** | **Cut** | Completely eliminated to minimize performance overhead and narrow development scope.

 |
| **Static Phantom Tracking AI** | **Cut** | Removed because complex enemy pathfinding didn't align with a casual puzzle loop.

 |
| **Flashlight / Battery Limits** | **Cut** | Removed alongside the horror theme to streamline a clean puzzle layout.

 |
| **Analog VHS Visual Shaders** | **Cut** | Exchanged for clean 2D styles to maximize frame rates and avoid mobile GPU throttling.

 |

### 5.3. Step-by-Step AI Development Report

Because C# scripting syntax is not my primary technical strength and rapid asset creation was required to hit deadlines, Gemini and visual AI tools were integrated directly throughout the entire pipeline:

* **Step 1: Loop Brainstorming & Architecture Pivot**
I used AI to evaluate how to scale down my project cleanly. We brainstormed casual puzzle archetypes that could run efficiently on mobile engines without requiring vast, heavy 3D environmental builds.
* **Step 2: Designing Grid Interaction in C#**
I prompted the AI to generate the core math calculations for touch inputs. It successfully built scripts that map finger drags to specific world units, locking translations to a single geometric axis while verifying grid boundary limitations.
* **Step 3: Implementing DOTween Sequences & Callbacks**
AI was utilized to format the explicit syntax for chaining DOTween actions in Unity 6.4. It provided clean templates for writing multi-step sequences for menu openings and corrected the syntax for attaching `.OnComplete()` events to prevent button-mashing errors during scene transitions.
* **Step 4: 2D Generation Asset Pipeline**
To establish a clean, cohesive visual direction within a compressed timeline, generative AI tools were leveraged to create 100% of the game's 2D assets. This included designing perfectly square, uniform block textures, contrasting color profiles for the player block, and sleek minimalist UI icons for the main menu and pause panels.

To download: https://drive.google.com/file/d/1kvGQ-hfJSChxZima4m_mRnbHuHs8ffxZ/view?usp=sharing
