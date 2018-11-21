# Software Visualizaton

### 구성
#### 설치시 용량: 약 10G

```
- CentOS7
- php
- apache
- tomcat
- redmine
- jenkins
- Subversion
- MySQL
- ruby
- rubygems
- Graphviz
- SourceNavigator.....
```
### 디렉토리 구조
**SWV**
- dev
  - ruby
  - rubygems
- htdocs
  - redmine(web file)
- server
  - apache
  - tomcat
  - mysql
  - svn
- webapps
  - jenkins
- toolchain
  - SNavi
  - graphviz
- tools
  - redmine(config file)

**설치는 root 계정으로 진행 하였음**

## 1. 비즈니스 네트워크 아카이브 (BNA) 생성

[하이퍼레저 컴포저 개발 툴](https://github.com/IBM/BlockchainNetwork-CompositeJourney/blob/master/README-ko.md#1-%ED%95%98%EC%9D%B4%ED%8D%BC%EB%A0%88%EC%A0%80-%EC%BB%B4%ED%8F%AC%EC%A0%80-%EA%B0%9C%EB%B0%9C-%ED%88%B4-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0)을 설치합니다.

저장소를 복제하십시오:
```
git clone https://github.com/IBM/BlockchainEvents-CompositeJourney.git
```

파일 구조가 유효한지 확인하려면 비즈니스 네트워크 정의에 대한 BNA (Business Network Archive) 파일을 생성합니다. BNA 파일은 배포 가능한 유닛으로 실행을 위해 컴포저 런타임에 배포할 수 있습니다.

다음 명령을 사용하여 네트워크 아카이브를 생성합니다:
```bash
cd Composer
npm install
```
아래와 같은 결과가 나옵니다:
```bash
> mkdirp ./dist && composer archive create --sourceType dir --sourceName . -a ./dist/events.bna

Creating Business Network Archive


Looking for package.json of Business Network Definition
	Input directory: /Users/ishan/Documents/demo/BlockchainEvents-CompositeJourney/Composer

Found:
	Description: Sample product auction network with events
	Name: events
	Identifier: events@0.0.1

Written Business Network Definition Archive file to
	Output file: ./dist/events.bna

Command succeeded
```

`composer archive create` 명령을 사용하여 `dist` 폴더에 `events.bna`라는 파일을 생성했습니다.

Node.js 프로세스에서 '블록체인' 인메모리 상태를 저장하는 임베디드 런타임에 대해 비즈니스 네트워크 정의를 테스트할 수 있습니다.
프로젝트 작업 디렉토리에서 test/productAuction.js 파일을 열고 다음의 명령을 실행하십시오:
```
npm test
```
아래와 같은 결과가 보입니다 :
```
> events@0.0.1 test /Users/ishan/Documents/demo/BlockchainEvents-CompositeJourney/Composer
> mocha --recursive

  ProductAuction - AddProduct Test
    #BiddingProcess
      ? Add the product to seller list (154ms)
      ? Authorized owner should start the bidding (117ms)
      ? Members bid for the product (181ms)
      ? Close bid for the product (96ms)


  4 passing (2s)
```

---------------------------------------
# 설치 시 주의사항
* root 권한으로 모든 설치를 수행한다.
* wget을 이용해 소프트웨어를 다운로드 하는 경우 링크가 바뀌거나 사라질 수 있으므로, 
  wget 다운로드가 실패하면 아래의 소프트웨어 리스트의 site address를 참조하여 
  다운로드 링크를 바꿔야 함. 
* OS: CentOS v7
## 1. SWV 환경 구축을 위한 기본 디렉토리 생성
총 6개의 디렉토리를 생성한다 :
```bash
mkdir /usr/local/SWV
mkdir /usr/local/SWV/dev
mkdir /usr/local/SWV/tools
mkdir /usr/local/SWV/server
mkdir /usr/local/SWV/src
mkdir /usr/local/SWV/toolchain
```

## 2. Apache HTTP Server installation
Utility program installation by using yum
yum -y install gcc make gcc-c++ pcre-devel httpd-devel apr-devel apr-util-devel
yum -y install expat-devel
