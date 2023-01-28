# -_-
#c
n개를 입력하고 정사각형(n*n)을 입력한다. (1은 집이 있음 0은 없음) 인접한집끼리가 단지가 된다 대각선은 안되고 상하좌우만 가능하다 단지수와 단지에 속하는 집의 수를 오름차순으로 출력하는 프로그램을 작성해보자!
dfs-> 깊이 탐색알고리즘을 이용해보자
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int answer[26][26] = {0};
int apartment[26*26] = {0}, n, count, sum = 0;
int xx[4] = {-1, 1, 0, 0};
int yy[4] = {0, 0, -1, 1};

int check(int x, int y){
    if(x < 0 || y < 0 || x >= n || y >= n) {
        return 0;
    }
    if(answer[x][y] == 1) {
        answer[x][y] = 0; count++;
        int i;
        for( i = 0; i < 4; i++) {
            check(x + xx[i], y + yy[i]);}
        return 1;
        
    }
    return 0;   
}


int main()
{
	int i,j;
    scanf("%d", &n);
    for(i = 0; i< n; i++){
        for(j = 0; j< n; j++){
            scanf("%1d", answer[i] + j);
        }
    }
    for(i = 0; i < n; i++) {
        for(j = 0; j < n; j++) {
            if(check(i, j) == 1) {
                apartment[count]++; count=0;
                sum++;
            }
        }
    }
    printf("%d\n", sum);
    for(i = 0; i< 26*26; i++) {
        if(apartment[i] != 0){
            int k = apartment[i];
            for(j = 0; j < k; j++) {
                printf("%d\n", i);}}
    }
    return 0;
}
//생각보다 구현하는것이 어렵다
