# Geppetto Plugin v2.0.0 – Setup

This section explains how to install and configure the Geppetto plugin in your Unreal Engine project.

If you have any question, contact us at: **contact@xandimmersion.com**

> **Note:** This documentation assumes you are already familiar with Unreal Engine terminology and workflows.

---

## 1.1. Prerequisites

There are two versions of the plugin:

- **Compiled Plugin**: for Unreal Engine 5.2, 5.3, and 5.4
- **Uncompiled Plugin**: for Unreal Engine 5.0 to 5.4

> ⚠️ To use the uncompiled version, you must be able to compile C++ code for Unreal Engine.  
You’ll need:
- [Visual Studio Build Tools](https://visualstudio.microsoft.com/downloads/)
- [.NET SDK](https://dotnet.microsoft.com/download)

**Test your setup**:
1. Create a new C++ Unreal Project.
2. Open it in Unreal Editor.
3. Press **Compile** (bottom-right).
4. Ensure the compilation succeeds.

![Setup Prerequisites](/docs/images/setup_page_1.png)

---

## 1.2. Metahuman Compatibility

If you plan to use **Metahuman**, follow these official guides to set up the required assets and configurations:

- [Downloading and exporting Metahumans – Quixel Bridge](https://dev.epicgames.com/documentation/en-us/metahuman/downloading-and-exporting-metahumans/quixel-bridge)
- [Downloading Metahumans](https://dev.epicgames.com/documentation/en-us/metahuman/downloading-and-exporting-metahumans/downloading-metahumans)
- [Requirements & Config Settings](https://dev.epicgames.com/documentation/en-us/metahuman/downloading-and-exporting-metahumans/requirements-and-configuration-settings)
- [Using Metahumans in UE5](https://dev.epicgames.com/documentation/en-us/metahuman/downloading-and-exporting-metahumans/unreal-engine-5)

![Metahuman Setup](/docs/images/setup_page_2.png)

---

## 1.3. Installation via Unreal Marketplace

If you purchased the plugin via Unreal Marketplace:

1. Open **Epic Games Launcher**.
2. Go to **Library > Vault**.
3. Click **Install to engine** on the Geppetto Plugin.

Then:

- Open your project.
- Go to `Edit > Plugins`.
- Search for **Geppetto**.
- ✅ Ensure it's **enabled**.

![Install from Marketplace](/docs/images/setup_page_3.png)
![Enable Plugin UI](/docs/images/setup_page_4.png)

---

## 1.4. Installation via Source Code

1. **Close** your Unreal project.
2. Extract the plugin `.zip` into the **root** directory of your Unreal project.
3. Reopen your project by right-clicking on `<YourProject>.uproject` and selecting **Open**.

> Optional: If the **Missing Modules** window appears, click **Yes**.

If you get: Could not be compiled. Try rebuilding from source manually

Ensure you have the required build tools installed (see section 1.1).

Once the project is open:

- Go to `Edit > Plugins`
- Search for **Geppetto**
- ✅ Ensure it's **enabled**

![Install from Source Code](/docs/images/setup_page_5.png)
![Missing Modules Dialog](/docs/images/setup_page_6.png)
![Plugin Enabled Check](/docs/images/setup_page_7.png)

# 2. Demo

The Geppetto plugin includes a demo level with a skeletal mesh configured with morph targets.  
It uses the asset **Rigged T-Pose Human Male w/ 50 Face Blendshapes by Mike Alger**, licensed under Creative Commons Attribution.

---

## 2.1. How to Open the Demo Level

1. Create or open a project with the Geppetto plugin installed (see section 1.3 or 1.4).
2. Open the **Content Drawer** (`Ctrl + Space`).
3. In the top-right corner, click **Settings** and enable:
   - ✅ Show Plugin Content
   - ✅ Show Engine Content
4. Navigate to:
   - **Marketplace install**: `All > Engine > Plugins > Geppetto Content > GeppettoExampleScene`
   - **Source install**: `All > Plugins > Geppetto Content > GeppettoExampleScene`

5. Load the level and hit **Play**.
6. Use number keys `1` to `0` (or the numpad) to trigger different demo features.

---

## 2.2. Play with the Demo Level

You can trigger the following events at runtime:

| Key | Action |
|-----|--------|
| `1` | Pre-generated lip sync with emotion tags |
| `2` | Pre-generated lip sync (no emotion) |
| `3` | Toggle **happy** emotion |
| `4` | Toggle **neutral** emotion |
| `5` | Start **blink** loop |
| `6` | Stop **blink** loop |
| `7` | Start **eyedart** loop |
| `8` | Stop **eyedart** loop |
| `9` | Runtime lip sync from audio URL (with emotion tags) |
| `0` | Runtime lip sync from a SoundWave (must contain PCM data) |

---

## 2.3. Understand the Demo Level

To explore the Blueprint logic, open `BP_GeppettoExampleActor > Event Graph`.

Each keyboard event is implemented as a separate node block. There is also logic in **BeginPlay** to initialize all components.

---

### 2.3.1. Required Components

To use the plugin on an actor, ensure the following components are attached:

- ✅ A Skeletal Mesh with **facial Morph Targets**
- ✅ An **Audio Component** or **MediaSound Component**
- ✅ A **Geppetto Player Component** (e.g. `DemoPlayer`)
- ✅ Either a **Geppetto SoundWave Player** or a **Geppetto URL Player**

> The audio/media component and Geppetto player depend on whether you're using **pre-generated** or **runtime** animation. You can use both on the same character.

---

### 2.3.2. Begin Play Initialization

During the **BeginPlay** event, the following components are initialized:

- Geppetto SoundWave Player
- Geppetto URL Player
- Geppetto Player (Demo Player)

The `Initialize` node uses **Phoneme**, **Emotion**, and **Micro Expression** tables.  
You can create your own Data Tables to support custom morph targets. See sections:

- **4.5** – Phoneme Table
- **4.6** – Emotion Table
- **4.7** – Micro Expression Table

---

### 2.3.3. Phonemes / Lip Sync

- Keys `1` and `2` use **pre-generated phonemes**.
- Keys `9` and `0` use **runtime phoneme generation**.

📚 Related sections:
- **3.1.1** – Pre-generated phoneme generation
- **3.1.2** – Play phonemes with SoundWave
- **3.2** – Runtime phoneme generation
- **4.10.1** – Geppetto Data Asset
- **4.9.1 / 4.9.2** – Generate phonemes (URL / SoundWave)
- **4.5** – Phoneme Data Table

---

### 2.3.4. Emotions

- Key `3`: Toggle Happy
- Key `4`: Toggle Neutral

📚 Related sections:
- **3.3** – Change Emotions
- **3.5** – Emotion Tag System
- **4.12.2** – Geppetto Emotion structure
- **4.4.7** – Set Emotion Custom Curve
- **4.6** – Emotion Data Table

---

### 2.3.5. Micro Expressions

- Keys `5` and `6`: Start/Stop Blink loop
- Keys `7` and `8`: Start/Stop EyeDart loop

📚 Related sections:
- **3.4** – Play or loop Micro Expressions
- **4.4.9 / 4.4.11 / 4.4.12** – Micro Expression nodes
- **4.7** – Micro Expression Data Table


