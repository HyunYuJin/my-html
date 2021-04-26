# my-html
🍽저만의 html boilerplate를 만들어보는 공간입니다.

<br />

### Doctype
HTML5가 제대로 구현돼 있지 않은 브라우저에서도 내용을 표준 모드로 전환하여 호환성 문제를 염려할 필요가 없습니다.

```html
<!DOCTYPE html>
```
* 브라우저에 의해 처리될 문서가 어떤 버전의 마크업 언어로 작성되었는지 알려줍니다. 
* Doctype 선언 이전에 다른 요소가 들어간다면 비표준모드로 렌더링이 될 수 있음을 주의합시다!
* 다양한 렌더링 모드를 가지고 있습니다.
  * 표준모드(Standards mode): HTML, CSS가 모든 표준에 따라 엄격하게 렌더링이 됩니다. **IE6 이상 버전**을 포함한 모든 브라우저에서 표준 모드로 렌더링 됩니다.
  * 비표준모드(Quirks mode): 브라우저가 구버전 브라우저의 렌더링도 흉내내줌으로써 비표준 기능도 허용을 해줍니다. IE6 이상 버전에서 관용모드를 사용하면 사실 **윈도우용 IE5.5**와 똑같이 렌더링됩니다.
    * IE6 에서는 XML선언을 넣으면 관용모드로 작동합니다.
    ```html
    (<?xml version="1.0' encoding="UTF-8"?>)
    ```
  * 거의 표준모드 / 엄격모드(Almost standards mode / Strick mode): 표준모드와 단 한가지만을 제외하고 동일합니다. - table 셀에서만 비표준모드로 실행하고 나머지는 모두 표준모드를 따릅니다.

* 표준모드와 비표준 모드 차이
  * table에서의 font-size
    * 표준모드: table 내의 텍스트는 기본 font-size를 따릅니다.
    * 비표준모드: table 내의 텍스트는 기본 font-size를 따르지 않습니다.

<br />

### 휴먼랭귀지와 Modernizr
휴먼랭귀지는 웹 브라우저나 음성 브라우저에서 올바르게 해석할 수 있도록 작성된 콘텐츠의 언어를 선언합니다.

```html
<html lang="ko" class="no-js">
```

* 한국어(ko) 
* 영어 (en) 
* 일어(ja)

<br />

### 문자 세트 지정
charset 속성으로 문자 세트를 지정합니다. 
문자 세트는 사용언어를 표현하는 데 필요한 모든 문자를 모아둔 것으로, 여기에는 기호, 공백 등도 포함됩니다.

```html
<meta charset="utf-8">
```

문서에서 사용한 문자 인코딩 방식이 무엇이지를 선언합니다.
추천 인코딩 방식은 utf-8 입니다.
* UTF-8: 전세계의 모든 문자를 통용할 수 있는 유니코드 입니다.
* ERC-KR: 한글, 한자와 영어를 지원해주는 유니코드로 한글 한자를 2Byte로 합니다.

<br />

### IE 렌더링 모드 지정
IE 브라우저로 접근했을 경우 렌더링 모드를 지정합니다.

```html
<meta http-equiv="x-ua-compatible" content="ie=edge">
```

* ie=edge는 항상 최신의 엔진으로 렌더링을 합니다.

<br />

### 문서의 제목과 콘텐츠 소개
문서의 제목은 검색엔진의 최적화 부분과 관련이 깊습니다.

```html
<title></title>
<meta name="description" content="">
```

* title은 IE 브라우저의 인코딩과 연관된 보안 문제를 예방하기 위해 가능한 빨리 선언되어야 합니다.
* description meta tag는 문서가 포함하는 콘텐츠의 내용을 간략하게 작성합니다.

<br />

### 모바일 뷰표트 제어
PC, 모바일 휴대폰, 태블릿과 같은 다양한 기기들의 화면의 크기를 제어합니다.

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

<br />

### Favicon 등록
로고와 비슷한 역할을 하는 것으로 해당 웹 페이지의 성격을 보여줍니다.

루트(root) 디렉토리에 **16x16** 과 **32x32**의 이미지를 하나에 품은(multiple sizes1) favicon.ico 파일을 위치시킵니다.

* PNG Favicon: Chrome, Firefox, Opera 7+, Safari 4+ 지원
* ICO FAvicon: Chrome, Safari (ICO > PNG 우선 순위)

```html
 <!-- 32×32 -->
<link rel="icon" href="/favicon.ico">
<link rel="icon" href="/icon.svg" type="image/svg+xml">

<!-- 180×180 -->
<link rel="apple-touch-icon" href="/apple-touch-icon.png"> 
<link rel="manifest" href="/manifest.webmanifest">
```

<br />

### Stylesheet 삽입
CSS 초기화를 위한 Normalize.css와 페이지의 스타일을 담당하는 css 파일을 삽입합니다.

```html
<link rel="stylesheet" href="css/normalize.css">
```

<br />

### Modernizr 스크립트 삽입
Modernizr는 JS 오픈소스 라이브러리로, HTML와 CSS의 요소와 속성들에 지원 여부를 점검하는 방식으로 기존의 (Legacy)보다 더 정확한 분류가 가능합니다.

* 특히 구형 IE 브라우저에서 지원하지 않는 Sementic tag를 지원하기 위해서 html55Shiv를 추가할 수 있습니다.
