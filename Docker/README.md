# SKT FLY AI Challenger
## Docker 실습
- 2023.07.10 ~ 2023.07.14

### 도커 정리


### 과제
- git hook 또는 git action을 이용하여 커밋한 소스코드 테스트 자동화 구축
- 2개의 서비스를 만들고 dockerizing
- docker 구축 시 env를 포함한 명령어 사용
- 배포 시 docker run 적절한 옵션 설정

1. git hook 또는 git action을 이용한 커밋 소스코드 자동화 테스트
   1) 문법 오류가 있는 test.py 생성
   2) .git > hooks 레포지토리로 이동
   3) pre-commit.sample 파일을 수정하거나 pre-commit 파일을 생성하여 아래 내용 입력
      !/bin/sh
      set -e
      ######## RUN UNIT TEST HOOK START ########
      git stash -q --keep-index
      ./gradlew test
      RESULT=$?
      git stash pop -q
      exit $RESULT
      ######## RUN UNIT TEST HOOK END ########
   4) 이후 커밋을 실행하면 자동적으로 테스트 실행 후 문제 없으면 커밋, 문제 발생 시 커밋 X

2. docker 이미지 파일 생성하여 2개의 서비스 구축하기
   1) Dockerfile 생성
      ![carbon-9](https://github.com/rydbs/FLYAI/assets/117563202/8b7d90f2-7f6e-486c-ad20-dfeaa71529cb)
   2) 웹페이지 정보를 담은 python 파일 생성
      ![carbon-7](https://github.com/rydbs/FLYAI/assets/117563202/82e2d312-15c3-4cac-978a-c5f9c43dd0a2)
      ![carbon-8](https://github.com/rydbs/FLYAI/assets/117563202/04c53c33-cccd-4828-a82e-c0ad7a81ee11)
   3) 작성한 Dockerfile을 이용해 이미지 생성
      docker build -t [빌드할 이미지 이름] .
      <img width="1440" alt="스크린샷 2023-07-16 오전 12 42 53" src="https://github.com/rydbs/FLYAI/assets/117563202/155b0203-6ebe-4225-a969-95ac197b7508">
      <img width="1440" alt="스크린샷 2023-07-16 오전 12 38 00" src="https://github.com/rydbs/FLYAI/assets/117563202/6972f9ca-dce9-47f0-9a42-d54974c09d58">
   4) 

