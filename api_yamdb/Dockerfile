FROM python:3.7-slim
RUN mkdir /api_yamdb
COPY requirements.txt /api_yamdb
RUN pip3 install -r /app/requirements.txt --no-cache-dir
COPY ./ /api_yamdb
WORKDIR /api_yamdb
CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000"]