# Imperative UI (명령형 UI)   
- 전통적인 방식
- view를 '어떻게' 구성하는지를 명시
- 원하는 모양의 UI를 그리려면, 그리고자 하는 도형의 정보를 정확히 알아야 함
  
# Declarative UI (선언형 UI)
- view가 '무엇을' 구성하는지를 명시
- F(State) = View : 위젯 또는 함수에 인자로 State를 넘겨주면 View로 보여준다는 진리
- Flutter의 방식
***

# State
보여주고자 하는 데이터 혹은 모습
## AppDate
- 앱 전반에서 사용되는 데이터
- 변경점이 생기면 다른 페이지들에서도 변경된 내용을 보여줘야 함
## WidgetData
- 위젯에서 사용되는 데이터
- 위젯에서만 사용되기 때문에 여기에 나오는 데이터들을 다른 페이지들에서 필수적으로 변경하지 않아도 됨
***

# Stateless
- 상태가 없다는 것은 표현할 모습이나 데이터가 없는 것
- 첫 모습이 보여주고자 하는 전부이고, 보여줄 다른 무언가가 없다는 것
- 정적이고, 처음 보여준 그대로 멈춰있음
- **새로고침이 없는** 위젯

# Stateful
- 상태가 있기에 변화할 것이 있음
- 동적이고, 처음 보여준 모습에서 많은 부분이 바뀔 수 있음
- **새로고침이 있는** 위젯
- 대부분의 유저 상호작용이 있는 앱들
- **setState()** : 위젯을 다시 그려줌
- **setState((){})의 매개변수** : 위젯을 다시 그려주기 전에 수행할 명령어 집합
***

# Provider
- 리소스의 단순화된 할당과 해제
- 지연 로딩 (lazy-loading)
- 클래스를 새로 만들 때마다 매번 작성해야 했던 부분을 크게 줄임
- devtool 친화적 : Provider를 사용하면 Application State가 Flutter devtool에 표시됨
- InheritedWidget들을 소비하는 일반적인 방법을 제시
- 복잡성이 기하급수적으로 증가하는 수신 매커니즘을 가진 클래스에 대한 확장성 향상
## 값 노출하기
### 새 객체 인스턴스 노출하기
- 단순히 값을 노출시켜줄 뿐만 아니라 값의 생성, 수신, 해제를 할 수 있도록 함
- **create** 안에서 신규 오브젝트를 생성
- 객체 생성 위해 Provider.value 사용 X
- 시간에 따라 변경될 수 있는 변수로 객체 생성 X
### 기존 객체 인스턴스 재사용하기
- 이미 존재하는 ChangeNotifier의 공급 위해 **ChangeNotifierProvider.value** 사용
- 기본 생성자 사용 X

## 값 읽기
- BuildContext의 확장 메소드 활용
- **context.watch<T>()** : 위젯이 T의 변화를 감지할 수 있도록 함
- **context.read<T>()** : T를 변화 감지 없이 return
- **context.select<T, R>(R cb(T value))** : T의 일부 작은 영역에 대해서만 위젯이 변화를 감지할 수 있도록 함

## provider의 선택적 의존
- context.watch<Model>() : 매칭되는 provider를 찾지 못한 경우 **ProviderNotFoundException 예외** 발생
- context.watch<Model?>() : 매칭되는 provider를 찾지 못한 경우 예외 발생 대신 **null 반환**
***

# Riverpod
### 선언적 프로그래밍 (Declarative programming)
- Stateless 위젯과 유사한 방식으로 비즈니스 로직 작성
- 필요할 때 자동으로 다시 계산하고 로직을 쉽게 재사용/구성/유지관리
### 일반적인 UI 패턴 쉽게 구현
- "pull to refresh" / "search as we type" 등과 같은 일반적이지만 복잡한 UI 패턴
### 툴링 준비
- 일반적인 실수를 컴파일 오류로 만들어 컴파일러 향상
- 맞춤 린트 규칙 및 리팩터링 옵션 제공
- 문서 생성을 위한 명령줄
***

# GetX
- **성능** : 성능과 최소한의 리소스 소비에 중점을 둠. Streams나 ChangeNotifier 사용X
- **생산성** : 쉽고 친숙한 구문을 사용하여 개발 시간을 아끼고 애플리케이션을 최대 성능으로 제공
- **조직화** : 화면, 프레젠테이션 로직, 비즈니스 로직, 종속성 주입 및 네비게이션을 완전히 분리
## 상태 관리
### 반응형 상태 관리자
- StreamControllers 만들 필요 X
- 각 변수에 대해 StreamBuilder 만들 필요 X
- 각각의 상태(State)를 위한 클래스 만들 필요 X
- 초기값을 위한 get 필요 X
- 코드 생성기 사용할 필요 X
## 라우트 관리
- **GetMaterialApp()**
- **Get.to(NextScreen());** : 새로운 화면으로 이동
- **Get.toNamed('/details');** : 명칭으로 새로운 화면 이동
- **Get.off(NextScreen());** : 다음 화면으로 이동하고 이전 화면으로 돌아갈 필요가 없는 경우
- **Get.offAll(NextScreen());** : 다음 화면으로 이동하고 이전 화면들 모두 닫는 경우
