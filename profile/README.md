# StorePilot

온라인 쇼핑몰 상품 등록 과정에서 반복되는 카테고리 탐색과 상품 정보 정리를 자동화하는 서비스입니다.

## What is StorePilot?

상품마다 카테고리를 찾고 키워드를 정리해야 하는 판매자의 반복 작업을 줄이기 위해 만들었습니다.

상품 엑셀을 업로드하면 기존 상품 데이터와 카테고리 정보를 기반으로 적합한 네이버 쇼핑 카테고리를 찾습니다. 이후 사용자별 마이카테고리 코드로 매핑하고 검색 키워드를 생성해, 결과를 엑셀로 제공합니다.

웹 검색 대신 미리 구축한 임베딩 데이터를 활용하며, 검토한 기존 상품 데이터를 추가해 검색 근거를 보강합니다.

## Architecture

```text
상품 엑셀 업로드
    ↓
상품명 전처리 · Embedding
    ↓
FAISS 유사상품 검색 + 카테고리 직접 검색
    ↓
카테고리 후보 생성
    ↓
명확한 결과는 자동 선택 · 판단이 어려우면 LLM 활용
    ↓
사용자별 마이카테고리 매핑 · 키워드 생성
    ↓
결과 엑셀 다운로드
```

## Repositories

| Repository | 주요 역할 | 기술 |
| --- | --- | --- |
| [Backend](https://github.com/storepilot-app/be) | 비동기 엑셀 작업, 사용자별 매핑, 인증 및 사용량 관리 | Java / Spring Boot / MySQL |
| [AI Server](https://github.com/storepilot-app/ai-server) | 임베딩 기반 검색, 카테고리 후보 생성 및 LLM 판단 | Python / FastAPI / FAISS / Solar Embedding API |
| [Frontend](https://github.com/storepilot-app/fe) | 파일 업로드, 작업 진행률 확인, 결과 다운로드 | Next.js / TypeScript |

## Service

[StorePilot 서비스 바로가기](https://storepilot-three.vercel.app/) · [사용 안내](https://literate-marquis-4cc.notion.site/StorePilot-3d2c3b070b418090809ad8e419b2df0e)
