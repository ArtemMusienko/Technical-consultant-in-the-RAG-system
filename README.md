![Google Colab](https://img.shields.io/badge/Google%20Colab-%23F9A825.svg?style=for-the-badge&logo=googlecolab&logoColor=white)![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)![Google Drive](https://img.shields.io/badge/Google%20Drive-4285F4?style=for-the-badge&logo=googledrive&logoColor=white)![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white)

## Technical consultant in the RAG-system

![enter link description here](https://cdn.sanity.io/images/7m9jw85w/production/88941f3dfaf0e7d0f07dc58057830025b7828d73-1800x980.png)  

[![ru](https://img.shields.io/badge/README_на_русском-2A2C39?style=for-the-badge&logo=github&logoColor=white)](README.ru.md)

This repository is based on **LlamaIndex**, a data framework for building applications based on large language models (LLM). It allows you to connect user and private data to LLM to make the work of artificial intelligence useful and relevant to a specific task.

In this approach, I created a knowledge base as a *Google document* and uploaded it to a **Google Colab** project, having previously opened read access in **Google Drive**. A detailed instruction on how to create a structure and information in the knowledge base is provided within the project.

Before running the code, pay attention to the versions of the libraries that are being loaded. After loading, you will need to reload the project and run it again.

In the library import block, you will need to specify your *API key*, which can be generated in the profile settings on **Hugging Face**.

I am using the **LlamaIndex** framework as the basis for implementing the neural assistant. To view the traces, I implemented **Phoenix** with its **UI**, but to make it work properly, I created a secure tunnel using **[Cloudflared](https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64)**. Additionally, I used the command `nest_asyncio.apply()` for parallel computing in the notebook environment. 

I chose **[IlyaGusev/saiga_yandexgpt_8b](https://huggingface.co/IlyaGusev/saiga_yandexgpt_8b)** as the LLM model, and **[sentence-transformers/paraphrase-multilingual-MiniLM-L12-v2](https://huggingface.co/sentence-transformers/paraphrase-multilingual-MiniLM-L12-v2)** as the embedding model.

Also, for more correct and better operation of the *RAG-system*, the following approaches were implemented to solve the problem of "pain points":

- **Pain point 1:** missing content (implemented data cleaning and prompt improvement);

- **Pain point 4:** context is not extracted (content reshuffler was used);

- **Pain point 8:** scalability of the received data (parallel processing is applied);

- **Pain point 12:** **LLM** security (via **NeMo Guardrails** ).

<img  width="1301"  height="740"  alt="image"  src="https://github.com/user-attachments/assets/288ab2a9-05a1-4814-ac2e-4d7ae7074863"  />

> To run this code, I strongly recommend using a
>  **T4 graphics accelerator** or better!