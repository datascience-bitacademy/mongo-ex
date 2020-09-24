### Redis install on CentOS 6/7

### Repository 추가

```bash
### CentOS/RHEL 7 
yum install epel-release

### CentOS/RHEL 6 
rpm -Uvh http://download.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
```

### Install redis

```bash
yum install redis
```

### Setting up redis

```bash
# in /etc/rc.d/init.d/
cd /etc/rc.d/initd
less redis
```

- redis config : /etc/redis.conf
- redis log : /var/log/redis/redis.log
- rdb 파일 위치 : 
- 기본 포트 : 6379
- 데이터베이스 파일 위치: /var/lib/redis

```bash
# 외부에서 접속하려면
# in /etc/redis.conf
bind 0.0.0.0
```

### 서비스 시작

```bash
service redis start
chkconfig redis on # 시작 서비스로 등록
```

### iptables 등록

```bash
vi /etc/sysconfig/iptables
-A INPUT -m state NEW -m tcp --dport 6379 -j ACCEPT
```

### 추천 Windows Client

- P3X : https://www.electronjs.org/apps/p3x-redis-ui

### Client 실행

```
redis-cli
redis-cli --raw # 한글이 깨질 때]
```

### 언어별 redis-client

- https://redis.io/clients