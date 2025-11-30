
---

## 🔐 저작권 안내
- 본 문서는 교육·연구 목적의 참고 용도로만 사용 가능  
- 대회 제공 가상 데이터 기반  
- **주최측 요청 시 저장소 전체가 삭제될 수 있습니다.**




# 🕵️‍♂️ 디지털범인을찾아라 2025 – 디지털 포렌식 보고서
**작성자: 전수빈**  
**원본 PDF:** `디범찾2025_전수빈.pdf`

---

## ⚠️ 공지
이 분석 보고서는 디지털범인을찾아라2025 대회 제출용 자료이며,  
**주최측의 요청 시 저장소에서 비공개 또는 삭제될 수 있습니다.**

---

## 📚 목차
- 분석 환경
- 무결성 검증
- 문제 1 — ChatGPT 활용 딥페이크 제작 정황
- 문제 2 — 웹사이트·앱 기반 딥페이크 제작 입증
- 문제 3 — 설치된 딥페이크 프로그램 사용 정황
- 문제 4 — 안티포렌식 탐지 및 복구

---

## 🔧 분석 환경
- OS: Windows 11  
- 도구: FTK Imager 4.7.3.81, Autopsy  

---

## 🔒 무결성 검증
- 원본 디스크와 수집 이미지에 대해 **SHA-256 해시 검증**
- 두 해시값이 동일함을 확인함  
→ 증거 이미지 무결성 유지

---

## 🧩 문제 1  
### ChatGPT를 이용한 딥페이크 제작 정황 분석

- `Downloads/aa...` 파일에서 ChatGPT 다운로드 흔적 발견  
- ZoneTransfer 메타데이터에 다음 포함:
  - `ReferrerUrl=https://chatgpt.com/`
  - `HostUrl=https://sdmntpreastus.oaiusercontent.com/...`
- ChatGPT Installer.exe 존재  
- Prefetch 디렉터리 내 `CHATGPT.EXE-XXXX.pf` 기록 확인  
- Web History에서 AI 딥페이크 기술 관련 검색 기록 발견  

---

## 🧩 문제 2  
### 웹사이트 및 애플리케이션 기반 딥페이크 제작 입증

- DeepFaceLab workspace 내부에 다음 파일 존재:
  - `new_Quick96_encoder.npy`
  - `new_Quick96_decoder.npy`
  - `merger_session.dat`
  - `summary.txt`
- 모든 파일의 수정 시간이 동일 (딥페이크 학습 수행 시점 파악 가능)
- Quick96 모델 구조 및 타임스탬프가 DeepFaceLab 프리셋과 일치함  
→ 영상 합성이 실제로 수행된 증거

---

## 🧩 문제 3  
### 설치된 딥페이크 제작 프로그램 사용 정황

- PC 경로 `Documents/DeepFaceLab_DirectX12` 에서 DeepFaceLab 설치 확인
- `data_src` 폴더:
  - 국회의원 **이석호 사진 241장**
  - `data_src.mp4` (deeVid.ai 생성 흔적)
- `data_dst` 폴더:
  - 일론머스크 사진 **435장**
  - `faceset.pak` 생성됨
- `merged` 폴더:
  - 합성된 이미지 **1619장**

→ 딥페이크 제작 학습 및 합성이 실제 수행되었음

---

## 🧩 문제 4  
### 안티포렌식 탐지 및 복구

- 삭제된 파일이 **unallocated space**에서 발견됨
- 파일 헤더만 존재하고 나머지는 **0x00(null) 패딩 덮어쓰기**
- 단순 삭제가 아닌 **보안 삭제(안티포렌식)** 시도로 판단
- 얼굴 추출 및 랜드마크 검출 산출물도 일부 복구됨  

---

## 📁 Repository Structure
```
├── README.md
├── 디범찾2025_전수빈.pdf
```

