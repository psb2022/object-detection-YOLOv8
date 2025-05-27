
# 🧠 YOLOv8 기반 실시간 객체 인식 웹 서비스

---

## 🔧 프로젝트 개요
Google Colab과 Flask, React, YOLOv8을 이용하여 **브라우저에서 실시간으로 객체를 인식하는 웹 서비스**를 구현한 프로젝트입니다.  
추론은 YOLOv8 모델을 활용하고, pyngrok을 통해 외부에서도 접속 가능한 실시간 API를 제공하며, 프론트엔드에서는 카메라 영상에 대해 실시간으로 바운딩 박스를 시각화합니다.

- **프로젝트명:** YOLOv8 실시간 객체 인식 웹앱
- **주요 목표:** 브라우저에서 실시간 영상 기반 객체 인식이 가능한 경량 AI 웹 애플리케이션 구현
- **사용 환경:** Google Colab (Python 기반), 모바일 웹 접속 가능

---

## 🛠 기술 스택

| 영역        | 기술                                   |
|-------------|----------------------------------------|
| Frontend    | HTML, React.js, Bootstrap, Canvas API  |
| Backend     | Flask, Flask-CORS, pyngrok, OpenCV     |
| 모델        | YOLOv8 (ultralytics 라이브러리)        |
| 개발 환경   | Google Colab (Jupyter Notebook 기반)   |
| 배포 접근   | ngrok (https 기반 터널링)              |

---

## ⚙️ 시스템 아키텍처

```
[Browser (React)] ⇄ REST API ⇄ [Flask 서버 (Colab)] → YOLOv8 모델
       │                              ↑
   사용자 카메라               ngrok로 외부에 공개
     실시간 캡처
```

---

## 🔍 핵심 처리 메커니즘

1. 사용자의 브라우저에서 실시간으로 카메라 스트림을 가져옵니다.
2. 일정 간격으로 영상을 캡처하여 base64로 인코딩 후 Flask 서버에 전송합니다.
3. Flask 서버는 이미지를 YOLOv8 모델로 분석하여 객체의 위치와 이름을 추출합니다.
4. 분석 결과는 JSON 형태로 클라이언트로 반환되고, 바운딩 박스와 라벨이 캔버스 위에 시각화됩니다.

---

## 🚧 주요 기능

- 📷 실시간 카메라 영상 입력
- 🎯 YOLOv8 기반 객체 인식
- 🖼 감지 결과 실시간 시각화 (바운딩 박스)
- 🔄 전면/후면 카메라 전환 기능
- 🌐 ngrok으로 외부 접속 가능한 HTTPS URL 제공

---

## 🧪 구현 과정 중 해결한 주요 이슈

| 문제 | 해결 방법 |
|------|------------|
| Colab은 외부 접속 불가 | pyngrok으로 외부 HTTPS 터널 생성 |
| 카메라 접근 오류 | HTTPS 환경에서 getUserMedia 사용 및 facingMode 설정 |
| YOLOv8 추론 지연 | YOLOv8n 경량 모델 사용 및 주기 제어 |
| 바운딩 박스 위치 불일치 | Canvas 비율 보정 적용 |
| Payload Too Large 오류 | 이미지 압축률 조절 및 해상도 축소 |

---

## 📚 학습한 기술 및 인사이트

- YOLOv8 모델의 구조와 출력 처리 방식
- React 상태 관리 및 Canvas API 활용
- Flask API와 프론트 간 비동기 통신 처리
- Colab 기반 AI 서비스 배포 환경 구성 방법
- 실시간성과 성능 사이의 트레이드오프 감각

---

## 📈 향후 개선 방향

- [ ] YOLOv8s/m로 정확도 향상 실험
- [ ] 서버 환경을 Colab → AWS/GCP로 이관
- [ ] 감지 결과 저장 및 분석 기능 추가
- [ ] 사용자 인증 및 API 보안 강화
- [ ] 객체 클래스 필터 및 경고 시스템 도입

---

## 🚀 실행 방법 (Colab 기준)

1. Colab에서 `app.py` 및 `run_server.py` 실행
2. YOLOv8 모델 로드 (`ultralytics.YOLO('yolov8n.pt')`)
3. `run_server.py` 실행 시 ngrok URL 확인
4. 모바일 브라우저에서 해당 URL 접속
5. 실시간 객체 인식 테스트 진행

---

## 📂 디렉토리 구조

```
📦 root
├── app.py               # Flask 서버
├── run_server.py        # ngrok 실행 스크립트
├── uploads/             # 임시 이미지 저장 폴더
├── www/
│   ├── index.html       # 웹 인터페이스
│   └── js/
│       └── app.js       # React 코드
```

---

## 📌 포트폴리오 링크

👉 [GitHub Repository Link](https://github.com/your-username/yolov8-object-detection-webapp)

---

## 📜 라이선스

MIT License  
본 프로젝트는 학습 및 비상업적 연구 목적으로 자유롭게 사용할 수 있습니다.
