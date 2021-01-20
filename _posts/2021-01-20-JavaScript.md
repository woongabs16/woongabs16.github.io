# JavaScript
1. 사용자와 상호작용 하는 언어<br>
2. 웹브라우저는 한 번 화면에 출력되면 바꿀 수 없지만 JavaScript를 이용하여 바꿀 수 있다. <br>
3. JavaScript가 HTML을 제어하는 언어다.<br>
4. JavaScript - 동적 / HTML - 정적

---
<br/>

## 1. JacaScript 태그
- `<script> </script>` : 웹브라우저에게 자바스크립트라는 것을 알려주기 위해<br>
- `<input type="button">` :버튼 태그<br>
  `<input type="button" value="hi">` : 버튼 안에 글씨 넣고 싶을 때 <br>
- alert : 경고창
 `<input type="button" value="hi" onclick="alert('hi')">` <br>
- 사건,event : 웹브라우저 위에서 일어나는 일 <br>
    -> event가 일어났을 때 javascript가 실행되도록 하는 것이 onclink<br>
    ex) onclink, onchange, onkeydown<br>
- `<input type="text">`:네모 안에 글씨 입력<br>
- onchange : 변화가 일어났는지 감지<br>
  `<input type="text" onchange="alert('changed')">` <br>
- onkeydown : 키를 눌렀을 때 이벤트 <br>
  `<input type="text" onkeytdown="alert('key down!')">` <br>
- console : 자바스크립트를 자동으로 실행시켜 줌. <br>
  - (검사->console or element에서 Esc)
  - 글자수 세기 : `' '.length`
* `document.querySelector('')` : 제공한 선택자 또는 선택자 뭉치와 일치하는 문서 내 첫 번째 Element를 반환
  - 배경색 : `document.querySelector('body').style.backgroundColor = '색';`
  - 글씨색 : `document.querySelector('body').style.color = '색';` 


-----
<br>

## 2. JavaScript 데이터 타입
* Number 숫자
  - 산술연산자 : + - * /
* 문자  " "   ' '
* 문자열 string https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String
 - `" ".toUpperCase()` : 소문자를 대문자로
 - `" ".indexOf('문자')` : 특정문자 위치찾기
 - `" ".trim()` : 공백없애기
* 1 숫자 / "1" 문자열 / 1+1 숫자(2) / "1"+"1" 문자열(11)

---
<br>

## 3. 변수와 대입연산자
* 변수 : 바뀔 수 있는 값 <br>
  ex) var name='soo'; <br>"My name is "+name+" Kim"
---
<br>

## 4. 비교연산자와 Boolean 데이터 타입
- 비교연산자
  - A === B : A와 B가 같은가<br/>
    ex) document.write(1===1)
  - A &lt; B : A가 B보다 작은가<br/>
    ex) document.write(1>2) <br/>
    EX) 
      ```
      <h3>1===1</h3>
        <script>
          document.write(1===1);
        </script>

        <h3>1===2</h3>
        <script>
          document.write(1===2);
        </script>
    ```
    ```
       1===1 
       true  
       1===2 
       false
    ```
* Boolean : True/False

---
<br>

## 5-1. 조건문
  ```
  <h2>IF-true</h2>
    <script>
      document.write("1<br>");
      if(true){
        document.write("2<br>");
      } else {
        document.write("3<br>");
      }
      document.write("4<br>");
    </script>
 ```
 ```   
   1
   2
   4
 ```
 ```
  <h2>IF-false</h2>
    <script>
      document.write("1<br>");
      if(false){
        document.write("2<br>");
      } else {
        document.write("3<br>");
      }
      document.write("4<br>");
    </script>
```
```
   1
   3
   4
```
<br>

## 5-2. 조건문 활용 
* java element value 가져오기 : `document.querySelector(' ').value`
```
 <input id="night_day" type="button" value="night" onclick="
        if(document.querySelector('#night_day').value === 'night'){
          document.querySelector('body').style.backgroundColor = 'black';
          document.querySelector('body').style.color = 'white';
          document.querySelector('#night_day').value = 'day';
        } else {
          document.querySelector('body').style.backgroundColor = 'white';
          document.querySelector('body').style.color = 'black';
          document.querySelector('#night_day').value = 'night';
        }
      ">
```
 -> night: 배경검정,글씨하양,버튼 day로 바꾸기 / day: 배경하양,글씨검정,버튼 night로 바꾸기

---
## 6. 리팩토링 - ex1.html
### 리팩토링(refactoring) 
: 동작 그대로 두고 코드를 효율적으로 만들어서 가독성 높이고 유지보수 편리하게 만들고 중복코드를 낮추는 방향으로 코드를 개선하는 작업
* `this.value()`
  - index 태그를 참조하는 것은 this로 하기 때문에 id없어도 됨
 ```
  ex) <input type="button" value="night" onclick="
        if(document.querySelector('#night_day').value === 'night'){
             ~
          document.querySelector('#night_day').value = 'day';
        }

   => <input type="button" value="night" onclick="
        if(this.value === 'night'){
            {
           ~
          this.value = 'day';
        }
```        

### 중복 제거 - 변수활용
   `var target = document.querySelector('body');`
   ```
  ex) <input type="button" value="night" onclick="
        if(this.value === 'night'){
            {
           document.querySelector('body').style.backgroundColor = 'black';
           document.querySelector('body').style.color = 'white';
           this.value = 'day';
        }
  => <input type="button" value="night" onclick="
        var target = document.querySelector('body');
         if(this.value === 'night'){
          target.style.backgroundColor = 'black';
          target.style.color = 'white';
          this.value = 'day';
        }
   ```

--- 
<br>

## 7. 배열
* var coworkers = ["yeon", "soo"]; <br/>
-> coworkers 변수에 배열이라는 새로운 데이터타입을 담음
* 배열 가져오기 <br/>
   document.write(coworkers[0]); <br/>
   document.write(coworkers[1]); <br/>
  => yeonsoo
* 배열 카운트 :  `document.write(coworkers.length);`
* 배열 데이터 추가 :  `coworkers.push(' ');`

---
<br>

## 8. 반복문  ex7.html
### 8-1. 반목문 ex)
```
 var i = 0;
       while(i < 3){
         document.write('<li>2</li>');
         document.write('<li>3</li>');
         i = i + 1;
       }
```
  => i가 0부터 시작해서 1,2까지 실행되고 다음3부터는 Fasle가 되어 실행 안됨.
<br/>
<br/>
### 8-2.  배열과 반복문 
* 배열 : 순서대로 연관된 데이터를 정리하는 것
* 반복문 : 순서대로 배열에 담겨있는 데이터를 하나씩 꺼내서 자동화 처리하는 것
<br/>

### 8-3. 배열과 반복문의 활용
`document.querySelectorAll(' ')` : 배열(노드리스트 출력)
```
var alist = document.querySelectorAll('a');
          var i = 0;
          while(i < alist.length){
            alist[i].style.color = 'blue';
            i = i + 1;
```
---
<br/>

## 9. 함수
```
function nightDayHandler(self){
        var target = document.querySelector('body');
        if(self.value === 'night'){
          target.style.backgroundColor = 'black';
          target.style.color = 'white';
          self.value = 'day';

          var alist = document.querySelectorAll('a');
          var i = 0;
          while(i < alist.length){
            alist[i].style.color = 'powderblue';
            i = i + 1;
          }
        } else {
          target.style.backgroundColor = 'white';
          target.style.color = 'black';
          self.value = 'night';

          var alist = document.querySelectorAll('a');
          var i = 0;
          while(i < alist.length){
            alist[i].style.color = 'blue';
            i = i + 1;
          }
        }
      }
```
```
<input id="night_day" type="button" value="night" onclick="
     nightDayHandler(this);
   ">
```
--- 
## 10. 객체
* 객체 : 이름이 있는 정리정돈 상자
### 객체 문법
  - 객체 만드는 방법
    ``` 
    var coworkers = {
      "programmer" : "egoing",
      "designer" : "leezche"
    };
    ```
  - 객체 불러오는 방법 <br>
    ```
    coworkers.programmer <br>
    coworkers.designer
    ```
  - 객체 정보 추가하는 방법 <br>
     ```
     ex) coworkers.bookkeeper = "deru";
         coworkers.bookkeeper
     ex) coworkers["data scientist"] = "taeho"
         coworkers["data scientist"]
     ```
  - 생성된 데이터 모두 가져오는 방법
    ```
    for(var key in 객체이름){
      document.write(key);
    }  //객체에 있는 데이터 수 만큼 중괄호가 실행되는데 실행될때마다 key값이 객체에 있는 하나하나를 변수값으로 세팅해줌
    ```
  - 객체에 소속된 값으로 함수 지정하는 방법
    ```
    coworkers.변수 = function(){
      for(var key in this){
        document.write(key+' : '+this[key]+'<br>');
      }
    }
    ```
 
 

