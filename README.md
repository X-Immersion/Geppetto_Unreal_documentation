![Logo](./docs/images/General_image_1.png)

Welcome to the **Geppetto UE Plugin** for Unreal Engine. This document will show you how to use the plugin in Unreal Engine.

**Geppetto is a facial animation and lip-sync plugin for Unreal Engine, designed to automatically generate lip-sync animations from audio or text files.**

**The latest version (2.1.0) introduces a better lipsync render and the ability to export your Geppetto sequence as an animation asset, enabling versatility and increased customization. This version also includes new features like headshift.**


# Table of contents

### **[Setup](./docs/Setup.md)**

- **[Prerequisites](./docs/Setup.md#11-prerequisites)**
- **[Metahuman](./docs/Setup.md#12-metahuman)**
- **[Installation – Fab](./docs/Setup.md#13-installation---fab)**
- **[Installation – Source Code](./docs/Setup.md#14-installation---source-code)**

### **[Getting Started](./docs/GettingStarted.md)**

- **[What is Geppetto ?](./docs/GettingStarted.md#21-what-is-geppetto-)**
- **[Character setup](./docs/GettingStarted.md#22-character-setup)**
- **[Geppetto Data Tables](./docs/GettingStarted.md#23-geppetto-data-tables)**
  - **[Phoneme Data Table](./docs/GettingStarted.md#231-phoneme-data-table)**
  - **[Emotion Data Table](./docs/GettingStarted.md#232-emotion-data-table)**
  - **[Micro Expression Data Table](./docs/GettingStarted.md#233-micro-expression-data-table)**
  - **[Headshift Data Table](./docs/GettingStarted.md#234-headshift-data-table)**
- **[Generate phonemes and emotions in the editor](./docs/GettingStarted.md#24-generate-phonemes-and-emotions-in-the-editor)**
- **[Play editor lip-sync assets on a character](./docs/GettingStarted.md#25-play-editor-lip-sync-assets-on-a-character)**
- **[Export lipsync as an animation](./docs/GettingStarted.md#26-export-lipsync-as-an-animation)**
- **[Generate phonemes and emotions on runtime](./docs/GettingStarted.md#27-generate-phonemes-and-emotions-on-runtime)**
- **[Play an emotion on a character](./docs/GettingStarted.md#28-play-an-emotion-on-a-character)**
- **[Play a micro expression on a character](./docs/GettingStarted.md#29-play-a-micro-expression-on-a-character)**

### **[Demo](./docs/Demo.md)**

- **[How to Open the Demo Level](./docs/Demo.md#21-how-to-open-the-demo-level)**
- **[Play with the Demo Level](./docs/Demo.md#22-play-with-the-demo-level)**
- **[Understand the Demo Level](./docs/Demo.md#23-understand-the-demo-level)**

### **[API](./docs/API.md)**

#### *Components*
- **[Geppetto Base Component](./docs/API.md#41-geppetto-base-component)**
- **[Geppetto Sound Wave Player Component](./docs/API.md#42-geppetto-soundwave-player-component)**
- **[Component Inheritance](./docs/API.md#43-component-inheritance)**

#### *Data Tables*
- **[Phoneme Data Table](./docs/API.md#44-geppetto-phoneme-data-table)**
- **[Emotion Data Table](./docs/API.md#45-geppetto-emotion-data-table)**
- **[Micro expression Data Table](./docs/API.md#46-geppetto-micro-expressions-data-table)**
- **[Headshift Data Table](./docs/API.md#47-geppetto-headshift-data-table)**

#### *Blueprint Libraries (Nodes)*
- **[Geppetto BP Library](./docs/API.md#48-geppetto-blueprint-library)**
  - **[Generate phonemes (using SoundWave)](./docs/API.md#481-generate-phonemes-using-soundwave)**
  - **[Generate phonemes (using PCM bytes)](./docs/API.md#482-generate-phonemes-using-pcm-bytes)**
  - **[Generate phonemes (using File bytes)](./docs/API.md#483-generate-phonemes-using-file-bytes)**
  - **[Apply Delay (phonemes)](./docs/API.md#484-apply-delay-phonemes)**
  - **[Apply Delay (emotions)](./docs/API.md#485-apply-delay-emotions)**
  - **[Get Morph Targets for Phoneme](./docs/API.md#486-get-morph-targets-for-phoneme)**
  - **[Get Morph Targets for Emotion](./docs/API.md#487-get-morph-targets-for-emotion)**
  - **[Safe Lerp](./docs/API.md#488-safe-lerp)**

- **[Curve Generator BP Library](./docs/API.md#49-geppetto-curve-generator-blueprint-library)**
  - **[Create Phoneme Curves](./docs/API.md#491-create-phoneme-curves)**
  - **[Create Emotion Curves](./docs/API.md#492-create-emotion-curves)**
  - **[Create All Curves](./docs/API.md#493-create-all-curves)**
  - **[Extract Phonemes and Emotions from Sequence](./docs/API.md#494-extract-phonemes-and-emotions-from-sequence)**
  - **[Get Curves Max Time](./docs/API.md#495-get-curves-max-time)**

- **[Headshift BP Library](./docs/API.md#410-geppetto-headshift-blueprint-library)**
  - **[Initialize new Movement](./docs/API.md#4101-initialize-new-movement)**
  - **[Update Generic Movement](./docs/API.md#4102-update-generic-movement)**
  - **[Blend Emotion Headshift](./docs/API.md#4103-blend-emotion-headshift)**

- **[Geppetto Editor BP Library *(Editor only)*](./docs/API.md#411-geppetto-blueprint-library-editor-only)**
  - **[Save Geppetto Phonemes as Data Asset](./docs/API.md#4111-save-geppetto-phonemes-as-data-asset)**
  - **[Save as Sequence](./docs/API.md#4112-save-as-sequence)**
  - **[Convert Geppetto Sequence into animation](./docs/API.md#4113-convert-geppetto-sequence-into-animation)**
  - **[Create editor Data Preset](./docs/API.md#4114-create-editor-data-preset)**
  - **[Show Save File Selection Dialog](./docs/API.md#4115-show-save-file-selection-dialog)**
  - **[Get Documentation URL](./docs/API.md#4116-get-documentation-url)**
  - **[Is PIE Mode Active](./docs/API.md#4117-is-pie-mode-active)**

#### *Assets*
- **[Geppetto DataAsset](./docs/API.md#4121-geppetto-data-asset)**
- **[Geppetto Sequence](./docs/API.md#4122-geppetto-sequence)**
- **[Geppetto Preset DataAsset *(Editor only)*](./docs/API.md#4123-geppetto-preset-data-asset-editor-only)**

#### *Enums*
- **[Emotion Transition](./docs/API.md#4131-geppetto-emotion-transition)**
- **[Format](./docs/API.md#4132-geppetto-format)**
- **[Language](./docs/API.md#4133-geppetto-language)**
- **[Quality](./docs/API.md#4134-geppetto-quality)**
- **[Sequence FPS](./docs/API.md#4135-geppetto-sequence-fps)**

#### *Structs*
- **[Phoneme](./docs/API.md#4141-geppetto-phoneme)**
- **[Emotion](./docs/API.md#4142-geppetto-emotion)**
- **[Micro expression](./docs/API.md#4143-geppetto-micro-expression)**
- **[Dynamic Micro expression](./docs/API.md#4144-dynamic-micro-expression)**
- **[Headshift Movement](./docs/API.md#4145-geppetto-headshift-movement)**
- **[Headshift Data](./docs/API.md#4146-geppetto-headshift-data)**
- **[Emotion Headshift](./docs/API.md#4147-geppetto-emotion-headshift)**
- **[Amplitude](./docs/API.md#4148-geppetto-amplitude)**
- **[Silence](./docs/API.md#4149-geppetto-silence)**
- **[Response Settings](./docs/API.md#41410-geppetto-response-settings)**
- **[Tuple Float](./docs/API.md#41411-tuple-float)**

### **[Others](./docs/Others.md)**

- **[Resources & General explanations](./docs/Others.md#5-resources--general-explanations)**
  - **[How does the Geppetto model work ?](./docs/Others.md#51-how-does-the-geppetto-model-work)**
  - **[Amplitude Calculation](./docs/Others.md#52-amplitude-calculation)**
- **[Adding Emotion Tags](./docs/Others.md#6-adding-emotion-tags)**
- **[Output](./docs/Others.md#7-output)**
- **[Known bugs](./docs/Others.md#8-known-bugs)**


# Contact

If you have any question, do not hesitate to contact us through our [Discord server](https://discord.gg/qDMwNCDE8X) or by mail at [support@xandimmersion.com](mailto:support@xandimmersion.com).
