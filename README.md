<h1 align="center">Edunime</h1>
<h3 align="center">

</h3>

> :warning: This project is in its early stages and is currently under **active development**.

> :warning: If you want to run the server remotely and access it on a different machine, such as running the server on your computer and access it on your phone, you will need to configure `https`, because the microphone on the front end will only launch in a secure context (a.k.a. https or localhost). See [MDN Web Doc](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia). Therefore, you should configure https with a reverse proxy to access the page on a remote machine (non-localhost).

## ⭐️ What is this project?

**Edunime** is a unique **voice-interactive AI companion** that not only supports **real-time voice conversations** and **visual perception** but also features a lively **Live2D avatar**. All functionalities can run completely offline on your computer!

You can treat it as your personal AI companion — whether you want a `Naruto`, `Batman` or any other character, it can meet your expectations. The project fully supports `Windows`, `macOS`, and `Linux`, and offers two usage modes: web version and desktop client (with special support for **transparent background desktop pet mode**, allowing the AI companion to accompany you anywhere on your screen).

Although the long-term memory feature is temporarily removed (coming back soon), thanks to the persistent storage of chat logs, you can always continue your previous unfinished conversations without losing any precious interactive moments.

In terms of backend support, we have integrated a rich variety of LLM inference, text-to-speech, and speech recognition solutions. If you want to customize your AI companion, you can refer to the [Character Customization Guide](https://open-llm-vtuber.github.io/docs/user-guide/live2d) to customize your AI companion's appearance and persona.

### Relevance to problem statement

Learning becomes truly engaging when it resonates with students' personal interests, transforming education from a routine task into an exciting adventure. By featuring Naruto Uzumaki as a live 2D AI tutor, this project taps into the deep connection many school students have with the Naruto anime, blending entertainment with education. Naruto’s energetic personality and familiar voice make lessons feel interactive and relatable, fostering focus and enthusiasm. This approach aligns perfectly with the idea of shaping lessons around what learners already love, turning abstract concepts into memorable experiences. It’s like having a favorite hero guide them through their studies, making learning fun, personal, and immersive.

### Work Logs

So, we first used Open LLM Vtuber as a base to create the UI for the character interaction and likes. We faced many issues while trying to use this UI, and after commenting out the parts that were giving issues and were not necessary for our project while resolving other issues, it worked.

One of the important issues we faced was the integration of Live2D characters with Open LLM Vtuber. Even after properly following the documentation we were not able to add Naruto Live2D. The issue seems to be with the texture of the character. After recreating the Live2D model’s texture the issue was fixed.

The API call for the LLM we are using is Deepseek. The prompt engineering was fairly simple, and with a clear instruction set, it performed very well on the given tasks.

Voice of character
One of the difficulties, we faced was reproducing the voice of Naruto, the online tools which were available were unable to produce a decent output, and even the ones which were paid didn’t give a workable output.
I first tried integrating AstraMindAI, a Text-to-Speech model based on XTTS2-GPT, which is open source. Its voice was good, but not up to the mark.
So, I moved to another open-source model called Fish. First, I used Triton accelerator, but it was giving issues and not working, I found that it was made for Linux library and often gives issues while running on Windows. So, I reconfigured my virtual environment without using the Triton library. Then, it ran on the CPU, and its compute time was around 2 minutes and 30 seconds for 2 sentences. We found it excessive, so we installed Cuda libraries and torch for Cuda, and after integrating the GPU, we brought the same compute time down to 27 sec. But, we were unable to use my laptop as a host, so we went with XTTS2-GPT API. but there were some implementation issues, so we went with stock audio.

Future Scope:
More characters can be added, which can cater to different student preferences.
A feature can be added to improve the character's animations to immersify the user, improve the knowledge base, and improve factual correctness and relevance.
Language support for other languages to widen the audience that can access.

### 👀 Demo

![](https://github.com/asli-nobita/Charactor-AI/blob/main/assets/Screenshot%20from%202025-03-22%2016-51-59.png)

## ✨ Features & Highlights

-   🖥️ **Cross-platform support**: Perfect compatibility with macOS, Linux, and Windows. We support NVIDIA and non-NVIDIA GPUs, with options to run on CPU or use cloud APIs for resource-intensive tasks. Some components support GPU acceleration on macOS.

-   🔒 **Offline mode support**: Run completely offline using local models - no internet required. Your conversations stay on your device, ensuring privacy and security.

-   💻 **Attractive and powerful web and desktop clients**: Offers both web version and desktop client usage modes, supporting rich interactive features and personalization settings. The desktop client can switch freely between window mode and desktop pet mode, allowing the AI companion to be by your side at all times.

-   🧠 **Extensive model support**:

    -   🤖 Large Language Models (LLM): Ollama, OpenAI (and any OpenAI-compatible API), Gemini, Claude, Mistral, DeepSeek, Zhipu AI, GGUF, LM Studio, vLLM, etc.
    -   🎙️ Automatic Speech Recognition (ASR): sherpa-onnx, FunASR, Faster-Whisper, Whisper.cpp, Whisper, Groq Whisper, Azure ASR, etc.
    -   🔊 Text-to-Speech (TTS): sherpa-onnx, pyttsx3, MeloTTS, Coqui-TTS, GPTSoVITS, Bark, CosyVoice, Edge TTS, Fish Audio, Azure TTS, etc.

-   🔧 **Highly customizable**:
    -   ⚙️ **Simple module configuration**: Switch various functional modules through simple configuration file modifications, without delving into the code
    -   🎨 **Character customization**: Import custom Live2D models to give your AI companion a unique appearance. Shape your AI companion's persona by modifying the Prompt. Perform voice cloning to give your AI companion the voice you desire
    -   🧩 **Flexible Agent implementation**: Inherit and implement the Agent interface to integrate any Agent architecture, such as HumeAI EVI, OpenAI Her, Mem0, etc.
    -   🔌 **Good extensibility**: Modular design allows you to easily add your own LLM, ASR, TTS, and other module implementations, extending new features at any time
