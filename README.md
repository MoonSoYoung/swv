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
#mkdir /usr/local/SWV
#mkdir /usr/local/SWV/dev
#mkdir /usr/local/SWV/tools
#mkdir /usr/local/SWV/server
#mkdir /usr/local/SWV/src
#mkdir /usr/local/SWV/toolchain
```

## 2. Apache HTTP Server installation
* Utility program installation by using yum
``` bash
#yum -y install gcc make gcc-c++ pcre-devel httpd-devel apr-devel apr-util-devel
#yum -y install expat-devel
```

* Utility program download and installation by wget
``` bash
# cd /usr/local/SWV/server
# wget http://archive.apache.org/dist/httpd/httpd-2.4.29.tar.gz
# wget http://mirror.apache-kr.org/apr/apr-1.6.5.tar.gz
# wget http://mirror.apache-kr.org/apr/apr-util-1.6.1.tar.gz
# wget http://downloads.sourceforge.net/project/pcre/pcre/8.41/pcre-8.41.tar.gz
# tar -xvzf httpd-2.4.29.tar.gz
# tar -xzvf apr-1.6.5.tar.gz
# tar -xzvf apr-util-1.6.1.tar.gz
# tar -xzvf pcre-8.41.tar.gz
# mv apr-1.6.5 ./httpd-2.4.29/srclib/apr
# mv apr-util-1.6.1 ./httpd-2.4.29/srclib/apr-util
# cd pcre-8.41
# ./configure
# make
# make install

```

* httpd 설치
```bash
# cd /usr/local/SWV/server/httpd-2.4.29
# ./configure --prefix=/usr/local/SWV/server/httpd
# make
# make install
# mv /usr/local/SWV/server/httpd/htdocs /usr/local/SWV/
```

* 웹서버 환경설정 파일 열기
```'bash
# ln /usr/local/SWV/server/httpd/bin/httpd /bin/httpd
# vim /usr/local/SWV/server/httpd/conf/httpd.conf
```

