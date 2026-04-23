# Git & GitHub

## 1. 영역 (작업 폴더 → 스테이징 → 저장소 → GitHub)
- 작업 폴더(working directory): 작업 폴더
- 스테이징 영역(staging area): 커밋할 파일들을 모아두는 곳
- 로컬 저장소(local repository): 커밋된 파일들을 저장하는 곳
    - .git 폴더 안에 저장됨
- 원격 저장소(remote repository): GitHub 저장소

---

## 2. 초기 작업
- **커밋 작성자 정보 설정**: 처음 한 번만 사용
    - **git config --global user.name "이름"**
    - **git config --global user.email "이메일"**
- **git init**: 현재 폴더를 Git 관리 시작
    - .git 이라는 숨김 폴더 생성됨
- **git remote add origin 원격저장소주소**: 원격 저장소 연결
    - origin → 원격 저장소의 별명
    - 저장소주소 → GitHub 저장소 주소

---

## 3. 기본 동작

### 3.1 파일 추가 및 저장
- **git add 파일명**: 변경된 특정 파일을 스테이징 영역에 올림
    - . → 현재 폴더 전체
- **git commit -m "메시지"**: 스테이징된 파일들을 로컬 저장소에 저장
    - 메시지 → 변경 내용 요약

### 3.2 GitHub에 업로드
- **git push**: 로컬 저장소 → 원격 저장소
    - git push -u origin main: 처음 한 번만 사용

### 3.3 GitHub에서 다운로드
- **git pull**: 원격 저장소 → 로컬 저장소
    - git pull -u origin main: 처음 한 번만 사용
    - 동작 원리: git fetch + git merge
        - git fetch: 원격 저장소의 최신 내용을 다운로드
        - git merge: 다운로드한 내용을 현재 브랜치에 병합

---

## 4. 브랜치
- 원본(main)을 건드리지 않고 따로 작업하는 공간
    - 브랜치를 바꿀 때마다 내 작업 폴더가 그 브랜치의 상태로 바뀐다
- 브랜치는 파일 복사가 아니라 커밋을 가리키는 포인터
- 브랜치는 **로컬**과 **원격**에 둘 다 따로 존재 가능

### 4.1 생성
- 로컬에서만 브랜치가 생성됨
- **git branch 브랜치명**: 현재 커밋 기준으로 새 브랜치 생성
- **git checkout 브랜치명**, **git switch 브랜치명**: 브랜치 이동
- **git checkout -b 브랜치명**, **git switch -c 브랜치명**: 브랜치 생성 및 이동

#### 4.1.1 브랜치명
- 구분: 소문자 + 하이픈(-), 슬래시(/)
- 접두어
    - feature/: 새로운 기능 개발
    - bugfix/: 버그 수정
    - hotfix/: 긴급 수정
    - refactor/: 코드 리팩토링
    - test/: 테스트
    - chore/: 잡일(설정 등)

### 4.2 작업 & 커밋
- **git add .**
- **git commit -m "메시지"**

### 4.3 병합 & 업로드
- **병합 후 업로드**
    - **git merge 브랜치명**: 현재 브랜치로 브랜치 병합
    - **git push**
```
git checkout main         # main 브랜치로 이동
git merge feature/login   # feature/login 브랜치의 내용을 main 브랜치로 병합 (로컬)
git push                  # GitHub에 업로드
```

- **브랜치 직접 업로드**
    - 원격에 브랜치 생성 (main은 그대로)
    - **git push origin 브랜치명**: 브랜치를 GitHub에 업로드
        - git push -u origin 브랜치명: 처음 한 번만 사용
        - 브랜치마다 각각 원격 브랜치와 “연결(upstream)”이 따로 잡힌다
```
git push origin feature/login   # feature/login 브랜치를 GitHub에 업로드
```

### 4.4 삭제
- **로컬 브랜치 삭제**
    - **git branch -d 브랜치명**: 이미 merge된 브랜치 삭제
        - 현재 브랜치는 삭제 못 함 (브랜치 이동 후 삭제)
    - **git branch -D 브랜치명**: 강제 삭제
- **원격 브랜치 삭제**
    - **git push origin --delete 브랜치명**

### 4.5 브랜치 목록 확인
- **git branch**: 로컬 브랜치 목록 확인
- **git branch -r**: 원격 브랜치 목록 확인

---

## 6. 정리

### 6.1 처음 만들 때
```
git init
git remote add origin 원격저장소주소
git add .
git commit -m "커밋메시지"
git push -u origin main
```

---

## 7. 상태 확인
- **git status**: 현재 상태 확인
    - 파일 수정 여부
    - 파일 add 여부
    - 파일 commit 여부
- **git log**: 커밋 기록 확인
- **git diff**: 스테이징 전 변경 사항 확인
    - **git diff --staged**: 스테이징 후 변경 사항 확인
