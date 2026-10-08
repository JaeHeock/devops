# ---------------------------------------------------------------
# 학생 과제: 아래 각 줄이 무엇을 하는지 주석으로 설명을 달아보세요.
# ---------------------------------------------------------------

# Docker 이미지 지정(-slim은 경량화 버전)
FROM python:3.12-slim
# 작업 디렉터리 설정(없으면 생성)
WORKDIR /app
# 호스트 컴퓨터의 파일을 복사
COPY requirements.txt .
# 빌드할 때 실행, 이미지에 결과 남음
RUN pip install --no-cache-dir -r requirements.txt
# 모든 파일을 복사 
COPY . .
# 새로운 유저 생성
RUN useradd -m appuser
USER appuser
# 환경 변수 설정
ENV APP_TITLE="재혁's DevOps 방명록" \
    THEME_COLOR="#FAED27"
# 5000번 포트를 사용하겠다 선언 
EXPOSE 5000
# 컨테이너 시작할 때 실행
CMD ["python", "app.py"]
