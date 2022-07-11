### Teamming (Bonding) - 랜카드 2개로 대역폭 늘리기
```powershell
Get-NetAdater
new-netswitchteam -Name "Wi-Fi Team" -TeamMembers "이더넷", "Wi-Fi 3"
```

### 멀티부팅 설치 USB 툴
ventoy  
https://www.ventoy.net/en/download.html  
https://kimsungjin.tistory.com/398  

### 윈도우에서 iOS 사파리 디버깅(Web Inspect) 하기
무료 오픈소스를 이용한 방법인데 버그가 있어 찾아보니 무료 버전은 개발 중단되고 유료 버전을 만들고 있더라.

안정적으로 개발하실 분들은 유료버전을 사용하시길.

https://inspect.dev/

사파리 기기에서 설정 변경 (설정 -> Safari -> 고급 -> 웹 속성 활성화)
윈도우 PC에 itunes 설치 https://apple.co/ms
itunes 실행
사파리 기기 USB 연결 및 동기화
node.js 설치 https://nodejs.org/ko/
powershell 관리자 권한으로 실행
scoop 설치
```
Set-ExecutionPolicy RemoteSigned -scope CurrentUser // 권한 오류가 날 수 있으니 미리 실행
iex (new-object net.webclient).downloadstring('https://get.scoop.sh')
scoop install git
scoop bucket add extras
```
ios-webkit-debug-proxy 설치

```
scoop install ios-webkit-debug-proxy
```
remotedebug-ios-webkit-adapter 설치

```
remotedebug-ios-webkit-adapter
```
remotedebug_ios_webkit_adapter 실행 (방화벽 허용, 디버깅 하는 동안 창 닫지 않기)

```
remotedebug_ios_webkit_adapter --port=9000
```
크롬에서 chrome://inspect/#devices 로 접속  
network target에 http://localhost:9000/ 추가   
사파리 열고 inspect   
