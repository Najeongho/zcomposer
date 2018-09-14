---
title: Getting Started
permalink: /docs/home/
redirect_from: /docs/index.html
---

# Cloud Z Action 시작하기

## Step 1. Cloud Z Action 주문하기

- Cloud Z Action을 사용하기 위해서는 먼저 Cloud Z 포털에 서비스 주문을 해야합니다.

### 회원가입 하기

[www.cloudz.co.kr](http://www.cloudz.co.kr) 에 접속하여 `로그인` 버튼 -> `회원가입` 버튼 순으로 클릭합니다. '회원가입 유형'은 기업으로 선택합니다.  

![Step1_6](../img/QuickStart/Step1_6.png)

회원가입 전 서비스 이용 약관 내용에 동의해야 합니다.  
![Step1_7](../img/QuickStart/Step1_7.png)

회원가입에 필요한 정보들을 모두 입력 후 **가입 신청하기** 버튼을 클릭합니다.  
![Step1_8](../img/QuickStart/Step1_8.png)

- 정보 입력 시 **메일 주소는 정확하게 입력**하셔야 합니다. 해당 메일주소로 승인메일(비밀번호, 접속URL 정보 포함)이 발송됩니다.

### 주문하기
회원가입한 정보로 로그인 후 우측 상단에 `콘솔` 버튼을 눌러 콘솔화면으로 이동합니다.  

![Step1_1](../img/QuickStart/Step1_1.png)

콘솔 화면에서 좌측 네비게이션바에 있는 Compute -> Cloud Z Action을 선택한 후 `+ Cloud Z Action` 버튼을 클릭합니다.  

![Step1_2](../img/QuickStart/Step1_2.png)

`주문하기` 버튼을 클릭합니다.  

![Step1_3](../img/QuickStart/Step1_3.png)

상품 구성에 대해 원하는 상품을 선택하고 `주문하기` 버튼을 클릭합니다.  

![Step1_4](../img/QuickStart/Step1_4.png)

최종적으로 주문내역을 확인 및 동의를 하고 `확인` 버튼을 클릭합니다.  

![Step1_5](../img/QuickStart/Step1_5.png)

## Step 2. Cloud Z Action 포털에 로그인하기

[action.cloudz.co.kr](action.cloudz.co.kr) 에 접속 후 우측 상단에 <로그인> 버튼을 눌러 로그인 합니다.  

![Step2_1](../img/QuickStart/Step2_1.png)

로그인 시 Step 1 ([www.cloudz.co.kr](http://www.cloudz.co.kr)) 에서 가입한 회원정보로 로그인 합니다.  

![Step2_2](../img/QuickStart/Step2_2.png)


## Step 3. Cloud Z Action 함수액션 생성하기

- **액션(Action) 이란?: Cloud Z Action을 이용하여 생성 가능한 모든 단위의 추상화된 개념입니다. Cloud Z Action에는 함수액션, 스위치액션, 액션플로우가 존재합니다.**

### 함수액션 생성하기
메인 페이지에서 좌측 상단에 `새로만들기` 버튼을 클릭합니다.  

![Step2_1](../img/QuickStart/Step2_1.png)

`함수` 버튼을 클릭합니다.  

![Step3_1](../img/QuickStart/Step3_1.png)

- 함수 (Function): 코드를 포함한 기본적인 액션입니다.(javascript, python)
- 스위치 (Switch): 조건에 따라 수행되는 액션을 다르게 분기하며, 병렬수행을 가능하게 합니다.
- 플로우 (Flow): 플로우는 정의된 순서대로 여러개의 액션을 호출합니다.
- 트리거 (Trigger): 트리거는 이벤트를 수신하여 연결된 액션을 호출합니다.
- 블루프린트 (Blueprint): 기본제공되는 템플릿 및 다른 사용자들이 공유한 액션을 이요하면 보다 손쉽게 액션을 만들 수 있습니다.

함수액션 생성을 위한 정보들을 입력합니다. 정보 입력 후 <함수만들기> 버튼을 클릭합니다.  

![Step3_2](../img/QuickStart/Step3_2.png)

- \* 는 필수 입력 사항입니다.
- 함수이름: 중복될 수 없습니다.
- 패키지: 선택하지 않으면 '기본 패키지'로 생성 됩니다. `신규 패키지` 버튼을 누르면 패키지를 생성할 수 있습니다. **패키지 생성 후 패키지 안에 함수를 포함시키는 것을 권장합니다.**
- 런타임: 사용할 언어를 선택할 수 있습니다.(베타오픈 기간 **지원 언어는 Nodejs 6, 8** 입니다. python, golang, php7 등의 언어는 추후에 제공 예정입니다.)
- 버전: 코드의 버전관리가 가능합니다.
- 태그: 태크를 통해 여러 함수들을 효율적으로 관리할 수 있습니다. (**태그 생성 방법: 태그명을 입력 후 [Enter]키 or [,]키를 입력하세요**)

## Step 4. 코드 작성하기 후 함수액션 테스트하기

### 코드 작성하기
> 아래 코드는 API호출시 요청된 인자를 params를 통해 받을 수 있고, params에 name과 place값을 반환하는 예제입니다. 만약 name과 place값이 없다면 'Hello, Noone from Nowhere'를 반환하게 됩니다.

- Nodejs 6, 8

```    
module.exports = function (context, params) {
  let name = "Noone";
  if (params.name) {
      name = params.name;
  }
  let place = "Nowhere";
  if (params.place) {
      place = params.place;
  }
  return {myField: 'Hello, ' + name + ' from ' + place}
};
``` 
 
### 함수액션 테스트하기
작성한 코드를 아래와 같이 입력하고, `저장` 버튼을 누른 후 `테스트` 버튼을 눌러 함수액션이 제대로 실행하는지 확인합니다.  

![Step4_1](../img/QuickStart/Step4_1.png)

## Step 5. 함수액션 편집 및 API엔드포인트 사용하기

`구성 정보` 버튼을 누르면 다음과 같은 화면이 나타납니다.  

![Step5_1](../img/QuickStart/Step5_1.png)

- 기본정보: 패키지를 바꿀 수 있고, 태그, 함수액션에 대한 설명을 수정할 수 있습니다.
- 매개변수: 매개변수를 추가하면 API 엔드포인트로 함수액션을 호출할 때 원하는값을 넘겨줄 수 있습니다.
- 런타임:
  * 타임아웃: 함수액션이 실행되는 제한시간(타임아웃)을 5초에서 300초까지 설정할 수 있습니다.
  * 메모리: 함수액션이 실행되는 환경의 메모리 용량을 설정할 수 있습니다. 메모리는 64MB, 128MB, 256MB, 512MB 단위로 선택할 수 있습니다.
- API 엔드포인트:
  * Public/Private: Public은 누구나 접근 가능한 API 엔드포인트를 설정하고, Private은 API 엔드포인트가 API KEY로 보호합니다.
  * API KEY: Private API 엔드포인트를 사용할 때 필요한 값입니다.
  * API 엔드포인트 사용: 체크 시 API 엔드포인트를 사용할 수 있고 언체크 시 API 엔드포인트를 잠금할 수 있습니다.
  * HTTP 메소드: GET, POST, PUT, DELETE를 선택할 수 있습니다.
  * Content Type: 현재는 JSON만 제공합니다.
  * URL:[https://api.action.cloudz.co.kr/](https://api.action.cloudz.co.kr/)`<함수액션 ID>`/`<함수액션 이름>` 형식으로 API 엔드포인트를 보여줍니다.
  * CURL: 설정한 HTTP 메소드, 매개변수, API KEY를 포함하여 curl명령을 작성해 줍니다.

### curl을 통해 API 엔드포인트 요청하기

> <구성 정보\> 화면에서 작성된 curl 명령어를 복사하여 터미널창에서 실행합니다.

```  
$ curl --request GET -G --data "name=PMS&place=KOREA" -H "apikey: ***" https://api.action.cloudz.co.kr/<함수액션 ID>/myFunction
``` 

> <구성정보\> 에서 매개변수를 설정했기 때문에 'Hello, Noone from Nowhere' 대신 'Hello, PMS from KOREA'가 반환되는 것을 볼 수 있습니다.

``` 
  $ {"myField":"Hello, PMS from KOREA"}
``` 
