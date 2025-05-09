# RAG
RAG-system creation 

https://drive.google.com/file/d/1mMFubhKgBNJHrq-SqPKk57hO1HOe5OPX/view?usp=drive_link

Отчет о построении RAG для туристического помощника

1. Произведена предобработка данных
   
▸ Для очистки датасета использована комбинация фильтров по тектовому описанию и по изображениям, к которым составлены описания

▸ Наблюдается зависимость между наличием изображения, не относящемся к туристической тематике, и низким tf-idf слова в описании данного

▸ На основании наблюдаемого факта из датасета исключены объекты выбросы

▸ Также исключены объекты с отсутствующим полностью описанием или id Wikidata

▸ Объекты сгруппированы так, чтобы один объект описывал, по возможности, одну достопримечательность. ▸ Тексты описания объединены, при помощи BLEU повышена уникальность предложений в объединенных описаниях

2. Построена RAG-система
   
▸ Модель эмбеддингов = intfloat/multilingual-e5-large

▸ Основная языковая модель = teknium/OpenHermes-2.5-Mistral-7B квантизованная

▸ Векторная база данных = FAISS

▸ Реранкер = colbert-ir/colbertv2.0

3. Построена PCA и UMAP визуализация эмбеддингов базы данных в 2D-пространстве
Отчетливо наблюдаются кластеры, образованные городами: Владимир, Ярославль, Нижний Новгород, Екатеринбург.

4. Проверена функциональность RAG-системы
RAG-система функционирует. Приведен обзор метрик оценки RAG-системы:

▸ Faithfullness

▸ Answer Relevancy

▸ Context Recall

▸ Context Precision

▸ Answer Semantic Similarity

▸ Answer Correctness

5. Качество RAG протестировано
В соответствии с документацией RAGAS cоздана функция для проверки качества Answer Relevancy. Качество усреднено по 100 случайным парам вопрос-ответ и составляет 0.89.
