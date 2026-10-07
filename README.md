# turin

**아이디어에서 운영까지, 서비스를 끝까지 만듭니다.**

백엔드 중심 풀스택 개발자입니다. 학교생활 통합 플랫폼 **SCIN**을 직접 기획하고, 만들고, 배포하고, 운영하고 있습니다.
화면 뒤의 API · 데이터 · 인프라를 설계하는 일을 가장 좋아합니다.

[turin.my](https://turin.my) · [scin.kr](https://scin.kr) · [me@turin.my](mailto:me@turin.my)

---

## Currently building — SCIN (스인)

> 학생이 학교생활에 필요한 정보를 여러 곳에서 찾지 않고, 하나의 서비스에서 확인하도록 만든 학교생활 통합 플랫폼

- 나이스(NEIS) 교육정보 API로 전국 **13,309개 학교**의 급식 · 시간표 · 학사일정을 가져오고, 그 위에 공지 · 과제 · 공부 타이머 · 성적 · 독서 기록 · 알림을 얹었습니다.
- 중앙 API 하나를 웹 · Flutter 앱이 함께 쓰고, 인증(OAuth · 전화번호 인증 · RBAC · 보호자 동의 · Redis 세션)은 직접 만들었습니다.
- `main` push 한 번에 Dokploy 자동 배포와 GitHub Actions(셀프호스트 러너) CI가 함께 돌고, 앱은 GitHub Release로 APK가 배포됩니다.
- 레포 커밋 1,000+ · 하루 최대 방문자 300

```text
Web (scin.kr) ──┐                    ┌── Auth (OAuth · RBAC)
                ├──► SCIN API ───────┼── PostgreSQL (Prisma)
Mobile (Flutter)┘    api.scin.kr     ├── Redis (세션 · 캐시)
                                     └── NEIS 교육정보 API
```

| 시기 | 변화 |
| --- | --- |
| 2026.03 | 서비스별 앱과 공유 패키지를 하나의 저장소로 — 모노레포 전환, Railway 첫 배포 |
| 2026.04 | Expo/EAS + GitHub Actions로 Android APK 빌드 자동화 |
| 2026.04 – 06 | Flutter로 앱 재구축 (5탭 구조, NEIS 영양 · 알레르기 정보) |
| 2026.06 | Railway → Ship → Dokploy(셀프호스트 PaaS)로 이관 |
| 2026.09 | 앱 중심 대개편 — 10개가 넘던 웹 앱을 중앙 API · 랜딩 · 관리자 · Flutter 앱으로 정리 |

## Dmail — 팀 마쉬메로우 (2025.08 –)

Discord에서 Gmail · IMAP 새 메일 알림을 받고 메일을 보내는 서비스입니다. 개인 공개봇 'E-mail봇'으로 시작해 팀 마쉬메로우의 Dmail로 키웠고, 주 개발자로 봇 · 사용자 웹 · 관리자 대시보드를 만들었습니다.

- **v2 (2026.08)** — TypeScript로 다시 설계: discord.js 봇 · Fastify API · 독립 메일 워커를 PostgreSQL · Redis · BullMQ로 연결
- **Durable Outbox** — 메일 저장과 전달 작업을 같은 PostgreSQL 트랜잭션에 기록하고 워커가 재시도하며 전달
- **Lease Token** — 오래된 워커 작업이 새 작업을 덮어쓰거나 완료 처리하지 못하게 막음
- **Encrypted Body** — 수신 메일 본문은 암호화해 저장하고, 전달 큐에는 본문 대신 outbox ID만

## Stack

실제로 쓰고 운영하는 도구들입니다.

| 영역 | |
| --- | --- |
| Backend · API | TypeScript · Node.js · Next.js · Python · FastAPI |
| Data · Queue | PostgreSQL · Prisma · Drizzle · Redis · BullMQ |
| App · Web | Flutter · Android · React · Tailwind · Discord bots |
| Infra · Ops | Docker · Dokploy · Cloudflare (DNS · WAF · R2) · Linux · WireGuard · nftables · Grafana · GitHub Actions |

## Contact

함께 만들 서비스가 있거나 개발 이야기를 하고 싶다면 편하게 연락해 주세요.

**[me@turin.my](mailto:me@turin.my)** · **[turin.my](https://turin.my)**
