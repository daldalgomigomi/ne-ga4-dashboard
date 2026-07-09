# NE능률 GA4 유입·구매 대시보드

구글시트(구매 raw, 유입 raw)를 실시간으로 읽어오는 정적 대시보드입니다.
로컬 파일(`file://`)로 열면 브라우저 보안 정책 때문에 시트 연동이 막힐 수 있어서,
GitHub + Vercel로 배포해서 링크로 공유하는 걸 권장합니다.

## 배포 방법 (Vercel — 추천, 기존 BSA 대시보드와 동일 방식)

1. GitHub에서 새 repository 생성 (예: `ne-ga4-dashboard`), Public 또는 Private 모두 가능
2. 이 폴더의 `index.html`을 repo 루트에 업로드
   - GitHub 웹에서 "Add file → Upload files"로 드래그해도 되고
   - 터미널 쓰신다면:
     ```
     git init
     git add index.html
     git commit -m "GA4 대시보드 초기 배포"
     git branch -M main
     git remote add origin https://github.com/<본인계정>/ne-ga4-dashboard.git
     git push -u origin main
     ```
3. [vercel.com](https://vercel.com) 로그인 → "Add New Project" → 방금 만든 repo 선택 → Deploy
   - Framework Preset은 "Other"로 두면 됩니다 (빌드 과정 없이 정적 HTML 그대로 서빙)
4. 배포 완료되면 `https://ne-ga4-dashboard.vercel.app` 같은 URL이 생성됩니다 — 이 링크를 팀에 공유하면 됩니다.
5. 이후 대시보드 코드를 수정할 때는 GitHub repo의 `index.html`만 업데이트하면 Vercel이 자동으로 재배포합니다.

## 배포 방법 (GitHub Pages — 더 간단, Vercel 계정 없이도 가능)

1. 위와 동일하게 GitHub repo 생성 + `index.html` 업로드
2. repo의 **Settings → Pages** 이동
3. "Source"에서 `main` 브랜치 / `/ (root)` 선택 → Save
4. 몇 분 후 `https://<본인계정>.github.io/ne-ga4-dashboard/` 형태의 링크 생성

## 시트 연동 관련 참고

- 대시보드는 아래 두 게시된 CSV 링크를 5분마다 자동으로 다시 읽어옵니다 (우측 상단 "↻ 새로고침"으로 즉시 갱신도 가능)
- 구매 raw: `gid=0`
- 유입 raw: `gid=654212895`
- 시트의 "웹에 게시" 설정이 취소되거나 탭이 삭제되면 연동이 끊깁니다. 헤더 순서를 바꾸지 않는 한 행 추가는 자유롭게 하셔도 됩니다.
- 배포 후에도 연동 상태 배지가 빨간 점으로 계속 뜬다면, 해당 시트 탭의 "파일 > 공유 > 웹에 게시" 상태가 살아있는지 다시 확인해주세요.
