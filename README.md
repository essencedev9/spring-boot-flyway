# 사용 방법

### 선행 조건

* docker, docker-compose 설치

### docker-compose.yml 파일 변경
```
db:
    image: mysql:5.7
    ports:
        - "3306:3306"
    environment:
        MYSQL_USER: user
        MYSQL_PASSWORD: user
        MYSQL_ROOT_PASSWORD: root
        MYSQL_DATABASE: user
```

### docker 실행

``` sh
docker-compose up -d
```

### build.gradle 파일 변경
```
flyway {
	url = "jdbc:mysql://localhost:3306/user"
	user = "user"
	password = "user"
	locations = ["classpath:/db/migration/schema","classpath:/db/migration/data"];
	encoding = 'UTF-8'
	outOfOrder = false
	validateOnMigrate = true
}
```

### 마이그레이션

``` sh
./gradlew flywayMigrate
```

### 마이그레이션 롤백
``` sh
./gradlew flywayClean
```