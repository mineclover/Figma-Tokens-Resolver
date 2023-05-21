플러그인 연동과 git action으로 tokens/tokens.json 와 tokens/themes.txt를 받는다

index.js을 실행한다

## 권장 설정

피그마 토큰에서 rem 단위를 사용할 수 있다

```css
* {
  box-sizing: border-box;
  position: relative;
}
```

## 장점

그 값을 연산할 때 무슨 과정이 있었던지 간에 그 결과값은 계산돼서 css 가 생성된다그리고 이름을 공유할 수 있기 때문에 스타
일 스왑이 가능해진다

## 규칙

속성 이름과 같은 이름을 쓰면 안된다

- Color , BorderWidth 등

최상위 토큰 명(첫 그룹 객체)명에서 숫자로 시작하는 이름은 쓰면 안된다

- 설정창에서 이름이 숫자로 시작하면 안된다

값에 ; 쓰면 안된다

이 조건이 충족할 때 build/out 에 생기는 CSS, JS 의 값-value는 완전히 같아야한다 ( JS의 경우 순서 보장 안됨 )

## 구조

기본적으로는 필요한 css 값으로만 매칭해준다

### 토큰을 사용하기 좋은 형태로 재생성

tokens.json themes.txt

### css 값으로 생성하는 기능

붙여넣은 inspect 값으로 css를 생성해준다 pairing.js 에서 매핑 값을 관리함 ( 수동임 )

### 토큰 값을 볼 수 있는 시트 폼 만드는 기능

작업을 단순화하기 위해 auto layout 없이도 전체 형태를 볼 수 있도록 구조를 만들려고 하였음  
넓이 높이가 자동으로 설정되는데, 넓이의 경우 컨텐츠 텍스트를 기준으로 생성되어한글이 들어가면 잘릴 수 있음

피그마에 붙여 넣을 수 있는 svg 생성 ( 플러그인에서 자체지원하지 않는 한 이정도가 한계 )

### 추가 옵션

description에 추가 설명을 넣어서 옵션 선택을 처리하도록 했다

color 와 boxShadow는 대상에 따라 들어가는 키가 다르다

- border의 경우 피그마 플러그인에서 잡아준다
- color , background

box shadow 는 그림자의 속성 값에도 차이가 있다 text-shadow , box-shadow

asset은 키가 매우 다양하다  
asset의 경우 url을 담고 있을 뿐이고 사용할 수 있는 요소가 다양하다...

그런데 그냥 default 를 설정해뒀다 'background', 'listStyle', 'content', 'cursor', 'borderImage', 'src', 'offsetPath',
'maskImage'

### index

기존의 피크마 토큰이 가지고 있는 Token to css,js 를 실행하는 영역

### listUp

css 랑js 를 포멧 상관 없이 읽을 수 있는 형태로 가공해 주는 목적 원본 js 는 esm 방식이어가지고읽는 것에 제한이 있음그걸포
함해주기 위한 작업, 그 외로 유효성 검사를 위해 두 개 다 읽어온다

### toStyled

인풋을 가지고 특정한 규칙을 통해서 css텍스트로 변환 하는 코드

# WEB 버전이 안됬던 이유

시작할 때 토큰을 전부 받아서 지금 하던 방식처럼... 아 근데 지금 그게 없다  
지금 스타일 딕셔너리에 종속성이 있어서 변경이 안된다  
하려면 토큰 js 를 직접 수정해야 되고  
토큰 json 안에 있는 외부 변수 가져오는 것에 대해서 어떻게 실행할지 동작 예측이 안 된다

## 05/19 기준

borderColor left , right 는 없다 borderStyle 과 하위 속성도 없음 border로 해결하는 것을 권장함작업 필요 : typography 에
대한 대응은 작업되지 않았음

## 05/21 기준

피그마 호환 되는 형태로 수정 완료
