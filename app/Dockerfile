# Python 3:11-slim Base Image 
FROM python@sha256:233de06753d30d120b1a3ce359d8d3be8bda78524cd8f520c99883bfe33964cf AS builder

WORKDIR /app

COPY requirements.txt . 

RUN pip install --no-cache-dir --prefix=/install -r requirements.txt

COPY . . 

FROM gcr.io/distroless/python3-debian12@sha256:2fdb05402a2cf21cf78fdb3ba4c5db167241e9e498140f5bf689d7efb773731f

COPY --from=builder /install/lib/python3.11/site-packages /usr/lib/python3.11
COPY --from=builder /app /app

WORKDIR /app

USER nonroot

EXPOSE 8080

CMD ["-m", "uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8080"]