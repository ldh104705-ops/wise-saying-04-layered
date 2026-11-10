# 명언 앱 ④ 레이어드 아키텍처 (11단계)

콘솔 명언 앱을 Controller · Service · Repository 구조로 나눈 버전입니다. 저장소는 메모리 리스트입니다.

## 요청 흐름

```
App(입력) → Controller(입출력) → Service(비즈니스 로직) → Repository(데이터) → List
```

| 클래스 | 역할 |
| --- | --- |
| `com.back.Main` | 앱 실행 |
| `com.back.App` | 입력을 받아 알맞은 컨트롤러로 넘김 |
| `com.back.global.app.AppContext` | 공유 객체(Scanner, 컨트롤러, 서비스, 리포지터리)를 하나씩만 생성 |
| `com.back.global.rq.Rq` | 명령어 파싱 (`삭제?id=1`) |
| `domain.system.controller.SystemController` | 종료 |
| `domain.wiseSaying.controller.WiseSayingController` | 등록·목록·삭제·수정 응대 (Scanner·출력 사용) |
| `domain.wiseSaying.service.WiseSayingService` | 순수 비즈니스 로직 (Scanner·출력 없음) |
| `domain.wiseSaying.repository.WiseSayingRepository` | 생성·조회·수정·삭제 (Scanner·출력 없음) |
| `domain.wiseSaying.entity.WiseSaying` | 명언(번호·내용·작가) |

## 명령어

- `등록`, `목록`(최신순), `삭제?id=N`, `수정?id=N`, `종료`
- 없는 번호는 `N번 명언은 존재하지 않습니다.` 안내

## 실행 / 테스트

```
./gradlew run
./gradlew test
```
