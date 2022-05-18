### npm & yarn

npm	|yarn	|의미  
-----|-----|------
npm init	|yarn init	|초기화  
npm install	|yarn 또는 yarn install	|package.json의 패키지 설치  
npm install —save [package name]	|yarn add [package name]	|의존성으로 추가  
npm install —save-dev [package name]	|yarn add —dev [package name]	|개발 의존성으로 추가  
npm install —global [package name]	|yarn global add [package name]	|전역으로 추가  
npm update —save	|yarn upgrade	|패키지 업데이트  
npm run [스크립트명]	|yarn [스크립트명]	|package.json의 스크립트 명령 실행  
npm uninstall —save [package name]	|yarn remove [package name]	|패키지 삭제  
npm cache clean	|yarn cache clean	|캐시 삭제  

#### 단축 플래그
명령어	|단축 플래그	|의미  
------|-----------|-----
global	|-g	|전역 설치  
install	|i	|설치  
uninstall	|uni	|삭제  
—save-dev	|-D	|devDependencies 에 추가  
—save-exact	|-E	|^, ~대신 정확한 버전으로 설치  
—save-optional	|-O	|optionalDependencies에 추가 (선택정 의존성 모듈)  

#### 기타 명령어
명령어	|의미  
------|----
npm update jquery	|^ : Minor Level 범위에서 가장 최신 버전으로 업데이  
| |~ : Patch Level 범위에서 가장 최신 버전으로 업데이트  
ls	|패키지 목록  
npm i 모듈명@n.n.n	|특정 버전설치  
npm i 모듈명@latest	|최신 버전설치  
npm outdated	|설치된 패키지 버전확인  

#### 버전 관리
;특정 depth 까지만 보기
$ yarn list --depth=0 ( 혹은 보고 싶은 depth 숫자 )

$ yarn remove {PACKAGE_NAME}

@ 은 특정 패키지의 특정 버전을 의미한다. ex : yarn add weppack@4.0.0
~ (tilt) : 최하위버전의 업데이트만 허용
^ (carot) : 최상위 버전의 업데이트까지 자유롭게 허용.

;패키지 업데이트
;yarn.lock 파일은 변경이 되었지만 package.json 파일은 아무 변경이 없다
$ yarn upgrade

; syncyarnlock 설치
$ yarn global add syncyarnlock

; yarn.lock에서 설치된 버전으로 package.json을 업데이트합니다.
$ syncyarnlock -s -k

; package.json의 현재 버전 제약 조건으로 yarn.lock을 업데이트합니다.
$ yarn install

; 최신 안정 버전이 더 이상 현재 범위와 일치하지 않을 때 실행하면 package.json 파일이 업데이트된다. 단점으로는 package.json에 지정된 버전의 범위를 무시하기 때문에 의도치 않게 Major 업데이트가 될 수 있다.
$ yarn upgrade --latest
