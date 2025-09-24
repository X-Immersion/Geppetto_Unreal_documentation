# Geppetto UE 2.0.0 – Others

This chapter documents all the components, nodes, structures, enums, and tools provided by the Geppetto plugin.


**[← Table of contents](../README.md#table-of-contents)**

---

### On this page

- **[Resources & General explanations](#5-resources--general-explanations)**
  - **[How does the Geppetto model work ?](#51-how-does-the-geppetto-model-work)**
  - **[Amplitude Calculation](#52-amplitude-calculation)**
- **[Adding Emotion Tags](#6-adding-emotion-tags)**
- **[Output](#7-output)**
- **[Known bugs](#8-known-bugs)**


---

## 5. Resources & General explanations

---

### 5.1. How does the Geppetto model work?

---

#### Text Acquisition

![](./images/RessourcesGeneral_image_1.png)

The text can either be provided directly or generated through Speech-to-Text, which also captures onomatopoeia. For the best results, it is recommended to provide a text that explicitly includes onomatopoeia. Emotion tags associated with the text are also extracted.

---

#### Text-to-Phoneme Conversion

The text is converted into phonemes using a machine learning model. This model is language-sensitive, and currently, Geppetto supports English, French, German, Italian, and Spanish.  
If additional language support is needed, please contact us.

![](./images/RessourcesGeneral_image_3.png)

---

#### Quality

![](./images/RessourcesGeneral_image_4.png)

There are four types of quality available, each of them uses a different combination of model, alignment with audio, and phonemizer:

##### Low

Use the fastest models for phonemes generation and alignment with audio. The results can sometimes be inaccurate.

##### Medium

Use a more precise model for phonemes generation. Still use the fastest model for phonemes alignment with audio.

##### High

Use the same model as 'Normal' for phonemes generation, but use a better model for alignment.

##### Highest

Use the most precise models for alignment. The generation is the same as 'Normal' and 'High'

#### Beta

Use the best model for phonemes generation (still in beta) and phoneme alignment. The phoneme generation time can be very long (>1min.) according to the audio length. *This parameter is still in Beta and might not work as expected*

---

#### Types of models and alignment with audio files.

##### Model 0

This is a machine learning model that aligns silences in the audio with punctuation in the text. Using linear interpolation between the segmented text and audio, it predicts the most probable phonemes for each sequence and assigns a corresponding timestamp based on its position in the text. 

- **Advantage**: This method is fast and requires minimal computing power, making it ideal for real-time applications.  
- **Limitation**: Since it relies on a simple mapping strategy, it may not perfectly capture variations in speech rhythm or nuanced pronunciations.

##### Model 1

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

## 5.2 Amplitude Calculation

![](./images/RessourcesGeneral_image_5.png)

The minimum amplitude is set as the lower bound between 0 and 100, based on the detected phoneme amplitude. This ensures that the phoneme remains visible during execution, even when its natural amplitude is very low.

Similarly, the maximum amplitude acts as an upper limit to prevent excessive deformation of blendshapes, maintaining more natural transitions.

The amplitude sinus step defines the incremental step between two consecutive phonemes' amplitudes, preventing abrupt jumps. This value ranges between 0 and 1:

1. The closer it is to 1, the more significant the amplitude variations between phonemes can be.

2. Lower values ensure smoother transitions, reducing sudden amplitude shifts.

## 6. Adding Emotion Tags

![](./images/RessourcesGeneral_image_6.png)

Emotion tags are integrated into the audio at the appropriate timestamps based on their placement within the sentence, ensuring that the speaker’s tone and emotional expression are accurately reflected.

![](./images/RessourcesGeneral_image_7.png)

You can also enable the automatic emotion detection parameter. Using a deep learning model, it predicts the most appropriate emotion based on both the text and the audio.

Disable this option if you prefer maximum control and optimized performance speed.

### Syntax

`<emotion name intensity 80 transition 300 function_type linear>`


### Parameters

| Parameter         | Description                               | Default      |
|---------------|-------------------------------------------|--------------|
| emotion       | Name of the emotion                       | (required)   |
| intensity     | Intensity (0-100)                         | 50           |
| transition    | Transition time in ms                     | 200          |
| function_type | Interpolation function (linear, cubic…)  | cubic        |

### Example

![](./images/Emotion_Tag_System_image_1.png)

![](./images/Emotion_Tag_System_image_2.png)

You can mix tags with runtime Blueprint emotion changes for full control.
Please read section [Play an emotion on a character](./GettingStarted.md#28-play-an-emotion-on-a-character) of the documentation for more details on how to change an emotion at Runtime using Blueprints.

## 7. Output

The final output is a structured list of (phoneme, timestamp, amplitude). This list is returned via API, but the computation can also be performed locally for real-time deployment in player environments. Please contact us for this option.

---

## 8. Known bugs

**The plugin shows control-related errors**

If some controls used (named like `CTRL_expressions_…`) are missing in the MetaHuman and you have error messages when you try to initialize the Geppetto Player Component, it is probably due to the MetaHuman version.

✅ Make sure that you have downloaded the MetaHuman with the same Unreal Engine version that you are using for your project.

- MetaHumans downloaded with **UE5.0 and 5.1** are compatible with **UE5.0, 5.1 and 5.2**
- MetaHumans downloaded with **UE5.2 and 5.3** are compatible with **UE5.2 and 5.3**
