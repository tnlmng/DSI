FROM python:3.10

WORKDIR /dssi

COPY ./requirements.txt /dssi/requirements.txt

RUN pip install --no-cache-dir --upgrade -r /dssi/requirements.txt

COPY ./server.py ./server.py
COPY ./src ./src
COPY ./models ./models
COPY ./metadata ./metadata

CMD ["python", "server.py"]
