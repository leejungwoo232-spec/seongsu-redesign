# 성수역 리디자인 — 1인칭 탐방 페이지

서울 지하철 2호선 성수역(고가역) 리디자인을 웹에서 걸어 다니며 보는 페이지입니다.
Blender에서 모델링·조명을 굽고(lightmap), 그 결과를 three.js로 그립니다.

## 파일 구성

| 파일 | 내용 |
|---|---|
| `index.html` | 페이지 전체 (HTML·CSS·JS 한 파일). three.js 0.160 · three-mesh-bvh 0.7.6 은 jsDelivr CDN 에서 불러옴 |
| `seongsu_model*.json`, `seongsu_bld.json`, `seongsu_streets.json` | 역·주변 건물·거리 기하 |
| `lm_*.webp` (`_s` 는 저용량판) | 구운 조명(lightmap) |
| `seongsu_v10.json` … `seongsu_v68.json` | 리디자인 단계별 변경 자료 (V68: 금속 승강장 바닥, 유리 블록 안 붉은 벽돌 기둥과 풀, 계단 정면 끝벽 통유리, 출구 볼트, 하이라인식 통로 등) |
| `*_stain.png`, `v67_atlas_web.jpg`, `voile_weave_v1.png`, `map_r.webp` | 텍스처 |
| `.nojekyll` | GitHub Pages 가 파일을 그대로 내보내게 함 |

모든 파일이 25 MB 이하라 GitHub 웹 화면에서 끌어다 올려도 됩니다.

## GitHub Pages 로 배포

1. 새 저장소를 만들고 이 폴더의 파일을 **전부** 저장소 맨 위(루트)에 올립니다 (`.nojekyll` 포함).
   ```bash
   git init
   git add -A
   git commit -m "성수역 리디자인 탐방 페이지"
   git branch -M main
   git remote add origin https://github.com/<아이디>/<저장소>.git
   git push -u origin main
   ```
2. 저장소 **Settings → Pages → Build and deployment** 에서 Source 를 `Deploy from a branch`, Branch 를 `main` / `(root)` 로 저장.
3. 1–2분 뒤 `https://<아이디>.github.io/<저장소>/` 에서 열립니다.

## 로컬에서 미리 보기

페이지가 `fetch()` 로 자료를 읽으므로 파일을 더블클릭(`file://`)하면 안 열립니다. 폴더에서 간단한 서버를 띄우세요.

```bash
python -m http.server 8000
# → http://localhost:8000
```

## 참고

- 첫 로딩에 약 110 MB 를 내려받습니다 (휴대폰은 화질 "보통"에서 일부 자료를 덜 씀).
- `terrazzo_tiles.jpg` 는 없어도 됩니다 — 없으면 페이지가 기본 바닥 질감으로 그립니다.
