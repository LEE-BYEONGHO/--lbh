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
