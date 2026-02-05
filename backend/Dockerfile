FROM python:3.9

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir --upgrade pip setuptools
RUN pip install --no-cache-dir gunicorn==23.0.0
RUN pip install --no-cache-dir -r requirements.txt

# Копирование всего проекта
COPY . .

# Создание папки для статики (на случай, если её нет)
RUN mkdir -p /app/collected_static

RUN python -c "import django; print(django.get_version())"

# Запуск Gunicorn
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "backend.wsgi"]