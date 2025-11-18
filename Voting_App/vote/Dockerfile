FROM python:3.11-slim

RUN useradd -m toka

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

RUN chown -R toka:toka /app
USER toka

ENV OPTION_A="Cats" OPTION_B="Dogs"

EXPOSE 8080

CMD ["gunicorn", "-b", "0.0.0.0:8080", "app:app"]
