
# 🚀 Tethered: Lost in Orbit

Welcome to the development repository for **Tethered: Lost in Orbit**, a retro-inspired 2D pixel-art survival game with strategic turn-based combat. This project is built using **Visual Studio 2022** and the **.NET Framework (Windows Forms)**.

---

## 🗺️ Map Layout Draft
Keep this ship layout in mind as you program transitions, room boundaries, and coordinate coordinates!
* **Sectors:** Main Hall, CO2, Security, Navigation, Electrical, Reactor (North & South), and Engine.

---

## 🛠️ Getting Started

### 1. Prerequisites
* **IDE:** [Visual Studio 2022](https://visualstudio.microsoft.com/vs/)
* **Workload:** Make sure you have **.NET Desktop Development** installed in your Visual Studio Installer.
* **Target Framework:** `.NET Framework 4.8` or newer.

### 2. Setting Up Your Local Workspace
1. **Clone the Repository:**
   ```bash
   git clone [https://github.com/hogles1234/Tethered-Lost-in-Orbit.git](https://github.com/hogles1234/Tethered-Lost-in-Orbit.git)

```

2. Open Visual Studio 2022, choose **Open a project or solution**, and select the `.sln` file once the initial project structure is pushed to `main`.

---

## 🌿 Branch Workflow & GitHub Rules

To prevent overwriting each other's work and to avoid painful merge conflicts, we use a **Feature-Branch Workflow**.

### Rules of the Road:

* 🚫 **NEVER push directly to `main`.** All work must be done on your designated feature branch.
* 🔄 **Pull `main` frequently:** Before writing code, pull the latest changes from `main` to ensure you aren't working on outdated files:
```bash
git checkout main
git pull origin main
git checkout feature/your-branch-name
git merge main

```


* 📢 **Pull Requests (PR):** When your feature is complete and tested, push your branch to GitHub and open a Pull Request to merge it into `main`. At least one other team member must review it before it is merged.

### Active Feature Branches:

* `feature/engine-grid-movement` — Grid arrays, coordinates, player movement, collisions.
* `feature/turn-based-combat` — RPG battle screens, combat turn loops, class calculations.
* `feature/map-renderer-fog` — Drawing loops, dithered flashlight masks, room overlays.
* `feature/survival-systems-oxygen` — Oxygen countdown, HP, emergency alerts, respawns.
* `feature/scavenge-inventory` — Item spawning, interaction handlers, storage chest.
* `feature/interactive-puzzles` — Sector mini-games (CO2, Security, Electrical, Navigation).
* `feature/engine-room-climax` — Final act timers, camera tracking, final override logic.

<img width="1380" height="718" alt="step2" src="https://github.com/user-attachments/assets/c6a702c3-073c-433d-899e-3028e32a95aa" />
<img width="1434" height="846" alt="step1" src="https://github.com/user-attachments/assets/e090bbc3-19f0-49e6-b47a-27383c5b7c74" />

<img width="1383" height="683" alt="step4" src="https://github.com/user-attachments/assets/a7c9e788-c335-40da-bd1a-fa5c5e9ff131" />
<img width="1444" height="832" alt="step3" src="https://github.com/user-attachments/assets/7c277773-e654-498e-b74e-0ab4c712e3f1" />

---

## 📏 Strict Coding & Naming Guidelines

Every class, variable, and file in this codebase must adhere to these rules. This ensures our separate scripts plug into each other seamlessly without compilation errors!

### 1. Case Conventions

* **PascalCase** for Class names, Properties, and Method names.
* **camelCase** for local variables and method parameters.
* **UPPERCASE_WITH_UNDERSCORES** for constants.

```csharp
public class PlayerCharacter // PascalCase Class
{
    public const int MAX_OXYGEN = 100; // UPPERCASE Constant

    public int CurrentHP { get; set; } // PascalCase Property
    public bool HasFlashlight { get; set; } // Boolean prefixed with 'Has'

    public void MoveToTile(int targetX, int targetY) // PascalCase Method, camelCase parameters
    {
        bool isWalkable = CheckCollision(targetX, targetY); // camelCase local variable
    }
}

```

### 2. Class Directories & Namespaces

Ensure your custom classes are saved in the correct physical folders so namespaces match up:

* Data models (e.g., `Player.cs`, `Enemy.cs`, `Tile.cs`) live in the `Models` folder. Namespace: `TetheredGame.Models`
* GUI panels and UserControls live in the `UI` folder. Namespace: `TetheredGame.UI`

---

## 🗃️ Unified Data Dictionary (Do Not Modify Core Types!)

If you are referencing player or enemy data in your scripts, use these exact property names:

### `Player` Properties:

* `ClassRole` (`string`) — `"Architect"`, `"Analyst"`, or `"Warden"`
* `CurrentHP` / `MaxHP` (`int`) — Player health points
* `BaseDamage` (`int`) / `BaseDefense` (`double`) — Combat attributes
* `GridX` / `GridY` (`int`) — Player coordinates on the active grid
* `HasFlashlight` (`bool`) — Determines if visibility radius is $2 \times 2$ or $5 \times 5$
* `OxygenLevel` (`int`) — 0 to 100 countdown value

### `Enemy` Properties:

* `EnemyType` (`string`) — `"Crawler"`, `"Mimic"`, or `"Parasite"`
* `CurrentHP` / `MaxHP` (`int`) — Enemy health points
* `GridX` / `GridY` (`int`) — Current location on the grid
* `IsAlertState` (`bool`) — Buffed movement state if player flees combat

```

```
