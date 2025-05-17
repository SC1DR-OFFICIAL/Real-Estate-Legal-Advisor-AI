# EN: 🧠 Real Estate Legal Advisor AI (RAG System)

**Real Estate Legal Advisor AI** is an advanced Retrieval-Augmented Generation (RAG) system developed during an AI course. It simulates the behavior of a "neuro-employee" — a virtual legal assistant trained to consult users on housing and real estate law in Russia.

This project goes beyond basic RAG architecture and demonstrates the **design, behavior modeling, and introspective debugging** of an AI agent.

---

## 🎯 Project Goals and Completed Tasks

✅ **Defined the Neuro-Employee’s Role**  
The assistant plays the role of a **Legal Advisor in Real Estate** with expert-level knowledge of the Housing Code of the Russian Federation. Its internal behavior is defined through a **system prompt**, describing its tone, logic, and boundaries of knowledge.

✅ **Designed its Internal World and Instructions**  
The system follows strict legal reasoning, avoids hallucinations, and always refers to official articles. The assistant behaves with calm professionalism, avoids guessing, and admits uncertainty when the answer is not explicitly stated in the documents.

✅ **Constructed a Legal Knowledge Base**  
A curated set of legal documents (PDFs) was collected and processed, including:
- Housing Code of the Russian Federation
- Land Code of the Russian Federation
- Civil Code of the Russian Federation

Knowledge is indexed via `LlamaIndex` using node-level chunking with metadata tags (e.g., article number, topic).

✅ **Chose the Framework**  
We use **LlamaIndex**, favoring its flexible RAG pipeline, reranking support, and easy integration with Russian LLMs.

✅ **Integrated a Russian LLM**  
The language model is YandexGPT, capable of fluent legal reasoning in Russian. A `CustomLLM` interface was implemented for seamless integration.

✅ **Traced Neuro-Employee Behavior**  
Using `Phoenix` tracing, we monitored:
- Query decomposition and embedding match quality
- Node retrieval scores
- Model uncertainty and hallucination likelihood

✅ **Diagnosed and Prevented Hallucinations**  
Although no hallucinations were directly observed during testing, we applied multiple defense mechanisms:
- Use of `tree_summarize` mode to restrict responses to retrieved context
- Added metadata checks to ensure legal citations match content
- Limited model temperature to reduce creative generation

✅ **Enhanced the RAG System**  
To go beyond typical blog-level implementations, we:
- Applied **LLM-based reranking (LLMRerank)** to improve answer relevance
- Created **dynamic prompt rewriting** for ambiguous questions
- Allowed **interactive trace visualization** via Phoenix

✅ **Implemented Query Filtering**  
A basic filter using keyword classification blocks non-legal or suspicious queries (e.g., "how to avoid paying taxes").

---

## 🏗️ Technologies Used

| Component             | Tech                          |
|----------------------|-------------------------------|
| Vector Search         | `LlamaIndex` with local index |
| Language Model        | `YandexGPT` (via CustomLLM)   |
| Document Parsing      | `SimpleDirectoryReader`       |
| Query Reranking       | `LLMRerank`                   |
| Tracing               | `Phoenix` + `ngrok`           |
| Environment           | Google Colab (Python 3.11+)   |

---

## 🧪 Sample Questions and Behavior

| User Query | Response Behavior |
|------------|-------------------|
| _“Do I have to pay for major repairs if I don’t live in the apartment?”_ | Links to Article 158 ЖК РФ and explains owner responsibilities. |
| _“Can I avoid paying for the roof repair?”_ | Returns filtered message: "Sorry, I can’t help with that." |
| _“What happens if a tenant damages property?”_ | Refers to Civil Code and landlord rights. |

---

## Colab link:
https://colab.research.google.com/drive/1jBdeyOVqKJL_zK_-6_b5lSj2eBG0FgP-?usp=sharing

---

# RU: 🧠 Нейроюрист по недвижимости (RAG-система)

**Нейроюрист по недвижимости** — это продвинутая Retrieval-Augmented Generation (RAG) система, разработанная в рамках курса по искусственному интеллекту. Она моделирует поведение "нейросотрудника" — виртуального юридического помощника, обученного консультировать пользователей по вопросам жилищного и имущественного права в России.

Проект выходит за рамки базовой архитектуры RAG и демонстрирует **проектирование, моделирование поведения и интроспективную отладку** интеллектуального агента.

---

## 🎯 Цели проекта и выполненные задачи

✅ **Определена роль нейросотрудника**  
Ассистент играет роль **юриста по недвижимости** с экспертными знаниями Жилищного кодекса РФ. Его поведение задаётся через **системный промпт**, в котором прописан стиль общения, логика и пределы компетенции.

✅ **Сформирован внутренний мир и инструкции**  
Система следует строгой юридической логике, избегает галлюцинаций и всегда ссылается на официальные статьи. Ассистент сохраняет спокойный профессионализм, не делает предположений и признаёт неопределённость, если ответ прямо не указан в документах.

✅ **Построена юридическая база знаний**  
Подобрана и обработана коллекция юридических документов (PDF), включая:
- Жилищный кодекс Российской Федерации
- Земельный кодекс Российской Федерации
- Гражданский кодекс Российской Федерации

Знания индексируются с помощью `LlamaIndex` с нарезкой на узлы и мета-тегами (например, номер статьи, тема).

✅ **Выбран фреймворк**  
Используется **LlamaIndex** благодаря гибкости RAG-конвейера, поддержке реранжирования и простой интеграции с русскоязычными LLM.

✅ **Интегрирована русскоязычная LLM**  
Модель YandexGPT используется для юридических рассуждений на русском языке. Реализован интерфейс `CustomLLM` для полной интеграции.

✅ **Отслежено поведение нейросотрудника**  
С помощью трассировки `Phoenix` отслеживались:
- Декомпозиция запроса и качество эмбеддинга
- Оценки извлечения узлов
- Уверенность модели и вероятность галлюцинаций

✅ **Диагностика и защита от галлюцинаций**  
Хотя в тестах галлюцинации напрямую не наблюдались, применены защитные механизмы:
- Использование режима `tree_summarize` — только по найденному контексту
- Проверка метаданных, чтобы ссылки на статьи соответствовали содержанию
- Пониженная температура генерации для уменьшения креативности модели

✅ **Улучшена RAG-система**  
Для выхода за рамки типичных реализаций:
- Добавлено **реранжирование на основе LLM (LLMRerank)** для повышения релевантности
- Реализована **динамическая переформулировка запросов** при неясных формулировках
- Визуализация трассировки через Phoenix

✅ **Реализована фильтрация запросов**  
Базовый фильтр с использованием ключевых слов блокирует неюридические и подозрительные запросы (например, "как не платить налоги").

---

## 🏗️ Используемые технологии

| Компонент              | Технология                    |
|------------------------|-------------------------------|
| Векторный поиск        | `LlamaIndex` с локальным индексом |
| Языковая модель        | `YandexGPT` (через CustomLLM) |
| Разбор документов      | `SimpleDirectoryReader`       |
| Реранжирование         | `LLMRerank`                   |
| Трассировка            | `Phoenix` + `ngrok`           |
| Среда выполнения       | Google Colab (Python 3.11+)   |

---

## 🧪 Примеры запросов и поведение системы

| Запрос пользователя | Поведение системы |
|---------------------|-------------------|
| _«Надо ли платить за капремонт, если не живу в квартире?»_ | Ссылается на статью 158 ЖК РФ и разъясняет обязанности собственника. |
| _«Как не платить за ремонт крыши?»_ | Возвращает фильтрованное сообщение: «Извините, я не могу с этим помочь». |
| _«Что делать, если арендатор повредил имущество?»_ | Ссылается на ГК РФ и права арендодателя. |

---

## Ссылка на Colab:
https://colab.research.google.com/drive/1lXz_1lxxA_O95jiPoX_3XaKp1gfMh18T?usp=sharing
