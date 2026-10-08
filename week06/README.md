1. ghcr.io/jaeheock/guestbook:v2

2. #추후 캡처본 추가

3. guestbook의 Dockerfile 발췌
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

4. <img width="1133" height="477" alt="image" src="https://github.com/user-attachments/assets/2c366309-876c-409a-ac7f-009afa8187c7" />

5. 코드는 app.py에서 / ENV는 Dockerfile에서 / -e는 RUN할 때 값을 설정하고, 우선순위는 -e > ENV > app.py이다.

