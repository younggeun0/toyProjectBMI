# BMI지수 계산기 구현 기록

## 2018-12-03
* 콘솔로 구현

![01](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi01.PNG?raw=true) 

---

## 2018-12-10
* java AWT를 이용한 GUI 구현(Frame만)


![02](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi02.png?raw=true) 

![03](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi03.png?raw=true) 



## 2018-12-11
* 종료버튼 event처리 구현


## 2018-12-13
* GUI 디자인(Frame)과 이벤트처리(Listener 인터페이스들) 분리 구현
* 키, 몸무게 입력 후 계산버튼 클릭시 라벨값 변경, TextArea에 계산결과에 해당하는 결과 
* 클래스다이어그램과 결과창


![05](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi05.png) 

![04](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi04.png)



## 2018-12-13
* Dialog를 사용한 결과출력 구현
* 패키지를 run, view, event로 분리했음
  * Dialog 작업을 위한 클래스 추가 생성(BMIResult, BMIResultEvt)
  * 계산버튼 클릭 시 연산작업 후 결과값을 Dialog에게 전달해서 결과 출력


![06](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi06.png)

![07](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi07.png)


## 2018-12-14
* Swing을 이용하여 구현
  * Dialog로 직접 InputDialog, MessageDialog, ConfirmDialog를 구현할 필요가 없어짐(JOptionPane 이용)
  * 따라서 아래 클래스 다이어그램처럼 구현 내용이 줄어진다
  * AWT에 비해 조금 더 향상된 컴포넌트를 보여준다.


![08-classDiagram](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi08.png)

![09-Swing](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi09.png)


## 2019-12-15
* "BMI란?"을 Label이 아닌 TitledBorder로 구현
* 예외처리
  * 키나 몸무게 TextField에 입력이 안됐을 시 Message Dialog 띄우고 Focus처리
  * 문자열 입력시 MessageDialog로 재입력 유도


![10](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi10.png) 


## 2018-12-20
* 히스토리 UI 디자인, Swing을 이용한 다이얼로그 구현
* 입력 내용(키,몸무게)과 실행 날짜, BMI결과값을 HistoryVO로 객체로 저장
  * ArrayList로 결과를 저장 후 BMIHistory에 전달 후 JTable로 결과 표시
  * ~~현재 history 결과창 출력시 빈 row가 들어가는 이슈있음(보완예정)~~

![11](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi11.png?raw=true) 

![12](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi12.png) 

![13](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi13.png) 


## 2018-12-21
* 빈 row가 들어가는 문제 해결
  * listRow.size()를 DefaultTableModel 생성자 파라미터로 줬었기 때문에 추가된 row만큼 빈 row가 생겼었음
* 실행시 loadHistory메서드로 `history.dat` 파일이 존재하는지 확인 후 읽어들임
  * 읽은 List데이터를 BMIEvt에 전달, History버튼 눌리면 BMIHistory에 전달, 출력
* 실행시 저장된 내용을 불러들일지 묻는 Dialog 구현
  * `history.dat`가 존재하면 내용을 읽어들여서 History 버튼 클릭시 history 데이터를 뿌려줌
* 종료할때 저장할 경로를 묻고 입력하면 저장, 입력안하면 종료된다.

![14](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi14.png) 

![15](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi15.png) 

![16](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi16.png) 

## 2018-12-26
* history.dat를 직렬화 사용 Object형태로 저장, 읽어오기 구현
* 객체가 직렬화되어 저장, 쉽게 알아볼 수 없어서 보안성향상
* 직렬화를 사용하여 클래스 다이어그램 수정

![17](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi17.png) 

![18](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi18.png) 

## 2019-01-13

* JDBC DB 설계 및 저장, 불러오기 구현
* 프로그램이 시작될 때 이름을 받기
	* HistoryVO에 name을 추가

![19](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi19.png) 

* HistoryVO 정보를 저장할 테이블 생성

```sql
-- table 생성
CREATE TABLE bmi_history (
  name VARCHAR2(15) NOT NULL,
  input_date DATE DEFAULT SYSDATE,
  bmi_result VARCHAR2(100) NOT NULL,
  height NUMBER(5,2) NOT NULL,
  weight NUMBER(5,2) NOT NULL,
  bmi_num NUMBER(5,2) NOT NULL
);

-- 가데이터 삽입
INSERT INTO bmi_history(name, bmi_result, height, weight, bmi_num)
VALUES('test01', 'test_result', 1.0, 1.0, 1.0);
INSERT INTO bmi_history(name, bmi_result, height, weight, bmi_num)
VALUES('test02', 'test_result', 1.0, 1.0, 1.0);
INSERT INTO bmi_history(name, bmi_result, height, weight, bmi_num)
VALUES('test03', 'test_result', 1.0, 1.0, 1.0);
INSERT INTO bmi_history(name, bmi_result, height, weight, bmi_num)
VALUES('test04', 'test_result', 1.0, 1.0, 1.0);
INSERT INTO bmi_history(name, bmi_result, height, weight, bmi_num)
VALUES('test05', 'test_result', 1.0, 1.0, 1.0);

-- COMMIT
COMMIT;

-- 결과 확인    
SELECT * FROM bmi_history;
```
![21](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi21.png) 


* DB에 저장된 History 내역을 .dat 파일로 저장하는 "저장" 추가
* 파일 읽어들여서 DB에 추가하는 "불러오기" 추가

![20](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi20.png) 

![22](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi22.png) 

* JDBC를 추가한 새로운 클래스 다이어그램

![23](https://github.com/younggeun0/younggeun0.github.io/blob/master/_posts/img/toyProjects/bmi/bmi23.png) 
