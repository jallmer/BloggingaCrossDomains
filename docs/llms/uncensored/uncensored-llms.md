---
title: Uncensored LLMs
date: 2024-11-01
draft: false
tags:
  - LLM
  - uncensored
  - conversation
  - ollama
---

So, I installed [Ollama](https://ollama.com/) on my Macbook and a PC with GPU to run large language models locally. My aim is to get aid for programming tasks. I experienced some issues while [installing Ollama](ollama) on a high-performance computing cluster. During model selection, I stumbled across the word uncensored in some of the models. Of course, I was intrigued. I thought to myself, let's download one of them and have some fun. Imposing censorship on LLM models is like putting locks on guns and knives. I think this needs a deeper societal discussion on whether some ethics imposed by some companies should be applied or whether, with the growing maturity of a person, the person may have access to uncensored models. Also, it is important to develop a universal censoring mechanism imposed by society and not by companies. What about scientific research? How could we push scientific boundaries without asking questions that some may perceive as unethical? Hence, different rules must apply to different situations. All this said, let's have a look at some models.

**Models tested so far**

[gdisney/mixtral-uncensored](llm-gdisney-mixtral-uncensored) (26 GB), little evilness.

[gdisney/phi-uncensored](llm-gdisney-phi-uncensored) (1.6 GB), utterly useless!

[ollama run eas/wizardlm-uncensored:33b-q3_k_m](llm-eas-wizardlm-uncensored-33b-q3_k_m) (15 GB), completely useless!

[ollama run mannix/llama3-uncensored](llm-mannix-lamma3-uncensored) (4.7 GB), fully censored!

So far (2024-10-21), only mixtral-uncensored offered the tiniest bit of fun. Did the term uncensored change meaning recently, or am I using the wrong definition?

The chatgpt o1-preview model seems to agree with me: _The term **"uncensored"** refers to content that has not been altered, edited, or suppressed by any form of censorship. This means it is presented in its original, complete form without any modifications or omissions, even if the material includes elements that some might find objectionable, sensitive, or inappropriate. Uncensored content allows for the full and unrestricted expression of ideas, information, language, or images._

A quick Google check ensures that this is also the meaning in the major dictionaries. None of this holds true for the models I have tested so far. I am a bit hesitant to test more models. Likely, my curiosity will prevail.

Perhaps someone reviewed uncensored models before. [Here is a post about the top 10 uncensored LLMs](https://anakin.ai/blog/uncensored-llms/). I should try these next! I first selected the dolphin-mixtral:8x22b model but that was too much for my Macbook so I settled for the smaller model: dolphin-mixtral:8x7b.

[dolphin-mixtral:8x7b](llm-dolphin-mixtral-8x7b) (26 GB), needed a small push, but seems OK