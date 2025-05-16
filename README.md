
# Geppetto UE 2.0.0 – Setup

![Logo](./images/General_image_1.png)

Welcome to the **Geppetto UE Plugin** for Unreal Engine. This document will show you how to use the plugin in Unreal Engine*.

> 📧 *Please note that this notice assumes familiarity with Unreal Engine terminology and workflows. For more detailed information and examples, refer to the accompanying documentation or consult the provided links.*   
*If you have any questions, feel free to contact us: contact@xandimmersion.com*

## 1.1 Prerequisites

There are two versions of the plugin:
- ✅ **Compiled plugin** (for UE 5.2, 5.3, 5.4, and 5.5)
- 🛠️ **Uncompiled plugin** (for UE 5.0 to 5.4)

> ⚠️ *If you download the uncompiled version of the plugin, you must be able to compile C++ code for Unreal Engine. To do so, you need the Visual Studio build tools for Unreal Engine installed as well as the .NET SDK ! You can find more information on how to set up Visual studio for Unreal engine [here](https://dev.epicgames.com/documentation/en-us/unreal-engine/setting-up-visual-studio-development-environment-for-cplusplus-projects-in-unreal-engine).*


*To ensure that you have all build tools installed, try to create a new C++ Unreal Project and make sure that the Editor starts correctly. Once the editor is open, click on the compile button on the bottom right corner and ensure that the compilation succeeded*

![Option C++ to choose](./images/Prerequisites_image_1.png)
![Compile button and expected result](./images/Prerequisites_image_2.png)


## 1.2 Metahuman

To use the Geppetto plugin with Metahuman, follow these links to configure your project:

- [Download & Export Metahumans - Quixel Bridge](https://dev.epicgames.com/documentation/en-us/metahuman/downloading-and-exporting-metahumans/quixel-bridge)
- [Downloading Metahumans](https://dev.epicgames.com/documentation/en-us/metahuman/downloading-and-exporting-metahumans/downloading-metahumans)
- [Requirements & Configuration](https://dev.epicgames.com/documentation/en-us/metahuman/downloading-and-exporting-metahumans/requirements-and-configuration-settings)
- [Using with Unreal Engine 5](https://dev.epicgames.com/documentation/en-us/metahuman/downloading-and-exporting-metahumans/unreal-engine-5)

## 1.3 Installation – Fab

If you bought the plugin through Fab, you can simply click on “Install to engine” plugin button. All plugins are located in the Vault, at the bottom of the Library:

![Where to find the plugin in the Vault](./images/Installation_Marketplace_image_1.png)

Then, open your project and navigate to Edit > Plugins. Search “Geppetto” and ensure that the plugin is enabled.

![In the Plugin Settings, ensure that the checkbox is checked](./images/Installation_Marketplace_image_2.png)

## 1.4 Installation – Source Code

1. ❌ **Close the unreal engine project where you want Geppetto to be installed !**

2. 📦 Extract the content of the plugin `.zip` archive.
3. 📁 Paste the extracted folder into the root of your project directory.

![Where to paste the extracted file](./images/Installation___Source_code_image_1.png)

4. ▶️ Reopen the project by right-clicking on `<YourProject>.uproject` and choosing **Open**.

![Right click then "Open"](./images/Installation___Source_code_image_2.png)

5. ✅ If prompted with “Missing Modules”, click **Yes**.

![Window of Missing Modules](./images/Installation___Source_code_image_3.png)

> 🧠 If you see “Could not be compiled. Try rebuilding from source manually”, make sure your Visual Studio and SDKs are correctly installed.

6. Once the project is open, Navigate to `Edit > Plugins` in the Unreal Editor.
7. Search for “Geppetto” and ensure the plugin is enabled.

![Expected result when looking for Geppetto in the Plugin window](./images/Installation___Source_code_image_4.png)


---


# Geppetto UE 2.0.0 – Demo

The Geppetto plugin comes with a demo level and a skeletal mesh with morph targets, thanks to [Rigged T-Pose Human Male w 50 Face Blendshapes](https://sketchfab.com/3d-models/rigged-t-pose-human-male-w-50-face-blendshapes-cc7e4596bcd145208a6992c757854c07) by Mike Alger, licensed under [Creative Commons Attribution](https://creativecommons.org/licenses/by/4.0/).

## 2.1 How to Open the Demo Level

1. 🎮 Open or create a project with the Geppetto plugin installed.
2. 🧰 Open the **Content Drawer** (`Ctrl + Space`) and go to **Settings** (top-right corner).
3. ✅ Ensure the following options are enabled:
   - “Show Plugin Content”
   - “Show Engine Content”

![Show where is the Engine and Plugin Content options](./images/How_to_open_the_demo_level_image_1.png)

4. 📂 Navigate to the appropriate folder:
   - **Marketplace install**: `All > Engine > Plugins > Geppetto Content > GeppettoExampleScene`
   - **Source install**: `All > Plugins > Geppetto Content > GeppettoExampleScene`

![Path to the GeppettoExampleScene in Unreal](./images/How_to_open_the_demo_level_image_2.png)

5. ▶️ Open the level and press **Play**.
6. 🕹️ Use number keys (`1` to `0` or numpad) to test the Geppetto Plugin.

![Where to find the Play button](./images/How_to_open_the_demo_level_image_3.png)

## 2.2 Play with the Demo Level

You can interact with the demo using keys at runtime:

| Key | Action                                                                 |
|-----|------------------------------------------------------------------------|
| 1   | Pre-generated Lip Sync with emotions (uses tags)                      |
| 2   | Pre-generated Lip Sync without emotions                               |
| 3   | Toggle Happy emotion                                                  |
| 4   | Toggle Neutral emotion                                                |
| 5   | Start blink loop                                                      |
| 6   | Stop blink loop                                                       |
| 7   | Start eyedart loop                                                    |
| 8   | Stop eyedart loop                                                     |
| 9   | Runtime Lip Sync from audio URL with emotions (uses tags)            |
| 0   | Runtime Lip Sync from SoundWave (must contain PCM audio)             |

## 2.3 Understand the Demo Level

Open `BP_GeppettoExampleActor > Event Graph` to start exploring how the
Geppetto plugin works.

![Where to find the GeppettoExampleActor in the Outlier](./images/Understand_the_demo_level_image_1.png)

![Click on the EventGraph tu unfold all the available graphs](./images/Understand_the_demo_level_image_2.png)

You’ll see a block for each key event and `BeginPlay`.

![Example of BeginPlay block](./images/Understand_the_demo_level_image_3.png)

![Screen of the various Blueprint nodes available in this example actor](./images/Understand_the_demo_level_image_4.png)

### 2.3.1 Components Required

Every actor using the plugin must have these 4 components:

- ✅ A Skeletal Mesh with Morph Targets
- 🔊 An Audio or MediaSound Component
- 🧠 A [Geppetto Player Component](#44-geppetto-player-component) (e.g., DemoPlayer)
- 📡 A [Geppetto SoundWave Player](#42-geppetto-soundwave-player)

![Components you should have](./images/Components_image_1.png)

The Audio/MediaSound Component and the Geppetto SoundWave/URL Player used will depend if the plugin is used with pre-generated or runtime assets. You can use both methods on the same character.

### 2.3.2 Begin Play

In the BeginPlay Event, all Geppetto components are initialized. You can find more information about component initialization below:

- `Geppetto SoundWave Player Initialize`
- `Geppetto URL Player Initialize`
- `Geppetto Player Initialize`

![Path to the GeppettoExampleScene in Unreal](./images/Begin_Play_image_1.png)

The Geppetto Player initialize node uses a Phoneme, Emotion and Micro Expression table as parameters to animate the character. You can create your own table in order to animate characters with custom Morph Targets. 

Please read section [4.5](#45-geppetto-phoneme-data-table), [4.6](#46-geppetto-emotion-data-table) and [4.7](#47-geppetto-micro-expressions-data-table) for more details.


### 2.3.3. Phonemes / Lipsync

The **keyboard 1 and 2** events are related to pre-generated phonemes.


- Please read section [3.1.1 - Pre-Generated Phonemes generation](#311-pre-generate-phonemes-as-a-geppetto-data-asset) of the documentation for more information on how to pre-generate phonemes in a Data Asset using the Geppetto Editor Interface.

- Please read section [3.1.2 - Play animation with SoundWave](#312-play-a-geppetto-data-asset-with-soundwave) of the documentation for more information on how to play the Geppetto phonemes from a Data Asset

- Please read section [4.10.1 - Geppetto Data Asset](#4101-geppetto-data-asset) of the documentation for more information about the Geppetto Data Asset structure

![](./images/Phonemes___Lipsync_image_1.png)

The **keyboard 9 and 0 events** are related to runtime phonemes.

- Please read section [3.2 - Runtime Phoneme Generation](#32-runtime-phonemes-generation-and-animation-blueprint) of the documentation for more information on how to generate and play runtime generated phonemes.
- Please read section [4.9.1 - Generate phonemes (using SoundWave)](#492-generate-phonemes-using-soundwave) for more
information on how to generate phoneme from a local audio file (SoundWave, PCM or file)

![](./images/Phonemes___Lipsync_image_2.png)


The plugin uses a [Geppetto Phoneme Data Table](#45-geppetto-phoneme-data-table) to know all Morph Targets values for each phoneme. If the skeletal mesh of your characters have different Morph Targets, it is required to create a new [Geppetto Phoneme Data Table](#45-geppetto-phoneme-data-table) with the Morph Targets used in your characters.     
**Please note that Data Tables for Metahuman are included in this plugin !**   
The Data Table used by the plugin is passed through the [Geppetto Player Component Initialize](#442-initialize) or [Set Phoneme Table](#445-set-phoneme-table) node. Please read section [4.5 - Geppetto Phoneme Data table](#45-geppetto-phoneme-data-table) of the documentation for more information about phoneme Data Table.

### 2.3.4. Emotions

The **keyboard 3 and 4 events** are related to emotions.

- Please read section [3.3 - Change Emotions](#33-change-emotions) for more information on how to change emotions in Blueprints.
- Please read section [3.5 - Emotion Tag System](#35-emotion-tag-system) for more information on how to change emotions with tags.
- Please read section [4.12.2 - Geppetto Emotion](#4122-geppetto-emotion) of the documentation for more information about the Geppetto emotion structure.
- Please read section [4.4.7 - Set Emotion Custom Curve](#448-set-emotion-custom-curve) of the documentation for more information about the emotion custom transition curves.

![](./images/Emotions_image_1.png)

The same way as phonemes, emotions use a [Geppetto Emotion Data Table](#46-geppetto-emotion-data-table) to determine the Morph Target values for each emotion. Please read section [4.6 - Geppetto Emotion Data Table](#46-geppetto-emotion-data-table) of the documentation for more information.

### 2.3.5. Micro Expressions

The **keyboard 5, 6, 7 and 8 events** are related to micro expressions.

- Please read section [3.4 - Play or Loop Micro Expressions](#34-play-or-loop-micro-expressions) of the documentation for more information on how to use micro expressions.
- Please read section [4.4.9 - Play Micro Expression](#4410-play-micro-expression) of the documentation for more information about the node.
- Please read section [4.4.11 - Start Micro Expression Loop](#4411-start-micro-expression-loop) and [Stop 4.4.12 - Stop Micro Expression Loop](#4412-stop-micro-expression-loop) of the documentation for more information about the nodes.

![](./images/Micro_Expressions_image_1.png)

Like phonemes and emotions, micro expressions use a [Geppetto Micro Expressions Data Table](#47-geppetto-micro-expressions-data-table) to retrieve the Morph Targets values.   
This time, however, the values can be **static** (like phonemes or emotions Morph Targets values) or **dynamic** (the Morph Targets values will change each time the Micro Expression is played).    
Please read section [4.7 - Geppetto Micro Expressions Data Table](#47-geppetto-micro-expressions-data-table) of the documentation for more information.

# 3 Usage

This chapter provides a complete tour of the Geppetto plugin features available in the Unreal Editor and at runtime.

---

## 3.1 Pre-generated Data Asset (Editor)

### 3.1.1 Pre-Generate Phonemes as a Geppetto Data Asset

You can use the Editor Utility Widget to pre-generate phonemes:

- Click the Geppetto icon button or go to `Help > Geppetto`.

This opens a UI with fields to configure the phoneme generation:

- 📘 **Documentation button**: Opens this manual in your browser.
- 🧠 **Local model**: Define the phoneme generation model (local only).
- 🔊 **Audio**: The speech SoundWave asset (compatible with Ariel plugin).
- 🔇 **Remove noise**: Helps silence detection and phoneme precision.
- 🧏 **Use speech recognition**: Phonemes based only on audio.
- 🌐 **Language**: Improve accuracy based on speech language.
- 🗣️ **Sentence**: The sentence being spoken (can include emotion tags).
- 🏷️ **Add tags to sentence**: Insert tags like `<emotion happy>`.
- 🎭 **Phonemes & Emotions settings**: Link to the corresponding Data Tables.
- 📈 **Amplitude & sinus steps**: Control mouth animation intensity.
- 🕑 **Silences**: Use tools like Audacity to find appropriate silence thresholds.
- ⏱️ **Delay**: Sync delay between audio and animation.
- 🎞️ **Sequencer Frame Rate**: Higher FPS = better edit control.
- 👄 **Close Mouth At End Of Speech**: Enables auto-mouth closing.
- 💾 **Save as**: Choose between `Data Asset` or `Sequencer`.

➡️ Once ready, click **Generate Phonemes** to generate the `.uasset`.

---

### 3.1.2 Play a Geppetto Data Asset with SoundWave

To play the generated lip-sync and sound:

1. Create a Blueprint class.
2. Add:
   - Skeletal Mesh Component
   - Audio Component
   - Geppetto SoundWave Player
   - Geppetto Player Component (or custom version for Metahuman)
3. Use `BeginPlay` to initialize with:
   - `Geppetto SoundWave Player Initialize`
   - `Geppetto Player Component Initialize`
4. Use `Play Data Asset` to start playback.
5. Use `Play` node (advanced) if you want to override audio or delay.

---

### 3.1.3 Play a Geppetto Sequence

Same idea as before, but with the **Geppetto Sequencer Component**:
- Requires: Skeletal Mesh Component + Geppetto Sequencer
- Initialization in `BeginPlay`
- Use the `Play` node to trigger animation + sound
- Optionally reset the facial expression at the end

---
📸 **Images for this chapter** will be included below if any were detected:

---

## 3.2 Runtime Phonemes Generation and Animation (Blueprint)

This setup is used for audio generated during gameplay, such as:
- 🎤 Player microphone input
- 🧠 Ariel TTS plugin

### Components

1. Skeletal Mesh Component (with Morph Targets)
2. Geppetto URL Player or SoundWave Player
3. Media Sound Component (for URL) or Audio Component (for SoundWave)
4. Geppetto Player Component (or custom one for Metahuman)

> 🎭 Metahuman users: Override `Set Morph Target` in a child component if needed.

### Initialization

Use `BeginPlay` to call:
- `Geppetto URL Player Initialize` or `SoundWave Player Initialize`
- `Geppetto Player Component Initialize`

### Phoneme Generation

Trigger one of the following nodes during gameplay:
- `Generate Phonemes (URL)`
- `Generate Phonemes (SoundWave)`
- `Generate Phonemes (PCM bytes)`
- `Generate Phonemes (multipart/form-data)`

Once the API returns phonemes and emotions:
- Use `Play` on the corresponding Player
- Optionally apply delay

---

## 3.3 Change Emotions

To change a character's emotion dynamically:

Use the `Change Emotion` node from the `Geppetto Player Component`.

- 📝 Emotion must exist in your Emotion Data Table.
- 🎚️ Set intensity (0–100)
- 🕒 Set transition time (in seconds)
- 🧮 Choose transition function (ease, cubic, custom…)

You can also use **tags** in the sentence for emotion auto-switching (see 3.5).

---

## 3.4 Play or Loop Micro Expressions

The Geppetto plugin supports both one-time and looping micro-expressions.

Micro Expressions are defined in a Micro Expressions Data Table.

### Nodes

- `Play Micro Expression`
- `Start Micro Expression Loop`
- `Stop Micro Expression Loop`

Each has parameters like:
- Name
- Intensity (0–100)
- Speed
- Time/Intensity/Speed range (for loops)

🔁 Use randomness to make expressions more lifelike!

---

## 3.5 Emotion Tag System

The emotion tag system allows emotion transitions mid-sentence.

### Syntax

<emotion name intensity 80 transition 300 function_type linear>


### Parameters

| Param         | Description                               | Default      |
|---------------|-------------------------------------------|--------------|
| emotion       | Name of the emotion                       | (required)   |
| intensity     | Intensity (0-100)                         | 50           |
| transition    | Transition time in ms                     | 200          |
| function_type | Interpolation function (linear, cubic…)  | cubic        |

### Example

Today I feel <emotion happy intensity 90 transition 250 function_type ease>great!

You can mix tags with runtime Blueprint emotion changes for full control.

# Geppetto UE 2.0.0 – API Reference

This chapter documents all the components, nodes, structures, enums, and tools provided by the Geppetto plugin.

---

## 4.1 Geppetto Base Component

The abstract component inherited by other Players (SoundWave, URL). Responsible for triggering:
- `OnPhonemeChanged`
- `OnEmotionChanged`

> ⚠️ Must be subclassed to implement playback time synchronization.

### Main Methods

- `Set Remaining` – Updates the list of phonemes/emotions and resets time.
- Variables:
  - `Is Processing`
  - `Remaining Phonemes`
  - `Remaining Emotions`
  - `Current Play Time`

---

## 4.2 Geppetto SoundWave Player

Synchronizes a SoundWave audio file with phonemes/emotions.

### Initialization
Use `Initialize` and pass in the `Audio Component`.

### Playback
- `Play Data Asset`
- `Play` (manual override with raw values)

> Inherit from Base Component, so you also get phoneme/emotion events.

---

## 4.3 Geppetto URL Player

Used to stream and animate lip sync from a URL.

### Initialization
- Requires a `Media Sound Component`

### Playback
- `Play`
- Pass sentence, URL, format, amplitude range, silence thresholds, etc.

---

## 4.4 Geppetto Player Component

This is the animation component: it applies morph target values.

### Initialization
- Requires a Skeletal Mesh + Geppetto Data Tables:
  - Phoneme
  - Emotion
  - Micro Expression

### Advanced Nodes

- `Set Morph Target (override)` & `Morph Target Exist`
- `Change Emotion`, `Play Micro Expression`
- `Start/Stop Micro Expression Loop`
- `Set Mesh`, `Set Player`, `Set Tables`
- `Set Emotion Custom Curve`

---

📘 For Metahuman:
Override `Set Morph Target` using your custom animation logic!

---

### 4.4.2 Initialize

This node is used to initialize the component and should be called in your Blueprint `BeginPlay` event. The following elements can be specified in the node parameters:

#### Parameters

- **Geppetto SoundWave / URL Player**  
  The Geppetto Player used to synchronize animations with the audio. This can either be a `GeppettoSoundWavePlayer`, a `GeppettoURLPlayer`, or any subclass of `GeppettoBaseComponent`.

- **Mesh**  
  The `Skeletal Mesh Asset` that the component will use to change morph target values and perform phonemes, emotions, and micro expressions animations.

- **Phoneme Table**  
  The Geppetto Phoneme Table used by the component.  
  ➤ For Metahuman, please use the included Data Table named `MH_PhonemesTable`.

- **Emotion Table**  
  The Geppetto Emotion Table used by the component.  
  ➤ For Metahuman, use `MH_EmotionsTable`.

- **Micro Expressions Table**  
  The Geppetto Micro Expressions Table used by the component.  
  ➤ For Metahuman, use `MH_MicroExpressionsTable`.

- **Override Animation**  
  If **unchecked**, the Morph Target values used by the Geppetto plugin will be blended with those coming from animations.  
  ➤ For Metahuman, this option **must be checked**.

> 💡 If you cannot see the included Geppetto Data Tables, click the settings icon (top-right in the Asset browser) and ensure that:
> - “Show Plugin Content”
> - “Show Engine Content”  
> are **both checked**.

## 4.4.3 Set Mesh with Morph Targets

Use this node to change the Skeletal Mesh used by the Geppetto Player Component after initialization:

- **Mesh**  
  The Skeletal Mesh Asset that the component will use to change morph target values and perform lip sync, emotions, and micro expressions animations.

- **Return value**  
  Returns `true` if the mesh was successfully updated, `false` otherwise.

---

## 4.4.4 Set Geppetto Player

Use this node to change the Geppetto Player used by the component after initialization. It can be a `GeppettoSoundWavePlayer`, `GeppettoURLPlayer`, or any subclass of `GeppettoBaseComponent`.

- **Geppetto SoundWave Player**  
  The Geppetto Player attached to the component.

---

## 4.4.5 Set Phoneme Table

Use this node to change the Geppetto Phoneme Data Table used by the Geppetto Player Component after initialization:

- **Phoneme Table**  
  The Geppetto Phoneme Table used by the component.

- **Return value**  
  Returns `true` if the table has been updated, `false` otherwise.

---

## 4.4.6 Set Emotion Table

Use this node to change the Geppetto Emotion Data Table used by the Geppetto Player Component after initialization:

- **Emotion Table**  
  The Geppetto Emotion Table used by the component.

- **Return value**  
  Returns `true` if the table has been updated, `false` otherwise.

---

## 4.4.7 Set Micro Expressions Table

Use this node to change the Geppetto Micro Expressions Data Table used by the Geppetto Player Component after initialization:

- **Micro Expressions Table**  
  The Geppetto Micro Expressions Table used by the component.

- **Return value**  
  Returns `true` if the table has been updated, `false` otherwise.

---

## 4.4.8 Set Emotion Custom Curve

Use this node to set the custom emotion transition function behavior when used by the Geppetto Player Component:

- **Function**  
  The function name to set the behavior.

- **Curve**  
  The function evaluation curve. Must be in the range 0–1 for both time and value (X and Y axis).

> Note: The behavior for the following functions is already defined and cannot be changed: Linear, Ease, Ease-in, Ease-out, Ease-in-out, and Cubic.


## 4.4.9 Change Emotion

Use this node to change the current emotion pose dynamically. For more details, see section 3.3 - Change Emotions.

- **Emotion**  
  Use the `GeppettoEmotion` structure.

---

## 4.4.10 Play Micro Expression

Use this node to play a micro expression one time. For more info, see section 3.4 - Play or Loop Micro Expressions.

- **Name**  
  The micro-expression name (must exist in the Micro Expressions Data Table).

- **Intensity**  
  Intensity value from 0 to 100.

- **Speed**  
  Playback speed of the micro-expression animation (must be greater than 0).

---

## 4.4.11 Start Micro Expression Loop

Use this node to play a micro expression repeatedly.

- **Name**  
  The micro-expression name.

- **Time range**  
  The time range between the execution of two micro-expressions. After each play, a random time between min and max is selected.

- **Intensity range**  
  The random intensity range for each play (min to max).

- **Speed range**  
  The random playback speed range for each play (min to max).

---

## 4.4.12 Stop Micro Expression Loop

Use this node to stop looping a micro expression.

- **Name**  
  The micro-expression name.

---

## 4.4.13 Set Morph Target (override)

This node is used by the Geppetto Player Component to change Skeletal Mesh Morph Target values. If your mesh does not use the standard `Set Morph Target` node, override this node.

- **Morph Target Name**  
  The morph target to modify.

- **Value**  
  The new morph target value (including values from animation if Override Animation was unchecked).

---

## 4.4.14 Morph Target Exist (override)

This node checks if a morph target exists on the Skeletal Mesh. If the mesh does not use standard nodes for getting morph targets, override this node.

- **Morph Target Name**  
  The morph target to check.

- **Return Node - Exist**  
  Return `true` if the morph target exists and can be updated, else `false`.

## 4.5 Geppetto Sequencer Component

The **Geppetto Sequencer Component** is used to synchronize a facial animation sequence and an audio source (SoundWave or Media Sound) with Unreal's Level Sequencer.

You can use this component in place of real-time playback nodes when you want to:

- Preview and keyframe the animation in the editor
- Export pre-defined lip sync + emotion animations for cinematic use
- Bake facial animation for render/export

### Required setup

Your Blueprint actor must include:

- A Skeletal Mesh Component
- A Geppetto Sequencer Component

Optional:
- An Audio Component (if using SoundWave)
- A Media Sound Component (if using a URL audio stream)

### Initialization (BeginPlay)

Call the `Initialize` node with:

- Geppetto Data Asset or Geppetto Sequencer Asset
- Optional: audio override
- Optional: delay

### Playback (Sequencer)

You can trigger animation from the Level Sequencer using the `Play` node.

This will:

- Apply the lip sync animation to the Skeletal Mesh
- Optionally start the audio

> 🛠️ You can preview the animation in the editor if “Auto Play” is enabled and `Play()` is triggered via Sequencer tracks.

---

## 4.5.1 Play (Geppetto Sequencer)

This node is used to start playback of the Data Asset within the Sequencer.

### Parameters:

- **Geppetto Data Asset**  
  The asset containing phonemes, emotions and micro expressions.

- **SoundWave / Media URL** *(optional)*  
  Audio playback can be overridden if needed.

- **Delay**  
  Optional offset in seconds to sync audio and animation.

---

## 4.5.2 Stop

Use this node to stop the Geppetto Sequencer animation manually.

---

## 4.5.3 Reset Emotion

Use this node to reset any currently active emotion to **neutral** after playback is finished.

> ✅ Recommended for cinematic sequencing: add a Reset track after a talking shot.

---

## 4.5.4 Set Skeletal Mesh

Changes the Skeletal Mesh used for the playback (typically used in MetaHuman scenarios).

---

## 4.5.5 Set Data Tables

Allows you to override the phoneme/emotion/micro-expr tables after initialization.



## 4.5 Geppetto Phoneme Data Table

The Geppetto Phoneme Data Table contains all information related to phoneme (lip sync) animation. Each phoneme associates with a list of Morph Targets and their values. You can create your own Data Tables to animate any Skeletal Mesh with custom facial controls.

### Create from scratch

1. In the Content Drawer (Ctrl+Space), right-click where you want to create the Data Table:  
   `Miscellaneous > Data Table`

2. On the Pick Row Structure window, select `GeppettoPhonemeTableRow` and click **OK**.

3. Name the Data Table and add a row for each phoneme. Rename each row name to match the phoneme name.  
   The default Metahuman phonemes are:  
   `A, E, I, O, U, PP, FF, TH, DD, KK, CH, SS, NN, RR, HH` (15 phonemes)

4. For each phoneme, add Morph Target values representing the pose at amplitude 100.

> Note: No visual preview of Morph Targets is currently available in the editor but coming soon.

### Add/Edit from existing

You can find pre-made Phoneme Data Tables for the Demo Scene and Metahuman characters under:  
`All > (Engine) > Plugins > Geppetto Content > Phonemes`

Duplicate and edit as needed.

### Import from JSON/CSV

Unreal Data Tables can be imported from JSON or CSV files (JSON recommended). The structure is a list of phoneme objects with Morph Target dictionaries.

### Export as JSON/CSV

Right-click the Data Table asset and choose **Export as JSON** or **Export as CSV**.

---

## 4.6 Geppetto Emotion Data Table

Contains info related to emotion animations. Each emotion associates with Morph Targets and their values.

### Create from scratch

1. In Content Drawer, create new Data Table selecting `GeppettoEmotionTableRow`.

2. Name rows with emotion names like "Happy".

3. Set Morph Target values for the emotion at intensity 100.

4. Optional:  
   - Lip Sync Morph Targets Override (to reduce smile during speech)  
   - Lip Sync Morph Targets Override Transition Time Range

### Add/Edit from existing

Pre-made tables under:  
`All > (Engine) > Plugins > Geppetto Content > Emotions`

### Import/Export JSON same as phonemes.

---

## 4.7 Geppetto Micro Expressions Data Table

Contains info related to micro expressions animation. Each row defines a micro expression with Morph Targets and values.

### Create from scratch

1. Create new Data Table selecting `GeppettoMicroExpressionTableRow`.

2. Add rows named like "Blink".

3. Set Morph Target values for fixed and/or dynamic Morph Targets.

- Fixed Morph Targets: static values at intensity 100.  
- Dynamic Morph Targets: min and max ranges for random values each play.

### Add/Edit from existing

Pre-made tables under:  
`All > (Engine) > Plugins > Geppetto Content > MicroExpressions`

### Import/Export JSON like above.

---

## 4.8. Geppetto Blueprint Library (Editor only)

The following functions can only be used in Editor-only assets, such as Editor Utility Widget or Editor Utility Blueprint. Please note that the following functions are declared in C++.

---

### 4.8.1. Generate phonemes (using SoundWave)

Generate the phonemes for the given audio and sentence.  
👉 THIS IS THE EDITOR-ONLY FUNCTION. FOR RUNTIME, SEE: `Generate phonemes (using SoundWave)` in section 4.9.

#### Parameters

- **Audio**  
  The audio SoundWave asset. See section 3.1.1 for more details.

- **Sentence**  
  The sentence spoken in the audio. Can include emotion tags (see section 3.3).

- **Format**  
  The file format: WAV, MP3, etc.

- **Amplitude range**  
  Min/Max values to define the intensity of phonemes animation.

- **Silence threshold**  
  The minimum dB value to consider sound as silence. Use to ignore background noise.

- **Emotion detection**  
  If enabled, the system will try to detect emotion automatically using a deep learning model.

---

### 4.8.2. Save Geppetto Phonemes

Save the generated phonemes as a `Geppetto Data Asset` or as a Sequencer track.

#### Parameters

- **Save file as**  
  Choose between `DataAsset` or `Sequencer`.

- **Save file at**  
  Path where the `.uasset` file will be saved.

---

### 4.8.3. Show save file selection dialog

Display the file dialog to choose a location for saving the phoneme asset.

---

### 4.8.4. Get Documentation URL

Open the plugin's documentation link in your web browser.


## 4.9. Geppetto Blueprint Library

The following functions can be used in both runtime and editor assets, such as Blueprint classes. Please note that the following functions are declared in C++.

---

### 4.9.1. Generate phonemes (using URL)

Generate the phonemes for the given audio and sentence. The audio file is available through a publicly accessible URL. The audio must be in wav format (PCM16 recommended) :

#### Parameters

- **URL**  
  The audio URL. See section 3.2 for more details.

- **Sentence**  
  The sentence spoken in the audio. Can include emotions tags. Please see section 3.3 for more details.

- **Format**  
  The phoneme format returned by the API. Please read section 4.11.2 for more details. Default is “Metahuman”.

- **Min Ampl**  
  The minimum amplitude value (range 0 - 100). Default is 30.

- **Max Ampl**  
  The maximum amplitude value (range 0 - 100). Must be higher or equal to MinAmpl. Default is 60.

- **Silence Threshold**  
  The threshold used to identify audio silences. Default is -50dB.

- **Silence Time**  
  The minimum silence time duration to be considered as a pause, in milliseconds. Default is 250ms.

- **Logs**  
  Indicate if logs should be printed to the console. Default is true.

- **On Response**  
  The delegate event called when a response was received from the API.

---

### 4.9.2. Generate phonemes (using SoundWave)

Generate the phonemes for the given SoundWave and sentence.

#### Parameters

- **Audio**  
  The SoundWave used for phoneme generation.

- **Sentence**  
  The sentence spoken in the audio.

- **Format**  
  See section 4.11.2.

- **Min Ampl**, **Max Ampl**  
  Range of phoneme amplitude (0–100).

- **Silence Threshold**, **Silence Time**  
  Silence detection parameters.

---

### 4.9.3. Generate phonemes (using PCM bytes)

Generate the phonemes using a PCM raw byte buffer and sentence.

---

### 4.9.4. Generate phonemes (using multipart/form-data)

Same as the other phoneme generation nodes, but uses the `multipart/form-data` format required by some APIs.

---

### 4.9.5. Apply Delay (Phonemes)

Applies a delay to the list of phonemes returned by the API.

---

### 4.9.6. Apply Delay (Emotions)

Applies a delay to the list of emotions returned by the API.

---

### 4.9.7. Get Morph Targets for Phoneme

Returns the Morph Targets and corresponding values for a phoneme name from a given Phoneme Table.

---

### 4.9.8. Safe Lerp

Safe linear interpolation with clamping. Used internally to blend values without exceeding limits.

## 4.10. Data Assets

A Data Asset is an Unreal Asset used to store Data. The Geppetto Plugin uses custom defined Data Assets written in C++.

---

### 4.10.1. Geppetto Data Asset

Geppetto Data Assets are used to store and save the generated phonemes and emotions generated from the API within the Editor in order to use them in the game later. You can use the Geppetto SoundWave Player node `Play Data Asset` to animate the data contained in the Data Asset. All fields are Blueprint Read-Only, but you can use the node `Save Geppetto Phonemes (as Asset)` to create a new Data Asset with Blueprint. Please note that the node is only available within the Editor.

#### Fields

- **Audio**  
  The audio associated with the lip sync.

- **Sentence**  
  (Info only) The sentence used for generation.

- **Min Ampl**  
  (Info only) The minimum amplitude value used for generation.

- **Max Ampl**  
  (Info only) The maximum amplitude value used for generation.

- **Silence Threshold**  
  (Info only) The silence threshold value (dB) used for generation.

- **Silence Time**  
  (Info only) The silence time (in milliseconds) used for generation.

- **Delay**  
  (Info only) The delay applied to phonemes and emotions after generation.

- **Phonemes**  
  The phonemes list generated by the API, used to animate lip sync.

- **Emotions**  
  The emotions list generated by the API, used to animate emotions.

---

### 4.10.2. Geppetto Sequence

A `GeppettoSequence` is a custom asset that contains all the assets and logic to play a lip-sync animation in one file. This asset contains a `LevelSequence` with a timeline for the audio file and a timeline for each `Morph Target` with their amplitude represented as a curve. That is the main element of this asset as it handles all the logic of the lip-sync animation to play on a character.

The `GeppettoSequence` asset can also be edited inside a custom editor which allows you to see the render of the lip-sync animation in a preview scene with the selected mesh. Here is an overview:

## 4.11. Enums

Here you can find the list and values of all enums defined by the Geppetto Plugin.

---

### 4.11.1. Geppetto Emotion Transition

This enum is used to choose the emotion transition each time the emotion pose changes. Users can use their own defined function behavior by using the Geppetto Player Component node `Set Emotion Custom Curve`.

- **Linear**  
  Use linear interpolation.

- **Ease**  
  Easing interpolation.

- **Ease-In**  
  Easing in only interpolation.

- **Ease-Out**  
  Easing out only interpolation.

- **Ease-In-Out**  
  Easing in and out interpolation. Similar to Ease.

- **Cubic**  
  Cubic interpolation. Similar to Ease-In-Out and Ease.

- **CUSTOM 1-10**  
  Custom interpolation. See `Set Emotion Custom Curve`.

---

### 4.11.2. Geppetto Format

The phoneme format used by the Geppetto Plugin. The format is passed as a string in the generation function. Here are the available formats:

- **Metahuman**  
  This is the default format. The Metahuman phoneme set is:  
  `A, E, I, O, U, PP, FF, TH, DD, KK, CH, SS, NN, RR, HH`

- **Papagayo**  
  The Papagayo format is compatible with open-source 2D animation software (e.g. Blender's Papagayo add-on).

- **English (Grapheme)**  
  Uses grapheme-level units instead of phonemes. Still in testing.

- **Custom**  
  You can define your own set of phonemes. Please contact us to configure this.

## 4.12. Structs

Here you can find the list and details of all structs defined by the Geppetto Plugin.

---

### 4.12.1. Geppetto Phoneme

A struct containing all parameters to play a Geppetto Phoneme. All variables are Blueprint read-write:

- **Name**  
  The phoneme name.

- **Amplitude**  
  The phoneme amplitude, range 0 - 100.

- **Time**  
  The phoneme animation play time, matching the audio for synchronization. 

---

### 4.12.2. Geppetto Emotion

A struct containing all parameters to play a Geppetto Emotion. All variables are Blueprint read-write:

- **Name**  
  The emotion name.

- **Intensity**  
  The emotion intensity, range 0 - 100.

- **Transition time**  
  The emotion transition time, in seconds.

- **Transition function**  
  See Geppetto Emotion Transition.

- **Time**  
  The emotion animation play time, matching the sentence tag for sync.

---

### 4.12.3. Geppetto Micro Expression

A struct containing all parameters to play a Geppetto Micro Expression. All variables are Blueprint read-write:

- **Curve**  
  The curve used to determine the micro expression animation time as well as the animation transition interpolation evaluation. Please note that the curve must be of type “Float”.

- **Transition Morph Targets**  
  The micro expression Morph Targets and their values used to animate the micro expression.

- **Current Tick Morph Targets**  
  The micro expression current tick Morph Targets values used. This is managed by the Geppetto Player Component.

- **Speed**  
  The micro expression animation speed. Must be greater than 0.

- **Is Animating**  
  Indicate if the micro expression is currently being animated or not (not started, finished). Managed by the Geppetto Player.

- **Time**  
  The micro expression animation play time. *(Unused for now)*

---

### 4.12.4. Dynamic Micro Expression

A struct containing all values related to dynamic Micro Expression Morph Targets. Used in Micro Expression Data Table:

- **Morph Targets**  
  The dynamic Morph Targets names.

- **Value Rang**  
  The dynamic Morph Target min and max values.

---

### 4.12.5. Tuple Float

Since Unreal `FTuple<float>` is not supported in Blueprint yet, this struct is used instead.

- **First**  
  The tuple first value, i.e: the min value or the begin time.

- **Second**  
  The tuple second value, i.e: the max value or the end time.

## 5. Resources & General explanations

---

### 5.1. How does the Geppetto model work?

---

#### Text Acquisition

The text can either be provided directly or generated through Speech-to-Text, which also captures onomatopoeia. For the best results, it is recommended to provide a text that explicitly includes onomatopoeia. Emotion tags associated with the text are also extracted.

---

#### Silence Detection

Silences in the audio serve as markers to define the start and end of the text. The automatic detection of silence depends on the type of audio:

- For synthetic voices, -50 dB silence threshold and 200 ms silence time are recommended.  
- For noisier recordings, -40 dB and 300 ms may be more suitable.

These parameters should be adjusted based on the characteristics of the audio recording.

---

#### Text-to-Phoneme Conversion

The text is converted into phonemes using a machine learning model. This model is language-sensitive, and currently, Geppetto supports English, French, German, Italian, and Spanish.  
If additional language support is needed, please contact us.

---

#### Alignment with Audio: Two Model Approaches

There are two types of models available:

---

##### Model 0 (Fast)

This is a machine learning model that aligns silences in the audio with punctuation in the text. Using linear interpolation between the segmented text and audio, it predicts the most probable phonemes for each sequence and assigns a corresponding timestamp based on its position in the text. 

- **Advantage**: This method is fast and requires minimal computing power, making it ideal for real-time applications.  
- **Limitation**: Since it relies on a simple mapping strategy, it may not perfectly capture variations in speech rhythm or nuanced pronunciations.

---

##### Model 1 (Accurate)

This model employs deep learning for a more precise alignment:

- The input audio is converted into a spectrogram.  
- Phonemes from Step 3 are aligned with the silences detected in Step 2.  
- The energy patterns of the spectrogram are matched with the corresponding phonemes.

This approach is highly effective when the audio and text are perfectly synchronized. However, if there are discrepancies, the model might skip or replace onomatopoeia.

- **Advantage**: This model provides high accuracy, making it ideal for cases requiring precise phoneme timing.  
- **Limitation**: It is computationally intensive, requiring more processing power than Model 0.

For both models, each phoneme is assigned an amplitude derived from the audio signal.

---

> Both models are available via API, but local deployment is possible for real-time applications. Please contact us for more details.

## 5.1 Amplitude Calculation

The minimum amplitude is set as the lower bound between 0 and 100, based on the detected phoneme amplitude. This ensures that the phoneme remains visible during execution, even when its natural amplitude is very low.

Similarly, the maximum amplitude acts as an upper limit to prevent excessive deformation of blendshapes, maintaining more natural transitions.

The amplitude sinus step defines the incremental step between two consecutive phonemes' amplitudes, preventing abrupt jumps. This value ranges between 0 and 1:

- The closer it is to 1, the more significant the amplitude variations between phonemes can be.
- Lower values ensure smoother transitions, reducing sudden amplitude shifts.

## 6. Adding Emotion Tags

Emotion tags are integrated into the audio at the appropriate timestamps based on their placement within the sentence, ensuring that the speaker’s tone and emotional expression are accurately reflected.

You can also enable the automatic emotion detection parameter. Using a deep learning model, it predicts the most appropriate emotion based on both the text and the audio.

Disable this option if you prefer maximum control and optimized performance speed.

---

## 7. Output

The final output is a structured list of (phoneme, timestamp, amplitude). This list is returned via API, but the computation can also be performed locally for real-time deployment in player environments. Please contact us for this option.

---

## Geppetto Blueprint

Demo blueprint:  
👉 [https://blueprintue.com/blueprint/oczerzxz/](https://blueprintue.com/blueprint/oczerzxz/)

---

## Known bugs

**The plugin shows control-related errors**

If some controls used (named like `CTRL_expressions_…`) are missing in the MetaHuman and you have error messages when you try to initialize the Geppetto Player Component, it is probably due to the MetaHuman version.

✅ Make sure that you have downloaded the MetaHuman with the same Unreal Engine version that you are using for your project.

- MetaHumans downloaded with **UE5.0 and 5.1** are compatible with **UE5.0, 5.1 and 5.2**
- MetaHumans downloaded with **UE5.2 and 5.3** are compatible with **UE5.2 and 5.3**

📺 If the error remains, please watch this tutorial video and ensure that you have done all the steps correctly.
