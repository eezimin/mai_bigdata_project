FROM jupyter/pyspark-notebook:latest

USER root

# Установка дополнительных пакетов
RUN apt-get update && apt-get install -y \
    wget \
    && rm -rf /var/lib/apt/lists/*

# Установка дополнительных Python пакетов
RUN pip install \
    findspark \
    psycopg2-binary

# Скачивание JDBC драйвера PostgreSQL
RUN wget https://jdbc.postgresql.org/download/postgresql-42.7.4.jar -P /workspace

# Создание рабочей директории
WORKDIR /workspace

# Переключение обратно на пользователя jovyan
USER jovyan

# Отключение токена для Jupyter Notebook
ENV JUPYTER_TOKEN=""
CMD start-notebook.sh --NotebookApp.token=''
