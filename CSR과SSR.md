# CSR SSR

**CSR**

- CSR 예시

```html
<div id='root'></div>
<script src=' .js'></script>
```

- 우선 빈페이지를 렌더해준다음 js코드를 다운로드 받게 됨
- 프레임워크나 라이브러리에 대한 소스코드들이 들어있기 때문에 크기가 큼 그리하여 다운로드 받는데 시간이 소요됨
- 추가로 필요한 데이터가 있다면 서버에 요청한 후 이것들을 기반으로 해서 동적으로 HTML을 형성한다음 보여줌
- 사용자가 웹사이트를 봄과 동시에(TTV) 사용자가 클릭이 가능하게 된다(TTI)

`단점`

- 사용자가 화면을 보는데에 시간이 오래걸릴 수 있음
- SEO에 좋지 않다
    - html 파싱하는 봇이 검색엔진에 등록하기 위해서는 html 바디를 읽어내려가야하는데 CSR의 경우 코드가 숨겨져 있기 때문에

**SSR**

- 웹사이트에서 url을 입력하면 미리 서버에서 필요한 파일을 모두 가져와서 html 파일을 만들게 됨 그리고 동적으로 제어할 수 있는 소스코드와 함께 클라이언트에게 보내주게 됨
- CSR을 사용했을때 보다 첫번째 페이지 로딩이 빨라짐
- 모든 컨텐츠가 HTML에 담겨져 있기 때문에 SEO에 좋다
- TTV와 TTI가 동시에 일어나지 않음

`단점`

- 사용자가 클릭을 하게되면 전체적인 웹사이트를  다시 받아오게 되기 때문에 깜빡임이 존재할 수 있다
    - 좋지 않은 user experience
    - 서버에 과부하가 걸리기 쉬움
    - 페이지는 빠르게 로딩되지만 자바스크립트를 아직 다 다운 받지 못해서 클릭을 해도 반응이 없는 경우가 존재할 수 있음

**TTV** : **T**ime **T**o **V**iew

**TTI** : **T**ime **T**o **I**nteraction