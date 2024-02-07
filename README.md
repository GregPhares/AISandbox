# AISandbox
This was intially followed from https://github.com/JustanProvence/AISandbox.

##Installation 
### System Requirements/ Prep
Prior to installing prior to installing llama-cpp-python, the following dependencies will need to be installed. To install the following packages use either ```pip install <package_name>``` or ```sudo apt-get install <package_name>```. I prefer pip so I decided to install that prior to installing the dependencies.

```
pip install --upgrade pip
pip install swig
pip install scikit-build-core
pip install numpy
pip install starlette_context
pip install sse_starlette
pip install fastapi
pip install starlette
pip install anyio
pip install uvicorn
```
!!!NOTE: This installation will be done on Ubuntu with Python3.10.12.


###Installing llama-cpp-python 
Install this package in the folder ***AISandbox/llamacpp***
```
cd llamacpp
pip install llama-cpp-python
```
###Installing Huggingface
The following will install the python package to allow to hook into hugginface's repo.

```
pip install huggingface-hub
```

!!!NOTE: Need to make the following folders, to house the models for pathing purposes from llamacpp ./models/mistral

```
mkdir models; cd models; mkdir mistral
huggingface-cli download TheBloke/Mistral-7B-Instruct-v0.2-GGUF mistral-7b-instruct-v0.2.Q5_K_S.gguf --local-dir . --local-dir-use-symlinks False
cd mistral
huggingface-cli download TheBloke/Mistral-7B-v0.1-GGUF mistral-7b-v0.1.Q5_K_S.gguf --local-dir . --local-dir-use-symlinks False
```
##Running llama-cpp
###Quick Test
To do a quick local run from the root of the llamacpp folder. This should do a quick run of the AI and run a test question.
```
python3 main.py
```
### Running llama-cpp server
To spind up and self host the llama server run the following command
```
 python3 -m llama_cpp.server --model ./models/mistral-7b-instruct-v0.2.Q5_K_S.gguf --n_ctx 16192 --chat_format chatml
 ```

Now you need a way to interact with your sever, so for this we will be using the vscode plugin [continue](https://marketplace.visualstudio.com/items?itemName=Continue.continue).
Once this plugin is installed:
* select continue 
* select config(next to help icon)
* copy the file from [here]() into the config.json for continue
* then return continue prompt, to start using the llama server
