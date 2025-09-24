# Geppetto UE 2.0.0 – Getting Started

This chapter provides a complete flow of the Geppetto plugin to create a pre-generated or a runtime lipsync in the Unreal Editor.

**[← Table of contents](../README.md#table-of-contents)**

---

### On this page

- **[What is Geppetto ?](#21-what-is-geppetto-)**
- **[Character setup](#22-character-setup)**
- **[Geppetto Data Tables](#23-geppetto-data-tables)**
  - ***[Phoneme Data Table](#231-phoneme-data-table)***
  - ***[Emotion Data Table](#232-emotion-data-table)***
  - ***[Micro Expression Data Table](#233-micro-expression-data-table)***
  - ***[Headshift Data Table](#234-headshift-data-table)***
- **Editor (pre-generated) usage**
  - **[Generate phonemes and emotions in the editor](#24-generate-phonemes-and-emotions-in-the-editor)**
  - **[Play editor lip-sync asset on a character](#25-play-editor-lip-sync-assets-on-a-character)**
  - **[Export lipsync as an animation](#26-export-lipsync-as-an-animation)**
- **Runtime (live) usage**
  - **[Generate phonemes and emotions on runtime](#27-generate-phonemes-and-emotions-on-runtime)**
  - **[Play an emotion on a character](#28-play-an-emotion-on-a-character)**
  - **[Play micro expression on a character](#29-play-a-micro-expression-on-a-character)**

---

## 2.1 What is Geppetto ?

**Geppetto is a facial animation and lip-sync plugin for Unreal Engine, designed to automatically generate lip-sync animations from audio or text files.**

**The latest version (2.1.0) introduces a better lipsync render and the ability to export your Geppetto sequence as an animation asset, enabling versatility and increased customization. This version also includes new features like headshift.**


<br/>

## 2.2 Character setup

In order to use Geppetto on a character, the Skeletal Mesh must have Morph Targets *(aka Blendshapes)* and/or an Anim Instance that cover facial animation (such as Metahuman `Face_AnimBP` Blueprint class).

For this example, we will use this  [rigged character](https://sketchfab.com/3d-models/rigged-t-pose-human-male-w-50-face-blendshapes-cc7e4596bcd145208a6992c757854c07) made by [Mike Alger](https://mikealger.com/).    
This character possesses 50 face blendshapes that we will use to create a lip-sync animation.

Here are the steps to set up the character in Unreal:

1. Download the character in FBX format from sketchfab with the link given above.
2. Unzip the character archive wherever you want.
3. Create a new Unreal project or open an existing one.
4. Drag and drop the fbx file of the character in the wanted folder. Here we will place it inside the "Example" folder. The import window will open.
5. **Do not forget to import the MorphTarget by checking the appropriate boxes. Then click on "Import".**

![](./images/Getting_Started_image_1.png)


6. To ensure the character was correctly imported, open the skeletal mesh asset and go into the "MorphTargets" tab. Here you should have the 50 blendshapes.

![](./images/Getting_Started_image_2.png)

> [!NOTE]  
> The "MorphTargets" tab may vary a bit depending on your version of the engine but the content still remains the same. 

**Well done! Your character is now set up and can be used with Geppetto!**    
Check the next steps to learn how to bind Geppetto to your character and play a lip-sync animation.


<br/>

## 2.3 Geppetto Data Tables


### 2.3.1 Phoneme Data Table

**The Geppetto Phoneme Data Table in Unreal Engine is designed to drive facial animation through phoneme-based lip sync.**    
Each row represents a phoneme (like A, E, U, etc.) and contains values for Morph Targets, which are specific facial poses. This allows for detailed, expressive character dialogue.    
Here is an example with the **DEMO_PhonemesTable** that converts phonemes into the blendshapes of the rigged character we just imported:

![](./images/Getting_Started_image_4.png)

You can either create a new Phoneme DataTable in Unreal or import an existing one from a csv or json file.<br/>
Predefined tables are available under *(Engine) > Plugins > Geppetto Content > Phonemes*, and you’re free to duplicate or customize them.<br/>
For more information, please see the section [Geppetto Phoneme Data Table](./API.md#44-geppetto-phoneme-data-table).

> [!NOTE]  
> If you do not see the **Plugins** folder or the **Geppetto Content** folder, click on **"Settings"** in the **Content Browser** and tick **"Show Plugin Content"**.     
>If the Geppetto is installed within the Engine and not the project, you also have to tick **"Show Engine Content"**. 
>
>![Show where is the Engine and Plugin Content options](./images/How_to_open_the_demo_level_image_1.png)


### 2.3.2 Emotion Data Table

The Geppetto Emotion Data Table is used to animate facial expressions tied to emotions. Each row corresponds to an emotion (like Happy, Sad, Angry, etc.) and specifies Morph Target values that sculpt the facial mesh into an expressive pose. This is ideal for customizing character emotion systems in Unreal Engine.    
Here is an example with the **DEMO_EmotionsTable** that converts emotions into the blendshapes of the rigged character we just imported:

![](./images/Getting_Started_image_5.png)

You can either create a new Emotion DataTable in Unreal or import an existing one from a csv or json file.<br/>
Predefined tables are available under *(Engine) > Plugins > Geppetto Content > Emotions*, and you’re free to duplicate or customize them.<br/>
For more information, please see section [Geppetto Emotion Data Table](./API.md#45-geppetto-emotion-data-table).


### 2.3.3 Micro-expression Data Table

The Geppetto Micro Expressions Data Table defines subtle facial movements like blinks or eyebrow twitches. Each row maps a micro expression to Morph Target values, either fixed or dynamic.     
Dynamic targets introduce random variation to keep animations lively and natural.

![](./images/Geppetto_MicroExpressions_DataTable_image_5.png)

You can either create a new Micro Expression DataTable in Unreal or import an existing one from a csv or json file.<br/>
Predefined tables are available under *(Engine) > Plugins > Geppetto Content > MicroExpressions*, and you’re free to duplicate or customize them.<br/>
For more information, please see section [Geppetto Micro Expressions Data Table](./API.md#46-geppetto-micro-expressions-data-table).


### 2.3.4 Headshift Data Table

The Geppetto Headshift Data Table defines neck movements. Each row represents one or several neck movements to play procedurally or when an emotion is played.     
Each neck movement is composed of a curve, a speed, an amplitude, and influenced axis.

![](./images/Geppetto_Headshift_DataTable_image_1.png)

You can either create a new Headshift DataTable in Unreal or import an existing one from a csv or json file.<br/>
Predefined tables are available under *(Engine) > Plugins > Geppetto Content > MicroExpressions > Headshift*, and you’re free to duplicate or customize them.<br/>
For more information, please see section [Geppetto Headshift Data Table](./API.md#47-geppetto-headshift-data-table).


<br/>

## 2.4 Generate phonemes and emotions in the Editor

To pre-generate phonemes, you can use the Editor Utility Widget included in the plugin.     
You can open the Window by clicking on the Geppetto icon button or in the menu **Help > Geppetto**:

![](./images/Pre_Generate_Phonemes_image_1.png)
![](./images/Pre_Generate_Phonemes_image_2.png)

The interface will open. It contains several parameters to customize your phonemes and emotions generation.     

![](./images/Getting_Started_image_3.png)

Here are the following steps to generate a basic lip-sync animation. You can find more information about all fields in the dropdown menu [below](#complete-list-of-editor-parameters).

1. Pass your audio file in the `Audio` parameter.    
For this example, we will use **SentenceExample_MaleVoice_1** which is available in *(Editor) > Plugins > Geppetto Content > Examples* if you want to use it, but you are free to choose **any audio file speech you want**.

2. We will tick the checkbox `Use speech recognition` to perform Speech-To-Text recognition using the audio file. You can also untick it and write the speech text by yourself. Either way, do not forget to change the language to match the speech language.

3. Tick the `Add emotion tag automatically` checkbox to allow Geppetto to automatically detect emotions in your audio file (based on the speech).

4. Then, choose where to store your generated phonemes with the `Save file as` parameter.    
There are two types of assets: [Geppetto DataAsset](./API.md#4121-geppetto-data-asset) and [Geppetto Sequence](./API.md#4122-geppetto-sequence). Each of them has different use cases.   
[Below](#25-play-editor-lip-sync-assets-on-a-character), you will find an example on how to use and play both assets on your Character.

5. Finally, hit the `Generate Phonemes` button to generate your .uasset file.     
**This may take a while depending on the audio duration and phonemes quality selected.**

### Complete list of editor parameters

<details>
<summary><strong>Editor parameters details</strong></summary>

| Icon | Element                                   | Description                                                                 |
|-------|-------------------------------------------|-----------------------------------------------------------------------------|
| 📘    | **Documentation button**                  | Opens this Geppetto documentation in your browser.                          |
| 🗒️    | **Preset**                                | The preset used to automatically save all editor fields data. You can create new presets by giving a name and click the "+" button. |
| 🧠    | **Local model** *(not available on Fab)*  | Define the phoneme generation model *(local only)*.                         |
| 🔊    | **Audio**                                 | The speech SoundWave asset *(compatible with [Ariel TTS](https://www.fab.com/listings/7a3354f0-44c7-43ea-8656-23814c9f393d) and [VoiceMaker TTS](https://www.fab.com/listings/0b0b84dd-04bf-4bb4-990d-b50cbf3ad15b) plugins)*.                  |
| 🔇    | **Remove noise**                          | Remove the background noise in the audio before processing the phonemes generation. |
| 🧏    | **Use speech recognition**                | Perform STT (remotly) on the provided audio to extract the text sentence. |
| 🌐    | **Language**                              | Select the speech language to improve accuracy. |
| 🗣️    | **Sentence**                              | The sentence being spoken (can include emotion tags).                       |
| 🏷️    | **Add tags to sentence** ❌ not working   | Insert tags like `<emotion happy>`. This feature is not working with the latest version, please manually write `<emotion EmotionName>` in the sentence where you want to change the emotion *(example: `Hello everyone. <emotion Happy> How are you doing?`)* |
| 📈    | **Advanced Settings > Amplitudes**         | Control phonemes generation minimum and maximum amplitude (will control how big the mouth opens to animate phonemes) |
| 🕑    | **Advanced Settings > Silences**          | Use tools like Audacity to find appropriate silence thresholds.             |
| ⏱️    | **Advanced Settings > Delay**               | Apply a global delay to all generated phonemes/emotions. Can be positive or negative. |
| 👄    | **Close Mouth At End Of Speech**          | Force to add a phoneme that closes the mouth at the end of the animation. |
| 🎞️    | **Sequencer Frame Rate**                 | Higher FPS = better edit control and better animation but use more performance. |
| 💾    | **Save as**                               | Choose between [Data Asset](API.md#4121-geppetto-data-asset) or [Sequencer](API.md#4122-geppetto-sequence). |
| 📁    | **Save as > At**                          | Specify the asset save location. Must be inside the project. Click "Choose" to open a save dialog window. |
</details>
</br>


**Once done**, choose a destination to save the generation. You can either save the generation as a [Data Asset](API.md#4121-geppetto-data-asset) or as a [Sequence](API.md#4122-geppetto-sequence). Geppetto Sequence can then be converted to Unreal Animation Asset. [See more](GettingStarted.md#26-export-lipsync-as-an-animation).

> [!TIP]
> See chapter [Play lip-sync on a character](#25-play-editor-lip-sync-assets-on-a-character) below to use and play your saved geppetto assets at runtime!


<br/>

## 2.5 Play Editor lip-sync assets on a character

As we talked about before, there are two assets that store generated phonemes: [Geppetto DataAsset](API.md#4121-geppetto-data-asset) and [Geppetto Sequence](API.md#4122-geppetto-sequence).    
Here is an example on how to use both types to play a lipsync animation on a character.

| Step                        | Geppetto Data Asset                                                                                                                                                                                                                                             | Geppetto Sequence                                                                                                                                          |
|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **1. Create Blueprint**     | Create a Blueprint class or use an existing one.                                                                                                                                                                                                                | Same logic here, use any Blueprint class or create a new one.                                                                                              |
| **2. Add Components**       | - Skeletal Mesh Component  <br> - Audio Component  <br> - `Geppetto SoundWave Player Component` *(or any child component)*  <br>  <br> ![](./images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_3.png)                | - Skeletal Mesh Component  <br> - Audio Component  <br> - `Geppetto SoundWave Player Component` *(or any child component)*  <br>  <br> ![](./images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_3.png)                             |
| **3. Create Variables**     | Create a variable of type `Geppetto DataAsset` and assign the previously generated DataAsset as its default value.     ![](./images/Getting_Started_image_10.png)                                                                                                  | Create a variable of type `Geppetto Sequence` and assign the previously generated Sequence as its default value.        ![](./images/Getting_Started_image_11.png)                                    |                                            |
| **4. Play Animation**       | Use `Play from Data Asset` node to play phonemes from a DataAsset.  <br>  <br> ![](./images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_5.png) | Use `Play from Sequence` node with a reference to the `Geppetto Sequence` asset.  <br>  <br> ![](./images/Play_a_Geppetto_Sequence_image_5.png)                           |

                
> [!NOTE]
> The `Geppetto Demo Player Component` can be subclassed to override default behavior. This is especially useful for custom characters or animation systems that require tailored playback logic or integration with other systems like emotion blending or gameplay triggers.   
> Please read the section concerning the [Geppetto Sound Wave Player Component](./API.md#42-geppetto-soundwave-player-component) for more information.

That is all about how to play a pre-generated lip-sync.   
You now have all the essentials to create your own animation and play it on any character.   
If you have any questions, please feel free to contact us by mail at support@xandimmersion.com or on our [Discord server](https://l.linklyhq.com/l/1fMJz).


<br/>

## 2.6 Export lipsync as an animation

With Geppetto, you can export a lipsync animation as an Animation Asset or as an FBX file, compatible with any external animation software.   
Here is a step-by-step tutorial to export your lipsync:

1. Generate a Geppetto Sequence asset as explained [above](#24-generate-phonemes-and-emotions-in-the-editor).
2. Open your new Geppetto Sequence and add a `Skeletal Mesh Asset`, a `PhonemeDataTable` and an `EmotionDataTable`.

![](./images/Export_a_Geppetto_Sequence_image_1.png)

> Be sure that these settings are valid as you will not be able to export your lipsync as an animation otherwise.

3. Right click on your new `GeppettoSequence`, then click on *Export as an AnimSequence*.

![](./images/Export_a_Geppetto_Sequence_image_2.png)

> Depending on your Skeletal Mesh Asset, the exportation might take some time (around 30s most of the time).

4. Your lipsync animation was successfully converted into an Animation asset.    
You can now use your lipsync as is or export it as a FBX.

![](./images/Export_a_Geppetto_Sequence_image_3.png)


<br/>

## 2.7 Generate phonemes and emotions on runtime

To generate and play lip-sync at runtime, such as from microphone input or a TTS system, you will need to follow these steps:

1. Create a new Blueprint Actor or open an existing one.

2. Add a `Skeletal Mesh Component`, an `Audio Component`, and the `GeppettoSoundWavePlayerComponent`.
> [!IMPORTANT]
> If your Skeletal Mesh Component uses an Animation Blueprint or a custom function to set Morph Targets (such as Metahumans). You must create a new child component that inherit from `GeppettoSoundWavePlayerComponent` and override the function 'Set Morph Target'.    
You can see on the `GeppettoDemoPlayerComponent` how this is done for the Demo player Actor. [More information](API.md#43-component-inheritance)

> [!NOTE]
> This also applies if your Blueprint Actor have multiple Skeletal Mesh Component. By default, the `GeppettoSoundWavePlayerComponent` will use the first found Skeletal Mesh Component using the node ***Get Component By Class***. In this case, please ensure that the Skeletal Mesh Component with the face Morph Targets is the first Component returned by ***Get Component By Class*** or create a new child component that inherit from `GeppettoSoundWavePlayerComponent` and override the function 'Set Morph Target'. [More information](API.md#43-component-inheritance)

![](./images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_3.png) 


>If you want to have audio spatialization, check the “Allow Spatialization” box and set a sound attenuation in the Audio Component (you can create a new one if needed) :

![](./images/Runtime_Phonemes_generation_and_animation__Blueprint__image_5.png)
</br>
</br>

3. Click on the **Skeletal Mesh Component** and assign the previously imported Mike Alger to it.

![](./images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_3b.png)

3. Click on the **Geppetto Component** and assign the corresponding Data Table for phonemes, emotions and micro expressions (use your own Data tables or use the predefined ones, like `DEMO_PhonemeTable`)

![](./images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_3c.png)

4. Add a new variable of type SoundWave to your Blueprint and set **SentenceExample_MaleVoice_1** *(or any other audio speech)* as default value.

![](./images/Getting_Started_image_7.png) 

> [!IMPORTANT]  
> Make sure to set the `Loading Behaviour Override` parameter to `Force Inline` to enable runtime lip-sync in a packaged project.    
**This setting is required for Unreal Engine version 5.2 and above.** Otherwise, The Geppetto Plugin won't be able to extract the audio data from the SoundWave at runtime!
> ![](./images/Getting_Started_image_12.png) 

> [!NOTE]
> You can also generate the audio at runtime and pass it into your SoundWave variable to use it in the runtime lip-sync. In this case, the SoundWave can be a `USoundWaveProcedural`   

5. Into your Event Graph, call the node [Generate Phonemes (using SoundWave)](API.md#481-generate-phonemes-using-soundwave) and place it after your BeginPlay or any nodes you want in order to call the function.     
Here, we will call the `Space Bar` which act as an event called the input **Space** is pressed.

6. Change the following parameters *([more information](API.md#481-generate-phonemes-using-soundwave))*: 

    - `Sound Wave` : Set your **SoundWave** variable
    - *(optional)* `Sentence` : Enter the audio speech text
    - `Quality` : Set it to **High**
    - *(optional)* `Close Mouth at End` : Set it to **true**
    - *(optional)* `Auto Emotion` : Set it to **true**
    - `Remove Noise` : Set it to **false**
    - `On Response` : Create a new custom event from this pin. We will call it `OnPhonemesGenerated`.

![](./images/Getting_Started_image_8.png)

> [!NOTE]
> For a better result with Mike Alger Skeletal Mesh, we recommand to use **Amplitude Settings** between 50 and 100,
> instead of the default values (30-70).  

![](./images/Getting_Started_image_8b.png)

7. On the `OnPhonemesGenerated` custom event, call the function [Play from Arrays](API.md#423-play-from-arrays) from `GeppettoSoundWavePlayerComponent` *(or any child component)*.

8. Bind the SoundWave parameter to your SoundWave variable. Bind the Phonemes and Emotions parameters to those in `OnPhonemesGenerated`.

![](./images/Getting_Started_image_9.png) 

> In our example we added a Branch node to ensure the validity of our generated phonemes and emotions.

**Well done! You learned how to generate and play a runtime lip-sync animation!**    


<br/>

## 2.8 Play an emotion on a character

You will need to use a [Geppetto Sound Wave Player Component](./API.md#42-geppetto-soundwave-player-component) or any inherited Component.

The [Geppetto Sound Wave Player Component](./API.md#42-geppetto-soundwave-player-component) allows you to control character facial animations in real time. You can change emotions using the [Change Emotion](API.md#416-change-emotion) node, specifying the emotion name, intensity (0–100), and transition time.     
 **Emotions must be defined in the Geppetto Component Emotion Data Table.**

 ![](./images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_3c.png)

 > [!TIP]
 > Emotions can be changed when a sentence is pronounced by using tags. Please read the section [Emotion Tag System](./Others.md#6-adding-emotion-tags) for more information on how to use tags. 

![](./images/Change_Emotions_image_3.png)

[More information about GeppettoEmotion struct](./API.md#4142-geppetto-emotion)

<br/>

## 2.9 Play a micro expression on a character

Micro-expressions, such as blinks or subtle twitches, can be triggered using either [Play Micro Expression](API.md#417-play-micro-expression) for single animations or [Start Micro Expression Loop](API.md#418-start-micro-expression-loop) to repeat them at random intervals.    
**Micro expressions must be defined in the Geppetto Component Micro Expression Data Table.**

![](./images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_3c.png)
![](./images/Play_or_Loop_Micro_Expressions_image_1.png) <!-- TODO rempalce image with one that does not have Get Micro Expression Optimal Parameters (does not exist outside of BP_ExampleActor) -->


[More information about GeppettoMicroExpression struct](./API.md#4143-geppetto-micro-expression)