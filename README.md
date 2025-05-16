
# Geppetto UE 2.0.0 – Setup

![Logo](./docs/images/General_image_1.png)

Welcome to the **Geppetto UE Plugin** for Unreal Engine. This document will show you how to use the plugin in Unreal Engine*.

> 📧 *Please note that this notice assumes familiarity with Unreal Engine terminology and workflows. For more detailed information and examples, refer to the accompanying documentation or consult the provided links.*   
*If you have any questions, feel free to contact us: contact@xandimmersion.com*

## 1.1 Prerequisites

There are two versions of the plugin:
- ✅ **Compiled plugin** (for UE 5.2, 5.3, 5.4, and 5.5)
- 🛠️ **Uncompiled plugin** (for UE 5.0 to 5.4)

> ⚠️ *If you download the uncompiled version of the plugin, you must be able to compile C++ code for Unreal Engine. To do so, you need the Visual Studio build tools for Unreal Engine installed as well as the .NET SDK ! You can find more information on how to set up Visual studio for Unreal engine [here](https://dev.epicgames.com/documentation/en-us/unreal-engine/setting-up-visual-studio-development-environment-for-cplusplus-projects-in-unreal-engine).*


*To ensure that you have all build tools installed, try to create a new C++ Unreal Project and make sure that the Editor starts correctly. Once the editor is open, click on the compile button on the bottom right corner and ensure that the compilation succeeded*

![Option C++ to choose](./docs/images/Prerequisites_image_1.png)
![Compile button and expected result](./docs/images/Prerequisites_image_2.png)


## 1.2 Metahuman

To use the Geppetto plugin with Metahuman, follow these links to configure your project:

- [Download & Export Metahumans - Quixel Bridge](https://dev.epicgames.com/documentation/en-us/metahuman/downloading-and-exporting-metahumans/quixel-bridge)
- [Downloading Metahumans](https://dev.epicgames.com/documentation/en-us/metahuman/downloading-and-exporting-metahumans/downloading-metahumans)
- [Requirements & Configuration](https://dev.epicgames.com/documentation/en-us/metahuman/downloading-and-exporting-metahumans/requirements-and-configuration-settings)
- [Using with Unreal Engine 5](https://dev.epicgames.com/documentation/en-us/metahuman/downloading-and-exporting-metahumans/unreal-engine-5)

## 1.3 Installation – Fab

If you bought the plugin through Fab, you can simply click on “Install to engine” plugin button. All plugins are located in the Vault, at the bottom of the Library:

![Where to find the plugin in the Vault](./docs/images/Installation_Marketplace_image_1.png)

Then, open your project and navigate to Edit > Plugins. Search “Geppetto” and ensure that the plugin is enabled.

![In the Plugin Settings, ensure that the checkbox is checked](./docs/images/Installation_Marketplace_image_2.png)

## 1.4 Installation – Source Code

1. ❌ **Close the unreal engine project where you want Geppetto to be installed !**

2. 📦 Extract the content of the plugin `.zip` archive.
3. 📁 Paste the extracted folder into the root of your project directory.

![Where to paste the extracted file](./docs/images/Installation___Source_code_image_1.png)

4. ▶️ Reopen the project by right-clicking on `<YourProject>.uproject` and choosing **Open**.

![Right click then "Open"](./docs/images/Installation___Source_code_image_2.png)

5. ✅ If prompted with “Missing Modules”, click **Yes**.

![Window of Missing Modules](./docs/images/Installation___Source_code_image_3.png)

> 🧠 If you see “Could not be compiled. Try rebuilding from source manually”, make sure your Visual Studio and SDKs are correctly installed.

6. Once the project is open, Navigate to `Edit > Plugins` in the Unreal Editor.
7. Search for “Geppetto” and ensure the plugin is enabled.

![Expected result when looking for Geppetto in the Plugin window](./docs/images/Installation___Source_code_image_4.png)


---


# Geppetto UE 2.0.0 – Demo

The Geppetto plugin comes with a demo level and a skeletal mesh with morph targets, thanks to [Rigged T-Pose Human Male w 50 Face Blendshapes](https://sketchfab.com/3d-models/rigged-t-pose-human-male-w-50-face-blendshapes-cc7e4596bcd145208a6992c757854c07) by Mike Alger, licensed under [Creative Commons Attribution](https://creativecommons.org/licenses/by/4.0/).

## 2.1 How to Open the Demo Level

1. 🎮 Open or create a project with the Geppetto plugin installed.
2. 🧰 Open the **Content Drawer** (`Ctrl + Space`) and go to **Settings** (top-right corner).
3. ✅ Ensure the following options are enabled:
   - “Show Plugin Content”
   - “Show Engine Content”

![Show where is the Engine and Plugin Content options](./docs/images/How_to_open_the_demo_level_image_1.png)

4. 📂 Navigate to the appropriate folder:
   - **Marketplace install**: `All > Engine > Plugins > Geppetto Content > GeppettoExampleScene`
   - **Source install**: `All > Plugins > Geppetto Content > GeppettoExampleScene`

![Path to the GeppettoExampleScene in Unreal](./docs/images/How_to_open_the_demo_level_image_2.png)

5. ▶️ Open the level and press **Play**.
6. 🕹️ Use number keys (`1` to `0` or numpad) to test the Geppetto Plugin.

![Where to find the Play button](./docs/images/How_to_open_the_demo_level_image_3.png)

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

![Where to find the GeppettoExampleActor in the Outlier](./docs/images/Understand_the_demo_level_image_1.png)

![Click on the EventGraph tu unfold all the available graphs](./docs/images/Understand_the_demo_level_image_2.png)

You’ll see a block for each key event and `BeginPlay`.

![Example of BeginPlay block](./docs/images/Understand_the_demo_level_image_3.png)

![Screen of the various Blueprint nodes available in this example actor](./docs/images/Understand_the_demo_level_image_4.png)

### 2.3.1 Components Required

Every actor using the plugin must have these 4 components:

- ✅ A Skeletal Mesh with Morph Targets
- 🔊 An Audio or MediaSound Component
- 🧠 A [Geppetto Player Component](#43-geppetto-player-component) (e.g., DemoPlayer)
- 📡 A [Geppetto SoundWave Player](#42-geppetto-soundwave-player)

![Components you should have](./docs/images/Components_image_1.png)

The Audio/MediaSound Component and the Geppetto SoundWave/URL Player used will depend if the plugin is used with pre-generated or runtime assets. You can use both methods on the same character.

### 2.3.2 Begin Play

In the BeginPlay Event, all Geppetto components are initialized. You can find more information about component initialization below:

- `Geppetto SoundWave Player Initialize`
- `Geppetto URL Player Initialize`
- `Geppetto Player Initialize`

![Path to the GeppettoExampleScene in Unreal](./docs/images/Begin_Play_image_1.png)

The Geppetto Player initialize node uses a Phoneme, Emotion and Micro Expression table as parameters to animate the character. You can create your own table in order to animate characters with custom Morph Targets. 

Please read section [4.5](#45-geppetto-phoneme-data-table), [4.6](#46-geppetto-emotion-data-table) and [4.7](#47-geppetto-micro-expressions-data-table) for more details.


### 2.3.3. Phonemes / Lipsync

The **keyboard 1 and 2** events are related to pre-generated phonemes.


- Please read section [3.1.1 - Pre-Generated Phonemes generation](#311-pre-generate-phonemes-as-a-geppetto-data-asset) of the documentation for more information on how to pre-generate phonemes in a Data Asset using the Geppetto Editor Interface.

- Please read section [3.1.2 - Play animation with SoundWave](#312-play-a-geppetto-data-asset-with-soundwave) of the documentation for more information on how to play the Geppetto phonemes from a Data Asset

- Please read section [4.10.1 - Geppetto Data Asset](#4101-geppetto-data-asset) of the documentation for more information about the Geppetto Data Asset structure

![](./docs/images/Phonemes___Lipsync_image_1.png)

The **keyboard 9 and 0 events** are related to runtime phonemes.

- Please read section [3.2 - Runtime Phoneme Generation](#32-runtime-phonemes-generation-and-animation-blueprint) of the documentation for more information on how to generate and play runtime generated phonemes.
- Please read section [4.9.1 - Generate phonemes (using SoundWave)](#492-generate-phonemes-using-soundwave) for more
information on how to generate phoneme from a local audio file (SoundWave, PCM or file)

![](./docs/images/Phonemes___Lipsync_image_2.png)


The plugin uses a [Geppetto Phoneme Data Table](#45-geppetto-phoneme-data-table) to know all Morph Targets values for each phoneme. If the skeletal mesh of your characters have different Morph Targets, it is required to create a new [Geppetto Phoneme Data Table](#45-geppetto-phoneme-data-table) with the Morph Targets used in your characters.     
**Please note that Data Tables for Metahuman are included in this plugin !**   
The Data Table used by the plugin is passed through the [Geppetto Player Component Initialize](#442-initialize) or [Set Phoneme Table](#445-set-phoneme-table) node. Please read section [4.5 - Geppetto Phoneme Data table](#45-geppetto-phoneme-data-table) of the documentation for more information about phoneme Data Table.

### 2.3.4. Emotions

The **keyboard 3 and 4 events** are related to emotions.

- Please read section [3.3 - Change Emotions](#33-change-emotions) for more information on how to change emotions in Blueprints.
- Please read section [3.5 - Emotion Tag System](#35-emotion-tag-system) for more information on how to change emotions with tags.
- Please read section [4.12.2 - Geppetto Emotion](#4122-geppetto-emotion) of the documentation for more information about the Geppetto emotion structure.
- Please read section [4.4.7 - Set Emotion Custom Curve](#448-set-emotion-custom-curve) of the documentation for more information about the emotion custom transition curves.

![](./docs/images/Emotions_image_1.png)

The same way as phonemes, emotions use a [Geppetto Emotion Data Table](#46-geppetto-emotion-data-table) to determine the Morph Target values for each emotion. Please read section [4.6 - Geppetto Emotion Data Table](#46-geppetto-emotion-data-table) of the documentation for more information.

### 2.3.5. Micro Expressions

The **keyboard 5, 6, 7 and 8 events** are related to micro expressions.

- Please read section [3.4 - Play or Loop Micro Expressions](#34-play-or-loop-micro-expressions) of the documentation for more information on how to use micro expressions.
- Please read section [4.4.9 - Play Micro Expression](#4410-play-micro-expression) of the documentation for more information about the node.
- Please read section [4.4.11 - Start Micro Expression Loop](#4411-start-micro-expression-loop) and [Stop 4.4.12 - Stop Micro Expression Loop](#4412-stop-micro-expression-loop) of the documentation for more information about the nodes.

![](./docs/images/Micro_Expressions_image_1.png)

Like phonemes and emotions, micro expressions use a [Geppetto Micro Expressions Data Table](#47-geppetto-micro-expressions-data-table) to retrieve the Morph Targets values.   
This time, however, the values can be **static** (like phonemes or emotions Morph Targets values) or **dynamic** (the Morph Targets values will change each time the Micro Expression is played).    
Please read section [4.7 - Geppetto Micro Expressions Data Table](#47-geppetto-micro-expressions-data-table) of the documentation for more information.

# 3 Usage

This chapter provides a complete tour of the Geppetto plugin features available in the Unreal Editor and at runtime.

---

## 3.1 Pre-generated Data Asset (Editor)

### 3.1.1 Pre-Generate Phonemes as a Geppetto Data Asset

If you want to pre-generate phonemes that will be saved as a [Geppetto Data Asset](#4101-geppetto-data-asset), you can use the Editor Utility Widget included in the plugin.     
You can open the Window by clicking on the Geppetto icon button or in the menu **Help > Geppetto**:

![](./docs/images/Pre_Generate_Phonemes_image_1.png)
![](./docs/images/Pre_Generate_Phonemes_image_2.png)

The interface will open. Please see the table on the next page to find more information about all fields.

![](./docs/images/Pre_Generate_Phonemes_image_3.png)

| Icône | Élément                                   | Description                                                                 |
|-------|-------------------------------------------|-----------------------------------------------------------------------------|
| 📘    | **Documentation button**                  | Opens this manual in your browser.                                          |
| 🧠    | **Local model**                           | Define the phoneme generation model (local only).                           |
| 🔊    | **Audio**                                 | The speech SoundWave asset (compatible with Ariel plugin).                  |
| 🔇    | **Remove noise**                          | Helps silence detection and phoneme precision.                              |
| 🧏    | **Use speech recognition**                | Phonemes based only on audio.                                               |
| 🌐    | **Language**                              | Improve accuracy based on speech language.                                  |
| 🗣️    | **Sentence**                              | The sentence being spoken (can include emotion tags).                       |
| 🏷️    | **Add tags to sentence**                 | Insert tags like `<emotion happy>`.                                         |
| 🎭    | **Phonemes & Emotions settings**          | Link to the corresponding Data Tables.                                      |
| 📈    | **Amplitude & sinus steps**               | Control mouth animation intensity.                                          |
| 🕑    | **Silences**                              | Use tools like Audacity to find appropriate silence thresholds.             |
| ⏱️    | **Delay**                                 | Sync delay between audio and animation.                                     |
| 🎞️    | **Sequencer Frame Rate**                 | Higher FPS = better edit control.                                           |
| 👄    | **Close Mouth At End Of Speech**          | Enables auto-mouth closing.                                                |
| 💾    | **Save as**                               | Choose between `Data Asset` or `Sequencer`.                                 |

The Editor Utility Widget uses the nodes [Generate Phonemes](#481-generate-phonemes-using-soundwave) and [Save Geppetto Phonemes](#482-save-geppetto-phonemes) to generate the phonemes and store them for further use.

➡️ Finally, hit the **“Generate Phonemes”** button to generate your .uasset file. **This may take a while according to the
audio duration !**

---

### 3.1.2 Play a Geppetto Data Asset with SoundWave

To play the generated lip-sync and sound :

1. Create a Blueprint class. **If you use Metahuman, you
can use the generated Blueprint class instead** (i.e: *BP_Ada* for the Metahuman named Ada).

![](./docs/images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_1.png)

2. Add the following components :
   - Skeletal Mesh Component
   - Audio Component
   - [Geppetto SoundWave Player](#42-geppetto-soundwave-player)
   - [Geppetto Player Component](#43-geppetto-player-component) (or custom version for Metahuman*)

*If your Skeleton doesn’t use the traditional node “Set Morph Target” to update Morph Target values, like Metahuman characters, you need to override some functions from the Geppetto Player Component, otherwise animation will not work.    
Please read section [4.4.1 - Component Inheritance](#441-component-inheritance) for more information.*

![](./docs/images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_2.png)
![](./docs/images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_3.png)

3. Use `BeginPlay` to initialize with:
   - `Geppetto SoundWave Player Initialize`
   - `Geppetto Player Component Initialize`

   ![](./docs/images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_4.png)

4. Use `Play Data Asset` to start playback.
5. Use `Play` node (advanced) if you want to override audio or delay.

You can use the node *Play Data Asset* from the [Geppetto SoundWave Player](#42-geppetto-soundwave-player) whenever you want in your game in order to play the lip sync animation. 
In the example below, the lip sync starts when the user presses the ‘s’ key (do not forget to enable input on this actor if you plan to do the same). 
*You must provide the Data Asset that you want to play*

  ![](./docs/images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_5.png)

If you want to [Apply Delay](#495-apply-delay-phonemes) to the phonemes or emotions before playing the animation, please use the Geppetto SoundWave Player Play node instead. This node can also be used to change the audio SoundWave played with the Geppetto animation (*not recommended*) :

  ![](./docs/images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_6.png)

---

### 3.1.3 Play a Geppetto Sequence

Same idea as before, but with the **[Geppetto Sequencer Component](#45-geppetto-sequencer-component)** and the generated **[Geppetto Sequence](#4102-geppetto-sequence)** :

1. Create a Blueprint class. **If you use Metahuman, you
can use the generated Blueprint class instead** (i.e: *BP_Ada* for the Metahuman named Ada).

![](./docs/images/Play_a_Geppetto_Sequence_image_1.png)

2. Add the following components :
   - Skeletal Mesh Component
   - [Geppetto Sequencer Component](#45-geppetto-sequencer-component)

*If your Skeleton doesn’t use the traditional node “Set Morph Target” to update Morph Target values, like Metahuman characters, you need to override some functions from the Geppetto Player Component, otherwise animation will not work.    
Please read section [4.4.1 - Component Inheritance](#441-component-inheritance) for more information.*

![](./docs/images/Play_a_Geppetto_Sequence_image_2.png)
![](./docs/images/Play_a_Geppetto_Sequence_image_3.png)

3. Use `BeginPlay` to initialize the [Geppetto Sequencer Component](#45-geppetto-sequencer-component) with `Initialize`.

   ![](./docs/images/Play_a_Geppetto_Sequence_image_4.png)

5. Use `Play` node to start the lip-sync animation. **You must provide the [Geppetto Sequence](#4102-geppetto-sequence) that you want to play.**

  ![](./docs/images/Play_a_Geppetto_Sequence_image_5.png)

---

## 3.2 Runtime Phonemes Generation and Animation (Blueprint)

This setup is used for audio generated during gameplay, such as:
- 🎤 Player microphone input
- 🧠 [Ariel TTS plugin](#https://www.fab.com/listings/7a3354f0-44c7-43ea-8656-23814c9f393d)

### Components

1. Skeletal Mesh Component (with Morph Targets)
2. [Geppetto SoundWave Player](#42-geppetto-soundwave-player)
3. Audio Component
4. [Geppetto Player Component](#43-geppetto-player-component) (or custom one for Metahuman)


If you want to have audio spatialization, check the “Allow Spatialization” box and set a sound attenuation in the Audio Component (you can create a new one if needed) :

![](./docs/images/Runtime_Phonemes_generation_and_animation__Blueprint__image_4.png)
![](./docs/images/Runtime_Phonemes_generation_and_animation__Blueprint__image_5.png)

### Initialization

Use `BeginPlay` to call:
- `SoundWave Player Initialize`
- `Geppetto Player Component Initialize`

![](./docs/images/Runtime_Phonemes_generation_and_animation__Blueprint__image_6.png)

### Phoneme Generation

Whenever you want in your blueprint, i.e: right after the audio file has been generated, call one of the `Generate Phonemes` nodes.    
Trigger one of the following nodes during gameplay:
- `Generate Phonemes (SoundWave)`
- `Generate Phonemes (PCM bytes)`
- `Generate Phonemes (multipart/form-data)`

![](./docs/images/Runtime_Phonemes_generation_and_animation__Blueprint__image_9.png)
![](./docs/images/Runtime_Phonemes_generation_and_animation__Blueprint__image_10.png)

Please note that **it could take up to 15 seconds to generate the phonemes, depending on your audio size and length !**    
For a small file and short sentence (10s or less, <100Kb), the generation should take less than a second.

Once the API returns phonemes and emotions:
- Use `Play` on the corresponding Player
- Optionally apply delay


→ If you use our Ariel plugin to generate the audio files at runtime, please see this example.

| Champ                | Description                                                                                                                                                                                                                                  |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **URL**              | The audio URL of the speech, in wav format.                                                                                                                                                                                                 |
| **Sound Wave**       | The audio SoundWave. It can be a SoundWave procedural. <br><br>⚠️ **WARNING**: If the SoundWave is an asset, double click on it from the Content Drawer to open it and set the Loading Behavior to **Force Inline** !!!                    |
| **File Bytes**       | The audio wav file bytes data. It must have the wave header bytes as well. <br> If you only have the PCM bytes, please use **Generate phonemes (using PCM bytes)** instead.                                                                |
| **Filename**         | The name of the file that will be sent through the form POST request.                                                                                                                                                                       |
| **File Content Type**| The MIME content-type of the audio file. [More information here](#) (tu peux remplacer ce lien par l’URL réelle si besoin).                                                                                                                 |
| **Sentence**         | The sentence(s) spoken in the audio file, including the emotion tags. <br>Refer to section **3.2 - Emotion Tag System** for more info.                                                                                                      |
| **Format**           | Select the phoneme format returned by the API. <br>⚠️ Use **Metahuman** format unless you have a custom Data Table. Even if you don’t use Metahuman characters. See section **4.5 - Geppetto Phoneme Data Table** for details.             |
| **Amplitude**        | Choose the amplitude range for the animation. <br>Higher values = more mouth articulation; Lower values = whisper effect.                                                                                                                   |
| **Silences Detection**| Parameters depending on your recording setup. <br>Use tools like **Audacity** to determine: <br>- **Threshold**: max dB recorded when you're silent. <br>- **Time**: min duration (ms) to count as a silence between phonemes.             |
| **Logs**             | Toggle whether Geppetto logs will be printed to console and/or screen (Debug only).                                                                                                                                                        |
| **Event Binding**    | From the **“On Response”** pin, drag to your Event Graph and select **Add Custom Event** or **Create Event**. You can name the event freely.                                                                                                 |


Drag the mouse from the “On Response” pin and drop it on your Event Graph. You can then select Add Custom Event or Create Event actions, and name the event as you want:

![](./docs/images/Runtime_Phonemes_generation_and_animation__Blueprint__image_11.png)
![](./docs/images/Runtime_Phonemes_generation_and_animation__Blueprint__image_13.png)
![](./docs/images/Runtime_Phonemes_generation_and_animation__Blueprint__image_12.png)
![](./docs/images/Runtime_Phonemes_generation_and_animation__Blueprint__image_14.png)
![](./docs/images/Runtime_Phonemes_generation_and_animation__Blueprint__image_15.png)

---

## 3.3 Change Emotions

The Geppetto plugin also allows you to animate emotion to your character. All emotions must have been defined in the [Emotion Data Table](#46-geppetto-emotion-data-table) used by the [Geppetto Player](#43-geppetto-player-component).   
Please read section [4.6 - Geppetto Emotion Data Table](#46-geppetto-emotion-data-table) for more details about how to create emotion Data Tables.   
**If you use Metahuman characters, you can use the existing Data Table named “MH_Emotions”.**

Emotions can be changed when a sentence is pronounced by using tags. Please read section [3.5 - Emotion Tag System](#35-emotion-tag-system) for more information on how to use tags.    
You can also use the Geppetto Player node `Change Emotion` to change your character emotion at any time you want.

![](./docs/images/Change_Emotions_image_1.png)
![](./docs/images/Change_Emotions_image_2.png)
![](./docs/images/Change_Emotions_image_3.png)



| Champ               | Description                                                                                                                                                                                                                         |
|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Emotion             | The emotion name. The emotion must be defined in the Emotion Data Table.                                                                                                                     |
| Intensity           | The emotion intensity percentage, range 0 - 100.                                                                                                                                               |
| Transition Time     | The switching emotion transition time, in seconds. For example, if the current character emotion is ‘Neutral’, the new emotion passed is ‘Happy’ and the transition time is 0.2s, then the character face will bend from neutral pose to happy pose in 0.2 seconds (200ms). |
| Transition Function | The transition interpolation function used to bend between emotions.                                                                                                                          |
| Time                | This parameter is used for internal purposes and should not be edited. This parameter will be hidden in the future version of the plugin.                                                    |

---

## 3.4 Play or Loop Micro Expressions

All micro-expressions must have been defined in the Micro Expressions Data Table used by the Geppetto Player. For more information about this, please read section [4.7 - Geppetto Micro Expressions Data Table](#47-geppetto-micro-expressions-data-table) of the documentation.    
**If you use Metahuman characters, you can use the existing Data Table named “MH_Emotions”.**

Micro-Expressions can be played in two ways : 

- An **unique** micro-expression
- A micro-expression **loop**. 

For example, you can decide to play a unique blink animation or decide to play a blink animation loop. You can use the Geppetto Player nodes [Play Micro Expression](#4410-play-micro-expression) and [Start Micro Expression Loop](#4411-start-micro-expression-loop) to animate micro-expression on your character.

![](./docs/images/_Play_or_Loop_Micro_Expressions_image_1.png)


### Nodes

- `Play Micro Expression`

| Champ    | Description                                                                                                                                                                                                                                                                                   |
|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name     | The micro-expression name. The micro-expression must have been defined in the Micro Expressions Data Table.                                                                                                                                             |
| Intensity| The micro-expression intensity. Range 0 - 100. For dynamic micro-expressions (i.e: EyeDart), we recommend always setting the intensity to 100.                                                                                                          |
| Speed    | The micro-expression animation playback speed. Must be greater than 0. The speed is related to the micro-expression curve duration defined in the Data Table. See Micro Expressions Data Table “Curve” parameter for more details.                     |


- `Start Micro Expression Loop`

| Champ            | Description                                                                                                                                                                                                                                                                                                                                                                                                     |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name             | The micro-expression name. The micro-expression must have been defined in the Micro Expressions Data Table.                                                                                                                                                                                                                                                              |
| Time range       | The waiting time ranges between the execution of two micro-expressions. The waiting time will be randomly selected after each time the micro-expression is played, between the specified min and max value (set the min and max fields to the same value in order to always have the exact same waiting time).                                                           |
| Intensity range  | The randomly selected intensity that will be used for the execution of each micro-expression. The value will be randomly selected after each time the micro-expression is played, between min and max value (set the min and max fields to the same value in order to always have the exact same intensity).                                                              |
| Speed range      | The randomly selected speed that will be used for the execution of each micro-expression. The value will be randomly selected after each time the micro-expression is played, between min and max value (set the min and max fields to the same value in order to always have the exact same playback speed).                                                            |


- `Stop Micro Expression Loop`

| Champ | Description                     |
|-------|---------------------------------|
| Name  | The micro-expression name.      |



🔁 Use randomness to make expressions more lifelike!

---

## 3.5 Emotion Tag System

The emotion tag system allows you to change the character emotion at a specific point of the sentence. Its base syntax is the following :

### Syntax

`<emotion name intensity 80 transition 300 function_type linear>`


### Parameters

| Param         | Description                               | Default      |
|---------------|-------------------------------------------|--------------|
| emotion       | Name of the emotion                       | (required)   |
| intensity     | Intensity (0-100)                         | 50           |
| transition    | Transition time in ms                     | 200          |
| function_type | Interpolation function (linear, cubic…)  | cubic        |

### Example

![](./docs/images/Emotion_Tag_System_image_1.png)

![](./docs/images/Emotion_Tag_System_image_2.png)

You can mix tags with runtime Blueprint emotion changes for full control.
Please read section [3.3 - Change Emotions](#33-change-emotions) of the documentation for more details on how to change an emotion at Runtime using Blueprints.

---

# Geppetto UE 2.0.0 – API Reference

This chapter documents all the components, nodes, structures, enums, and tools provided by the Geppetto plugin.

---

## 4.1 Geppetto Base Component

The abstract component inherited by other Players (SoundWave, URL). 
It checks on every tick if a phoneme or an emotion should be played based on the current play time.    
The Unreal events `OnPhonemeChanged` and `OnEmotionChanged` are broadcasted each time a phoneme or an emotion needs to be animated. 
> ⚠️ **Please note that the current play time is not updated by the base component itself and should be updated by the subclass component based on the audio playback !**


### `Set Remaining`

Assign a new phonemes and emotions list to the component.
Please note that both lists can be empty.    
The current play time is reseted to 0.0 when the node is called. **The node should not be called by anything other than the child component subclasses.**

![](./docs/images/Set_Remaining_image_1.png)

| Champ    | Description                                                                                                                                                         |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Phonemes | The new phonemes list that will be processed by the component. If there were already phonemes remaining, the previous value will be overwritten.                   |
| Emotions | The new emotions list that will be processed by the component. If there were already emotions remaining, the previous value will be overwritten.                   |


### Variables


| Champ               | Description                                                                                                                                                                                                                           |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Is Processing`       | Set this to true when the base component should start checking if a phoneme or emotion needs to be animated in tick. Will be automatically set to false (in C++) when there are no remaining phonemes and emotions.                |
| `Is Initialized`      | Unused by the Geppetto Base component itself, but can be useful for inherited subclasses.                                                                                                                                            |
| `Remaining Phonemes`  | Read-only variable containing the remaining phonemes for the current speech.                                                                                                                                                         |
| `Remaining Emotions`  | Read-only variable containing the remaining emotions for the current speech.                                                                                                                                                         |
| `Current play time`   | Update this variable according to the audio playback time in order to synchronize the phoneme animation with the audio speech. The variable is not updated by the component itself. Subclasses must update the value. Will be automatically set to 0.0 (in C++) when there are no remaining phonemes and emotions. |

### Events

| Événement                  | Description                                                                                                                                                                                                                                                                      |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `On Phoneme List Changed`   | This event is broadcasted each time the phoneme list has changed, meaning each time the node SetRemaining is called.                                                                                                                     |
| `On Phoneme Changed`        | This event is broadcasted each time a new phoneme needs to be processed with the following phoneme information:<br>- The current Phoneme (with name and amplitude)<br>- The next Phoneme (with name and amplitude)<br>- The current Phoneme play time, in seconds             |
| `On Emotion Changed`        | This event is broadcasted each time a new phoneme needs to be processed with the following emotion information:<br>- The emotion name<br>- The emotion Intensity<br>- The emotion Transition time<br>- The emotion Transition function<br>- The emotion play time, in seconds |


---

## 4.2 Geppetto SoundWave Player

The Geppetto SoundWave Player is a child of the [Geppetto Base Component](#41-geppetto-base-component) class. This component is used to synchronize phonemes/emotions animation from a [Geppetto Data Asset](#410-data-assets) with a SoundWave audio.

![](./docs/images/Geppetto_SoundWave_Player_image_1.png)
![](./docs/images/Geppetto_SoundWave_Player_image_2.png)

**Please note that the Geppetto SoundWave Player does not animate the phonemes and emotions itself, it only does the synchronization between the phonemes and the audio.**    
In order to completely animate phonemes and emotion, please use a Geppetto Player Component in addition. See section [3.1.2 - Play Animation with SoundWave](#312-play-a-geppetto-data-asset-with-soundwave) for more details.


### 4.2.1 `Initialize`

It should be called in ypur Blueprint *BeginPlay* event. Pass in the `Audio Component`.

| Parameter       | Description                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------|
| Audio Component | The audio component that will be used by the SoundWave player to play the audio file.            |


![](./docs/images/Geppetto_SoundWave_Player_image_3.png)

### 4.2.2 `Play Data Asset`

Call this function to perform the lip sync coming from a [Geppetto Data Asset](#4101-geppetto-data-asset). The Data Asset can be be selected directly from within the node or through a variable:

| Parameter   | Description                                                                    |
|-------------|--------------------------------------------------------------------------------|
| Data Asset  | The Geppetto Data Asset that will be played by the SoundWave Player.          |


### 4.2.3 `Play`

You can use the `Play` node to pass all parameters one by one.    
For example, this node can be useful if you want to edit the phonemes /emotions list (i.e.: Apply Delay) or if you want to use a different SoundWave than the one used (i.e.: add some audio effects) above:

![](./docs/images/Play_image_1.png)

| Parameter | Description                                                              |
|-----------|--------------------------------------------------------------------------|
| Audio     | The SoundWave file that will be played by the component.                 |
| Phonemes  | The phonemes list that will be processed by the component. Can be empty. |
| Emotions  | The emotions list that will be processed by the component. Can be empty. |

### 4.2.4 Variables

| Parameter                    | Description                                                                                                           |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------|
| Audio Component             | The audio component reference passed to the SoundWave Player when initializing. Internal use only.                   |
| Current Data                | The DataAsset reference passed to the SoundWave Player when playing lip sync. Internal use only.                     |
| Previous Playback Percent   | The previous audio component playback percent value. Internal use only.                                              |
| Update duration with Tick   | If the audio playback is at 100% but there are remaining phonemes or emotions, the component will use the tick delta seconds to play the remaining ones. |


---

## 4.3 Geppetto Player Component

This component is used to animate the Geppetto Phoneme, Emotions and Micro-Expressions used with your character(s).    
The Geppetto Player component uses [Geppetto Data Tables](#45-geppetto-phoneme-data-table) provided in the component initialization to perform animations. 

If the Skeletal Mesh or the Skeletal Anim Instance does not use the usual node Set Morph Target to update the Morph Target values, like Metahuman, it is required to create a new component that inherit the Geppetto Player Component and override the nodes to get and set a Morph Target. Please read the section [4.3.1 - Component Inheritance](#431-component-inheritance) below for more details.

![](./docs/images/Geppetto_Player_Component_image_1.png)
![](./docs/images/Geppetto_Player_Component_image_2.png)

### 4.3.1 Component Inheritance

When using Metahumans characters or a custom node to get and/or set the Morph Targets values to the Skeletal Mesh Asset used, it is required to create a new component class that will inherit from the Geppetto Player Component class and override the nodes [`Set Morph Target`](#4413-set-morph-target-override) and [`Morph Target Exist`](#4414-morph-target-exist-override).    
Follow these steps to create a new component :

1. Create a new Blueprint Class that have `GeppettoPlayerComponent` as parent class

![](./docs/images/Component_Inheritance_image_1.png)
![](./docs/images/Component_Inheritance_image_2.png)

2. Open the created Blueprint class and override the function named `Set Morph Target`

![](./docs/images/Component_Inheritance_image_3.png)

3. Put the nodes used to change the morph target values inside the function. You can delete the call to the parent node (`Parent: Set Morph Target`).

![](./docs/images/Component_Inheritance_image_4.png)

4. You can type `Get Skeletal Mesh` in the action selection to access the Skeletal Mesh Asset

![](./docs/images/Component_Inheritance_image_5.png)


> → *If required, you can also override the function `Morph Target Exist`.This function must return true when the input morph target name does exist, false otherwise.    
For Metahuman, it is not required to override it, unless for UE 5.4. Please watch [this video](https://www.youtube.com/watch?v=wGrN9uW1Bx0) for more details.*

### 4.3.2 Initialize

This node is used to initialize the component and should be called in your Blueprint `BeginPlay` event. The following elements can be specified in the node parameters:

![](./docs/images/Geppetto_Player_Component_image_3.png)

#### Parameters

| Parameter                    | Description |
|-----------------------------|-------------|
| **Geppetto SoundWave / URL Player** | The Geppetto Player used to synchronize animations with the audio. This can either be a `GeppettoSoundWavePlayer`, a `GeppettoURLPlayer`, or any subclass of `GeppettoBaseComponent`. |
| **Mesh** | The `Skeletal Mesh Asset` that the component will use to change morph target values and perform phonemes, emotions, and micro expressions animations. |
| **Phoneme Table** | The Geppetto Phoneme Table used by the component.  <br> ➤ For Metahuman, please use the included Data Table named `MH_PhonemesTable`. |
| **Emotion Table** | The Geppetto Emotion Table used by the component.  <br> ➤ For Metahuman, use `MH_EmotionsTable`. |
| **Micro Expressions Table** | The Geppetto Micro Expressions Table used by the component.  <br> ➤ For Metahuman, use `MH_MicroExpressionsTable`. |
| **Override Animation** | If **unchecked**, the Morph Target values used by the Geppetto plugin will be blended with those coming from animations. <br> ➤ For Metahuman, this option **must be checked**. |


![](./docs/images/Geppetto_Player_Component_image_4.png)

> 💡 If you cannot see the included Geppetto Data Tables, click the settings icon (top-right in the Asset browser) and ensure that:
> - “Show Plugin Content”
> - “Show Engine Content”  
> are **both checked**.

## 4.3.3 Set Mesh with Morph Targets

Use this node to change the Skeletal Mesh used by the Geppetto Player Component after initialization :

![](./docs/images/Geppetto_Player_Component_image_5.png)


| Parameter       | Description |
|-----------------|-------------|
| **Mesh**        | The Skeletal Mesh Asset that the component will use to change morph target values and perform lip sync, emotions, and micro expressions animations. |
| **Return value**| Returns `true` if the mesh was successfully updated, `false` otherwise. |


---

## 4.3.4 Set Geppetto Player

Use this node to change the Geppetto Player used by the component after initialization. It can be a `GeppettoSoundWavePlayer` or any subclass of `GeppettoBaseComponent`.

![](./docs/images/Geppetto_Player_Component_image_6.png)

| Parameter                         | Description                                  |
|----------------------------------|----------------------------------------------|
| Geppetto SoundWave/URL Player    | The Geppetto Player attached to the component. |


---

## 4.3.5 Set Phoneme Table

Use this node to change the Geppetto Phoneme Data Table used by the Geppetto Player Component after initialization :

![](./docs/images/Geppetto_Player_Component_image_7.png)

| Parameter       | Description                                               |
|-----------------|-----------------------------------------------------------|
| **Phoneme Table**| The Geppetto Phoneme Table used by the component.         |
| **Return value** | Returns `true` if the table has been updated, `false` otherwise. |


---

## 4.3.6 Set Emotion Table

Use this node to change the Geppetto Emotion Data Table used by the Geppetto Player Component after initialization :

![](./docs/images/Geppetto_Player_Component_image_8.png)

| Parameter       | Description                                               |
|-----------------|-----------------------------------------------------------|
| **Emotion Table**| The Geppetto Emotion Table used by the component.         |
| **Return value** | Returns `true` if the table has been updated, `false` otherwise. |


---

## 4.3.7 Set Micro Expressions Table

Use this node to change the Geppetto Micro Expressions Data Table used by the Geppetto Player Component after initialization :

![](./docs/images/Geppetto_Player_Component_image_9.png)

| Parameter                | Description                                               |
|--------------------------|-----------------------------------------------------------|
| **Micro Expressions Table** | The Geppetto Micro Expressions Table used by the component. |
| **Return value**          | Returns `true` if the table has been updated, `false` otherwise. |


---

## 4.3.8 Set Emotion Custom Curve

Use this node to set the custom emotion transition function behavior when used by the Geppetto Player Component :

![](./docs/images/Geppetto_Player_Component_image_10.png)

| Parameter  | Description                                                                       |
|------------|-----------------------------------------------------------------------------------|
| **Function** | The function name to set the behavior.                                           |
| **Curve**    | The function evaluation curve. Must be in the range 0–1 for both time and value (X and Y axis). |


> Note: The behavior for the following functions is already defined and cannot be changed: Linear, Ease, Ease-in, Ease-out, Ease-in-out, and Cubic.


## 4.3.9 Change Emotion

Use this node to change the current emotion pose dynamically. For more details, see section [3.3 - Change Emotions](#33-change-emotions) :

![](./docs/images/Geppetto_Player_Component_image_11.png)

| Parameter | Description                     |
|-----------|---------------------------------|
| **Emotion** | Use the `GeppettoEmotion` structure. |


---

## 4.3.10 Play Micro Expression

Use this node to play a micro expression one time. For more info, see section [3.4 - Play or Loop Micro Expressions](#34-play-or-loop-micro-expressions).

![](./docs/images/Geppetto_Player_Component_image_12.png)

| Parameter  | Description                                                        |
|------------|--------------------------------------------------------------------|
| **Name**     | The micro-expression name (must exist in the Micro Expressions Data Table). |
| **Intensity**| Intensity value from 0 to 100.                                    |
| **Speed**    | Playback speed of the micro-expression animation (must be greater than 0). |


---

## 4.3.11 Start Micro Expression Loop

Use this node to play a micro expression repeatedly.

![](./docs/images/Geppetto_Player_Component_image_13.png)

| Parameter       | Description                                                                                     |
|-----------------|-------------------------------------------------------------------------------------------------|
| **Name**        | The micro-expression name.                                                                      |
| **Time range**  | The time range between the execution of two micro-expressions. After each play, a random time between min and max is selected. |
| **Intensity range** | The random intensity range for each play (min to max).                                      |
| **Speed range** | The random playback speed range for each play (min to max).                                    |


---

## 4.3.12 Stop Micro Expression Loop

Use this node to stop looping a micro expression.

![](./docs/images/Geppetto_Player_Component_image_14.png)


| Parameter | Description                     |
|-----------|---------------------------------|
| **Name**  | The micro-expression name.      |


---

## 4.3.13 Set Morph Target (override)

This node is used by the Geppetto Player Component to change Skeletal Mesh Morph Target values. If your mesh does not use the standard `Set Morph Target` node, override this node.

![](./docs/images/Geppetto_Player_Component_image_15.png)

| Parameter           | Description                                                                                 |
|---------------------|---------------------------------------------------------------------------------------------|
| **Morph Target Name** | The morph target to modify.                                                                 |
| **Value**           | The new morph target value (including values from animation if Override Animation was unchecked). |


---

## 4.3.14 Morph Target Exist (override)

This node checks if a morph target exists on the Skeletal Mesh. If the mesh does not use standard nodes for getting morph targets, override this node.

![](./docs/images/Geppetto_Player_Component_image_16.png)

| Parameter             | Description                                                     |
|-----------------------|-----------------------------------------------------------------|
| **Morph Target Name**  | The morph target to check.                                      |
| **Return Node - Exist**| Return `true` if the morph target exists and can be updated, else `false`. |


## 4.5 Geppetto Sequencer Component

The **Geppetto Sequencer Component** is used to synchronize a facial animation sequence and an audio source (SoundWave or Media Sound) with Unreal's Level Sequencer.

You can use this component in place of real-time playback nodes when you want to:

- Preview and keyframe the animation in the editor
- Export pre-defined lip sync + emotion animations for cinematic use
- Bake facial animation for render/export


> **⚠️ Note: This component does not handle micro-expressions or emotional states, it is solely responsible for managing the Geppetto Sequence itself.
 If you want to use micro-expressions or emotions without lip-sync playback, consider using the [Geppetto Player Component](#43-geppetto-player-component) instead.**

### 4.5.1 Required setup

Your Blueprint actor must include:

- A Skeletal Mesh Component
- A Geppetto Sequencer Component

### 4.5.2 `Initialize`

This node is used to initialize the component and should be called in your Blueprint BeginPlay event.

![](./docs/images/Initialize_image_1.png)

| Parameter             | Description                                                    |
|-----------------------|----------------------------------------------------------------|
| SkeletalMeshComponent | The component that contains the SkeletalMesh of your character. |


### 4.5.3 Play

This node is used to play a Geppetto Sequence. Precisely, it creates a new LevelSequencePlayer from the LevelSequence contained inside the GeppettoSequence. This LevelSequencePlayer is then stored in the component as long as the lip-sync is playing.

![](./docs/images/Sequencer_Play_image_1.png)


| Parameter                    | Description                                                                                         |
|-----------------------------|-----------------------------------------------------------------------------------------------------|
| **GeppettoSequence**           | The GeppettoSequence to play. It should contain several timelines, one for each MorphTarget and one for the audio file to play. |
| **Reset Facial Expression at End** | Should the component reset any facial expression that is still active on the character (eg. a smile) ? |
| **Reset Delay**                 | Delay before starting to reset the facial expression.                                               |
| **Reset Duration**              | Duration of the reset, used to add a smooth effect on the reset.                                   |


## 4.5.3 Variables

| Parameter | Description |
|-----------|-------------|
| **Alpha**     | Alpha of the reset curve. Used to create an interpolation between character’s facial animation at the end of the Geppetto Sequence, and the default face. |



## 4.5.4 Events

| Événement                 | Description |
|---------------------------|-------------|
| **On Sequencer Start Playing** | This event is broadcasted each time a GeppettoSequence starts playing. |



## 4.6 Geppetto Phoneme Data Table

The Geppetto Phoneme Data Table contains all information related to phoneme (lip sync) animation. Each phoneme associates with a list of Morph Targets and their values. You can create your own Data Tables to animate any Skeletal Mesh with custom facial controls.

### Create from scratch

1. In the Content Drawer (Ctrl+Space), right-click where you want to create the Data Table (under `Miscellaneous > Data Table`) :

![](./docs/images/Geppetto_Phonemes_DataTable_image_1.png)

2. On the Pick Row Structure window, select `GeppettoPhonemeTableRow` and click **OK**.

![](./docs/images/Geppetto_Phonemes_DataTable_image_2.png)

3. Name the Data Table and add a row for each phoneme. Rename each row name to match the phoneme name.  
   The default Metahuman phonemes are:  
   ***A, E, I, O, U, PP, FF, TH, DD, KK, CH, SS, NN, RR, HH*** (15 phonemes)

![](./docs/images/Geppetto_Phonemes_DataTable_image_3.png)
![](./docs/images/Geppetto_Phonemes_DataTable_image_4.png)
![](./docs/images/Geppetto_Phonemes_DataTable_image_5.png)
![](./docs/images/Geppetto_Phonemes_DataTable_image_6.png)

> *See [section 4.11.2](#4112-geppetto-format) for more information about Geppetto phoneme formats.*

4. For each phoneme, add Morph Target values representing the pose at amplitude 100.

![](./docs/images/Geppetto_Phonemes_DataTable_image_7.png)

> Note: You can only have a visual preview of Morph Targets in the Geppetto Sequencer editor currently. To create a Geppetto Sequencer, please read [this section.](#4102-geppetto-sequence) 

### Add/Edit from existing

You can find pre-made Phoneme Data Tables for the Demo Scene and Metahuman characters under (`All > (Engine) > Plugins > Geppetto Content > Phonemes`).    
Feel free to duplicate and/or edit the existing Data Table in order to change the phonemes pose ! 

![](./docs/images/Geppetto_Phonemes_DataTable_image_8.png)

> *If the **Plugins** or the **Engine** folder is not showing, click on Settings at the top right of the window and ensure that “Show Plugin Content” and “Show Engine Content” is checked.*

![](./docs/images/How_to_open_the_demo_level_image_1.png)

### Import from JSON/CSV

Unreal Data Table can be imported from a JSON file or a CSV file. We highly recommend using JSON instead of CSV files. Create a new JSON file with the following structure :

![](./docs/images/Geppetto_Phonemes_DataTable_image_9.png)

Create a new Geppetto Data Table or open an existing one from within the editor. On the Data Table Details tab, choose the JSON file created and click “Import/Reimport”. If the JSON format is valid, the JSON data will be imported to the Data Table.

![](./docs/images/Geppetto_Phonemes_DataTable_image_10.png)

### Export as JSON/CSV

Right-click the Data Table asset and choose **Export as JSON** or **Export as CSV**.

![](./docs/images/Geppetto_Phonemes_DataTable_image_11.png)

---

## 4.6 Geppetto Emotion Data Table

The Geppetto Emotion Data Table contains all information related to the emotions animation. The Data Table associates each emotion with a list of Morph Targets and their values. The Geppetto plugin provides a way to create your own Data Tables in order to animate any Skeletal Mesh with custom facial controls (Morph Targets). The Emotion Data Table can be created directly within the inspector or imported from a JSON file.

*Morph Target (or Blendshapes or Shapekeys) can be added on any 3D models software that you want. You can use an add-on on Blender or Maya for exemple. Or you can use Iclone 8 to add the Arkit Shapekeys standard to your 3D model.*


### 4.6.1 Create from scratch

1. In Content Drawer, create new Data Table selecting `GeppettoEmotionTableRow`.

![](./docs/images/Geppetto_Phonemes_DataTable_image_1.png)
![](./docs/images/Geppetto_Emotions_DataTable_image_1.png)


2. Each row on the Data Table defines an emotion. The row name is used to identify the emotion name, like “Happy” (double-click on the “Row Name” field or press F2 to rename it) : 

![](./docs/images/Geppetto_Phonemes_DataTable_image_4.png)

3. Use the Row Editor to set the Morph Targets values :

![](./docs/images/Geppetto_Emotions_DataTable_image_5.png)

| Parameter                                           | Description |
|-----------------------------------------------------|-------------|
| **Morph Targets**                                   | The Morph Targets values that make the Skeletal mesh take on the emotion pose. The pose must be defined as if the emotion intensity were at its highest (100). |
| **Lip Sync Morph Targets Override**                 | *Optional.* The emotion Morph Targets values that will be overridden during lip sync animation. For example, if the emotion defined makes the character smile, use this to reduce the smile during speech to avoid an uncanny effect. |
| **Lip Sync Morph Targets Override Transition Time Range** | *Optional.* Transition time range between the standard emotion pose and the lip sync override pose. Randomly selected between "First" (min) and "Second" (max). Set both fields equal to fix the transition time. |


### 4.6.2 Add/Edit from existing

Pre-made tables under:  
`All > (Engine) > Plugins > Geppetto Content > Emotions`

Feel free to duplicate and/or edit the existing Data Table in order to change existing emotions or add new ones ! 

![](./docs/images/Geppetto_Emotions_DataTable_image_6.png)

> *If the **Plugins** or the **Engine** folder is not showing, click on Settings at the top right of the window and ensure that “Show Plugin Content” and “Show Engine Content” is checked.*

![](./docs/images/How_to_open_the_demo_level_image_1.png)

### 4.6.3 Import/Export JSON same as phonemes.

Like Phoneme Data Table, Emotion Data Table can be imported from a JSON file or a CSV file. We highly recommend using JSON instead of CSV files. The import and export steps are the same as Phoneme Data Table.   
Please read the section [Import from JSON/CSV](#import-from-jsoncsv) and [Export as JSON/CSV](#export-as-jsoncsv) for more details.

---

## 4.7 Geppetto Micro Expressions Data Table

The Geppetto Micro Expressions Data Table contains all information related to the micro expressions animation. The Data Table associates each micro expression with a list of Morph Targets and their values.    
The Geppetto plugin provides a way to create your own Data Tables in order to animate any Skeletal Mesh with custom facial controls (Morph Targets). The Micro Expressions Data Table can be created directly within the inspector or imported from a JSON file :

*Morph Target (or Blendshapes or Shapekeys) can be added on any 3D models software that you want. You can use an add-on on Blender or Maya for exemple. Or you can use Iclone 8 to add the Arkit Shapekeys standard to your 3D model.*

### 4.7.1 Create from scratch

1. On the Content Drawer (Ctrl+Space), right click at the desired location and create new Data Table (under *Miscellaneous > Data Table*).
On the Pick Row Structure window, select `GeppettoMicroExpressionTableRow` :

![](./docs/images/Geppetto_Phonemes_DataTable_image_1.png)
![](./docs/images/Geppetto_MicroExpressions_DataTable_image_1.png)

2. Each row on the Data Table defines a micro expression. The row name is used to identify the micro expression name, like “Blink”  (double-click on the “Row Name” field or press F2 to rename it).

![](./docs/images/Geppetto_Phonemes_DataTable_image_4.png)

3. Use the Row Editor to set the Morph Targets values :

![](./docs/images/Geppetto_MicroExpressions_DataTable_image_5.png)


| Parameter                        | Description |
|----------------------------------|-------------|
| **Alpha Curve**                  | The curve used to determine the micro expression animation time and transition interpolation. Must be of type **Float**. Custom curves can be created for specific use cases. |
| **Fixed Morph Targets**          | *Optional.* The Morph Target values that define the pose for the micro expression, as if the intensity were at its maximum (100). |
| **Dynamic Morph Targets**        | *Optional.* Morph Targets configured with random value ranges. Useful for varying the expression each time it is triggered. |

### Détails des Dynamic Morph Targets

| Champ            | Description |
|------------------|-------------|
| **Morph Targets**| The Morph Target names that will share a common randomly selected value. Allows grouped randomization. |
| **Value Range**  | The random range (min = "First", max = "Second") from which a new value will be chosen every time the micro expression is played. |

> *Please note that the same micro expression can have fixed and dynamic Morph Targets values. If a Morph Target is defined in both lists, the value defined in Fixed Morph Targets will be ignored.    
**We recommend to always plays dynamic micro expressions with the highest intensity (100), as the value is already chosen randomly between a min and a max.***

### 4.7.2 Add/Edit from existing

Pre-made tables under:  
`All > (Engine) > Plugins > Geppetto Content > MicroExpressions`

Feel free to duplicate and/or edit the existing Data Table in order to change existing emotions or add new ones ! 

![](./docs/images/Geppetto_MicroExpressions_DataTable_image_6.png)

> *If the **Plugins** or the **Engine** folder is not showing, click on Settings at the top right of the window and ensure that “Show Plugin Content” and “Show Engine Content” is checked.*

![](./docs/images/How_to_open_the_demo_level_image_1.png)

### 4.7.3 Import/Export JSON like above.

Like Phoneme Data Table, Micro Expressions Data Table can be imported from a JSON file or a CSV file. We highly recommend using JSON instead of CSV files. 
The import and export steps are the same as Phoneme Data Table.   
Please read the section [Import from JSON/CSV](#import-from-jsoncsv) and [Export as JSON/CSV](#export-as-jsoncsv) for more details.

---

## 4.8. Geppetto Blueprint Library (Editor only)

The following functions can only be used in Editor-only assets, such as Editor Utility Widget or Editor Utility Blueprint. Please note that the following functions are declared in C++.

---

### 4.8.1. Generate phonemes (using SoundWave)

Generate the phonemes for the given audio and sentence.  
👉 THIS IS THE EDITOR-ONLY FUNCTION. FOR RUNTIME, SEE: [Generate phonemes (using SoundWave) ](#481-generate-phonemes-using-soundwave) in section 4.9.

![](./docs/images/Runtime_Phonemes_generation_and_animation__Blueprint__image_9.png)

#### Parameters

### Audio Input Configuration

| **Parameter**         | **Description** |
|-----------------------|-----------------|
| **Audio**             | The `SoundWave` asset used as input audio. See [section 3.1.1](#311-audio-import) for more details. |
| **Sentence**          | The sentence spoken in the audio. You can include emotion tags (see [section 3.3](#33-emotion-tags)). |
| **Format**            | Audio file format. Supported formats include `WAV`, `MP3`, etc. |
| **Amplitude range**   | The minimum and maximum values used to determine the intensity of phoneme animations. |
| **Silence threshold** | The minimum decibel (dB) level considered as silence. Helps in ignoring background noise or breathing sounds. |
| **Emotion detection** | If enabled, a deep learning model will automatically analyze the audio and extract the emotion content. |


---

### 4.8.2. Save Geppetto Phonemes

Save the generated phonemes as a `Geppetto Data Asset` or as a Sequencer track.

![](./docs/images/GeppettoBlueprintLibrary_image_1.png)

#### Parameters

| **Parameter**     | **Description** |
|-------------------|-----------------|
| **Save file as**  | Choose the output format: `DataAsset` (for playback using the `SoundWavePlayer`) or `Sequencer` (for timeline-based facial animation using `GeppettoSequence`). |
| **Save file at**  | The directory path where the generated `.uasset` will be saved in your project. |


---

### 4.8.3. Show save file selection dialog

Show the operating system save file selection dialog for a Geppetto Data Asset.    
**Please note that the whole engine is freezed while the OS file selection window is opened.**

![](./docs/images/GeppettoBlueprintLibrary_image_2.png)


| **Parameter**      | **Description** |
|--------------------|-----------------|
| **Selected Path**  | The file path selected by the user, relative to the project's `Content` folder. Returns `"INVALID PATH"` or an empty string if no path was selected or if the path is invalid. |


### 4.8.4. Get Documentation URL

Open the plugin's documentation link in your web browser.

![](./docs/images/GeppettoBlueprintLibrary_image_3.png)


## 4.9. Geppetto Blueprint Library

The following functions can be used in both runtime and editor assets, such as Blueprint classes. Please note that the following functions are declared in C++.

### 4.9.1. Generate phonemes (using URL)

Generate the phonemes for the given audio and sentence. The audio file is available through a publicly accessible URL. The audio must be in wav format (PCM16 recommended) :

![](./docs/images/GeppettoBlueprintLibrary_image_4.png)


| **Parameter**         | **Description** |
|------------------------|-----------------|
| **URL**                | The audio URL. See section 3.2 for more details. |
| **Sentence**           | The sentence spoken in the audio. Can include emotion tags. Please see section 3.3 for more details. |
| **Format**             | The phoneme format returned by the API. Please read section 4.11.2 for more details. Default is `"Metahuman"`. |
| **Min Ampl**           | The minimum amplitude value (range 0–100). Default is `30`. |
| **Max Ampl**           | The maximum amplitude value (range 0–100). Must be greater than or equal to `Min Ampl`. Default is `60`. |
| **Silence Threshold**  | The threshold used to identify audio silences. Default is `-50 dB`. |
| **Silence Time**       | The minimum silence duration to be considered as a pause, in milliseconds. Default is `250 ms`. |
| **Logs**               | Whether logs should be printed to the console. Default is `true`. |
| **On Response**        | The delegate event called when a response is received from the API. |


### 4.9.2. Generate phonemes (using SoundWave)

Generate the phonemes for the given SoundWave and sentence.

![](./docs/images/GeppettoBlueprintLibrary_image_5.png)

**SoundWave detail Window** :

![](./docs/images/GeppettoBlueprintLibrary_image_6.png)


| **Parameter**           | **Description** |
|--------------------------|-----------------|
| **Audio**                | The SoundWave used for phoneme generation. |
| **Sentence**             | The sentence spoken in the audio. |
| **Format**               | See section 4.11.2. |
| **Min Ampl**, **Max Ampl** | Range of phoneme amplitude (0–100). |
| **Silence Threshold**, **Silence Time** | Silence detection parameters. |


### 4.9.3. Generate phonemes (using PCM bytes)

Generate the phonemes using a PCM raw byte buffer and sentence.

![](./docs/images/GeppettoBlueprintLibrary_image_6.png)

| **Parameter**      | **Description** |
|--------------------|-----------------|
| **PCM Bytes**      | The PCM waves data bytes. |
| **Sample Rate**    | The sample rate of the PCM waves (=frequency). Mostly 44100. |
| **Bit Depth**      | The bit depth of the PCM waves (=sample data length). Mostly 16 or 24. |
| **Num Channels**   | The amount of channels of the PCM waves (mono=1, stereo=2, etc.). |
| **Other parameters** | See Generate phonemes (using SoundWave). |


### 4.9.4. Generate phonemes (using multipart/form-data)

Same as the other phoneme generation nodes, but uses the `multipart/form-data` format required by some APIs.

![](./docs/images/Runtime_Phonemes_generation_and_animation__Blueprint__image_10.png)

| **Parameter**        | **Description** |
|----------------------|-----------------|
| **File Bytes**       | The file bytes. Can be all type of files. |
| **Filename**         | The filename that will be sent and read by the API. No real impact. |
| **File Content Type**| The HTTP MIME Content-Type of the file. Must match the file structure. |
| **Other parameters** | See Generate phonemes (using SoundWave). |


### 4.9.5. Apply Delay (Phonemes)

Applies a delay to the list of phonemes returned by the API.

![](./docs/images/GeppettoBlueprintLibrary_image_8.png)

| **Parameter**        | **Description** |
|----------------------|-----------------|
| **File Bytes**       | The file bytes. Can be all type of files. |
| **Filename**         | The filename that will be sent and read by the API. No real impact. |
| **File Content Type**| The HTTP MIME Content-Type of the file. Must match the file structure. |
| **Other parameters** | See Generate phonemes (using SoundWave). |

---

### 4.9.6. Apply Delay (Emotions)

Applies a delay to the list of emotions returned by the API.

![](./docs/images/GeppettoBlueprintLibrary_image_9.png)

| **Parameter**   | **Description**                                               |
|-----------------|---------------------------------------------------------------|
| **Delay**       | The delay that will be applied, in milliseconds. Can be positive or negative. |
| **Emotions**    | The emotions list to apply the delay to.                      |
| **Return Value**| The emotions list with the delay applied.                     |


---

### 4.9.7. Get Morph Targets for Phoneme

Returns the Morph Targets and corresponding values for a phoneme name from a given Phoneme Table.

![](./docs/images/GeppettoBlueprintLibrary_image_10.png)

| **Parameter**     | **Description**                                              |
|-------------------|--------------------------------------------------------------|
| **Phoneme**       | The phoneme name.                                            |
| **Phoneme Table** | The Phoneme Data Table used to retrieve Morph Targets values.|
| **Return Value**  | The list of all Morph Targets used for the phoneme and their values. |


---

### 4.9.8. Safe Lerp

Safe linear interpolation with clamping. Used internally to blend values without exceeding limits.

![](./docs/images/GeppettoBlueprintLibrary_image_11.png)

| **Parameter**   | **Description**                                                          |
|-----------------|--------------------------------------------------------------------------|
| **A**           | The minimum value, returned when Alpha <= 0.0                           |
| **B**           | The maximum value, returned when Alpha >= 1.0                           |
| **Alpha**       | The alpha value used to interpolate between A and B                     |
| **Return Value**| The safe linear interpolation result (either A, B, or a standard interpolation) |


---

## 4.10. Data Assets

A Data Asset is an Unreal Asset used to store Data. The Geppetto Plugin uses custom defined Data Assets written in C++.

---

### 4.10.1. Geppetto Data Asset

Geppetto Data Assets are used to store and save the generated phonemes and emotions generated from the API within the Editor in order to use them in the game later. You can use the Geppetto SoundWave Player node `Play Data Asset` to animate the data contained in the Data Asset. All fields are Blueprint Read-Only, but you can use the node `Save Geppetto Phonemes (as Asset)` to create a new Data Asset with Blueprint. Please note that the node is only available within the Editor.

![](./docs/images/Geppetto_DataAsset_image_1.png)

| Audio               | The audio associated with the lip sync.                                  |
|---------------------|-------------------------------------------------------------------------|
| **Sentence**            | (Info only) The sentence used for generation.                           |
| **Min Ampl**            | (Info only) The minimum amplitude value used for generation.            |
| **Max Ampl**            | (Info only) The maximum amplitude value used for generation.            |
| **Silence Threshold**   | (Info only) The silence threshold value (dB) used for generation.       |
| **Silence Time**        | (Info only) The silence time (in milliseconds) used for generation.     |
| **Delay**              | (Info only) The delay applied to phonemes and emotions after generation.|
| **Phonemes**            | The phonemes list generated by the API, used to animate lip sync.       |
| **Emotions**            | The emotions list generated by the API, used to animate emotions.       |


---

### 4.11 Geppetto Sequence

A `GeppettoSequence` is a custom asset that contains all the assets and logic to play a lip-sync animation in one file. This asset contains a `LevelSequence` with a timeline for the audio file and a timeline for each `Morph Target` with their amplitude represented as a curve. That is the main element of this asset as it handles all the logic of the lip-sync animation to play on a character.

The `GeppettoSequence` asset can also be edited inside a custom editor which allows you to see the render of the lip-sync animation in a preview scene with the selected mesh. Here is an overview:

![](./docs/images/Geppetto_Sequence_image_1.png)

- The red box is the viewport. It gives you a preview of what the lip-sync animation will look like in-game.

- The orange box is the sequencer editor. Here you can edit each Morph Target amplitude and the frame when the amplitude plays. You can also add or remove any timeline if you want.

- The blue box is the Detail Panel, here you have a few settings :
  - Preview Mesh : You can select the skeletal mesh to preview.
  - Advanced Parameters :
    - Face Animation : This is an optional parameter to use when your character does not contain Morph Targets but instead Controls (another kind of blendshapes used by some characters such as MetaHumans). 
    You should select the AnimationBlueprint of your character in order to properly preview the lip-sync animation.


## 4.12. Enums

Here you can find the list and values of all enums defined by the Geppetto Plugin.

---

### 4.12.1. Geppetto Emotion Transition

This enum is used to choose the emotion transition each time the emotion pose changes. Users can use their own defined function behavior by using the Geppetto Player Component node `Set Emotion Custom Curve`.

| Interpolation Type | Description                                  |
|--------------------|----------------------------------------------|
| **Linear**             | Use linear interpolation.                     |
| **Ease**               | Easing interpolation.                         |
| **Ease-In**            | Easing in only interpolation.                 |
| **Ease-Out**           | Easing out only interpolation.                |
| **Ease-In-Out**        | Easing in and out interpolation. Similar to Ease. |
| **Cubic**              | Cubic interpolation. Similar to Ease-In-Out and Ease. |
| **CUSTOM 1-10**        | Custom interpolation. See `Set Emotion Custom Curve`. |

---

## 4.13. Structs

Here you can find the list and details of all structs defined by the Geppetto Plugin.

---

### 4.12.1. Geppetto Phoneme

A struct containing all parameters to play a Geppetto Phoneme. All variables are Blueprint read-write:

![](./docs/images/Structs_image_1.png)

| Name      | Description                                                      |
|-----------|------------------------------------------------------------------|
| **Name**      | The phoneme name.                                                |
| **Amplitude** | The phoneme amplitude, range 0 - 100.                           |
| **Time**      | The phoneme animation play time, matching the audio for synchronization. |


---

### 4.12.2. Geppetto Emotion

A struct containing all parameters to play a Geppetto Emotion. All variables are Blueprint read-write:

![](./docs/images/Structs_image_2.png)

| Name               | Description                                                    |
|--------------------|----------------------------------------------------------------|
| **Name**               | The emotion name.                                              |
| **Intensity**          | The emotion intensity, range 0 - 100.                         |
| **Transition time**    | The emotion transition time, in seconds.                      |
| **Transition function**| See Geppetto Emotion Transition.                              |
| **Time**               | The emotion animation play time, matching the sentence tag for sync. |


---

### 4.12.3. Geppetto Micro Expression

A struct containing all parameters to play a Geppetto Micro Expression. All variables are Blueprint read-write:

![](./docs/images/Structs_image_3.png)

| Parameter              | Description                                                                                      |
|-----------------------|--------------------------------------------------------------------------------------------------|
| **Curve**                 | The curve used to determine the micro expression animation time and transition interpolation. Must be a “Float” type curve. |
| **Transition Morph Targets** | The micro expression Morph Targets and their values used for animation.                          |
| **Current Tick Morph Targets** | The current tick Morph Targets values used by the micro expression, managed by the Geppetto Player Component. |
| **Speed**                 | The animation speed of the micro expression. Must be greater than 0.                             |
| **Is Animating**          | Indicates whether the micro expression is currently animating (not started, finished). Managed by the Geppetto Player. |
| **Time**                 | The micro expression animation play time. *(Currently unused)*                                   |


---

### 4.12.4. Dynamic Micro Expression

A struct containing all values related to dynamic Micro Expression Morph Targets. Used in Micro Expression Data Table:

![](./docs/images/Structs_image_4.png)

| Parameter     | Description                       |
|---------------|---------------------------------|
| **Morph Targets** | The dynamic Morph Targets names.|
| **Value Range**   | The dynamic Morph Target min and max values. |


---

### 4.12.5. Tuple Float

Since Unreal `FTuple<float>` is not supported in Blueprint yet, this struct is used instead.

![](./docs/images/Structs_image_5.png)

| Parameter | Description                              |
|-----------|------------------------------------------|
| **First**     | The tuple first value, i.e. the min value or the begin time. |
| **Second**    | The tuple second value, i.e. the max value or the end time.   |


## 5. Resources & General explanations

---

### 5.1. How does the Geppetto model work?

---

#### Text Acquisition

![](./docs/images/RessourcesGeneral_image_1.png)

The text can either be provided directly or generated through Speech-to-Text, which also captures onomatopoeia. For the best results, it is recommended to provide a text that explicitly includes onomatopoeia. Emotion tags associated with the text are also extracted.

---

#### Silence Detection

![](./docs/images/RessourcesGeneral_image_2.png)

Silences in the audio serve as markers to define the start and end of the text. The automatic detection of silence depends on the type of audio:

- For synthetic voices, -50 dB silence threshold and 200 ms silence time are recommended.  
- For noisier recordings, -40 dB and 300 ms may be more suitable.

These parameters should be adjusted based on the characteristics of the audio recording.

---

#### Text-to-Phoneme Conversion

The text is converted into phonemes using a machine learning model. This model is language-sensitive, and currently, Geppetto supports English, French, German, Italian, and Spanish.  
If additional language support is needed, please contact us.

![](./docs/images/RessourcesGeneral_image_3.png)

---

#### Alignment with Audio: Two Model Approaches

![](./docs/images/RessourcesGeneral_image_4.png)

There are two types of models available:

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

![](./docs/images/RessourcesGeneral_image_5.png)

The minimum amplitude is set as the lower bound between 0 and 100, based on the detected phoneme amplitude. This ensures that the phoneme remains visible during execution, even when its natural amplitude is very low.

Similarly, the maximum amplitude acts as an upper limit to prevent excessive deformation of blendshapes, maintaining more natural transitions.

The amplitude sinus step defines the incremental step between two consecutive phonemes' amplitudes, preventing abrupt jumps. This value ranges between 0 and 1:

1. The closer it is to 1, the more significant the amplitude variations between phonemes can be.

2. Lower values ensure smoother transitions, reducing sudden amplitude shifts.

## 6. Adding Emotion Tags

![](./docs/images/RessourcesGeneral_image_6.png)

Emotion tags are integrated into the audio at the appropriate timestamps based on their placement within the sentence, ensuring that the speaker’s tone and emotional expression are accurately reflected.

![](./docs/images/RessourcesGeneral_image_7.png)

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
