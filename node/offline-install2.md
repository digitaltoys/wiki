1.npm 패키지 다운로드 url만 망을 풀어준다

2.yarn offline install을 이용한다

​

두 가지 방법을 모두 적용해 보았다.

결과적으로 우리는 1.npm 패키지 다운로드 url만 망을 풀어준다 를 이용해 편하게 개발을 할 수 있게 되었으나!

1번은 유관부서 협업이 필요한 거였구,

그 협력요청 전에 2번도 성공은 했다. 다만 귀찮고. 모듈 하나 더 추가하려고 하면 대환장 파티가 일어난다.

필요한 모듈이 이미 전부 확립된 상태라면 2번도 나쁘지 않다.

​

​

1.npm 패키지 다운로드 url만 망을 풀어준다

1번 방법을 이용할 때 풀어주어야 하는 url은 다음과 같다

// npm url
https://registry.npmjs.org/

// yarn url
https://registry.yarnpkg.com/
각각 packages-lock.json과 yarn.lock에서 가져온 것.

솔직히 저 두 개를 추가하고 npm install만 해봐서 각각이 npm주소, yarn 주소일 거란 건 아직

추측일 뿐이긴 하지만. url을 하나하나 검증하기엔 귀찮고 할일도 많고 .. ㅎ

​

​

2.yarn offline install을 이용한다

온라인 환경(폐쇄망 외부)에서 vue 프로젝트를 만들고, 모듈도 설치하는데

yarn을 이용해 모듈을 .tgz 형식으로 다운받아올 수 있다.

그걸 통째로 오프라인 환경으로 가져와서 yarn offline install을 하는 건데 자세히 적어보면.

​

<온라인 환경>

1.node 설치, npm으로 @vue/cli 설치, yarn 설치한 후 vue 프로젝트 생성

​

2.npm으로든 yarn으로든 원하는 패키지 설치(vuetify라든지, axios 라든지)

​

3.vue 프로젝트에서 아래 명령어 실행

yarn config set yarn-offline-mirror ./npm-packages-offline-cache
yarn config set yarn-offline-mirror-pruning true
하면 vue 프로젝트 바깥 디렉토리에 .yarnrc가 생긴다.

​

4.뷰 프로젝트 내부의 node_modules 폴더와 yarn.lock을 지운다

​

5.아래 명령어 실행

yarn cache clean
yarn install
하면 node_modules 폴더, yarn.lock 파일, 그리고 npm-packages-offline-cache 폴더가 생긴다.

npm-packages-offline-cache 안에 .tgz 파일들 쭈루룩 있는것 확인한다

​

6.node_modules는 다시 지우고, .yarnrc를 뷰프로젝트 내부로 넣어준 뒤

압축해서 폐쇄망 안 내 컴퓨터로 넣었다.

​

<폐쇄망/오프라인 환경>

1.node를 설치한다. 다행히 msi 설치파일을 쉽게 구할 수 있다

​

2.npm을 통해 yarn을 설치할 수 없으니, yarn js파일을 다운받는다. node를 통해 실행할 수 있다.

​

3.vue 프로젝트 압축을 풀고, 프로젝트 안에 yarn-1.22.10.js를 놓는다.

현재 vue프로젝트의 루트폴더에는 yarn-1.22.10.js, .yarnrc, npm-packages-offline-cache등이 있어야 한다.

​

4. .yarnrc를 열고 yarn-offline-mirror의 경로를 상대경로로 바꿔준다

...
yarn-offline-mirror "./npm-packages-offline-cache"
...
5.뷰프로젝트 루트경로에서 아래 명령어 실행

node ./yarn-1.22.10.js install
node_modules 경로가 생기고 라이브러리들이 죽죽 설치된다

​

6.뷰 프로젝트가 실행되는지 확인

npm run serve
이렇게 해서 밖에서 구성한 개발환경을 안으로 가지고 올 수는 있지만,

라이브러리 하나 추가할 때마다 너무 귀찮다.

귀찮게 하나 추가하려던 중에

1.npm 패키지 다운로드 url만 망을 풀어준다

이게 성공하게 되어서.. 해피해졌땅..ㅎㅎ

​
