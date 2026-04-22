# 데이터분석

## 1. 데이터분석용 Phyton 환경 이해 + Pandas 시작

### 1.1 Pandas란?
- 파이썬의 데이터 분석 라이브러리
- Series, DataFrame 등 다양한 데이터 구조 제공
- 데이터 조작, 분석, 시각화 등 다양한 기능 제공

### 1.2 핵심 객체

#### 1.2.1 Series
- 한 개의 열 같은 구조 [1차원]
```
import pandas as pd                 # 0 10
                                    # 1 20
s = pd.Series([10, 20, 30, 40])     # 2 30
print(s)                            # 3 40
```

#### 1.2.2 DataFrame
- 여러 개의 열을 가진 테이블 구조 [2차원]
```
import pandas as pd

df = pd.DataFrame({
    "name": ["Kim", "Lee", "Park"],     #    name  age  score
    "age": [20, 22, 21],                # 0   Kim   20     85
    "score": [85, 90, 78]               # 1   Lee   22     90
})                                      # 2  Park   21     78
print(df)                               
```

### 1.3 csv 파일
- **csv(Comma Separated Values) 파일**: 데이터를 쉼표로 나눠서 저장한 텍스트 파일
    - 데이터 타입 없음 (전부 문자열처럼 취급)
- **기본 함수**
    - **불러오기**: df = pd.read_csv(파일명)
    - **출력**
        - **행**
            - df.head(num): 상위 num개 행 출력 (기본값: 5)
            - df.tail(num): 하위 num개 행 출력 (기본값: 5)
        - **열**
            - df.columns: 컬럼명 확인
            - df['컬럼명']: 특정 컬럼 선택 (Series 반환)
            - df[['컬럼명']]: 단일 컬럼이지만 DataFrame 반환
            - df[['컬럼명1', '컬럼명2']]: 여러 컬럼 선택 (DataFrame 반환)
        - **행과 열**
            - df.shape: 데이터프레임 행과 열 반환
            - df.size: 데이터프레임 원소 개수 반환
    - **데이터프레임 정보**
        - df.info(): 데이터프레임 정보 출력
        - df.describe(): 데이터프레임 요약 통계 출력
    - **결측치**
        - df.isnull(): 결측치 확인
        - df.isnull().sum(): 결측치 개수 확인
        - df.isnull().sum().sum(): 결측치 총 개수 확인

### 1.4 변환
- **.to_frame()**: Series -> DataFrame
- **.to_csv(filename)**: DataFrame -> CSV
    - **매개변수**
        - index=False: 인덱스 제외

---

## 2. Pandas 기초 조작: 컬럼 선택, 행 필터링, 정렬, 조건문, 새 컬럼 만들기