# FALL 2025 Doubled-Up Homelessness: 공간 데이터 분석 및 시각화

이 레포지토리는 미국 전역의 인구통계학적 그룹 및 지리적 지역에 걸친 **doubled-up homelessness**을 분석하기 위한 포괄적인 데이터 정제 및 공간 통합 파이프라인을 포함합니다. 이 프로젝트는 주(state) 이하 단위(PUMA) 및 주 단위에서 인종, 민족, 경제적 위치에 대한 교차 분석을 가능하게 합니다.

최종 Tableau 시각화는 여기서 확인할 수 있습니다: [Tableau 대시보드](https://public.tableau.com/app/profile/yijun.kim3606/viz/FA25Doubled-UpHomelessness/StateOverviewDashboard)

---

## 시작하기

주요 결과물은 Tableau 시각화에 최적화된 정제된 공간 데이터셋입니다. `./DataCleaning.ipynb` 노트북에는 전체 데이터 처리 파이프라인이 포함되어 있습니다. 정제된 데이터셋은 `data/clean data/` 폴더에 위치합니다:

- `puma_data_integrated_spatial_2023/` - PUMA 수준 공간 데이터 (shapefile)
- `state_data_2023_cleaned_with_spatial.csv` - WKT 지오메트리가 포함된 주 수준 데이터

---

## 개요

doubled-up homelessness(DU)이란 경제적 어려움이나 주거 상실로 인해 다른 사람들과 함께 생활하는 가구를 의미합니다. 다양한 인구통계학적 그룹과 지리적 지역에 걸친 doubled-up homelessness의 패턴을 이해하는 것은 주거 불안정 문제를 해결하기 위해 노력하는 정책 입안자, 연구자, 옹호자들에게 매우 중요합니다.

문제는 미국 지역사회 조사(ACS)의 인구통계 및 주거 데이터가 의미 있는 지리적 시각화와 교차 분석을 가능하게 하려면 광범위한 정제, 표준화 및 공간 통합이 필요하다는 것입니다. 원시 데이터에는 적절한 지리적 식별자가 없고, 형식이 일관되지 않으며, 시각화에 적합한 데이터셋을 만들기 위해 공간 경계와 병합이 필요합니다.

이 프로젝트는 원시 ACS 데이터를 다음을 가능하게 하는 분석 준비 데이터셋으로 변환합니다:

- PUMA 및 주 수준에서의 doubled-up homelessness률 지리적 매핑
- 인종/민족별 인구통계학적 분석
- 경제적 지위 교차 분석 (빈곤 분석)
- Tableau에서의 동적 필터링 및 교차 분석

---

## 프로젝트 설명

이 프로젝트의 목표는 접근 가능하고 정확한 데이터 시각화를 통해 다양한 인구통계학적 그룹과 지리적 지역에 걸친 doubled-up homelessness의 패턴을 더 잘 이해하는 것입니다. 이를 위해 Tableau의 공간 시각화용 정제 데이터를 생성하여, PUMA 및 주 수준의 지리적 경계에서 인종, 민족, 경제적 지위의 교차 분석을 가능하게 합니다.

주요 과제는 원시 ACS 데이터를 시각화 준비 데이터셋으로 변환하는 포괄적인 데이터 정제 및 공간 통합 파이프라인을 개발하는 것입니다. 부차적인 과제는 지리적 식별자 표준화, 필터링 플래그 생성, Tableau 성능을 위한 데이터 구조 최적화입니다. 세 번째 목표는 공간 지오메트리를 인구통계 및 경제 지표와 통합하여 지리적 분석을 가능하게 하는 것입니다.

---

## 프로젝트 체크리스트

- ✅ PUMA 및 주 수준 데이터셋을 위한 포괄적인 데이터 정제 파이프라인 개발
- ✅ 표준화된 지리적 식별자 및 메타데이터 생성
- ✅ 인구통계 및 경제적 특성을 위한 필터링 플래그 시스템 구축
- ✅ 공간 지오메트리와 정제된 표 형식 데이터 통합
- ✅ Tableau 시각화 성능을 위한 데이터셋 최적화
- ✅ 다양한 형식의 시각화 준비 출력물 생성 (shapefile, WKT가 포함된 CSV)

---

## 기술 스택

- Python (Pandas, NumPy, GeoPandas)
- 데이터 정제 및 문서화를 위한 Jupyter Notebooks
- 공간 시각화 및 대시보드 생성을 위한 Tableau

---

## 프로젝트 구조

```
.
Doubled-Up/
├── .gitattributes
├── README_KOR.md
├── README_ENG.md
├── dataset-documentation.md
├─- DataCleaning.ipynb
│
├── Cleaned Data/
│   ├── puma_data_integrated_spatial_2023/
│   │   ├── puma_data_2023_integrated_spatial.cpg
│   │   ├── puma_data_2023_integrated_spatial.dbf
│   │   ├── puma_data_2023_integrated_spatial.prj
│   │   ├── puma_data_2023_integrated_spatial.shp
│   │   └── puma_data_2023_integrated_spatial.shx
│   ├── puma_data_integrated_spatial_2023.zip
│   └── state_data_2023_cleaned_with_spatial.csv
│
├── HexStatesPadded/
│   ├── HexStatesPadded.dbf
│   ├── HexStatesPadded.prj
│   ├── HexStatesPadded.shp
│   └── HexStatesPadded.shx
│
├── Raw data/
│   ├── US_2023_5y_state_RACE_poor.csv
│   ├── ipums_puma_2020_ipums_puma_2020.shp.csv
│   ├── puma_data_2023.csv
│   ├── state_2023_5y_all_row E label fix.csv
│   └── us-state-ansi-fips.csv
│
├── data/
│   ├── clean data/
│   │   └── puma_data_integrated_spatial_2023.zip
│   └── spatial file/
│       └── HexStatesPadded.zip
│
└── ipums_puma_2020/
    ├── ipums_puma_2020.CPG
    ├── ipums_puma_2020.dbf
    ├── ipums_puma_2020.prj
    ├── ipums_puma_2020.sbn
    ├── ipums_puma_2020.sbx
    ├── ipums_puma_2020.shp.xml
    └── ipums_puma_2020.shx
```

---

## 폴더 설명

### `data/`
모든 입출력 데이터셋이 포함된 메인 데이터 디렉토리입니다.

**`./data/clean data/`**
- 시각화에 바로 사용 가능한 최종 정제 및 통합 데이터셋
- `puma_data_integrated_spatial_2023/` - 통합 PUMA 공간 데이터 (shapefile 형식, 2,461개 레코드)
- `state_data_2023_cleaned_with_spatial.csv` - WKT 지오메트리가 포함된 통합 주 데이터 (51개 레코드)

**`./data/raw data/`**
- 처리 전 모든 원본 소스 파일
- `puma_data_2023.csv` - 원본 PUMA 수준 데이터 (2,462개 레코드)
- `state_2023_5y_all_row E label fix.csv` - 원본 주 수준 데이터 (51개 레코드)
- `US_2023_5y_state_RACE_poor.csv` - 주 수준 인종 및 빈곤 교차 데이터
- `us-state-ansi-fips.csv` - 주 FIPS 코드 매핑 파일 (51개 레코드)
- `ipums_puma_2020_ipums_puma_2020.shp.csv` - PUMA 지리 메타데이터 (2,486개 레코드)

**`DataCleaning.ipynb`**
- 전체 데이터 정제 및 공간 통합 파이프라인이 포함된 메인 Jupyter 노트북

**`dataset-documentation.md`**
- 스키마, 필드 설명, 사용 지침이 포함된 완전한 데이터셋 문서


---

## 데이터 소스

| 출처 | 유형 | 설명 | 링크 |
|------|------|------|------|
| American Community Survey (ACS) 2023 5개년 추정치 | CSV | PUMA 및 주 수준에서의 인구통계 및 doubled-up 노숙 지표가 포함된 원본 데이터 | [링크](https://drive.google.com/drive/folders/14gJlaHZU1O_ew-ffJjUAQFKGAGYEuOxW) |
| IPUMS USA | Shapefile | 2020년 인구 조사의 PUMA 지리적 경계 shapefile | [링크](https://usa.ipums.org/usa/volii/pumas20.shtml) |
| U.S. Census Bureau | CSV | 주 FIPS 코드 매핑 및 지리적 정의 | [링크](https://gist.github.com/dantonnoriega/bf1acd2290e15b91e6710b6fd3be0a53) |
| HexStatesPadded | Shapefile | 향상된 시각화를 위한 패딩이 적용된 육각형 기반 주 지도 shapefile | [링크](https://stanke.co/hexstatespadded/) |

**데이터셋 요약**
- 기본 데이터셋: 인구통계 및 경제 지표가 포함된 2,461개 PUMA 레코드 및 51개 주 레코드
- 지리적 범위: 미국 전체 주 및 2,461개 PUMA
- 데이터 기간: 2023년 (2019-2023년을 나타내는 5개년 추정치)
- 인구통계 카테고리: 백인, 흑인, AIAN, 아시아계, NHOPI, 히스패닉, 기타, 혼혈
- 경제 지표: Doubled-up 노숙률, 빈곤 지위, 인종 × 빈곤 교차 분석

---

## 데이터 처리 및 정제

### Step 1: PUMA 데이터 정제 및 공간 통합

**입력 데이터**
- `puma_data_2023.csv` - 메인 PUMA 데이터 (2,462개 레코드)
- `us-state-ansi-fips.csv` - 주 매핑 파일
- `ipums_puma_2020_ipums_puma_2020.shp.csv` - PUMA 지리 메타데이터
- `ipums_puma_2020.shp` - PUMA 공간 shapefile

**처리 과정**
1. GEOID를 7자리 zero-padded 문자열로 표준화
2. GEOID에서 주 FIPS 코드 추출
3. 주 이름 및 약어 병합
4. PUMA 이름 및 코드 병합
5. 인구통계 카테고리에 대한 이진 플래그 생성 (백인, 흑인, AIAN, 아시아계, NHOPI, 히스패닉, 기타, 혼혈)
6. 경제 플래그(`Poor_Flag`) 및 교차 플래그(`Race_Poor_Flag`) 생성
7. 불필요한 열 제거 및 Tableau 호환 축약 형식으로 열 이름 변경
8. GEOID 매칭을 통한 공간 shapefile 병합

**출력**
- `puma_data_2023_integrated_spatial/` - 2,461개 매칭 레코드가 포함된 shapefile 디렉토리
- 129개 열 (122개 데이터 열 + 7개 공간 메타데이터 열)

---

### Step 2: 주 데이터 정제 및 공간 통합

**입력 데이터**
- `state_2023_5y_all_row E label fix.csv` - 메인 주 데이터 (51개 레코드)
- `us-state-ansi-fips.csv` - 주 매핑 파일
- `US_2023_5y_state_RACE_poor.csv` - 인종 × 빈곤 교차 데이터
- `HexStatesPadded.shp` - 주 육각형 shapefile

**처리 과정**
1. 주 FIPS 코드를 2자리 zero-padded 문자열로 표준화
2. 주 이름 및 약어 병합
3. 인종 × 빈곤 교차 지표 병합
4. 인구통계 및 경제적 특성에 대한 이진 플래그 생성
5. 표준 오차 열 제거 (MOE 열만 유지)
6. 백분율 열을 소수점 2자리로 반올림
7. 주 약어를 사용하여 육각형 shapefile과 병합
8. CSV 호환성을 위해 지오메트리를 WKT 형식으로 변환

**출력**
- `state_data_2023_cleaned_with_spatial.csv` - WKT 지오메트리가 포함된 CSV (51개 레코드)
- 123개 열 (122개 데이터 열 + 1개 WKT 지오메트리 열)

---

## 팀 및 연락처

| 이름 | 역할 | 이메일 |
|------|------|--------|
| Yijun Kim | 프로젝트 매니저 - 학생 | yijunkim@bu.edu |
| Deniz Ozcakir | 프로젝트 멤버 - 학생 | dozcakir@bu.edu |
| Alex Noor | 프로젝트 멤버 - 학생 | alexnoor@bu.edu |
| Amira Zuniga | 프로젝트 멤버 - 학생 | azuniga@bu.edu |
| Catalina Sanhueza Schuller | 기술 프로젝트 매니저 | csanhuez@bu.edu |

**클라이언트 연락처**
- Molly Richard

**강좌 정보**
- 강좌: DS594 Data Visualization
- 프로그램: Boston University Spark!
- 학기: Fall 2025
- 클라이언트: Molly Richard

---

## 주요 연구 결과

**데이터 품질 개선**
- 표준화: 모든 GEOID 및 FIPS 코드를 zero-padded 문자열로 일관되게 형식화
- 열 최적화: PUMA 데이터 166개 → 122개, 주 데이터 139개 → 123개로 축소
- 명명 규칙: Tableau에 최적화된 축약 열 이름 (shapefile의 10자 제한)
- 플래그 시스템: 유연한 필터링을 위한 17개 이진 플래그 생성 (인구통계 8개 + 경제 1개 + 교차 8개)

**분석 가능 내용**
- 인구통계 분석: 플래그 또는 카테고리를 사용하여 인종/민족별 필터링
- 경제 분석: `Poor_Flag`를 사용하여 빈곤 지위별 필터링
- 교차 분석: 인구통계 × 경제 교차 플래그 (예: `White_Poor_Flag`)
- 공간 시각화: PUMA 및 주 수준에서의 매핑을 위한 전체 지리적 경계
- 통계 분석: 모든 지표에 대한 빈도, 백분율, MOE, CV 포함

---

## 향후 연구 방향

**대시보드 개선**
- 강력한 주 비교 모드: 나란히 배치되는 포괄적인 주 간 비교 기능 구현
- 향상된 필터링 기능: 인구통계 및 경제적 특성에 대한 더 유연하고 세분화된 필터링 옵션 추가
- 경량 PUMA 수준 비교: 성능 저하 없는 효율적인 PUMA 간 비교 지원
- 플랫폼 마이그레이션: Tableau에서 벗어나 더 빠른 로드 타임, 높은 커스터마이징 자유도, 더 반응적인 사용자 경험을 제공하는 플랫폼으로 이전

**즉각적인 확장**
- 추가 인구통계: 연령, 성별, 가구 구성 변수 포함
- 서비스 제공자 매핑: 자원 매핑을 위한 주거 서비스 제공자 위치 통합

---

## 라이선스 및 출처

**학술 인용**
```
Doubled-Up Homelessness: Spatial Data Analysis and Visualization. (2025).
BU Spark DS594 팀: Yijun Kim, Deniz Ozcakir, Alex Noor, Amira Zuniga.
Molly Richard와의 협력.
https://github.com/BU-Spark/data-viz-ciss-doubled-up
```

**데이터 출처**
- IPUMS USA: Integrated Public Use Microdata Series - https://usa.ipums.org/usa/
- 지리적 경계: U.S. Census Bureau 및 IPUMS USA

**사용 권한**
- 코드 및 분석: 연구 및 교육 목적의 오픈 소스
- 데이터셋: 공개 도메인 (ACS 데이터) - 공개 사용 제한 없음
- 시각화 및 보고서: 출처 표기 후 오픈 소스 - 교육 및 연구 목적으로 적합
- 정제된 데이터셋: 연구, 정책 분석, 교육 목적으로 사용 가능

**문의**
- 기술적 문의: yijunkim@bu.edu
- 데이터 사용 권한: U.S. Census Bureau 및 IPUMS USA (공개 도메인)
- 학술 협력: 연구 파트너십을 위해 프로젝트 팀원에게 연락
