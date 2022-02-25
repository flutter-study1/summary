## 7챕터에 새로 나온 위젯

1. **ListView** - Column 위젯처럼 위젯들을 세로로 배열 시켜주는 위젯입니다. Column 과 다른점은 ListView 는 스크롤하여 화면 바깥으로 넘친 영역을 볼 수 있도록 해줍니다.
2. **TextFormField** - TextField 와 유사하게 사용자 입력을 받을 수 있는 위젯입니다. TextField 와 다른 점은 validator 속성으로 유효성 검사를 할 수 있다는 것입니다. 
```dart
TextFormField(
  validator: (value) => value!.isEmpty ? "Please enter some text" : null,
  obscureText: text == "Password" ? true : false,
  decoration: InputDecoration(
    hintText: "Enter $text",
    enabledBorder: OutlineInputBorder(borderRadius: BorderRadius.circular(20)),
    focusedBorder: OutlineInputBorder(borderRadius: BorderRadius.circular(20)),
    errorBorder: OutlineInputBorder(borderRadius: BorderRadius.circular(20)),
    focusedErrorBorder: OutlineInputBorder(borderRadius: BorderRadius.circular(20)),
  ),
),
```
3. **Form** - TextFormField 를 여러개 사용하는 경우 묶어서 한번에 관리하게 해주는 위젯입니다.  
4. **GlobalKey**(위젯 아님) - class 내부에 key 변수로 미리 선언하고, Form 위젯 생성시에 key 속성에 연결합니다. 이후에 key 변수를 통해서 Form 위젯의 상태를 관리할 수 있습니다.
```dart
final _formKey = GlobalKey<FormState>();
```
5. **TextButton** - 버튼 위젯
```dart
TextButton(
    onPressed: () {
      // 3. 유효성 검사
      if (_formKey.currentState!.validate()) {
        Navigator.pushNamed(context, "/home");
      }
    },
    child: Text("Login"),
  ),
```
6. **ThemeData** - 앱 내부에서 전체적으로 공통 테마를 적용하기 위한 위젯입니다. MaterialApp 위젯을 선언할때 속성으로 추가합니다.
```dart
ThemeData(
    textButtonTheme: TextButtonThemeData(
      style: TextButton.styleFrom(
        backgroundColor: Colors.black,
        primary: Colors.white,
        shape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(30),
        ),
        minimumSize: Size(400, 60),
      ),
    ),
  )
```

## SVG 
SVG 란 점과 선으로 이루어진 vector 이미지입니다. 확대해도 깨지지 않고, 용량이 작다는 장점이 있습니다. 아이콘, 로고등 음영 효과가 안들어간 간단한 이미지를 다룰때 좋습니다. 
```yaml
flutter_svg: ^0.21.0-nullsafety.0
```
svg 를 사용하기 위해 위와같이 라이브러리를 추가합니다. 아래는 사용예시입니다.
```dart
SvgPicture.asset(
    "assets/logo.svg",
    height: 70,
    width: 70,
  )
```
