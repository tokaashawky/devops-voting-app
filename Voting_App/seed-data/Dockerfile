FROM python:3.12-slim

RUN apt-get update && \
    apt-get install -y apache2-utils && \
    rm -rf /var/lib/apt/lists/*

RUN useradd -m toka
WORKDIR /app

COPY make-data.py generate-votes.sh ./
RUN python3 make-data.py

USER toka

CMD ["sh", "generate-votes.sh"]
