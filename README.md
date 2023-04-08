# study

구글 지도 API Key 사용 위치 기반 출근 app
현재 위치와 특정 위치간 거리를 계산해 출근 또는 출근 불가 처리 App

Geolocator 플러그인

지리와 관련된 가능을 쉽게 사용할수있는 플러그인

3가지로 나뉨

1. 위치 서비스를 사용할수있는 권한 확인
2. GPS 위치가 바뀔때마다 현재 위치값을 받을수있음
3. 현재위치와 특정 위치의 거리를 계산

check point

기기의 위치 서비스가 켜져있는지

서비스가 꺼져있으면 권한 요청

기능이 켜졌는지 확인 가능한 함수로는

```dart
final isLocation = await Geolocator.isLocationServiceEnabled();
```

앱에서 위치 서비스가 사용할수있는 상태인지 확인은 checkPermission() 함수 사용

만약 권한이 없다면 requestPermission() 함수를 사용해서 권한 요청

```dart
final check = await Geolocator.checkPermission(); // 권한 확인
final check = await Geolocator.requestPermission(); // 권한 요청
```

requestPermission 요청시 5 가지로 응답받음

enum으로 처리할수 있음

1. denied
2. deniedForever
3. whileInUse
4. always
5. unableToDetermine

현재 위치 지속적 받기

getPositionStream() 함수를 사용하면 현재 위치가 변경될때마다 현재값을 position 클래스 형태로 주기적으로 반환 받을수 있음

```dart
Geolocator.getPositionStream().listen((Postion position) {
	print(position);
})
```

**position 의 주요 속성**

longitude : 경도

latitude : 위도

timestamp : 위치가 확인된 날짜 및 시간

accuracy : 위치 정확도, 특정 기기에서는 확인이 불가능할수도 있다고 함

speed : 이동속도, 측정 기기에서는 확인이 불가능할수도 있다고 함

speedAccuracy : 이동속도 정확도, 특정 기기에서는 확인이 불가능할수도 있다고 함

**두위치 거리값 구하기**

```dart
final distance = Geolocator.distanceBetween(
  sLat, // 시작점 위도
	sLng, // 시작점 경도
	eLat, // 끝지점 위도
	eLng,	// 끝지점 경도
);
```

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
