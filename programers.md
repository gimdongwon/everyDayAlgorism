# 머쓱 404 Not Found

머쓱이를 이용해서 404 Not Found 페이지를 꾸며주세요! 머쓱 머쓱..


## 머쓱 404 Not Found 템플릿 - Node.js

programmers의 과제 테스트는 VScode Editor를 이용하여 코드를 작성하고 실행할 수 있는 환경을 제공합니다.

아래 내용을 확인하여 프로젝트를 구성하고 과제를 수행한 뒤 코드를 제출해 보세요.

> 참고: 이 템플릿은 웹 어플리케이션 모듈인 [express.js](https://expressjs.com/ko/)가 미리 구성되어 있습니다.


### 터미널

터미널은 View -> Terminal 또는 단축키(ctrl + `)를 통하여 사용할 수 있습니다.


### 빌드 및 실행 명령어

다음과 같은 명령어를 통해서 코드를 빌드하거나 실행해볼 수 있습니다. migrate, seed, runserver 명령어는 build를 실행한 이후 가능합니다.


- /build : `Heroku buildpack`을 이용해 코드를 Build
- /migrate : `Procfile`의 migrate 프로세스 유형 실행
- /seed : `Procfile`의 seed 프로세스 유형 실행
- /runserver : `Procfile`의 web 프로세스 유형 실행
- /start : 위 4 단계 모두를 순차적으로 실행


### Procfile

제출한 코드는 [heroku buildpack](https://devcenter.heroku.com/)을 통해 실행됩니다. 따라서 `Procfile`이라는 파일 안에 앱 프로세스를 실행하는 명령을 지정해주셔야 합니다.

Procfile은 프로세스 유형을 개별 라인에 선언합니다. 각 라인은 다음 형식으로 되어 있어야 합니다.

```
<프로세스 유형>: <명령>
```

사용할 수 있는 프로세스 유형은 다음과 같습니다. (하단에 명시된 유형만 쓸 수 있으며, 다른 프로세스 유형은 지원하지 않습니다.)

##### web

웹 서버 프로세스를 실행하는 명령을 지정하는 유형입니다.

예시: 

`node.js`에서는 다음과 같이 작성

```
web: npm start
```

`yarn`을 쓸 거라면 다음과 같이 작성

```
web: yarn start
```

##### migrate

프로그래머스 플랫폼에서는 코드를 실행할 때마다 매번 새로운 데이터베이스 서버가 실행됩니다. 따라서 데이터베이스에 테이블을 생성하는 명령을 이 유형에 정의해주세요.

예시: 

```
migrate: ./node_modules/.bin/sequelize db:migrate
```

서버 실행 시 자동으로 db가 sync 되어 이 명령이 필요 없다면 다음과 같이 정의해주세요.

```
migrate: /bin/true
```

`sequelize` 외의 다른 SQL 모듈을 이용하고 싶다면 마이그레이션 cli 명령어를 `migrate: ` 에 작성해 주면 됩니다.

#### seed

초기 데이터를 데이터베이스에 입력하기 위한 명령을 지정하는 유형. migrate 이후에 실행됩니다.


예시:

```
seed: ./node_modules/.bin/sequelize db:seed:all
```


### 실행 및 제출 시 주의사항

- Port 번호는 **PORT 환경 변수** 또는 **5000** 을 사용해야 합니다.

- 루트 디렉토리에는 의존성 모듈들이 정의되어 있는 `package.json`가 있어야 합니다.

- 프로젝트는 하나만 있어야 합니다. 루트 디렉토리에 있는 `package.json` 파일만 참조하여 실행합니다.

- programmers에서 과제 실행 및 제출 시에는 `NODE_ENV` 는 **production**으로 지정됩니다.
  - 따라서 `devDependencies` 에 정의되어 있는 의존성 모듈은 설치되지 않습니다. 실행 시 필요한 모듈은 `dependencies` 에 정의해주세요.

- `.gitignore` 에는 아래 항목을 넣어주세요. `node_modules` 디렉토리와 `.env` 파일은 저장소에 포함하지 않아야 합니다.

  ```
  /node_modules
  npm-debug.log
  /*.env
  ```

  * 또한 `typescript`나 `webpack`을 사용하신다면 컴파일의 결과 디렉토리(`/dist` 등)도 저장소에 포함하지 않아야합니다.

- programmers에서 실행된 서버는 최대 10분 뒤에는 자동으로 종료됩니다.

* **[실행] 버튼을 누르기 전에는 꼭 서버를 띄워주세요. 서버는 터미널에서 `/runserver`를 치면 띄울 수 있습니다**
* **[최종 제출]을 누르면 테스트가 종료되며, 이후 다시 제출이 불가능합니다. [실행]을 눌러 충분히 테스트한 후에 코드를 제출해주세요**


### programmers 과제 실행 시스템 및 프레임워크 환경

programmers에서 실행된 과제는 다음 환경에서 동작합니다.

```
OS 버전: ubuntu 18.04
메모리 제한: 2048 MiB
MySQL 버전: 8.0.17
node.js 버전: 10.14.1
npm 버전: 6.4.1
yarn 버전: 1.12.3
```
