## DB 추가 후 해당 DB만 접근 가능한 유저 추가

1. DB 생성: CREATE DATABASE 'DB명'
2. 
    - localhost 유저 추가: CREATE USER '유저명'@'localhost' IDENTIFIED BY '비밀번호';
    - 외부 주소 유저 추가: CREATE USER '유저명'@'%' IDENTIFIED BY '비밀번호';
3. 
    - localhost 유저에 모든 권한 주기: GRANT ALL ON DB명.* TO '유저명'@'localhost';
    - 외부 주소 유저에 모든 권한 주기: GRANT ALL ON DB명.* TO '유저명'@'%';
4. FLUSH PRIVILEGES;
