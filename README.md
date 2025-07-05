
To deliver the "Try EDA" experience, we have created an EDA playground - a repository that contains everything you need to install and provision a demo EDA instance with the virtual network on the side. 

# Installation:
Proceed with cloning the EDA playground repository that contains everything you need to install and provision a demo EDA instance.

```
git clone https://github.com/nokia-eda/playground && \
cd playground
```
The prerequisites "make" and "docker" have already been installed in the VM.

Set the EXT_DOMAIN_NAME environment variable in your shell:
```
export EXT_DOMAIN_NAME=<x>.wwrkshpz.net
```
Note: if you want to enable the Natural Language support for the EDA Query functionality, provide the LLM key (OpenAI) with an additional environment variabl.

```
export LLM_API_KEY=<your-OpenAI-API-key>
```
