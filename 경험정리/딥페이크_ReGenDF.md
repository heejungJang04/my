# ReGen-DF — 딥페이크 탐지용 하이브리드 데이터셋

> 딥페이크 경진대회 / 연구용 데이터셋 (팀: Jinseok Kim, Uihyeon Maeng, **Heejung Jang(나)**, Suyeon Myeong)
> 깃허브: github.com/heejungJang04/ReGen-DF (README+assets, 데이터는 구글드라이브)
> GCP 설정 정리(노션): gainful-crowley-1f4.notion.site/GCP-27e7ebcc0c78801bba86d1e7804e32da
> **내 역할: 합성 데이터의 생성·수집**

## 데이터 구성 (드라이브 DEEPFAKE_oldboy 기준)
- **생성형 T2I 모델 다양**: Seedream(약 4.17GB, 최대), Flux, Imagen v4(imagen04), Kling, WAN + **나노바나나**
- **영상·립싱크(T2V)**: Kling으로 kling_gen_img / kling_gen_lipsync / kling_gen_video
- **Face Reenactment(감정 합성)**: deepfake_emotion — FFHQ 실제 얼굴 기반 재연, **GCP 클라우드 환경에서 실행**
- 규모: 수 기가바이트 (seedream 4.17GB, imagen 200MB+, wan/flux 90~100MB zip 등)
- code 폴더에 처리 스크립트

## 내가 한 일 (구체)
- 탐지 모델의 강인성을 위해 **단일 모델에 의존하지 않고 여러 생성 서비스를 조합** (데이터 다양성 확보 의도)
- Seedream·Flux·Imagen·Kling·나노바나나 등을 **직접 유료 토큰 결제**하며 합성 얼굴 대량 생성
- Kling으로 이미지뿐 아니라 **영상·립싱크**까지 생성 (위조 유형 확장)
- 실제 얼굴 기반 **감정 재연 위조는 GCP 클라우드 환경에서 직접 실행**
- 외부 도구에서 필요한 자료를 직접 만들어 모으고 정제 (※ "데이터셋 설계"까지는 아니고 생성·수집 기여)

## 면접 대비 포인트 (외워둘 것)
- **왜 여러 모델?** → 한 모델 산출물만 학습하면 그 모델 특징에만 과적합. 다양한 생성기로 만들어야 탐지 일반화.
- **유료 결제·적극성** → "필요한 데이터를 직접 비용 들여 만들어 온" 주도성
- **GCP 클라우드** → reenactment 생성을 GCP에서 직접 실행 (환경 세팅은 노션에 정리)
- ⚠️ **GCP 과금 사건**: 인스턴스를 안 끄고 둬서 비용이 청구됨 → "클라우드 리소스 종료·예산 관리의 중요성"을 몸으로 배운 경험 (자소서엔 긍정 프레임, 면접에서 솔직히)

## 자소서 활용
- ② 역량의 [데이터] 사례 (외부 자료 직접 생성·수집 + GCP 클라우드 + 멀티모델)
- "필요한 자료를 직접 만들어 해결하는" 적극성 어필
