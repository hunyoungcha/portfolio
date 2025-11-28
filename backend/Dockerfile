FROM python:3.11-slim

# 시스템 패키지 업데이트 및 pip 업그레이드
RUN apt-get update && apt-get install -y --no-install-recommends build-essential \
    && rm -rf /var/lib/apt/lists/* \
    && pip install --upgrade pip

# 작업 디렉터리
WORKDIR /app

# 의존성 설치
COPY backend/requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# alembic 관련 파일
COPY backend/alembic.ini .
COPY backend/alembic/ ./alembic/

# 앱 소스 복사
COPY backend/app ./app/

# 기본 실행 커맨드
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
