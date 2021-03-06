###### 20170512
## 마크업 이해 - HTML
출처 :html/css도서 -[웹표준가이드]

#### 1. 기본태그

#### 1. 기본 태그
HTML은 마크업언어로, 내용에 의미를 부여하는 언어이다. 따라서 각 요소의 속성 자체를 그대로 유지하는 것이 좋다. 디자인 요소는 최대한 css에서 해결하도록 한다.


##### # `<p>`
- 단락을 의미, paragraph
- 블록 요소
- 줄바꿈을 하려면 <br>을 사용
- ==다른 블록 요소를 포함할 수 없는 유일한 블록요소이다!!==

<br>
##### # `<pre></pre>`
HTML 파일에 작성한 단락 모습 그대로 화면에 출력한다. 따라서 줄바꿈을 위해 `<br>`을 사용할 필요가 없다. 
예><pre>
hello!
html!
</pre>



<br>
##### # `<div></div>`
- 특별한 의미가 없는 블록 요소
- 블록 요소와 인라인 요소 모두를 담을 수 있는 그릇이다. 
- 콘텐트를 논리그룹으로 묶어야하는 상황, 장이나 기사와 같이 콘텐트 의미별로 구역을 나눌 떄 사용
- class, id를 사용하여 css를 적용
- 문서전체 구조를 파악하는 데 큰 도움.
- 모든 종류의 콘텐트에 무분별하게 사용하지 않는다.

- **`<span>`** <br>
  div처럼 의미가 없다. 하지만 인라인 요소로, 특정 콘텐트에 상세한 특성을 부여할 때 사용한다. 

-	팁!<br>
이렇게 종료태그에 주석을 달아놓으면 나중에 닫는 태그를 매칭하는 데 시간을 단축할 수 있다. 

~~~
		</div><!--chapter1의 div-->
	</div><!--chapters의 div-->
</div><!--all-chapter의 div-->
~~~
		
		
##### # 중첩목록 

~~~
<ol>
 <li>커피</li>
 <li>콜라</li>
  <ul>
   <li>코카콜라</li>
   <li>펩시</li>
  </ul>
</ol>
~~~
<ol>
 <li>커피</li>
 <li>콜라</li>
  <ul>
   <li>코카콜라</li>
   <li>펩시</li>
  </ul>
</ol>

<br>
##### ==# 블록 요소와 인라인 요소==
|블록 요소|인라인 요소|
|:-----:|:-------:|
|h, p, pre, div, ol, ul, li, dt, dd|br, a, strong, em, i, abbr|

- 블록 요소는 다른 블록 요소 또는 인라인 요솔를 포함할 수 있다.
- 블록 요소는 인라인 요소 안에 포함될 수 없다.
- 인라인 요소는 다른 인라인 요소만 포함할 수 있다.
- p는 블록 요소이지만 다른 블록 요소를 포함할 수 없다. 

<br>
##### # 강조 - `<strong>과 <em>` 
- `<b>` 또는 `<i>`는 문서에 디자인 속성을 부여한다. 
- `<strong>` 또는 `<em>`는 문서의 의미를 강조한다.
- `<b>` 또는 `<i>` 를 사용하기 보다는 문서에 의미를 부여하는 `<strong>` 또는 `<em>`을 사용하는 것이 맞다.

##### # 인라인 요소 - `<abbr>`
- 약어를 의미한다.
- 예시

~~~
<abbr titile="World Wide Web Consortium'>W3C</abbr>
~~~

##### # 인라인 요소 - `<span>`
- 의미가 없음.
- 특정 컨텐츠에 상세특성을 부여할 때 사용
- 보통 가장 안쪽에서 쓰인다.

##### # 인라인 요소 - `<a>`
`<a href="id값">`
`<a href="#chapter1-2">`

- 같은 페이지 안에서 부여한 아이디 값을 기준으로 링크를 걸 수도 있다. 

- 중요!
`(x) <a href="dd.com"><h1>hello</h1></a>`
h1은 블록 요소이므로 a로 감쌀 수 없다. 따라서 h1 안에 a가 들어가야한다. 
`(o) <h1><a href="dd.com">hello</a></h1>`

<br>
<br>
#### 2. 내장 콘텐트 태그

- 브라우저는 기본적으로 이미지 포맷을 지원하여 이미지에 대한 플러그인은 필요없지만 비디오나 오디오는 플러그인을 지원해야한다.

##### # 비디오, 오디오 내장 - `<object>`

~~~
<object data="/video/a.mpeg" type="video/mpeg">
 <img src="images/error.png" alt="reload please">
</object>
~~~

* **data** : 포함할 파일의 url
* **type** : 브라우저가 콘텐트를 지원할 수 있는지 다운로드 전에 알 수 있다. 
<br>필수 속성은 아님. 그러나 포함하는 것이 좋음.<br>
==파이어폭스의 경우 필수로 적어야함.==
* 재생불가한 경우: **object 태그 안에 img태그를 넣어** 재생이 안될 때 이미지가 표시되도록 한다. 
 

- **콘텐트 타입 : MIME(Multipurpose Internet Mail Extensions)** <br> 서버에서 콘텐트를 제공할 때 콘텐트 타입을 제공하여 브라우저가 타입을 파악한다. <br> 기본: "text/html", or "video/mpeg"

==단점 : `<object>`태그는 너무 광범위하다.==

- 이미지, 플래시, 실버라이트, html, 오디오, 비디오 무엇이든지 삽입하는 용도로 설계되었다.
- 브라우저가 인식하지 못해 비디오와 오디오콘텐트에 특화된 기능(재생컨트롤)을 표시할 수 없다. 
- 가끔 비디오 전용 기능을 이미지 컨텐트에 삽입하기도 하는 오류를 범한다.

==대안 : 
비디오, 오디오가 아닌 플러그인 콘텐트: `<object>` 사용(플래시 기반)<br>
비디오, 오디오 콘텐트 : `<video>`태그!==

##### # `<video>` 태그 

~~~
<video poster="images/error.png">
 <source src="비디오파일출처1" type="video/mp4">
 <source src="비디오파일출처2" type="video/ogg">
</video>
~~~

* poster : 비디오 로딩중 또는 재생불가일 때 이미지를 불러와준다.
* autoplay : 비디오 로딩시 자동재생
* loop : 반복재생
* controls : 재생 컨트롤 표시
* width, height : 성능면에서 적는 것이 좋음. 

##### # `<audio>` 태그

~~~
<audio controls>
 <source src="오디오파일출처1" type="audio/mp3">
 <source src="오디오파일출처2" type="video/wave">
 <object data="플래시파일출처">
  <p>오디오 지원불가</p>
 </object>
</audio> 
~~~
 
* 오디오는 poster값을 지원하지 않는다.
* 재생불가 시 대신 object로 플래시 문구를 띄워준다.


<br>
<br>
#### 3. form 태그

##### # `<form>`
- **method** : 폼에 입력된 데이터가 전송되는 방식을 결정. GET/POST가 있음.
- **action** : 전송된 데이터를 표시할 스크립트의 url 정보를 부여.

<br>
##### # `<input>` 
- ==**name**== : 반드시 있어야함!! <br> 폼이 서버로 전송되었을 때 name의 속성값이 폼 데이터의 구분자가된다. 이 속성을 주지 않으면 서버는 전달 받은 데이터가 어떤 것인지 구분하지 못한다.<br>
- **disabled** : 폼 컨트롤을 비활성화.
- **checked** : 미리 체크해놓는 효과
- **multiple** : 다중선택 가능
- **type** : 폼 요소 구분. <br> ex_

	|종류|이름|내용|name속성|
|:--:|:--:|:--:|:--:|
|텍스트필드|text|**size**: 입력받을 문자의 크기(텍스트필드의 width값, css를 사용하는 것이 낫다.)<br> 사용할 수 있는 최대문자수(=maxlength)가 아님!!!|input은 전송받은 데이터와 name값을 연결지어 서버로 전송한다.|**value** : 해당 요소의 초깃값을 설정(힌트 등)
|체크박스|checkbox|체크되지 않은 값은 전송되지 않는다.<br>**checked** : 미리 체크한 상태로 전송 가능<br>사용자에게 입력을 강요(필수입력)하기 위해 사용한다.<br>여러 개 체크가능하다.|체크된 여러 개의 값이 name-value 쌍으로 연결되어 서버로 전송된다.| 
|라디오버튼|radio|여러 개 체크가 불가능하다.<br>**checked** : 미리 체크한 상태로 전송 가능<br>같은 name속성을 갖는 라디오버튼이 여러개 있으면 전송될 때 미리 checked를 적어놓은 것이 전송된다. 남자, 여자 라디오버튼을 선택할 때 체크하지않으면 미리 남자에 적용해놓은 checked가 작용하여 서버로 보내진다.|
|푸시버튼<br>**button**|버튼|타입 버튼도 있고 요소 버튼도 있다.<br>value값을 줘서 사용자 문구를 버튼 위에 입력할 수 있다.|
|푸시버튼<br>**submit**|제출|버튼 type의 디폴트값이다.<br>기본적으로 submit이라는 value값을 가지지만 value값을 따로 줘서 사용자문구를 버튼 위에 입력할 수 있다.|
|푸시버튼<br>**reset**|초기화|기본적으로 reset이라는 value값을 가지지만 value값을 따로 줘서 사용자문구를 버튼 위에 입력할 수 있다.|

<br>
##### # `<button>`
- 버튼
- 디폴트: submit
- 비어있지 않은 요소로, value가 아닌 요소 내부의 내용이 버튼 위에 적힌다.
- IE6, 7에서는 데이터전송에 오류가 많아 input으로 대체한다.|

<br>
##### # `<select>` - 드롭다운 메뉴.
- **option** : 메뉴 아이템(`<li>`와 비슷) 
- **optgroup** : 여러 개의 옵션을 그룹지어 보여준다.  
- **multiple** : 잘 안쓴다. 다수의 option을 체크할 때.

##### # `<textarea>` - 장문의 텍스트 입력필드
- 비어있지 않은 요소로, value에 값을 주지않고 요소 안에 내용을 입력하면 사용자가 입력할 데이터의 예제를 보여줄 수 있다.

<br>
##### # `<label>` - 폼 컨트롤에 대한 문구
- 사용자 입장에서 어떤 폼인지, 무엇을 입력해야 하는지 문구를 보여줄 수 있는 태그.
- 암묵적, 명시적 레이블 둘 다 쓴다. 
- (1) 암묵적 레이블 : `<label>`안에 input요소를 넣는 방식

~~~
<label>monkey type here: 
<input type="text" name="monkeytype" value="less than 10 letters">
</label>
~~~

<label>monkey type here: <input type="text" name="monkeytype" value="less than 10 letters"></label>

<br>

- (2) **명시적 레이블** : for 사용하여 인풋의 id값을 연결

~~~
<label for="monkey">monkey type here:
 <textarea name="monkeytype" id="monkey">
 hello! introduce yourself.
 </textarea>
<label>
~~~

<label for="monkey">monkey type here:
 <textarea name="monkeytype" id="monkey">
 hello! introduce yourself.
 </textarea>
<label>

- for의 값은 label요소의 내용을 부여할 폼의 id값이다.

<br>
##### # 테이블
- **colspan** : 가로병합 
- **rowspan** : 세로 병합
 
<br>

#### 4. 특수 문자 

|종류|모양|문자열 변환(escaping)|
|:--:|:--:|:--:|
|copyright|&copy;|`&copy;`|
|앰퍼센트|&amp;|`&amp;`|
|부등호|&lt;, &gt;|`&lt;`, `&gt;`|
|작은 따옴표|&lsquo;, &rsquo;|`&lsquo;`, `&rsquo;`|
|큰 따옴표|&ldquo;, &rdquo;|`&ldquo;`, `&rdquo;`|
|유로기호|&euro;|`&euro;`|
