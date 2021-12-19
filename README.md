
# 큐시즘 반올림데이 조편성 알고리즘 수도 코드
## 팀명: AI(C4)
## 대상 수상작
***

## 중점으로 둔 부분
1. 기획 / 개발 / 디자인을 따로 구성해서 합치는 방향
2. 요일을 기본으로 고려
3. 역량 점수를 그 다음으로 고려
4. 개발팀의 경우 개발 분야를 고려
5. 알고리즘으로 한 번에 해결되지 않을 수 있으므로 용도에 따른 교체 기능(성비, 점수, 분야)을 추가하여 균등하게 분배할 수 있도록 함


## 수도 코드
* 기획/개발/디자인 각각의 테이블로 분할

### 디자인팀
* 고려사항: 요일

* 요일이 열이고, 행이 이름인 테이블을 만들고
* 행별로 가능 요일 개수를 저장하는 열을 생성
* 가능 요일이 적은 순서로 행 정렬
* 상단에서부터 빈 요일 팀에 배치

### 기획 팀
* 고려사항: 요일, 기획 역량 점수

* 요일이 열이고, 행이 이름인 테이블을 만들고
* 행별로 가능 요일 개수를 저장하는 열을 생성
* [가능 요일이 적은] / [기획 역량 점수가 높은] 순서로 행 정렬
* 상단에서부터 빈 요일 팀에 배치
  - 만약 한 팀에 사람수가 3명일 경우 같은 요일 다른 팀으로 차선 배치, 없을 경우 다른 요일로 배치


### 개발 팀
* 고려사항: 요일, 개발 역량 점수, 분야

* 프론트 / 백엔드 / 데이터+인공지능으로 테이블을 분할(없음은 일단 대기)
* 각 분야별로 [개발 역량 점수가 높은] 순서로 행 정렬
* 상단에서부터 가능요일 세기
  - 요일별 가능한 사람수를 세고, 2보다 적을 경우 가능 요일에서 배제, 다시 가능 요일 세기
  - 4명 이상일 경우, 개발 역량 점수 순으로 분할
* 남는 자리에 없음 배치


### 합치기
* 개발 팀에서 생성된 요일 기준으로 나머지 팀은 병합

<br>

***

<br>

## 추가 기능 : 교체기능
### 입력: 바꾸고자하는 학회원의 이름, 용도
  - 용도: 성비, 점수, 분야

### 기본 알고리즘
* 같은 조일 경우 제외
* 같은 팀인 사람 중에서 교체하고자 하는 사람의 요일을 상호 포함하는 학회원의 이름을 리스트에 저장
* 기획/디자인
* 개발팀일 경우
  - 용도가 분야일 경우
    + 같은 분야의 사람 제외
    + 출력할 때 해당 분야 명시
  - 그렇지 않을 경우
    + 프론트 / 백 / 데이터+인공지능의 분야가 다르면 리스트에서 제외
    + 만약, 같은 분야가 없다면 출력할 때 분야 명시

### 출력
* 용도: 성비
  - 같은 점수인 사람 먼저 출력
* 용도: 점수
  - 입력된 이름의 해당 팀 역량 점수가 3점 이상일 경우, 오름차순으로 배치
  - 2점 이하일 경우, 내림차순으로 배치
* 용도: 분야
  - 출력할 때 해당 분야 명시


