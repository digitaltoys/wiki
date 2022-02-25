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
