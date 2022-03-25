### npmbox 설치
온라인 PC에 npmbox 설치
인터넷 연결 PC에서 수행

npm install npmbox -g
 

[참고] npm 에러 발생 시

npm ERR! code SELF_SIGNED_CERT_IN_CHAIN
npm ERR! errno SELF_SIGNED_CERT_IN_CHAIN
request to https://xxxx, reason: self signed certificate in certificate chain
만약 위와 같은 에러메시지가 출력될 경우 아래와 같이 npm의 ssl 설정을 변경해준다.

npm set strict-ssl false
※ 물론 이 설정은 보안 상 취약점이 될 수 있으므로 검토 후 적용하시기 바랍니다.

 

### 오프라인 PC에 npmbox 설치
온라인 PC에서 npmbox 패키지를 다운받아 박스로 생성한다

npmbox npmbox
아래와 같은 메시지가 출력되었다면 정상적으로 박스가 생성된 것이다.

Packing D:\temp\tui\npmbox.npmbox...
생성된 npmbox.npmbox 파일을 오프라인PC로 복사한다.

 

옮겨진 파일을 tar로 아카이빙을 해제한다.

(Unix or Mac)

tar --no-same-owner --no-same-permissions -xvzf npmbox.npmbox
※ Windows 환경일 경우 tar를 해제할 수 있는 다른 프로그램(7-zip, winzip 등)을 사용한다

 

압축을 해제하면 .npmbox.cache 폴더가 생성될 것이다.

 

이제 아래와 같이 명령어를 입력하여 npm으로 npmbox를 설치한다.

(Unix or Mac)

npm install --global --cache ./.npmbox.cache --optional --cache-min 99999999999 --shrinkwrap false npmbox
(Windows)

npm install --global --cache .\.npmbox.cache --optional --cache-min 99999999999 --shrinkwrap false npmbox
 

### 원하는 패키지 설치
온라인 PC에서 원하는 패키지를 다운받아 박스로 생성한다

npmbox somepackage
 

생성된 somepackage.npmbox를 오프라인 PC의 프로젝트 루트 path로 이동

 

오프라인 PC에서 해당 BOX를 UNBOX한다

npmunbox somepackage
(옵션 추가 시)

npmunbox [options] <npmbox-file>
npmunbox --path [폴더위치] somepackage  #npmbox 파일의 폴더 위치를 특정 시
npmunbox --global somepackage          #글로벌 설치 시
npmunbox --save                        #package.json 에 추가할 경우
 

(참고) 혹시 npmunbox 명령어가 인터넷 환경에 접속하려고 시도한다면 npm cache를 정리하는 것이 도움이 될 수도 있습니다.

npm cache clean
 

주의사항
npmbox가 완벽한 것은 아닙니다.

설치하려는 패키지가 Git 리파지토리를 호출하는 등 외부 스크립트를 실행하는 패키지인 경우, 이 영역은 npmbox가 통제할 수 있는 영역이 아니기 때문에 npmbox로도 오프라인 환경에서 설치가 불가능합니다.

이 경우 npmunbox를 실행해도 인터넷 환경에 접속하려고 시도하다가 실패로 끝날 것입니다.

이런 문제가 아니어도 npmunbox가 실패할 가능성은 개발자의 표현을 빌리면 TONS of edge cases 가 있다고 하니 사용 시 참고하시기 바랍니다.

 

참고로 저도 이런 이슈로 인해 몇몇 패키지를 설치하지 못했습니다.

인터넷 안되는 환경에서 일하는 건 정말 너무 힘드네요... ㅠㅠ

 

참고문서 : https://www.npmjs.com/package/npmbox
