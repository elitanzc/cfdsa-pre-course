FROM python:3.11-bullseye

WORKDIR /app

COPY main.py .
COPY requirements.txt .
COPY run.sh .
COPY utils.py .
COPY public public
COPY templates templates

ENV PORT=3000
ENV INSTANCE_NAME="some instance name"
ENV INSTANCE_HASH="6194ed6424df"

RUN pip install -r requirements.txt

ENTRYPOINT bash run.sh