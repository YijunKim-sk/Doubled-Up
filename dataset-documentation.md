# 데이터셋 문서 (한국어 번역)


## 프로젝트 정보

- **프로젝트 이름:** Doubled Up Homelessness

- **프로젝트 설명 및 목표:**
  다양한 인구통계학적 그룹과 지리적 지역에 걸친 doubled up homelessness의 패턴을 보다 잘 이해하기 위한 접근 가능하고 정확한 데이터 시각화를 제공하는 것이 목표입니다. 이를 위해 Tableau의 공간 시각화를 위한 정제 데이터를 생성하였으며, PUMA 및 주 수준의 지리적 경계에서 인종, 민족, 경제적 지위의 교차 분석이 가능합니다.

- **클라이언트:** Dr. Molly Richard

- **강좌:** DS594

---

## 데이터셋 정보

### 사용한 데이터셋

**1. PUMA 수준 데이터**
- `puma_data_2023.csv` - 메인 PUMA 수준 인구통계 및 doubled up homelessness 데이터 (2,462개 레코드)
- `ipums_puma_2020_ipums_puma_2020.shp.csv` - PUMA 지리 매핑 파일 (2,486개 레코드)
- `ipums_puma_2020.shp` - 지리 시각화를 위한 PUMA 공간 shapefile

**2. 주 수준 데이터**
- `state_2023_5y_all_row E label fix.csv` - 주 수준 인구통계 및 doubled up homelessness 데이터 (51개 레코드)
- `US_2023_5y_state_RACE_poor.csv` - 주 수준 인종 및 빈곤 교차 데이터
- `HexStatesPadded.shp` - 지리 시각화를 위한 주 육각형 shapefile

**3. 참조 데이터**
- `us-state-ansi-fips.csv` - 주 FIPS 코드 매핑 파일 (51개 레코드)

### 키워드 및 태그

**적용 도메인:**
- 지리공간 데이터 분석
- 인구통계학적 분석
- 데이터 시각화
- 공공 정책 분석

**적용 분야:**
- 주거 (Housing)
- 시민 기술 (Civic Tech)
- 보건 (Health)
- 사회 서비스 (Social Services)

---

## 동기 (Motivation)

**데이터셋이 생성된 목적:**

이 데이터셋은 Tableau의 공간 시각화를 위한 인구통계 및 경제 데이터를 준비하기 위해 생성되었습니다. 주요 목적은 다음과 같습니다:

- **지리적 매핑:** PUMA 및 주 수준에서 공간 분석이 가능하도록 지리적 식별자 및 메타데이터 추가
- **공간 데이터 통합:** Tableau 성능 향상을 위해 표 형식 데이터와 공간 지오메트리(shapefile) 병합
- **필터 생성:** 복잡한 계산 없이 빠른 필터링과 교차 분석이 가능하도록 인구통계 및 경제적 특성에 대한 이진 플래그 열 및 범주형 변수 생성
- **데이터 축소:** 파일 크기 줄이기 위해 표준 오차 열, 임차인 관련 열 등 불필요한 열 제거
- **열 이름 최적화:** shapefile 형식의 10자 제한으로 인해 PUMA 데이터셋의 열 이름을 축약

---

## 구성 (Composition)

**데이터셋의 인스턴스 유형:**

두 가지 데이터셋이 있으며 각각의 인스턴스는 다음과 같습니다:

1. **PUMA 데이터셋:** 공공 사용 마이크로데이터 지역 (PUMA)
   - 인구 100,000명 이상의 지역으로, 인구 조사 데이터 보고에 사용
2. **주 데이터셋:** 미국 주 (워싱턴 D.C. 포함)

데이터 형식은 다음을 결합한 멀티모달입니다:
- 표 형식 데이터 (CSV): 인구통계 및 경제 지표
- 지리공간 데이터 (PUMA는 ESRI Shapefile, 주는 CSV의 WKT 형식): 공간 경계 및 지오메트리

**인스턴스 수:**
- PUMA 데이터셋: 2,461개 (공간 및 데이터 레코드가 매칭된 항목)
- 주 데이터셋: 51개 (미국 전체 주 + D.C.)

**완전한 데이터셋 여부:**
두 데이터셋 모두 의도적인 제외 없이 가능한 모든 인스턴스를 포함합니다.

**각 인스턴스의 구성 요소:**

1. **지리적 식별자:** GEOID, State_FIPS, State_Name, State_Abbreviation, PUMA_Code, PUMA_Name (PUMA 데이터셋)
2. **인구통계 지표** (인종/민족별: 백인, 흑인, AIAN, 아시아계, NHOPI, 히스패닉, 기타, 혼혈):
   - 가중 빈도, 백분율, 변동 계수(CV), 오차 한계(MOE)
3. **경제 지표:**
   - doubled up homelessness(DU) 가중 빈도, 백분율, CV, MOE
   - 빈곤선 이하/근접 DU 개인 지표
   - 인종별 빈곤 인구 지표
4. **플래그 변수:**
   - 인구통계 카테고리 이진 플래그
   - 빈곤 지위 이진 플래그
   - 교차 플래그 (인구통계 × 빈곤)
   - 필터링을 위한 범주형 변수
5. **공간 데이터:** 지오메트리 열 (shapefile) 또는 Geometry_WKT 열 (CSV)

**결측값 여부:**
일부 인스턴스에 결측값이 있습니다. 특정 PUMA 지역이나 주에서 특정 인구통계 또는 빈곤 지위의 개인 조사 데이터를 수집할 수 없었기 때문입니다. 전처리 과정에서 백분율 및 빈도 열의 결측값은 적절한 경우 0으로 채웠습니다.

**권장 데이터 분할:** 해당 없음 (시각화 목적의 데이터 통합 및 정제 프로젝트)

**오류 및 중복 여부:**
CSV에는 존재하지만 shapefile에는 없는 PUMA GEOID(0100400)가 하나 있습니다. DU 비율 관련 데이터만 포함되어 있어 최종 공간 데이터셋에서 제외하기로 결정했습니다.

**외부 리소스 의존성:**
최종 출력물은 자체 완결적이나, 다음 외부 소스에서 생성되었습니다:
- PUMA 지리 데이터를 위한 IPUMS
- 외부 소스의 주 육각형 shapefile

**기밀 데이터 여부:** 없음. 모든 데이터는 PUMA 및 주 수준에서 집계되어 개인 정보를 보호합니다. 개인 식별 정보는 포함되지 않습니다.

**개인 식별 가능성:** 없음. 데이터는 지리적 수준(PUMA 및 주)에서 집계되며, PUMA 지역의 최소 인구가 100,000명이므로 개인 식별은 사실상 불가능합니다.

---

## 데이터셋 스냅샷

### PUMA 데이터셋

| 항목 | 값 |
|------|-----|
| 데이터셋 크기 | 214.5 MB (shapefile) |
| 인스턴스 수 | 2,461 |
| 필드 수 | 129 (데이터 열 122개 + 공간 메타데이터 열 7개) |
| 레이블 클래스 | 해당 없음 |
| 레이블 수 | 해당 없음 |

### 주 데이터셋

| 항목 | 값 |
|------|-----|
| 데이터셋 크기 | 51KB |
| 인스턴스 수 | 51 |
| 필드 수 | 123 (데이터 열 122개 + WKT 지오메트리 열 1개) |
| 레이블 클래스 | 해당 없음 |
| 레이블 수 | 해당 없음 |

---

## 수집 과정 (Collection Process)

**데이터 수집 방법:**
DU 비율 및 인구통계/경제 지위 데이터는 클라이언트로부터 제공받았습니다. 지리 데이터는 다음 기존 데이터셋에서 가져왔습니다:
- PUMA 지리 경계 및 메타데이터: [IPUMS USA](https://usa.ipums.org/usa/volii/pumas20.shtml)
- 주 수준 매핑 데이터: [Census/ACS 출처](https://gist.github.com/dantonnoriega/bf1acd2290e15b91e6710b6fd3be0a53#file-us-state-ansi-fips-csv)
- 패딩된 육각형 주 지도: [HexStatesPadded](https://stanke.co/hexstatespadded/)

**샘플링 전략:**
PUMA 데이터셋은 데이터 레코드와 매칭되는 2020년 인구 조사 경계의 모든 가용 PUMA 지역을 포함합니다. 결정론적 샘플링으로, 데이터 CSV와 shapefile 간 GEOID가 매칭되는 모든 레코드를 포함했습니다. 공간 지오메트리가 없는 레코드 1개는 제외되었습니다.

**데이터 수집 기간:**
- 데이터: 2023년 인구통계 및 경제 데이터 (주 데이터는 5개년 추정치)
- 공간 경계: 2020년 인구 조사 기준

---

## 전처리/정제/레이블링

**수행된 전처리 작업:**

1. **결측값 처리:**
   - 백분율 열의 결측값을 0으로 채움
   - 빈도/가중 빈도 열의 결측값을 0으로 채움
   - 결측값은 주로 표본 크기가 부족한 소규모 인구통계 그룹의 CV 및 MOE 필드에 존재

2. **데이터 타입 변환:**
   - GEOID를 7자리 zero-padded 문자열로 변환
   - 주 FIPS 코드를 2자리 zero-padded 문자열로 변환
   - 숫자 열을 적절한 타입으로 변환 (백분율은 float, 빈도는 int)
   - 플래그 열을 정수 타입(0 또는 1)으로 변환

3. **데이터 반올림:**
   - 모든 백분율 열을 소수점 2자리로 반올림

4. **인스턴스 제거:**
   - 공간 지오메트리 매칭 실패로 PUMA 레코드 1개 제거 (GEOID: 0100400)

5. **피처 생성 (레이블링):**
   - 각 인구통계 카테고리에 대한 이진 플래그 변수 생성 (White_Flag, Black_Flag 등)
   - 인구통계 그룹 범주형 변수 생성
   - 빈곤 지위 이진 플래그 생성 (Poor_Flag)
   - 인구통계와 빈곤 지위를 결합한 교차 플래그 생성 (White_Poor_Flag, Black_Poor_Flag 등)
   - 빈곤 범주형 변수 생성 (Poor_Category: "Poor" vs "Not Poor")

6. **텍스트 정제:**
   - PUMA 이름 끝의 "PUMA" 텍스트 제거
   - 열 이름 표준화 및 정제

**적용된 변환:**

1. **데이터 병합:**
   - 주 이름 및 약어를 추가하기 위한 주 매핑 데이터 병합
   - PUMA 이름 및 코드를 추가하기 위한 PUMA 지리 메타데이터 병합
   - 주 수준 분석을 위한 인종 × 빈곤 교차 데이터 병합

2. **열 제거:**
   - PUMA 데이터에서 44개 열 제거 (중복 열, 임차인 관련 열, 표준 오차 열)
   - 주 데이터에서 20개 열 제거 (표준 오차 열)

3. **열 이름 변경:**
   - 10자 이내로 단축하기 위해 115개 열 이름 변경
   - 인종 이름의 앞 두 글자 사용 (예: White → Wh, Black → Bl)
   - 표준화된 명명 패턴 적용 (예: {Race}_DU_WeightedFrequency → {Race_abbr}_Fre)

4. **공간 통합:**
   - PUMA 데이터: GEOID 매칭으로 ipums_puma_2020.shp과 병합
   - 주 데이터: State_Abbreviation 매칭으로 HexStatesPadded.shp과 병합
   - CSV 내보내기를 위해 주 데이터 지오메트리를 WKT 형식으로 변환
   - 데이터와 공간 지오메트리가 모두 있는 레코드만 포함하는 inner join 수행

5. **열 재정렬:**
   - 지리적 식별자를 첫 번째로 배치 (GEOID, State_FIPS, State_Name 등)
   - 지오메트리 열을 마지막으로 배치 (GeoPandas shapefile 요건)

**원시 데이터 보존 여부:**
네, 원시 데이터 파일이 보존되어 있습니다:
https://github.com/BU-Spark/data-viz-ciss-doubled-up/tree/yijun/data/raw%20data/FA25_Raw%20Data

**전처리 코드 가용 여부:**
네, 전처리 코드는 다음에서 확인할 수 있습니다:
https://github.com/BU-Spark/data-viz-ciss-doubled-up/blob/yijun/data/FA25_DataCleaning.ipynb

---

## 활용 (Uses)

**현재까지의 활용:**
- Tableau 공간 시각화
- PUMA 및 주 수준의 인구통계 분석
- 경제 분석 (빈곤 지표)
- 인구통계 및 경제적 특성을 결합한 교차 분석
- 지리적 매핑 및 공간 분석

**향후 활용 가능성:**
임차인 관련 피처가 포함된다면 경제적 지위에 대한 더 심층적인 분석이 가능합니다.

**사용 시 주의사항:**
열 이름이 Tableau에 최적화된 약어를 사용하므로, 새 사용자는 데이터 사전을 참고해야 할 수 있습니다.

**사용하지 말아야 할 작업:** 없음.

---

## 배포 (Distribution)

**접근 유형:** 공개 접근 (Open Access)

---

## 유지 관리 (Maintenance)

**기여 방법:**
데이터셋 확장/보완/기여를 원하는 경우 아래 Jupyter 노트북을 사용할 수 있습니다:
https://colab.research.google.com/drive/1H9SUC6cx-BCIhQ30XJrhLaLKZma-uCq2?usp=sharing


# 원본 영어 버전
## ***Project Information*** 

* **What is the project name?**
  * Doubled Up Homelessness

* **In your own words, what is this project about? What is the goal of this project?**
  * The goal is to provide accessible, accurate data visualizations to better understand patterns of doubled-up homelessness across different demographic groups and geographic regions. To accomplist this goal, a cleaned data was created for spatial visualization in Tableau, enabling intersectional analysis of race, ethnicity, and economic status across geographic boundaries at both sub-state (PUMA) and state levels.

* **Who is the client for the project?**
  * Dr. Molly Richard

* **Who are the client contacts for the project?**
  * molly.richard@uri.edu

* **What class was this project part of?**
  * DS594

## ***Dataset Information***

* **What data sets did you use in your project? Please provide a link to the data sets, this could be a link to a folder in your GitHub Repo, Spark! owned Google Drive Folder for this project, or a path on the SCC, etc.**

  * The project uses multiple datasets:
    1. PUMA Level Data:
         - puma_data_2023.csv - Main PUMA-level demographic and doubled-up homelessness data (2,462 records)
         - ipums_puma_2020_ipums_puma_2020.shp.csv - PUMA geographic mapping file (2,486 records)
         - ipums_puma_2020.shp - PUMA spatial shapefile for geographic visualization

    2. State Level Data:
       - state_2023_5y_all_row E label fix.csv - State-level demographic and doubled-up homelessness data (51 records)
       - US_2023_5y_state_RACE_poor.csv - State-level race and poverty intersection data
       - HexStatesPadded.shp - State hexagon shapefile for geographic visualization

    3. Reference Data:
       - us-state-ansi-fips.csv - State FIPS code mapping file (51 records)

* **Please provide a link to any data dictionaries for the datasets in this project. If one does not exist, please create a data dictionary for the datasets used in this project. (Example of data dictionary)**

  * https://github.com/BU-Spark/data-viz-ciss-doubled-up/blob/adding-new-dataset-and-codes/miscellaneous/Datadictionary.xlsx

* What keywords or tags would you attach to the data set?
  * Domain(s) of Application: Computer Vision, Object Detection, OCR, Image Classification, Image Segmentation, Facial Recognition, NLP, Topic Modeling, Sentiment Analysis, Named Entity Recognition, Text Classification, Summarization, Anomaly Detection, Other

    * Others:
      - Geospatial Data Analysis
      - Demographic Analysis
      - Data Visualization
      - Public Policy Analysis
      - Application Areas:

    * Sustainability, Health, Civic Tech, Voting, Housing, Policing, Budget, Education, Transportation, etc.
      - Housing
      - Civic Tech
      - Health
      - Social Services

### The following questions pertain to the datasets you used in your project.
## Motivation

* **For what purpose was the dataset created? Was there a specific task in mind? Was there a specific gap that needed to be filled? Please provide a description.**

  * The datasets were created to prepare demographic and economic data for spatial visualization in Tableau. The main purposes were:
    - Geographic mapping: Add geographic identifiers and metadata to enable spatial analysis at PUMA and state levels.
    - Spatial data integration: Merge tabular data with spatial geometries (shapefiles) to improve speed in Tableau.
    - Filter creation: Create binary flag columns and categorical variables for demographic and economic features to enable quick filtering and intersectional analysis without complex calculations. Data reduction: Remove unnecessary columns, such as standard error columns and renter-realted columns, (e.g., standard error columns, to reduce file size. Column name optimization: Shorten column names in PUMA dataset because the PUMA dataset was created in shapefile format, which has limitations on column name length up to 10 characteristics.

## Composition
* **What do the instances that comprise the dataset represent (e.g., documents, photos, people, countries)? Are there multiple types of instances (e.g., movies, users, and ratings; people and interactions between them; nodes and edges)? What is the format of the instances (e.g., image data, text data, tabular data, audio data, video data, time series, graph data, geospatial data, multimodal (please specify), etc.)? Please provide a description.**

  * There are two datasets in our project: state dataset and PUMA dataset. In each dataset, the instances are:
    1. PUMA dataset: Public Use Microdata Areas (PUMA)
       - geographic areas with populations of 100,000+ used for census data reporting
    2. State dataset: U.S. States (including District of Columbia)
       - The data is multimodal combining:
         - Tabular data (CSV format): Demographic and economic metrics
         - Geospatial data (ESRI Shapefile format for PUMA, WKT format in CSV for States): Spatial boundaries and geometries

* **How many instances are there in total (of each type, if appropriate)?**
  * PUMA dataset: 2,461 instances (matched spatial and data records)
  * State dataset: 51 instances (all U.S. states + DC)

* **Does the dataset contain all possible instances or is it a sample (not necessarily random) of instances from a larger set? If the dataset is a sample, then what is the larger set? Is the sample representative of the larger set? If so, please describe how this representativeness was validated/verified. If it is not representative of the larger set, please describe why not (e.g., to cover a more diverse range of instances, because instances were withheld or unavailable).**

  * Both datasets contain all possibble instances without intentional exclusion.

* **What data does each instance consist of? "Raw" data (e.g., unprocessed text or images) or features? In either case, please provide a description.**

  * Each instance consists of features, including:
    1. Geographic identifiers:
       - GEOID, State_FIPS, State_Name, State_Abbreviation
       - PUMA_Code, PUMA_Name for PUMA dataset
    2. Demographic metrics (for each race/ethnicity: White, Black, AIAN, Asian, NHOPI, Hispanic, Other, Multi):
       - Weighted frequencies
       - Percentages
       - Coefficient of Variation (CV)
       - Margin of Error (MOE) for frequencies and percentages
    3. Economic metrics:
       - Doubled-Up Homelessness (DU) weighted frequencies and percentages, CV, and MOE
       - DU individuals under or near poverty (Poordu) weighted frequencies, percentages, CV, and MOE
       - Race-specific poor population metrics

    4. Flag variables:
       - Binary flags for demographic categories
       - Binary flags for poverty status
       - Combined intersection flags (demographic × poor)
       - Categorical variables for filtering

    5. Spatial data:
       - Geometry column (for shapefiles) or Geometry_WKT column (for CSV)

* **Is there any information missing from individual instances? If so, please provide a description, explaining why this information is missing (e.g., because it was unavailable). This does not include intentionally removed information, but might include redacted text.**

  * Yes, some instances have missing values because the survey data of individuals with certain demographics or poverty status was not available or gathered in that PUMA area or state.
  * Missing values were filled with 0 for percentage and frequency columns where appropriate during preprocessing

* **Are there recommended data splits (e.g., training, development/validation, testing)? If so, please provide a description of these splits, explaining the rationale behind them**

  * No traditional data splits as this is primarily a data integration and cleaning project for visualization purposes.

* **Are there any errors, sources of noise, or redundancies in the dataset? If so, please provide a description.**

  * One PUMA GEOID (0100400) exists in the CSV but not in the shapefile. We decided to exclude this PUMA instance from the final spatial dataset because it only contained data related to DU rates.

* **Is the dataset self-contained, or does it link to or otherwise rely on external resources (e.g., websites, tweets, other datasets)? If it links to or relies on external resources?**

  * The dataset is self-contained for the final outputs. However, it was created from external sources:
    - IPUMS (Integrated Public Use Microdata Series) for PUMA geographic data
    - State hextile shapefiles from external sources

* **Are there guarantees that they will exist, and remain constant, over time?**

  * The source data from IPUMS should remain accessible, but specific datasets may be updated with new census cycles. The 2023 data represents a snapshot from that time period.

* **Are there official archival versions of the complete dataset (i.e., including the external resources as they existed at the time the dataset was created)?**

  * The source data (IPUMS, Census) has official archival versions, but this integrated dataset is a processed version created specifically for this project.

* **Are there any restrictions (e.g., licenses, fees) associated with any of the external resources that might apply to a dataset consumer? Please provide descriptions of all external resources and any restrictions associated with them, as well as links or other access points as appropriate.**

  * No.

* **Does the dataset contain data that might be considered confidential (e.g., data that is protected by legal privilege or by doctor-patient confidentiality, data that includes the content of individuals' non-public communications)? If so, please provide a description.**

  * No, all data is aggregated at the PUMA and State levels, which are designed to protect individual privacy. No personally identifiable information is included.

* **Does the dataset contain data that, if viewed directly, might be offensive, insulting, threatening, or might otherwise cause anxiety? If so, please describe why.**

  * No, the dataset contains demographic and economic statistics without any offensive content.

* **Is it possible to identify individuals (i.e., one or more natural persons), either directly or indirectly (i.e., in combination with other data) from the dataset? If so, please describe how.**

  * No, the data is aggregated at geographic levels (PUMA and State) specifically designed to protect individual privacy. PUMA areas have minimum populations of 100,000, making individual identification extremely unlikely.

* Dataset Snapshot, if there are multiple datasets please include multiple tables for each dataset. 

### PUMA Dataset

| Metric | Value |
|--------|-------|
| Size of dataset | 214.5 MB (shapefile) |
| Number of instances | 2,461 |
| Number of fields | 129 (122 data columns + 7 spatial metadata columns) |
| Labeled classes | N/A |
| Number of labels | N/A |

### State Dataset

| Metric | Value |
|--------|-------|
| Size of dataset | 51KB |
| Number of instances | 51 |
| Number of fields | 123 (122 data columns + 1 WKT geometry column) |
| Labeled classes | N/A |
| Number of labels | N/A |

## Collection Process
* **What mechanisms or procedures were used to collect the data (e.g., API, artificially generated, crowdsourced - paid, crowdsourced - volunteer, scraped or crawled, survey, forms, or polls, taken from other existing datasets, provided by the client, etc)? How were these mechanisms or procedures validated?**

  * The data on DU rates by demongraphics and economic status was provided by the client. However, the geograhical data was taken from other existing datasets:
    * IPUMS (Integrated Public Use Microdata Series) for PUMA geographic boundaries and metadata: https://usa.ipums.org/usa/volii/pumas20.shtml
    * State-level mapping data from Census/ACS sources: https://gist.github.com/dantonnoriega/bf1acd2290e15b91e6710b6fd3be0a53#file-us-state-ansi-fips-csv
    * Padded hextile state map: https://stanke.co/hexstatespadded/

* **If the dataset is a sample from a larger set, what was the sampling strategy (e.g., deterministic, probabilistic with specific sampling probabilities)?**

  * The PUMA dataset includes all available PUMA areas from the 2020 census boundaries that had matching data records. The sampling was deterministic, and all records with matching GEOIDs between the data CSV and shapefile were included. One record was excluded due to missing spatial geometry.

* **Over what timeframe was the data collected? Does this timeframe match the creation timeframe of the data associated with the instances (e.g., recent crawl of old news articles)? If not, please describe the timeframe in which the data associated with the instances was created.**

  * The data represents 2023 demographic and economic data of DU (5-year estimates for state data). The spatial boundaries are from the 2020 census. The PUMA data is 2023 data.

### Preprocessing/cleaning/labeling

* **Was any preprocessing/cleaning/labeling of the data done (e.g., discretization or bucketing, tokenization, part-of-speech tagging, SIFT feature extraction, removal of instances, processing of missing values)? If so, please provide a description. If not, you may skip the remaining questions in this section.**

  * Yes, extensive preprocessing was performed. The preprocessing included:
    1. Missing Value Processing:
       - Filled missing values with 0 for all percentage columns (where appropriate)
       - Filled missing values with 0 for all frequency/weighted frequency columns
       - Missing values were primarily in coefficient of variation (CV) and margin of error (MOE) fields for smaller demographic groups where sample sizes were insufficient

    2. Data Type Conversion:
       - Converted GEOID to string format with zero-padding to 7 digits
       - Converted State FIPS codes to zero-padded 2-digit strings
       - Converted all numeric columns to appropriate numeric types (float for percentages, int for frequencies)
       - Ensured flag columns are integer type (0 or 1)

    3. Data Rounding:
       - Rounded all percentage columns to 2 decimal places for cleaner display and consistency

    4. Instance Removal:
       - Removed 1 PUMA record (GEOID: 0100400) from the spatial integration due to missing spatial geometry match

    5. Feature Creation (Labeling):
       - Created binary flag variables (0/1) for each demographic category (White_Flag, Black_Flag, etc.) indicating presence of that demographic group
       - Created categorical variables for demographic groups (e.g., "White" vs "Not White")
       - Created binary flags for poverty status (Poor_Flag)
       - Created intersection flags combining demographic and poverty status (e.g., White_Poor_Flag, Black_Poor_Flag)
       - Created categorical variable for poverty (Poor_Category: "Poor" vs "Not Poor")

    6. Text Cleaning:
       - Removed trailing "PUMA" text from PUMA names
       - Standardized and cleaned column names

* **Were any transformations applied to the data (e.g., cleaning mismatched values, cleaning missing values, converting data types, data aggregation, dimensionality reduction, joining input sources, redaction or anonymization, etc.)? If so, please provide a description.**

  * Yes, multiple transformations:
    1. Data Merging:
       - Merged state mapping data to add state names and abbreviations to both PUMA and state datasets
       - Merged PUMA geographic metadata to add PUMA names and codes
       - Merged race × poor intersection data for state-level analysis
  
    2. Drop Columns:
       - Dropped 44 columns from PUMA data (redundant columns, renter-related columns, standard error columns)
       - Dropped 20 columns from State data (standard error columns)
       - Removed duplicate columns

    3. Column Renaming:
        - Renamed 115 columns to shorten names up to 10 characteristics
        - Used first two characters of race names (e.g., White → Wh, Black → Bl)
        - Standardized naming patterns (e.g., {Race}_DU_WeightedFrequency to {Race_abbr}_Fre)
      
    4. Spatial Integration:
       - Merged tabular data with spatial shapefiles:
       - PUMA data merged with ipums_puma_2020.shp using GEOID matching
       - State data merged with HexStatesPadded.shp using State_Abbreviation matching
       - Converted geometry to WKT (Well-Known Text) format for state data to enable CSV export with spatial information
       - Performed inner joins to ensure only matched records with both data and spatial geometry
      
    5. Column Reordering:  
        - Reordered columns to place geographic identifiers first (GEOID, State_FIPS, State_Name, etc.)
        - Ensured geometry column is last (GeoPandas requirement for shapefiles)

* **Was the "raw" data saved in addition to the preprocessed/cleaned/labeled data (e.g., to support unanticipated future uses)? If so, please provide a link or other access point to the "raw" data, this could be a link to a folder in your GitHub Repo, Spark! owned Google Drive Folder for this project, or a path on the SCC, etc.**

  * Yes, the raw data files are preserved in: https://github.com/BU-Spark/data-viz-ciss-doubled-up/tree/yijun/data/raw%20data/FA25_Raw%20Data

* **Is the code that was used to preprocess/clean the data available? If so, please provide a link to it (e.g., EDA notebook/EDA script in the GitHub repository).**

  * Yes, the preprocessing code is available in: https://github.com/BU-Spark/data-viz-ciss-doubled-up/blob/yijun/data/FA25_DataCleaning.ipynb

### Uses

* **What tasks has the dataset been used for so far? Please provide a description.**

  * The dataset has been used for:
    - Spatial visualization in Tableau
    - Demographic analysis at PUMA and State levels
    - Economic analysis (poverty metrics)
    - Intersectional analysis combining demographic and economic characteristics
    - Geographic mapping and spatial analysis

* **What (other) tasks could the dataset be used for?**

  * The dataset could be used for additional tasks if renter-related features are included, which would enable more in-depth analysis of economic status.

* **Is there anything about the composition of the dataset or the way it was collected and preprocessed/cleaned/labeled that might impact future uses?**

  * The column naming uses abbreviations optimized for Tableau, which may require a data dictionary for new users

* **Are there tasks for which the dataset should not be used? If so, please provide a description.**

  * None.

### Distribution
* **Based on discussions with the client, what access type should this dataset be given (eg., Internal (Restricted), External Open Access, Other)?**

  * Open Access.

### Maintenance
* **If others want to extend/augment/build on/contribute to the dataset, is there a mechanism for them to do so? If so, please provide a description.**

  * Yes, the link to a jupyter notebook to generate the dataset is: https://colab.research.google.com/drive/1H9SUC6cx-BCIhQ30XJrhLaLKZma-uCq2?usp=sharing

### Other
* **Is there any other additional information that you would like to provide that has not already been covered in other sections?**

  * None.
