---
title: "Ollama"
date: 2024-11-21
draft: false
tags:
  - LLM
  - ollama
  - HPC
  - models
  - setup
  - instructions
  - model directory
---

[Ollama](https://ollama.com/) is a convenient tool for quickly setting up a local LLM. Indeed, every prepper must have it on their system. 

The [setup of Ollama](https://github.com/ollama/ollama/) is unspectacular, and you can simply follow the instructions or use an installable. That should be done in a few minutes. You can then run any of the many [available models](https://ollama.com/search). Make sure to first start the server (ollama serve) and then load (ollama load llama3.2) or run (ollama run mistral) the model you choose. 

Now, this caused me a headache. 
On an HPC I have a small user directory. However, ollama stores models by default in a hidden directory under the user root (~/.ollama). Pulling a few models (llama3.2, granite, and mistral) filled up the available space. 

After some research, I found that the model directory can be set with an environment variable (export OLLAMA_MODELS="path to the root of the model dir"). Great. So, I copied the models to a different space on the HPC and set the variable accordingly. Surely, that should work -- No!  
OK, stupid, there is an (ollama cp) function for copying models. Turns out that this only copies models within the model directory using the name of the model and the desired new name of the model. (ollama cp source destination) sounds as if it might be possible to work with file paths. Maybe (ollama cp model new_model_name) would be more explicit?
So again, it's not working.
After some deliberation and frustration with trying various approaches to get the models onto the calculation node within the HPC, the only way that works is by pulling them from the internet. That is, of course, not acceptable for many reasons. 
I had to give up on the idea of copying the models locally, which is apparently not a use case. I also keep the executable in the same place on the HPC (there is a shared file space (lustre)). I do this because Ollama comes with checks that ensure that it downloaded the models, etc., so if I install it again each time I run it on a different node of the HPC, it might not recognize the models as its own and would download them again.  

# **Working strategy**
1) Select a shared directory that all nodes have access to.
2) create an ollama directory and unpack ollama into it. That will create a bin and a lib directory. The ollama executable is in the bin directory and can be used directly.
3) create an ollama_models directory (e.g., in the ollama directory).
4) export the environment variable to point to the ollama_models dir (export OLLAMA_MODELS="... /ollama/models"). 
5) start the ollama server (!you must do 4) first!) by calling ... /ollama/bin/ollama serve. Now, this will block your terminal so you can continue on a different terminal, but for me, that is inconvenient since there are many login nodes on the HPC, and they usually get transferred to a different one. Hence, the server would be invisible. Therefore, I like to start it in the background: "... /ollama serve > SERVER_LOG 2>&1 &". 
6) Now that you pointed to the desired models directory and you started the server, you can load or run models and they will appear in the desired directory. E.g., "... /ollama run llama3.2" will download the llama3.2 model and store it in the desired directory. 
7) Now, you can access the models and the Ollama executable from anywhere where you can see the shared file system. Furthermore, the home directory, which is often rather small, is not filled up with potentially large models of tens of gigabytes. 

That is not exactly what I wanted, but it works. And the small overhead of reading the model and executable from the file system once is irrelevant to me. If you were to start Ollama thousands of times on a node, that could cause issues, and then you might want to actually download Ollama and the models to the node in the first step (you might want to use a RAM disk). Subsequently, all steps are similar to the above. 

## That's it
Or is it? 
No, one more thing.
You might want to stop the Ollama server. However, that is not a supported use case. Ollama stop does not exist. Instead, it is ollama stop model_name, which unloads the model if it is running. The server happily continues running. Thus, to leave a clean environment behind, you would want to kill the process. First, make sure you get the process ID by first calling ".. /ollama serve > SERVER_LOG 2>&1 &" and then immediately after storing the process ID in a variable like this: "OLLAMA_PID=$!". Now, you can kill the process anytime you want by calling kill $OLLAMA_PID.

You could try running [uncensored LLMs](uncensored-llms) with Ollama, but be aware they are not raw models, so you may not get the desired results. 

## Future
In the future, it might be possible to [export and import models](https://github.com/ollama/ollama/issues/335) that would support precisely my use case, but for now, these methods are not directly available. 