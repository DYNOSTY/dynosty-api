> **통합 안내:** 현재 개발은 [DYNOSTY/dynosty](https://github.com/DYNOSTY/dynosty)에서 진행합니다.
> 아래 내용은 이전 4개 레포 구성의 기록입니다. 최신 구조와 역할은 통합 레포 README를 확인해 주세요.

# DYNOSTY API — 계정과 온라인 저장

DYNOSTY는 웹 브라우저에서 즐기는 3D 생존·도시 경영 게임입니다.
이 레포는 **게임 화면이 서버에 일을 요청하는 창구**를 담당합니다.

> 현재는 개발 계획을 정리한 단계입니다. 아래 기능은 앞으로 구현합니다.

## 맡은 일

- 사용자 계정과 로그인을 처리합니다.
- 게임 진행 상황을 저장하고 다시 불러옵니다.
- 랭킹을 도입할 때, 제출된 결과를 서버에서 검증합니다.

## 사용할 기술

| 기술 | 쉽게 말하면 |
| --- | --- |
| Node.js | 서버에서 TypeScript로 만든 프로그램을 실행하는 기반 |
| Fastify | 로그인·저장 같은 요청을 처리하는 도구 |
| TypeScript | 서버 코드를 작성하는 언어 |
| PostgreSQL | 계정과 게임 저장 기록을 보관하는 데이터베이스 |
| REST API·HTTPS | 필요한 일을 요청하고 응답받는 방식과 안전한 통신 |

## 다른 레포와의 연결

```text
Web의 저장 요청 → API → PostgreSQL에 보관
Web의 불러오기 요청 → API → 저장된 게임 전달
```

- [Web](https://github.com/DYNOSTY/dynosty-web)에서 보낸 요청을 처리합니다.
- [Core](https://github.com/DYNOSTY/dynosty-core)의 게임 상태·저장 형식을 함께 사용합니다.
- [Infra](https://github.com/DYNOSTY/dynosty-infra)가 API와 데이터베이스의 실행 환경을 관리합니다.

평소 게임 계산은 플레이어 PC에서 실행하고, 서버는 **계정·온라인 저장·결과 검증**을 맡습니다.
