<h1 align="center">Edunime</h1>
<h3 align="center">

</h3>

> :warning: This project is in its early stages and is currently under **active development**.

Link for frontend repository: [Edunime-frontend](https://github.com/asli-nobita/Edunime-AI-Frontend)
same as Open-LLM Vtuber repository.

## ⭐️ What is this project?

![](https://github.com/asli-nobita/Charactor-AI/blob/main/assets/Screenshot%20from%202025-03-22%2016-51-59.png)

**Edunime** is a unique **voice-interactive AI companion** that not only supports **real-time voice conversations** and **visual perception** but also features a lively **Live2D avatar**. All functionalities can run completely offline on your computer!

You can treat it as your personal AI companion — whether you want a `Naruto`, `Batman` or any other character, it can meet your expectations. The project fully supports `Windows`, `macOS`, and `Linux`.

### What we did:

We used OpenLLM Vtuber as a front end for our Naruto avatar, which we modelled. We did the prompt engineering for the LLM we used. We used Gemini Flash 2.0 Exp for API calls. We used the Edge-TTS model for text-to-speech conversion.
This is an end product which can be used to interact with Naruto Uzumaki, a famous anime character.

### Relevance to problem statement

Learning becomes truly engaging when it resonates with students' personal interests, transforming education from a routine task into an exciting adventure. By featuring Naruto Uzumaki as a live 2D AI tutor, this project taps into the deep connection many school students have with the Naruto anime, blending entertainment with education. Naruto’s energetic personality and familiar voice make lessons feel interactive and relatable, fostering focus and enthusiasm. This approach aligns perfectly with the idea of shaping lessons around what learners already love, turning abstract concepts into memorable experiences. It’s like having a favorite hero guide them through their studies, making learning fun, personal, and immersive.

### Work Logs

So, we first used Open LLM Vtuber as a base to create the UI for the character interaction and likes. We faced many issues while trying to use this UI, and after commenting out the parts that were giving issues and were not necessary for our project while resolving other issues, it worked.

One of the important issues we faced was the integration of Live2D characters with Open LLM Vtuber. Even after properly following the documentation we were not able to add Naruto Live2D. The issue seems to be with the texture of the character. After recreating the Live2D model’s texture the issue was fixed.

The API call for the LLM we are using is **Gemini 2.0 Flash Exp**. The prompt engineering was fairly simple, and with a clear instruction set, it performed very well on the given tasks.

Voice of character
One of the difficulties, we faced was reproducing the voice of Naruto, the online tools which were available were unable to produce a decent output, and even the ones which were paid didn’t give a workable output.
We first tried integrating AstraMindAI, a Text-to-Speech model based on XTTS2-GPT, which is open source. Its voice was good, but not up to the mark.
So, We moved to another open-source model called Fish. First, we used Triton accelerator, but it was giving issues and not working, we found that it was made for Linux library and often gives issues while running on Windows. So, we reconfigured my virtual environment without using the Triton library. Then, it ran on the CPU, and its compute time was around 2 minutes and 30 seconds for 2 sentences. We found it excessive, so we installed Cuda libraries and torch for Cuda, and after integrating the GPU, we brought the same compute time down to 27 sec. But, we were unable to use our laptops as host, so we went with **Edge-TTS**.

Future Scope:

-   More characters can be added, which can cater to different student preferences.
-   A feature can be added to improve the character's animations to boost user engagement and immersion.
-   Improve the knowledge base, and improve factual correctness and relevance.
-   Language support for other languages to widen the audience that can access.

We used OpenLLM Vtuber as a base and built upon that because we wanted to use front-end compatibilities. Hence, the number of contributors and extra files which may not be used in this project.

## How to run locally

1. Clone both repositories (Charactor-AI and Edunime-AI-Frontend).  
   `git clone https://github.com/asli-nobita/Charactor-AI.git`  
   `git clone https://github.com/asli-nobita/Edunime-AI-Frontend.git`

2. Navigate to the root directory `Charactor-AI` and run  
   `pip install .`

3. In the same directory, execute  
   `python run_server.py`

4. Navigate to the frontend directory and run this command  
   `npm install && npm run dev`  
   The application should start as an Electron desktop app.

### Demo

[![Video Thumbnail](https://img.youtube.com/vi/qAW1GG19-Og/0.jpg)](https://www.youtube.com/watch?v=qAW1GG19-Og)
