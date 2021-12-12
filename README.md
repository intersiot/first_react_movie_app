# first_react_movie_app
노마드코더 리액트 강의

<<필기 노트>>


	• 리액트는 컴포넌트 한개만 렌더링이 가능했는데 업데이트 되면서 다중 렌더링이 가능해졌다.
	• JSX에서 이해해야할 두번째로는 컴포넌트에 정보를 보낼 수 있다는 것.
	• prop을 제대로 전달받고 있는지 확인이 필요하기 때문에 레이팅을 사용한다.
	• component는 단지 jsx를 return하는 function이다.
	
	• state는 보통 동적 데이터와 함께 작업할 때 생성된다.
		○ 변하는 데이터, 변하지 않는 데이터, 생겨나고 사라지고 또는 변경된 데이터, 하나인 데이터, 두 개가 되고 또는 0이 되는 그런 종류의 것들.
		○ 기본적으로 데이터가 저장되는 곳
		
	• modifier 함수를 이용해서 state를 바꾸면 컴포넌트가 재생성되고 코드가 다시 한 번 실행된다. 리턴도 한번 더 실행되지만 새로운 값으로 실행된다. 다시 말해 카운터를 1로 세팅하면 리렌더링이 실행된다.
	• 중요한건 state가 바뀌면 리렌더링이 일어난다는 것!
	• state를 바꾸는 방법은 2가지가 있다.
		a. setCounter(이건 지금 작성하고 있는 코드의 함수명임)를 이용해서 원하는 값을 넣어주는 것. 즉 직접 값을 주는 것.
		b. 이전 값을 이용해서 현재 값을 계산해내는 것. 즉 현재 state를 바탕으로 다음 state를 계산하는 방법.
	• 리액트JS는 크롬에서 디버그시 바뀐 부분만 보여준다. -> 리액트의 강점 중 하나. 즉 바뀐 부분만 리렌더링(재생산) 된다는 것.
	
	• function component를 class component로 변경.
		○ class component는 function이 아니기 때문에 return을 가지고 있지 못함!
		○ render method를 가지고 있는데, 이 method 안에 return이 존재함.
		○ react는 자동적으로 class component의 render method를 실행한다. 자동으로!!
		○ render : 사용자에게 보여준다는 의미!
		○ 컴포넌트의 첫 글자는 반드시 대문자여야 한다!!
		
	왜 class component를 가져오는 걸까?
	: class component가 state라고 불리는 녀석을 가지고 있기 때문! ※ state = object
	state는 object이고 component의 data를 넣을 공간이 있고, 이 데이터는 변함.
	state에 바꾸고 싶은 data를 넣는 거임.
	
	• 리액트는 onClick을 자동으로 지원해줌. 이때 예를 들어서 add()라는 function이 있다고 치면 onClick="this.add"는 클릭했을 때만 function이 실행되도록 하는 것이고, onClick="this.add()"는 즉시 실행되도록 하는 것이다.
	
	• life cycle method는 기본적으로 react가 component를 생성하고 없애는 방법이다.
	※ component life cycle에서 주로 사용되는 function은?
		○ Mounting : 태어나는 것과 같음
			§ 먼저 호출되는 function이 있다 : 
				□ constructor( ) : Javascript에서 class를 만들 때 호출
		○ Updating : 일반적인 업데이트를 의미
		○ Unmounting : component가 죽는 걸 의미함.
			§ 컴포넌트가 어떻게 죽지? : 페이지가 이동할 때, state를 사용해서 컴포넌트를 교체하기도 함. 컴포넌트의 죽음에는 다양한 방법이 있다.
	• Props
		○ 일종의 방식. 부모 컴포넌트로부터 자식 컴포넌트에 데이터를 보낼 수 있게 해주는 방법이다.
		○ PropType : 어떤 타입의 prop을 받고 있는지 체크해준다.
		○ 주의해야 할 점은, prop을 전달할 때의 이름과 받아서 사용할 때의 이름이 동일해야 한다는 점이다.
	• export default … : 다른 곳에서 import 할 수 있게 한다.
	• 중요!! 
		○ state가 변화할 때 모든 component는 다시 실행되고, 모든 code들도 다시 실행된다. 즉 state를 변경할 때 모든 code들이 "항상" 다시 실행된다.
		○ 하지만 가끔은 component 내부의 몇몇 코드는 처음 딱! 한 번만 실행되고 다시는 실행되지 않게 하고 싶을 때가 있다. 이때 리액트에서 제공해주는게 useEffect다.
		○ useEffect(() => { … }, [ … ]); 
			§ [ … ] 이 부분이 제한을 주는 부분이다. 예를 들어서 keyword, counter가 됐을 때만 실행되도록 하고 싶다면 아래의 코드처럼 하면 된다.
			 useEffect(() => {
			    console.log("I run when 'keyword' changes.");
			  }, [keyword]);
			 useEffect(() => {
			   console.log("I run when 'counter' changes.");
			 }, [counter]);
			 useEffect(() => {
			   console.log("I run when keyword & counter change");
			 }, [keyword, counter]);
		○ 코드를 언제 실행할지 선택하는 것이 useEffect 다.
	• 알아두면 좋을 Cleanup
