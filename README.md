# 하둡과 빅데이터

1. 개요 

   > **하둡이란?**
   >
   > 기존 데이터베이스 관리도구
   >
   > 데이터를 수집, 저장, 관리, 분석할 수 있는 역량을 넘어서는 
   >
   > 대량의 정형 또는 비정형 데이터 집합으로부터 
   >
   > 가치를 추출하고 결과를 분석하는 기술

2. 정의

   > 정보 자산을 효율적으로 이용하기 위한 기술들을 
   >
   > 포괄하여 아우르는 말
   >
   > 비정형 데이터를 분석하여 활용가능한 정보를 추출하는 것

3. 비정형 데이터란?

   > 페이스북의 다양한 정보들



- 빅데이터

  > 3V 모델이다!(Volume, Velocity, Variety)
  >
  > 다양한 종류의 수많은 데이터를 빠르게 처리할 수 있다.

  |         항목          |                             의미                             |
  | :-------------------: | :----------------------------------------------------------: |
  |      Volume(양)       |                       대용량의 데이터                        |
  | Velocity(입출력 속도) |             큰 용량의 데이터를 빨리 처리해야 함              |
  |    Variety(다양성)    |      계량화 및 수치화가 어려운 비정형적 데이터를 포함함      |
  |   Veracity(정확성)    | 분석에서 목적에 맞는 데이터를 선별하고 수집하는 것이 분석 결과의 정확성에 영향을 미침 |
  |      Value(가치)      |        빅데이터를 통해 어떤 문제를 해결할 수 있는가?         |

  - 필요성

    > 다변화된 현대 사회를 더욱 정확하게 예측하여 효율적으로 작동케 하고 개인화된 현대 사회 구성원마다 맞춤형 정보를 제공, 관리, 분석하여 과거에는 불가능했던 기술을 실현

  - 문제점

    > 사생활 침해 및 정보 유출 측면, 개인정보 보호와 활용을 절충한 입법적 장치 필요
    >
    > 해결방안? 개인을 식별할 수 없는 정보를 활용하여 서비스를 제공하는 방법

  ***

  #### 빅데이터 처리 기법

  > 기술구성

  | 항목 |                             의미                             |
  | ---- | :----------------------------------------------------------: |
  | 기획 | 어떤 데이터를 수집 및 분석할 것인지 계획을 수립하고 추진하는 분야 |
  | 처리 | 데이터 수집,처리,시각화를 위해 사용되는 기술//IOT Seonsor,Haddop,D3 |
  | 분석 | 데이터간의 상관관계를 통해 의미있는 결론을 도출하는 기술(텍스트 마이닝, 오피니언 마이닝, 패턴 분석 등... )R, Python, 엑셀 |

  - 처리 기술

    > 대규모의 정형/비정형 데이터를 처리하는 데 있어 가장 기본적인 분석 인프라

    - 하둡, NoSQL, SPARK

  - 분석 기술

    > 기존 기술
    >
    > - 데이터 마이닝, 기계학습, 자연 언어 처리, 패턴 인식 ...
    >
    > **신규 기술**
    >
    > - 텍스트 마이닝 
    >
    >   > 비/반정형 텍스트 데이터에서 자연 언어 처리 기술에 기반하여 유용한 정보를 추출, 가공
    >
    > - 오피니언 마이닝
    >
    >   > 소셜미디어 등의 정형/비정형 텍스트의 긍정, 부정, 중립의 선호도를 판별
    >
    > - 소셜 네트워크 분석
    >
    >   > 소셜 네트워크의 연결 구조 및 강도 등을 바탕으로 사용자의 명성 및 영향력을 측정
    >
    > - 군집 분석
    >
    >   > 비슷한 특성을 가진 개체를 합쳐가면서 최종적으로 유사 특성의 군집을 발굴



### 하둡 서버 셋팅

1. Network Setting

2. hostname, etc/hosts

3. JDK& profile Setting

   - vi /etc/profile
   - JAVA_HOME=/etc/jdk1.8.0
     CLASSPATH=/etc/jdk1.8.0/lib
     PATH=.:$JAVA_HOME/bin:$PATH
   - export JAVA_HOME CLASSPATH

   - . /etc/profile

4. Hadoop download

   - tar xvfz hadoop-1.2.1.tar.gz
   - cd /usr/local
   - cp -r /root/다운로드/hadoop-1.2.1 .

5. Hadoop profile Setting

   - cd /usr/local

   - ls

   - mv /etc/jdk1.8.0/ .

   - mv /etc/eclipse/ .

   - vi /etc/profile

   - ```
     JAVA_HOME=/usr/local/jdk1.8.0
     CLASSPATH=$JAVA_HOME/lib
     HADOOP_HOME=/usr/local/hadoop-1.2.1
     
     
     PATH=.:$JAVA_HOME/bin:$HADOOP_HOME/bin:$PATH
     
     export JAVA_HOME CLASSPATH HADOOP_HOME
     ```

   - cd /usr/bin

   - rm java

   - rm eclipse

   - cd

   - . /etc/profile(변경된 profile 환경 설정을 적용)

6. SSH

   - ssh hadoopserver1

   - ssh-keygen -t dsa -P '' -f ~/.ssh/id_dsa

     > hadoopserver에 대한 Private/Public Key 생성

   - ls -a

     > 만들어진 ssh 파일을 확인한다.

   - cd .ssh

     > ssh 파일로 이동

   - ssh-copy-id -i id_dsa.pub root@hadoopserver1

     > id_dsa 에 대해 컴퓨터 자체 로그인을 할 때 key 값이 자동으로 매칭 되도록 authorized keys 가 만들어지도록 하는 명령문
     >
     > =>이후 ssh hadoopserver1으로 로그인 시 비밀번호를 묻지 않음

7. hadoop-env.sh

8. hadoop-1.2.1/conf/*.xml

   (core-site, hdfs-site,mapred-site)

   > 1. core-site.xml
   >
   >    > ```
   >    > <configuration>
   >    > <property>
   >    > <name>fs.default.name</name>
   >    > #how many file will you copy
   >    > <value>hdfs://hadoopserver1:9000</value>
   >    > </property>
   >    > 
   >    > <property>
   >    > <name>hadoop.tmp.dir</name>
   >    > #where to place name directory
   >    > <value>/usr/local/hadoop-1.2.1/tmp</value>
   >    > </property>
   >    > ```
   >
   > 2. hdfs-site
   >
   >    > ```
   >    > <configuration>
   >    > <property>
   >    > <name>dfs.replication</name>
   >    > #how many files will you copy
   >    > <value>1</value>
   >    > </property>
   >    > 
   >    > <property>
   >    > <name>dfs.name.dir</name>
   >    > #where to place name directory
   >    > <value>/usr/local/hadoop-1.2.1/name</value>
   >    > </property>
   >    > 
   >    > <property>
   >    > <name>dfs.data.dir</name>
   >    > <value>/usr/local/hadoop-1.2.1/data</value>
   >    > </property>
   >    > 
   >    > </configuration>
   >    > ```
   >
   > 3. mapred-site
   >
   >    > ```
   >    > <configuration>
   >    > <property>
   >    > <name>mapred.job.tracker</name>
   >    > <value>hadoopserver1:9001</value>
   >    > </property>
   >    > </configuration>
   >    > ```

9. hadoop namenode -format

10. start-all.sh //stop-all.sh

    name, data, tmp 파일이 생기지 않을 경우 폴더를 모두 삭제 후 7, 8번 점검, 9번부터 다시 만들기

***

1월 7일

- 하둡 파일 관리 서버 들어가는 주소

http://hadoopserver1(NameNode 서버 이름):50070

- 하둡에 파일 넣었다가 빼기

1. hadoop fs -put CHANGES.txt  mydata/CHANGES.txt

   > 하둡에 해당 파일을 어느 폴더의 무슨 이름으로 넣겠다

2. hadoop jar hadoop-examples-1.2.1.jar wordcount mydata/CHANGES.txt wordcount_output

3. hadoop fs -mkdir mydata2

4. cp anaconda-ks.cfg a.txt

5. zip a.txt.zip a.txt

6. hadoop fs -put a.txt.zip /mydata2

7. hadoop fs -get mydata2/a.txt.zip aa.zip



- 가상 분산 모드 예제 연습하기

hadoopserver1 -namenode -201

second				-secondary namenode -202

data1 				  -datanode -203

data2					-datanode -204

- 각 서버에게 할당했던 IP 주소

192.168.111.202 name
192.168.111.203 hadoopserver2
192.168.111.204 data1
192.168.111.205 data2

***

### HDFS 구축

1. name server setting

   > 앞서 만든 hadoopserver1의 복사본.

2. 각 서버(hadoopserver2, data1, data2)에 SSH 연결

3. name server : hadoop 및 기타 셋팅

   > ㅇㅇ

4. name 서버에서 /usr/local/hadoop-1.2.1/conf

   - master,slaves  파일 편집

   > ex) master => hadoopserver2
   >
   > ​	  slaves => hadoopserver2, data1, data2

   - hdfs-site.xml 에서
     - name .dir설정은 (메타 데이터)
     - data 폴더는 물리적으로 실제 데이터가 들어가는 폴더
   - core-site, hdfs-site, mapred-site 재설정

5. JDK 설정

6. hadoop과 jdk 압축

   >  tar cvfz hadoop-1.2.1.tar.gz hadoop-1.2.1/`

7. /etc/profile, hadoop, jdk 를 각 시스템에 전송

   > scp /etc/profile root@hadoopserver2:/etc
   > scp hadoop-1.2.1.tar.gz root@data1:/usr/local
   > scp jdk1.8.0.tar.gz root@data2:/usr/local

8. hadoop, jdk의 압축 해제

   > ssh root@data1 "cd /usr/local; tar xvf hadoop-1.2.1.tar.gz; rm -rf hadoop-1.2.1.tar.gz"
   >
   > `;`으로 명령을 덧붙여서 여러개 사용 가능
   >
   > `" "` 따옴표 안에 실행할 명령을 차례로 입력

9. hadoop 1.2.1 파일로 이동, 

   > hadoop namenode -format

10. start-all.sh/stop-all.sh

11. jps 실행 시 3개 뜸

    > - Jps
    > -  JobTracker
    > - NameNode
 1. hadoopserver2, data1, data2 에서 jps 실행시에 잘 작동되려면

   > systemctl stop firewalld
   >
   > systemctl disable firewalld
   >
   > > 방화벽 설정 해주기



예제 풀어보기

1. wordcount를 실행해보자(pg63)

   > - hadoop fs -put conf/hadoop-env.sh  conf/hadoop-env.sh
   > - hadoop jar hadoop-examples-*.jar wordcount conf/hadoop-env.sh wordcount_output
   > - hadoop fs -cat wordcount_output/part-r-00000

2. /boot 폴더에 있는 파일을 hadoop 시스템에 put, get

3. 모니터링 시스템을 통해 각 시스템의 상황을 모니터링 하기

***

server1을 이용하여 각 컴퓨터를 셋팅 한다.

1. 브릿지를 이용하여 IP 셋팅
2. namenode, second namenode(datanode), datanode1, datanode2
3. 대용량 파일 입력과 wordcloud를 실행해본다. 



***

### HIVE 설치하기

> hive의 메타 데이터를 저장해줄 공간 마련을 위해 MariaDB(MySQL)을 설치해준다.

1. yum -y remove mariadb-libs
2. yum -y localinstall Maria*
3. systemctl restart mysql
4.  systemctl status mysql
5. chkconfig mysql on
6. firewall-config
7. mysqladmin -u root password '111111'
8. mysql -u root -p
9. mysql -u hive -p
10. tar xvf apache-hive-1.0.1-bin.tar.gz 
11. cp -r apache-hive-1.0.1-bin /usr/local/hive

12. vi /etc/profile

    > ```
    > JAVA_HOME=/usr/local/jdk1.8.0
    > CLASSPATH=$JAVA_HOME/lib
    > HADOOP_HOME=/usr/local/hadoop-1.2.1
    > HIVE_HOME=/usr/local/hive
    > 
    > PATH=.:$JAVA_HOME/bin:$HADOOP_HOME/bin:$HIVE_HOME/bin:$PATH
    > 
    > export JAVA_HOME CLASSPATH HADOOP_HOME HIVE_HOME
    > export PATH USER LOGNAME MAIL HOSTNAME HISTSIZE HISTCONTROL
    > ```

13. reboot



14. mysql -u root -p(mysql 접속)





- grant all privileges on *.* to 'hive'@'localhost' identified by '111111';



- create database hive_db;



- grant all privileges on hive_db.* to 'hive'@'localhost' identified by '111111';



- grant all privileges on hive_db.* to 'hive'@'%'  identified by '111111' with grant option;



- http://apache.tt.co.kr/hive/hive-1.2.2/apache-hive-1.2.2-bin.tar.gz

  > hive 파일 다운받을 수 있는 곳



- hive config 

- vi hive-site.xml

  > 없어서 파일 새로 만든것 
  >
  > 밑에는 이 파일에 덧붙일 내용

***

```
<?xml version="1.0"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<configuration>
    <property>
        <name>hive.metastore.local</name>
        <value>true</value>
        <description>controls whether to connect to remove metastore server or open a new metastore server in Hive Client JVM</description>
    </property>
    <property>
        <name>javax.jdo.option.ConnectionURL</name>
        <value>jdbc:mariadb://localhost:3306/hive_db?createDatabaseIfNotExist=true</value>
        <description>JDBC connect string for a JDBC metastore</description>
    </property>
    <property>
        <name>javax.jdo.option.ConnectionDriverName</name>
        <value>org.mariadb.jdbc.Driver</value>
        <description>Driver class name for a JDBC metastore</description>
    </property>
    <property>
        <name>javax.jdo.option.ConnectionUserName</name>
        <value>hive</value>
        <description>username to use against metastore database</description>
    </property>
    <property>
        <name>javax.jdo.option.ConnectionPassword</name>
        <value>111111</value>
        <description>password to use against metastore database</description>
    </property>
</configuration>
```



***

- xml 파일 수정 후 하둡에 hive가 쓸 공간을 마련해준다.

  

1. cd /usr/local/hive/conf
2. hadoop dfs -mkdir /tmp
3. hadoop dfs -mkdir /tmp/hive
4. hadoop dfs -chmod 777 /tmp
5. hadoop dfs -mkdir /user/hive/warehouse
6. hadoop dfs -chmod 777 /user/hive/warehouse

- start-all.sh로 하둡을 실행해 준 후 hive로 로그인
