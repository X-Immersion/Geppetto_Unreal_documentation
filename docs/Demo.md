# Geppetto UE 2.0.0 – Demo

**[← Table of contents](../README.md#table-of-contents)**

---

### On this page

- **[How to Open the Demo Level](#21-how-to-open-the-demo-level)**
- **[Play with the Demo Level](#22-play-with-the-demo-level)**
- **[Understand the Demo Level](#23-understand-the-demo-level)**

---

The Geppetto plugin comes with a demo level and a skeletal mesh with morph targets, thanks to [Rigged T-Pose Human Male w 50 Face Blendshapes](https://sketchfab.com/3d-models/rigged-t-pose-human-male-w-50-face-blendshapes-cc7e4596bcd145208a6992c757854c07) by Mike Alger, licensed under [Creative Commons Attribution](https://creativecommons.org/licenses/by/4.0/).

## 2.1 How to Open the Demo Level

1. 🎮 Open or create a project with the Geppetto plugin installed.
2. 🧰 Open the **Content Drawer** (`Ctrl + Space`) and go to **Settings** (top-right corner).
3. ✅ Ensure the following options are enabled:
   - “Show Plugin Content”
   - “Show Engine Content”

![Show where is the Engine and Plugin Content options](./images/How_to_open_the_demo_level_image_1.png)

4. 📂 Navigate to the appropriate folder:
   - **Marketplace (Fab) install**: `All > Engine > Plugins > Geppetto Content > GeppettoDemoScene`
   - **Source install**: `All > Plugins > Geppetto Content > GeppettoDemoScene`

![Path to the GeppettoExampleScene in Unreal](./images/How_to_open_the_demo_level_image_2.png)

5. ▶️ Open the level and press **Play**.

![Where to find the Play button](./images/How_to_open_the_demo_level_image_3.png)

## 2.2 Play with the Demo Level

![Demo level overview](./images/Demo_level_overview.png)

<!-- TODO: Add colored box to the image and the text to be clearer, like for Ariel: https://github.com/X-Immersion/Ariel_Unreal_documentation/blob/main/doc/Quickstart.md#-editor-pre-generation -->

There are few things you can do on the demo scene:

* On the *middle right*, you can see the **Controls** that can be used to interact with the demo level. Use the keyboard key 1-5 (or numpad key) to perform actions:

| Key | Action                                                                 |
|-----|------------------------------------------------------------------------|
| 1   | Play the selected pre-generated Geppetto Sequence                     |
| 2   | Play the selected pre-genereted Geppetto Data Asset                     |
| 3   | Use the selected SoundWave to generate lipsync at runtime and play it |
| 4   | Change the camera angle |
| 5   | Toggle UI |

* On the *bottom right*, you can see the **Micro Expression** loops currently played. You can click on the (X) button to toggle them (on/off).

* On the *bottom center*, you can see the **Emotions** dropdown. If you change the emotion, the emotion transition animation will be played.

* On the *bottom left*, you can see the **Lip-sync** settings. Use them with the keys 1-3 to play various DataAsset/Sequence/SoundWave.

## 2.3 Understand the Demo Level

Open `BP_GeppettoExampleActor > Event Graph` to start exploring how the
Geppetto plugin works.

![Where to find the GeppettoExampleActor in the Outlier](./images/Understand_the_demo_level_image_1.png)

![Click on the EventGraph tu unfold all the available graphs](./images/Understand_the_demo_level_image_2.png)

You’ll see a block for each key event and `BeginPlay`.

![Example of BeginPlay block](./images/Understand_the_demo_level_image_3.png)

![Screen of the various Blueprint nodes available in this example actor](./images/Understand_the_demo_level_image_4.png)

### 2.3.1 Components Required

Every actor using the plugin must have these 3 components:

- ✅ A Skeletal Mesh with Morph Targets
- 🔊 An Audio Component
- 🧠 A [Geppetto Sound Wave Component](./API.md#41-geppetto-sound-wave-player-component) or any component that inherit from [Geppetto Base Component](API.md#component-inheritance) *(e.g., DemoPlayerV2)*

![Components you should have](./images/Components_image_1.png)

You can see on the [Geppetto Sound Wave Component](./API.md#41-geppetto-sound-wave-player-component) detail pannel the Data Tables used for phonemes, emotions, micro expressions and headshift.

![Component setup](./images/Components_image_2.png)

### 2.3.2 Begin Play

In the BeginPlay Event, there is no need to initialize anything. Instead, we use this event to start some common micro expressions.

- Blink
- EyeDart

![Path to the GeppettoExampleScene in Unreal](./images/Begin_Play_image_1.png)

A MicroExpression DataTable with the two micro expressions is needed to play them. You can check this by clicking on the Geppetto Sound Wave Player and looking at the MicroExpression DataTable value.   
> You can create your own table in order to animate characters with custom Morph Targets.    
Please read section [4.2](./API.md#42-geppetto-phoneme-data-table), [4.3](./API.md#43-geppetto-emotion-data-table) and [4.4](./API.md#44-geppetto-micro-expressions-data-table) for more details.


### 2.3.3. Phonemes / Lipsync

The **keyboard 1 and 2** events are related to pre-generated phonemes.


- Please read section [3.1.1 - Pre-Generated Phonemes generation](./Features.md#311-pre-generate-phonemes-as-a-geppetto-data-asset) of the documentation for more information on how to pre-generate phonemes in a Geppetto Sequence or a Data Asset using the Geppetto Editor Interface.

- Please read section [3.1.3 - Play a Geppetto Sequence](./Features.md#313-play-a-geppetto-sequence) of the documentation for more information on how to play the Geppetto phonemes from a Geppetto Sequence

- Please read section [4.9 - Geppetto Sequence](./API.md#49-geppetto-sequence) of the documentation for more information about the Geppetto Sequence asset

![](./images/Phonemes___Lipsync_image_1.png)

> Note that this is also possible to play the Geppetto phonemes from a Data Asset. For more information, please refer to the section [3.1.2 - Play a Geppetto Data Asset with SoundWave](./Features.md#312-play-a-geppetto-data-asset-with-soundwave).

The **keyboard 3 event** is related to runtime phonemes.

- Please read section [3.2 - Runtime Phoneme Generation](./Features.md#32-runtime-phonemes-generation-and-animation-blueprint) of the documentation for more information on how to generate and play runtime generated phonemes.
- Please read section [4.7.1 - Generate phonemes (using SoundWave)](./API.md#471-generate-phonemes-using-soundwave) for more
information on how to generate phoneme from a local audio file (SoundWave, PCM or file)

![](./images/Phonemes___Lipsync_image_2.png)


The plugin uses a [Geppetto Phoneme Data Table](./API.md#42-geppetto-phoneme-data-table) to know all Morph Targets values for each phoneme. If the skeletal mesh of your characters have different Morph Targets, it is required to create a new [Geppetto Phoneme Data Table](./API.md#42-geppetto-phoneme-data-table) with the Morph Targets used in your characters.     
**Please note that Data Tables for Metahuman are included in this plugin !**   
The Data Table used by the plugin is passed through the [Geppetto Sound Wave Player Component](./API.md#41-geppetto-sound-wave-player-component) variables.

### 2.3.4. Emotions

The **Emotion combo box in the scene** is related to emotions.

- Please read section [3.3 - Change Emotions](./Features.md#33-change-emotions) for more information on how to change emotions in Blueprints.
- Please read section [3.5 - Emotion Tag System](./Features.md#35-emotion-tag-system) for more information on how to change emotions with tags.
- Please read section [4.11.2 - Geppetto Emotion](./API.md#4112-geppetto-emotion) of the documentation for more information about the Geppetto emotion structure.

![](./images/Emotions_image_1.png)

The same way as phonemes, emotions use a [Geppetto Emotion Data Table](./API.md#43-geppetto-emotion-data-table) to determine the Morph Target values for each emotion. Please read section [4.3 - Geppetto Emotion Data Table](./API.md#43-geppetto-emotion-data-table) of the documentation for more information.

### 2.3.5. Micro Expressions

The **micro expressions scrollbox in the scene** is related to micro expressions.

- Please read section [3.4 - Play or Loop Micro Expressions](./Features.md#34-play-or-loop-micro-expressions) of the documentation for more information on how to use micro expressions.
- Please read section [4.1.6 - Play Micro Expression](./API.md#416-play-micro-expression) of the documentation for more information about the node.
- Please read section [4.1.7 - Start Micro Expression Loop](./API.md#417-start-micro-expression-loop) and [4.1.8 - Stop Micro Expression Loop](./API.md#418-stop-micro-expression-loop) of the documentation for more information about the nodes.

![](./images/Micro_Expressions_image_1.png)

Like phonemes and emotions, micro expressions use a [Geppetto Micro Expressions Data Table](./API.md#44-geppetto-micro-expressions-data-table) to retrieve the Morph Targets values.   
This time, however, the values can be **static** (like phonemes or emotions Morph Targets values) or **dynamic** (the Morph Targets values will change each time the Micro Expression is played).    
Please read section [4.4 - Geppetto Micro Expressions Data Table](./API.md#44-geppetto-micro-expressions-data-table) of the documentation for more information.