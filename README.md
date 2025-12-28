![Google Colab](https://img.shields.io/badge/Google%20Colab-%23F9A825.svg?style=for-the-badge&logo=googlecolab&logoColor=white)![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)![Google Drive](https://img.shields.io/badge/Google%20Drive-4285F4?style=for-the-badge&logo=googledrive&logoColor=white)![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white)

![enter image description here](https://camo.githubusercontent.com/4075c6d74fc7fcb4da8b8b87655bbdc71de0e5c80b98dd17b7e23a18e5a181eb/68747470733a2f2f63646e2e6261702d736f6674776172652e6e65742f323032342f30352f32373137343831382f4c6c616d61496e6465782d65313731363738313738313232382e706e67)

## Technical consultant in the RAG-system

В основе этого репозитория лежит **LlamaIndex** - это фреймворк данных для создания приложений на основе больших языковых моделей (LLM). Он позволяет подключать пользовательские и приватные данные к LLM, чтобы сделать работу искусственного интеллекта полезной и релевантной для конкретной задачи.

В данном подходе решения поставленной задачи я создал базу знаний в виде *Google-документа* и загрузил её в **Google Colab** проект, предварительно открыв доступ для чтения в **Google Диске**. Подробная инструкция по составлению структуры и информации в базе знаний представлена внутри проекта.

Перед запуском кода обратите внимание на версии загружаемых библиотек. Также после загрузки потребуется выполнить перезагрузку проекта и заново запустить.

В блоке импорта библиотек необходимо указать свой *API-ключ*, который можно сгенерировать в настройках профиля на **Hugging Face**.

За основу в реализации нейро-сотрудника я использую фреймворк **LlamaIndex**. Для просмотра трассировок был внедрен **Phoenix** с его **UI**, но для его полноценной работы я реализовал создание защищенного туннеля через **[Cloudflared](https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64)**. Также для Phoenix нужно выполнить команду `nest_asyncio.apply()`, которая необходима для параллельных вычислений в среде ноутбуков.

В качестве LLM-модели я выбрал **[IlyaGusev/saiga_yandexgpt_8b](https://huggingface.co/IlyaGusev/saiga_yandexgpt_8b)**, а в качестве эмбеддинг-модели - **[sentence-transformers/paraphrase-multilingual-MiniLM-L12-v2](https://huggingface.co/sentence-transformers/paraphrase-multilingual-MiniLM-L12-v2)**.

Также для более корректной и лучшей работы *RAG-системы* были реализованы следующие подходы, закрывающие проблему  **"болевых точек"**:

-   **Болевая точка 1:**  недостающий контент (реализовал очистку данных и улучшение промптов);
-   **Болевая точка 4:**  контекст не извлечен (использовался  **ресортировщик контента**);
-   **Болевая точка 8:**  масштабируемость полученных данных (применяется параллельная обработка);
-   **Болевая точка 12:**  Безопасность  **LLM**  (через  **NeMo Guardrails**).

<img width="1301" height="740" alt="image" src="https://github.com/user-attachments/assets/288ab2a9-05a1-4814-ac2e-4d7ae7074863" />

> Для выполнения этого кода настоятельно рекомендую использовать
> **графический ускоритель T4** или мощнее!
