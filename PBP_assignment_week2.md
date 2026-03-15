# 심화실습-1 보고서

<!-- 
👨🏻‍💻 작성요령
아래 양식에 맞춰 내용을 채워주세요.

⚠️ 주의 ⚠️
단, 해시테그(`#`)로 시작하는 줄은 수정하지 마세요.
제출 내용에서 해시테그로 시작하는 줄이 없어진 경우, 항목 누락으로 간주되어 감점이 있을 수 있습니다.

👀 참고자료
[1] GitHub, GitHub에서 쓰기 위한 빠른 시작, https://docs.github.com/ko/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/quickstart-for-writing-on-github
[2] GitHub, Markdown 기본 문법, https://docs.github.com/ko/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax
-->

## 1. 제출 정보

| 구분 | 내용 |
| --- | --- |
| 학년학기 | 2026학년도 1학기 |
| 과목명(학수번호) | 프로그래밍기초와실습 (DASF004-00) |
| 학번 | 2026310462 |
| 이름 | 이병호 |
| 과제명 | 심화실습-1 |

## 2. 현재 상태

### 2.1 배운적 있는 언어 및 현재 수준

- `{C}` - `{하}`
    - `상, 중, 하` 혹은 `해당없음`
        - 상: 어떤 요구사항을 받아도 어떻게든 구현할 수 있다.
        - 중: 기본적으로 어느정도 수준의 구현은 가능하지만 해당 언어의 고급기술 활용은 어렵다.
        - 하: 가볍게 배워본 정도이다.
- 예: Python - 상
- 예: Java - 중
- 예: C - 해당없음

### 2.2 실습 환경

| 사용한AI 도구 | 개발환경 |
| ChatGPT | GitHub Codespace |
| 예: ChatGPT | 예: GitHub Codespace |

## 3. 코드 리뷰 결과

### 3.1 AI가 생성한 코드를 얼마나 이해할 수 있었는지?
이해도 : 3점
초기에 변수들의 형식과 글자수 제한을 지정하고, 이후에 터미널 환경에서 사용자가 원하는 숫자를 입력하여 해당 메뉴에 접속 후 일정을 관리할 수 있는 프로그램으로 이해함.

- 이해도: 0 ~ 10점 (0점: 전혀 이해하지 못함, 10점: 완전히 이해함)
- 어떤식으로 동작하는 코드로 이해했는지 자유롭게 서술

### 3.2 최초에 입력한 프롬프트와 그 결과물에 대한 평가

#### 최초 프롬프트

```
C언어로 간단한 일정 관리 프로그램을 만들어주세요.
아래 말하는 필수기능이 들어가야됨.
1. 일정 추가
2. 일정 조회
3. 일정 수정
4. 일정 삭제
```

#### 최종 코드 및 실행 결과

> 본 문서 가장 아래 `부록` 섹션에서 `최종 결과물 코드`와 `실행 결과`에 각각 코드 및 실행 결과를 복사 & 붙여넣기로 첨부합니다.

### 3.3 최종 결과물을 얻기까지의 경험

- 처음 과제를 시작할 때, ChatGPT에게 코드를 물어보는 과정까지는 수월하게 진행되었다.
  하지만, 이후 코드스페이스 환경에서 해당 코드를 실행하는 과정 중 익숙하지 않은 인터페이스 덕에 헤매기도 하였고, 이 문제를 해결하기 위해 이전 강의를 다시 되돌려보며 스스로 강의를 복습할 수 있는 기회가 되었다.

## 4. 결론

- 서술형으로 자유롭게 작성
- 코드 분석 과정에서 어려웠던 점
- AI 시대 프로그래밍 학습에 대한 개인적인 견해나 느낀 점

## 참고문헌

- 사용한 AI 도구, 참고한 자료 등

---
---

## 부록

### 실행 결과

- 프로그램의 주요 기능 실행 화면을 터미널에서 텍스트를 복사&붙여넣기로 작성
- 프로그램 실행에 실패했다면, 실패와 관련된 내용을 담아도 좋음

```bash

```

### 최종 결과물 코드
#include <stdio.h>
#include <string.h>

#define MAX 100

struct Schedule {
    char title[50];
    char date[20];
    char time[20];
    char desc[100];
};

struct Schedule list[MAX];
int count = 0;

void addSchedule() {
    if (count >= MAX) {
        printf("일정 저장 공간이 가득 찼습니다.\n");
        return;
    }

    printf("제목: ");
    scanf(" %[^\n]", list[count].title);

    printf("날짜: ");
    scanf(" %[^\n]", list[count].date);

    printf("시간: ");
    scanf(" %[^\n]", list[count].time);

    printf("설명: ");
    scanf(" %[^\n]", list[count].desc);

    count++;
    printf("일정이 추가되었습니다.\n");
}

void viewSchedule() {
    if (count == 0) {
        printf("저장된 일정이 없습니다.\n");
        return;
    }

    for (int i = 0; i < count; i++) {
        printf("\n[%d]\n", i + 1);
        printf("제목: %s\n", list[i].title);
        printf("날짜: %s\n", list[i].date);
        printf("시간: %s\n", list[i].time);
        printf("설명: %s\n", list[i].desc);
    }
}

void editSchedule() {
    int num;

    if (count == 0) {
        printf("저장된 일정이 없습니다.\n");
        return;
    }

    viewSchedule();

    printf("\n수정할 일정 번호: ");
    scanf("%d", &num);

    if (num < 1 || num > count) {
        printf("잘못된 번호입니다.\n");
        return;
    }

    num--;

    printf("새 제목: ");
    scanf(" %[^\n]", list[num].title);

    printf("새 날짜: ");
    scanf(" %[^\n]", list[num].date);

    printf("새 시간: ");
    scanf(" %[^\n]", list[num].time);

    printf("새 설명: ");
    scanf(" %[^\n]", list[num].desc);

    printf("일정이 수정되었습니다.\n");
}

void deleteSchedule() {
    int num;

    if (count == 0) {
        printf("저장된 일정이 없습니다.\n");
        return;
    }

    viewSchedule();

    printf("\n삭제할 일정 번호: ");
    scanf("%d", &num);

    if (num < 1 || num > count) {
        printf("잘못된 번호입니다.\n");
        return;
    }

    for (int i = num - 1; i < count - 1; i++) {
        list[i] = list[i + 1];
    }

    count--;
    printf("일정이 삭제되었습니다.\n");
}

int main() {
    int menu;

    while (1) {
        printf("\n--- 일정 관리 프로그램 ---\n");
        printf("1. 일정 추가\n");
        printf("2. 일정 조회\n");
        printf("3. 일정 수정\n");
        printf("4. 일정 삭제\n");
        printf("5. 종료\n");
        printf("메뉴 선택: ");

        scanf("%d", &menu);

        switch (menu) {
            case 1:
                addSchedule();
                break;
            case 2:
                viewSchedule();
                break;
            case 3:
                editSchedule();
                break;
            case 4:
                deleteSchedule();
                break;
            case 5:
                printf("프로그램 종료\n");
                return 0;
            default:
                printf("잘못된 입력입니다.\n");
        }
    }

    return 0;
}


- AI가 생성한 전체 코드 첨부

```c

```
