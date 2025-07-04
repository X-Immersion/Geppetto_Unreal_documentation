# Geppetto UE 2.0.0 – Getting Started

**[← Table of contents](../README.md#table-of-contents)**

---

### On this page

- **[What is Geppetto ?](#21-what-is-geppetto)**
- **[Character setup](#22-character-setup)**
- **[Geppetto Data Tables](#23-geppetto-data-tables)**
- **[Generate phonemes and emotions in the editor](#24-generate-phonemes-and-emotions-in-the-editor)**
- **[Generate phonemes and emotions on runtime](#245-generate-phonemes-and-emotions-on-runtime)**
- **[Play lip-sync on a character](#25-play-lip-sync-on-a-character)**
- **[Play an emotion or a micro expression on a character](#255-play-an-emotion-or-a-micro-expression-on-a-character)**

---

## 2.1 What is Geppetto ?

**Geppetto is a facial animation and lip-sync plugin for Unreal Engine, designed to automatically generate lip-sync animations from audio or text files.**

**The latest version (2.0.1) introduces the Geppetto Sequence Editor, enabling advanced customization of lip-sync animations with precise timing and amplitude adjustments for morph targets. This version also includes new features like automatic emotion detection and improved voice recognition.**

## 2.2 Character setup

For this example, we will use this  [rigged character](https://sketchfab.com/3d-models/rigged-t-pose-human-male-w-50-face-blendshapes-cc7e4596bcd145208a6992c757854c07) made by [Mike Alger](https://mikealger.com/).    
This character possess 50 face blendshapes that we will use to create a lip-sync animation.

Here are the steps to set up the character in Unreal :

1. Download the character in FBX format from sketchfab with the link given above.
2. Unzip the character archive wherever you want.
3. Create a new Unreal project or open an existing one.
4. Drag and drop the fbx file of the character in the wanted folder. Here we will place it inside the "Example" folder.
5. **Do not forget to import the MorphTarget by checking the appropriate boxes and click on "Import".**

![](./images/Getting_Started_image_1.png)


6. To ensure the character was correctly imported, open the skeletal mesh asset and go into the "MorphTargets" tab. Here you should have the 50 blendshapes.

![](./images/Getting_Started_image_2.png)

> [!NOTE]  
> The "MorphTargets" tab may vary a bit depending of your version of the engine but the content still remains the same. 

**Well done ! Your character is now setup and can be used with Geppetto !**    
Check the next steps to learn how to bind Geppetto to your character and play a lip-sync animation.



## 2.3 Geppetto Data Tables

### 2.3.1 Phoneme Data Table

**The Geppetto Phoneme Data Table in Unreal Engine is designed to drive facial animation through phoneme-based lip sync.**    
Each row represents a phoneme (like A, E, U, etc.) and contains values for Morph Targets, which are specific facial poses. This allows for detailed, expressive character dialogue.    
Here is an example with the **DEMO_PhonemesTable** that convert phonemes into the blendshapes of the rigged character we just imported :

![](./images/Getting_Started_image_4.png)

You can either create a new Phoneme DataTable in Unreal or import an existing one from a csv or json file.    
Predefined tables are available under Plugins > Geppetto Content > Phonemes, and you’re free to duplicate or customize them.    
For more information, please see [4.5 Geppetto Phoneme Data Table](./API.md#45-geppetto-phoneme-data-table).

> [!NOTE]  
> If you do not see the **Plugins** folder or the **Geppetto Content** folder, click on **"Settings"** in the **Content Browser** and tick **"Show Plugin Content"**.     
>If the Geppetto is installed within the Engine and not the project, you also have to tick **"Show Engine Content"**. 
>
>![Show where is the Engine and Plugin Content options](./images/How_to_open_the_demo_level_image_1.png)


### 2.3.2 Emotion Data Table

The Geppetto Emotion Data Table is used to animate facial expressions tied to emotions. Each row corresponds to an emotion (like Happy, Sad, Angry, etc.) and specifies Morph Target values that sculpt the facial mesh into an expressive pose. This is ideal for customizing character emotion systems in Unreal Engine.    
Here is an example with the **DEMO_EmotionsTable** that convert emotions into the blendshapes of the rigged character we just imported :

![](./images/Getting_Started_image_5.png)

You can either create a new Emotion DataTable in Unreal or import an existing one from a csv or json file. 
Predefined tables are available under Plugins > Geppetto Content > Emotions, and you’re free to duplicate or customize them.
For more details, see [4.6 Geppetto Emotion Data Table](./API.md#46-geppetto-emotion-data-table).

### 2.3.3 Micro-expression Data Table

The Geppetto Micro Expressions Data Table defines subtle facial movements like blinks or eyebrow twitches. Each row maps a micro expression to Morph Target values, either fixed or dynamic.     
Dynamic targets introduce random variation to keep animations lively and natural.

![](./images/Geppetto_MicroExpressions_DataTable_image_5.png)

You can either create a new Micro Expression DataTable in Unreal or import an existing one from a csv or json file.   
For more information, see [4.7 Geppetto Micro Expressions Data Table](./API.md#47-geppetto-micro-expressions-data-table).

## 2.4 Generate phonemes and emotions in the editor

To pre-generate phonemes, you can use the Editor Utility Widget included in the plugin.     
You can open the Window by clicking on the Geppetto icon button or in the menu **Help > Geppetto**:

![](./images/Pre_Generate_Phonemes_image_1.png)
![](./images/Pre_Generate_Phonemes_image_2.png)

The interface will open. It contains several parameters to customize your phonemes and emotions generation.     
To find a complete list of all parameters and what they are doing, please read the part [3.1.1 Pre-Generate Phonemes as a Geppetto Data Asset](./Features.md#31-pre-generated-data-asset-editor).

![](./images/Getting_Started_image_3.png)

Here a the following steps to generate a basic lip-sync animation :

1. Pass your audio file in the `Audio` parameter.    
For this example, we will use **SentenceExample_MaleVoice_1** which is available in the plugin folder if you want to use it.

2. We will check the checkbox `Use speech recognition` to tell Geppetto to only use the audio file to create the lipsync animation.

3. For `Phonemes settings` and `Emotions settings`, please use the **DEMO_PhonemesTable** and **DEMO_EmotionsTable**.   
These two tables are made for the rigged character we chose previously.
They will convert the generated phonemes and emotions into blendshapes that can animate our character.

4. Enable `Use auto emotions` checkbox to allow Geppetto to automatically detect emotions in your audio file.

5. Then, choose in which asset store your generated phonemes with the `Save file as` parameter.    
There is two types of asset : [Geppetto DataAsset](./API.md#410-data-assets) and [Geppetto Sequence](./API.md#411-geppetto-sequence). Each of them has different use case.   
[Below](#26-play-lip-sync-on-a-character), you will find an example on how to use both assets.

6. Finally, hit the `Generate Phonemes` button to generate your .uasset file.     
**This may take a while according to the audio duration and other parameters.**

If you want to start the customization of your generated phonemes now, here are some parameters that might be useful :

- `Quality` : As the name suggests, you can define the overall quality of your pre generated lip-sync.  
Better quality also means higher generation time.    
**We recommend that your audio does not last more than 10 seconds.**

- `Language`: If your audio is not in English, select your language from this dropdown.    
**Adjusting this setting helps Geppetto better capture the unique characteristics of the chosen language.**

- `Emotion` : Click on this setting to add an emotion tag in your sentence. Emotion tag are used to specify a particular emotion at a chosen moment.  
For more information about this feature, please see chapter [3.5 Emotion Tag System](./Features.md#35-emotion-tag-system)

## 2.5 Generate phonemes and emotions on runtime

To generate and play lip-sync at runtime—such as from microphone input or a TTS system, you will need to follow these steps :

1. Create a new Blueprint or open an existing one.

2. Add a `Skeletal Mesh Component`, an `Audio Component`, the `Geppetto SoundWave Player`, and the `Geppetto Player Component`.

![](./images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_3.png) 

3. On BeginPlay, initialize both Geppetto components with their `Initialize` function.   
For the `Geppetto Player Component`, please provide the Phonemes, Emotions and Micro expressions tables you want to use.    
In this case, we will use once again the **DEMO** tables as they are adapted for our rigged character.

![](./images/Getting_Started_image_6.png) 

4. Add a new variable of type SoundWave to your Blueprint and set **SentenceExample_MaleVoice_1** as default value.

![](./images/Getting_Started_image_7.png) 

> [!IMPORTANT]  
> Make sure to set the `Loading Behaviour Override` parameter to `Force Inline` to enable runtime lip-sync in a packaged project.    
**This setting is required for Unreal Engine version 5.2 and above.**
> ![](./images/Getting_Started_image_12.png) 

> Note that you could also generate the audio at runtime as pass it into your SoundWave variable to use it in the runtime lip-sync.    
For more details, please check this [part](./Features.md#32-runtime-phonemes-generation-and-animation-blueprint).

5. Into your Event Graph, call the node `Generate Phonemes (using SoundWave)` and place it after your BeginPlay or any nodes you want in order to call the function.     
Here, we will call the `Space Bar` which act as an event called the input **Space** is pressed.


6. Change the following parameters :

    - `Sound Wave` : Set your **SoundWave** variable
    - `Quality` : Set **High**
    - `Close Mouth at End` : Set it to **true**
    - `Auto Emotion` : Set it to **true**
    - `Remove Noise` : Set it to **false**
    - `On Response` : Create a new custom event from this pin. We will call it `OnPhonemesGenerated`.

![](./images/Getting_Started_image_8.png) 

7. On the `OnPhonemesGenerated` custom event, call the function `Play` from `Geppetto Sound Wave Synchronizer`.

8. Bind the Audio parameter to your SoundWave variable. Bind the Phonemes and Emotions parameters to those in `OnPhonemesGenerated`.

![](./images/Getting_Started_image_9.png) 

> In our example we added a Branch node to ensure the validity of our generated phonemes and emotions.

**Well done ! You learned how to generate and play a runtime lip-sync animation !**    

See full details in [3.2 Runtime Phonemes Generation and Animation](./Features.md#32-runtime-phonemes-generation-and-animation-blueprint).

## 2.6 Play lip-sync on a character

As we talked about before there is two assets that stores generated phonemes : [Geppetto DataAsset](./API.md#410-data-assets) and [Geppetto Sequence](./API.md#411-geppetto-sequence).    
Here is an example on how to use both types to play a lipsync animation on a character.

| Step                        | Geppetto Data Asset                                                                                                                                                                                                                                             | Geppetto Sequence                                                                                                                                          |
|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **1. Create Blueprint**     | Create a Blueprint class or use an existing one.                                                                                                                                                                                                                | Same logic here, use any Blueprint class or create a new one.                                                                                              |
| **2. Add Components**       | - Skeletal Mesh Component  <br> - Audio Component  <br> - `Geppetto SoundWave Player`  <br> - `Geppetto Player Component` (or custom Metahuman version)  <br>  <br> ![](./images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_3.png)                | - Skeletal Mesh Component  <br> - `Geppetto Sequencer Component`  <br>  <br> ![](./images/Play_a_Geppetto_Sequence_image_3.png)                             |
| **3. Create Variables**     | Create a variable of type `Geppetto DataAsset` and assign the previously generated DataAsset as its default value.     ![](./images/Getting_Started_image_10.png)                                                                                                  | Create a variable of type `Geppetto Sequence` and assign the previously generated Sequence as its default value.        ![](./images/Getting_Started_image_11.png)                                    |
| **4. Initialize on BeginPlay** | - Call `Geppetto SoundWave Player Initialize`  <br> - Call `Geppetto Player Component Initialize`  <br>  <br> ![](./images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_4.png)                                                                    | - Call `Geppetto Sequencer Component Initialize`  <br>  <br> ![](./images/Play_a_Geppetto_Sequence_image_4.png)                                             |
| **5. Play Animation**       | Use `Play Data Asset` node to play phonemes in sync with audio or the `Play` node for advanced options.  <br>  <br> ![](./images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_5.png)  <br> ![](./images/Play_a_Geppetto_Data_Asset_with_SoundWave_image_6.png) | Use `Play` node with a reference to the `Geppetto Sequence` asset.  <br>  <br> ![](./images/Play_a_Geppetto_Sequence_image_5.png)                           |

                
> Both the `Geppetto Player Component` and `Geppetto Sequencer Component` can be subclassed to override default behavior. This is especially useful for custom characters or animation systems that require tailored playback logic or integration with other systems like emotion blending or gameplay triggers.

That is all about how to play a pre-generated lip-sync.   
You now have all the essentials to create you own animation and play it on any character.   
If you have any question, please feel free to contact us by mail or on Discord.

## 2.7 Play an emotion or a micro expression on a character

Either you used a Geppetto DataAsset or a Geppetto Sequence, you will need to use a [Geppetto Player Component](./API.md#43-geppetto-player-component).

The [Geppetto Player Component](./API.md#43-geppetto-player-component) allows you to control character facial animations in real time. You can change emotions using the `Change Emotion` node, specifying the emotion name, intensity (0–100), and transition time.      **Emotions must be defined in the Emotion Data Table.**

![](./images/Change_Emotions_image_3.png)

Micro-expressions, such as blinks or subtle twitches, can be triggered using either `Play Micro Expression` for single animations or `Start Micro Expression Loop` to repeat them at random intervals.    
**Each expression must exist in the Micro Expressions Data Table.**

![](./images/_Play_or_Loop_Micro_Expressions_image_1.png)

> You are free to customize timing, intensity, and playback speed for natural, lifelike results.    
For more control, stop any loop with `Stop Micro Expression Loop`.

For further details, see [3.3 Change Emotions](./Features.md#33-change-emotions) and [3.4 Play or Loop Micro Expressions](./Features.md#34-play-or-loop-micro-expressions).