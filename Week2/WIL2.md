# Flutter 기초 위젯
---
# Text 위젯   
**Text** : 문자를 보여주는 위젯. 원하는 문자열을 화면에 그려준다.   
> **Text("원하는 문자열")**
---
## TextStyle  
style 프로퍼티에 TextStyle 에 필요한 프로퍼티들을 채운뒤 넣어주면 된다.   
> **Text(   
    "안녕하세요.",   
    style: TextStyle(/*프로퍼티*/),   
  ),**   
### fontSize
- 폰트 크기 조절
- double 을 받음
- 기본 설정 14
### fontWeight
- 폰트 굵기 조절
- FontWeight 인스턴스 받음
- w100 ~ w900 ( w400 : normal, w700 : bold )
> fontWeight: FontWeight.w800
### color
- 폰트 색상 지정
- Color 인스턴스 받음
> color: Colors.blue
### backgroundColor
- 폰트 배경색 지정
- Color 인스턴스 받음
> backgroundColor: Colors.black
### fontFamily
- Flutter에서 기본 제공하는 폰트 외의 폰트를 pubspec.yaml에 지정했을 때, 적용 도와줌
- String 받음
- 해당되는 fontFamily 가 없다면 기본 폰트 Roboto 적용
> fontFamily: "내가 추가한 폰트 이름"
---
## TextAlign + TextDirection
### TextAlign enum
- center : 가운데 정렬
- start : 시작 지점부터 정렬
- end : 끝 지점부터 정렬
- justify : 양쪽 맞춰 정렬 (문자의 길이가 충분히 길지 않다면 동작하지 않음)
- left : 왼쪽 맞춰 정렬
- right : 오른쪽 맞춰 정렬
### TextDirection enum   
TextAlign enum인 start와 end는 나라권마다, 설정마다 달라질 수 있음 (textDirection 속성 따라감)
- ltr : 왼쪽부터 오른쪽 방향
- rtl : 오른쪽부터 왼쪽 방향
