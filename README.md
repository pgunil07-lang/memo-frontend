# memo-frontend

개인 소개 페이지 + 프론트엔드·백엔드 연동 실습 (클라우드 컴퓨팅 2주차 과제)

React(Vite)로 만든 메모장 화면이 Render에 배포된 FastAPI 백엔드를 호출해 메모를 저장·조회·삭제한다.
소개 페이지는 순수 HTML로 작성했고, 두 페이지는 서로 링크로 오갈 수 있다.

## 배포 주소

| 항목 | 주소 |
|---|---|
| 소개 페이지 (Vercel) | https://memo-frontend-phi.vercel.app/intro.html |
| 메모장 · 연동 실습 (Vercel) | https://memo-frontend-phi.vercel.app/ |
| 백엔드 Swagger UI (Render) | https://memo-backend-0kin.onrender.com/docs |
| 백엔드 저장소 | https://github.com/pgunil07-lang/memo-backend |


## 주요 구성

```
memo-frontend/
├── public/intro.html   # 개인 소개 페이지 (순수 HTML) → /intro.html
├── src/App.jsx         # 메모장 화면. fetch로 백엔드 /memos 호출
├── src/main.jsx        # React 진입점
├── index.html          # SPA 뼈대
└── .env                # VITE_API_URL (커밋하지 않음)
```

- `App.jsx`는 `import.meta.env.VITE_API_URL`로 백엔드 주소를 읽는다. 로컬은 `.env`, Vercel은 Environment Variables에서 넣는다.
- 소개 페이지(`/intro.html`) ↔ 메모장(`/`)은 상단 링크로 서로 이동한다.

## 로컬 실행

```bash
npm install
npm run dev        # http://localhost:5173  (백엔드는 memo-backend에서 fastapi dev main.py)
npm run build      # dist/ 생성 (Vercel이 배포하는 결과물)
```

## Vercel 설정

- Framework Preset: Vite / Build: `npm run build` / Output: `dist`
- Environment Variables: `VITE_API_URL` = Render 백엔드 주소 (`https://memo-backend-0kin.onrender.com`)
- 환경변수를 바꾸면 재배포해야 반영된다(빌드 시점에 주입).
