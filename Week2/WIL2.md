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
---
# Container 위젯
**Container** : UI요소를 감싸고, 다양한 형태를 취할 수 있는 위젯. SizedBox와의 결정적 차이점은 Container 위젯은 그 자체를 꾸밀 수 있다는 것.
> Container()
---
## Container 프로퍼티
### width, height
- 너비와 높이 값 조절
> Container( width: 200, height: 100, color: Colors.blue, ),
### color
- Color 클래스의 인스터스 받음
- Colors를 통해 미리 정의된 색상을 키워드를 통해 불러옴
### child
- Container는 하나의 자식 위젯을 child 프로퍼티를 통해 Container 내부에 넣을 수 있음
- 위젯이기만 하면 뭐든지
- 크기가 정해진 Container 보다 더 크게 설정되면 오버플로우
> Container(   
  width: 100, height: 100,   
  padding: EdgeInsets.all(10),   
  decoration: BoxDecoration(color: Colors.red, ),   
  child: Text("고라니"),   
)
### padding
- Container의 child와의 여백을 설정
- Container 내부의 여백
- EdgeInsetsGeometry 추상 클래스를 구현한 클래스들을 받음
### alignment
- Container 내부의 위젯을 어디에 정렬시킬지 정함
- AlignmentGeometry 추상 클래스를 구현한 클래스 받음
- topLeft, topCenter, topRight, centerLeft, center, centerRight, bottomLeft, bottomCenter, bottomRight
### decoration ( BoxDecoration )
- SizedBox 와의 차이
- BoxDecoration 클래스 받음
#### BoxDecoration 클래스의 프로퍼티
#### color
- Container의 color보다 우선도가 높지만 둘다 갖게 되면 에러
#### borderRadius
- 모서리 곡률
- BorderRadius 클래스 받음. (메소드: all, circular, zero, horizontal)
> decoration: BoxDecoration(   
    borderRadius: BorderRadius.all(   
      Radius.circular(8), ),   
  ),
#### shape
- 컨테이너의 모양 결정
- BoxShape enum 받음
- circle, rectangle(기본)
- circle 지정할 경우, borderRadius 값 비워놔야 함.
> decoration: BoxDecoration(   
    shape: BoxShape.circle, ),
---
## Container 크기
1. Container에 자식 위젯이 없을 때, width와 height도 없다면?
Container는 부모 위젯의 크기에 맞춰 화면을 최대한 채우려 한다.

2. Container에 자식 위젯이 있을 때, width와 height가 없다면?
Container는 자식 위젯에 최대한 맞게 크기를 잡는다.

3. width와 height가 설정된다면?
설정된 크기대로 따라간다. (둘 중 하나만 설정된다면, 위의 두 규칙을 따름)
---
# Row, Column 위젯
여러 개의 위젯 배치를 도와주는 Multichild-Layout 위젯   

**Row** : 가로축 방향으로 위젯 진열

**Column** : 세로축 방향으로 위젯 진열   

---
## Row, Column 위젯의 프로퍼티
### children
- List<Widget> 을 받음
- required, 필수 프로퍼티로 넣어줘야 함
- 내부에 들어간 위젯의 크기가 커지면 오버플로우
### MainAxisAlignment 와 CrossAxisAlignment
Row 위젯 : MainAxisAlignment - 가로축 정렬 / CrossAxisAlignment - 세로축 정렬   
Column 위젯 : MainAxisAlignment - 세로축 정렬 / CrossAxisAlignment - 가로축 정렬   

MainAxisAlignment enum : start(기본), center, end, spaceAround, spaceBetween, spaceEvenly   
CrossAxisAlignment enum : start, center(기본), end, stretch, baseline
