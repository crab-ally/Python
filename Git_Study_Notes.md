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

## 3. 파일 추가 및 저장
- **git add 파일명**: 변경된 특정 파일을 스테이징 영역에 올림
    - . → 현재 폴더 전체
- **git commit -m "메시지"**: 스테이징된 파일들을 로컬 저장소에 저장
    - 메시지 → 변경 내용 요약

## 4. GitHub에 업로드
- **git push**: 로컬 저장소 → 원격 저장소
    - git push -u origin main: 처음 한 번만 사용

## 5. GitHub에서 다운로드
- **git pull**: 원격 저장소 → 로컬 저장소
    - git pull -u origin main: 처음 한 번만 사용
    - 동작 원리: git fetch + git merge
        - git fetch: 원격 저장소의 최신 내용을 다운로드
        - git merge: 다운로드한 내용을 현재 브랜치에 병합

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
