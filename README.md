Unity New input System
======================
>## 프로젝트 설정
    1. Package Manager 에서 NewInputSystem 설치
    2. Project Setting - Player - OtherSetting - Configuration - Active input Handling 을 Both 또는 Input System Package(New)로 변경

>## InputActions 생성
    1. Project 폴더에서 우클릭 - Create - InputActions 생성
    2. 생성된 InputAction 더블클릭 후 Input Binding
![binding](./img/binding.png)
>## C#파일 생성
    1. InputAction 파일 클릭 Generate C# Class 체크 및 Apply

>## 사용 설정
```C#
NewInputSetting input;
private void OnEnable()
{
    input.Enable();
}

private void OnDisable()
{
    input.Disable();
}
private void Awake()
{
    input = new NewInputSetting();
}
```
>## 이벤트 할당
```C#
//ActionMap Keyboard 의 Action Move에 이벤트 할당
input.KeyBoard.Move.performed += OnMove;
public void OnMove(InputAction.CallbackContext context)
{
    Vecotor3 inputDirKey = context.ReadValue<Vector3>();
}
위와 같이 작성시 WASD키를 입력시마다 해당방향에 맞는 Vector3값을 input으로부터 ReadValue를 통해 읽어들인다.

input.KeyBoard.Jump.started += (context) =>
{
    Input_Jump?.Invoke();
};
람다식으로 할당도 가능하다.
```
