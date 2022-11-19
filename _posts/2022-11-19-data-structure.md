---
layout: single
title: "about Data Structure"
toc: true
toc_sticky: true
toc_label: "study"
categories:
    - Study
---

<br>

<br>

## 자료구조

<br>

- Algorithm

    - 문제를 해결하기 위한 단계적인 절차와 단계를 pseudo code를 사용하여 기술하며, 입력, 출력, 명확성, 유한성, 실제성의 5대 조건을 만족
    - 알고리즘에 대한 연산의 빈도수를 차수 (degree)로 표현하며, 연산 차수가 가장 높은 것을 O-표시법으로 사용 // O(1), O(mlog n), O(n), ...
    - 연산의 빈도에 대한 차수가 가장 낮은 것을 오메가-표시법으로 사용하며, O-표시법과 오메가-표시법의 교차집합이 되는 h-표 표시법을 최적 알고리즘으로 사용

- 배열
    - 연속적인 기억장치에 하나의 블록으로 저장
    - 연속적으로 배치된 기억장소의 위치이며, Index와 값(value)을 mapping
    - 2개 이상의 변수가 공통된 성질을 가지고, 하나의 변수와 첨자를 사용
    - row-oriented, column-oriented 배열로 구분

<br>

<br>


```c
int a[5] = {14,6,5,31,27}
int imsi, cnt, i;

for (i=0; i<5; i++) {

	imsi = a[i];
	cnt = i-1;
	while(cnt>=0 && imsi < a[cnt]) {

	a[cnt +1] = a[cnt];
	cnt = cnt-1;
}

a[cnt+1] = imsi;
// a 
for(j=0; j<5; j++)
printf("%d, ) a[j];

}
```

<br>
