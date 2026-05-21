# --- START OF FILE Dockerfile ---

FROM python:3.11-slim

# Отключаем буферизацию логов в Python!
ENV PYTHONUNBUFFERED=1

WORKDIR /app

# Install dependencies first to leverage Docker layer caching
COPY src/api_fastapi/requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY src/api_fastapi/src ./src

# Copy contracts directory
COPY src/contracts ./src/contracts

# Expose port 8000 for the FastAPI server
EXPOSE 8000

# Start Uvicorn server
CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8000"]