- 함수를 호출하는 방법에 의해 결정된다
- 자신이 속한 객체나 자신이 생성한 인스턴스를 가리키는 자기 참조 변수
- 즉, 누가 실행 했냐

1. **전역에서 실행**하면 window 전역 객체 참조
2. **strict mode**에서 실행 undefined
3. **메소드 내에서 this** 를 쓰면 method를 가지고 있는 object가 this이다

```jsx
let obj = {
	data : {
		fun : function () {
				console.log(this);
		},
	},
};

obj.data.fun();

// {fun:f}
```

1. **constructor**
    - object 비슷한 것을 여러개 만들고 싶다면 constructor을 만들어 사용
    - constructor 안에서 쓰면 constructor로 새로 생성되는 object를 의미
2. **eventlistener**
    - eventlistener에서 this 를 쓰면 e.currentTarget 지금 이벤트가 동작하는 곳과 같은 의미
    - this는 결국 누가 실행했냐 이므로 지금 현재 버튼에 클릭이벤트가 되면서 실행이된것이니까 버튼이 잡힘
    - 즉 addEventListener 부착된 html 요소

this 값은 즉 function을 만날때 마다 달라질 수 있기에 

**arrow function을 이용하여 this를 사용**

- 함수 내부의 this값을 새로 바꿔 주지 않음

```html
<button id='btn'>버튼</button>

<script>

	document.getElementById('btn').addEventListener('click', function() {
     let arr = [1, 2, 3];
     arr.forEach(function() {
       console.log(this);
    });
  });
	// window 객체 찍힘

    document.getElementById('btn').addEventListener('click', function() {
      let arr = [1, 2, 3];
      arr.forEach(() => {
        console.log(this);
      });
    });

	// <button id='btn'>버튼</button> 찍힘

</script>
```