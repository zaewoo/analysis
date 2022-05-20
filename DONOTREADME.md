<h1 align="center">프로젝트 기획안</h1>

<div align="Right">
    작성일자: 2022.05.19
    </br>
    수정일자: 2022.05.20
    </br>
    </br>
    박덕용 
    </br>
    한선아
    <br>
    박재우
</div>

## 외화 수입·유통 프로세스
![picture01 001-removebg](https://user-images.githubusercontent.com/97165359/169484913-e0d015c5-7e63-4e9a-a2c8-3ef1d38556b8.png)

## 개요

### 주제: 개봉 예정 영화 관객 수 예측
이 프로젝트의 주제는 머신러닝 모델을 이용하여 과거에 상영되었던 국내 영화 데이터의 다양한 특성을 학습하고 앞으로 상영이 예정되어 있는 국내 영화의 관객 수를 예측하는 것입니다.

### 목적: 개봉 예정 외화 관객 수 예측
이 프로젝트로 외국에 상영되었던, 혹은 외국에서 상영이 예정되어 있는 외국 영화 데이터의 다양한 특성을 입력하고 앞으로 국내에서 이를 개봉하였을 시 예상되는 영화의 관객 수를 예측할 수 있습니다.
그리고 외국으로부터 영화를 수입 및 배급하고 있는 회사가 이를 활용하여 외국에서 상영되었던, 혹은 외국에서 상영이 예정되어 있는 해외 영화의 수익성을 예상할 수 있습니다.

### 배경
외국으로부터 영화를 수입·배급하고 있는 회사의 구매 직원은 완성되지 않은 영화, 즉 영화의 감독, 배우, 시놉시스, 그리고 시나리오만을 보고 영화를 구매하고 있습니다. 그리고 이 영화의 구매에 대한 위험은 온전히 영화를 수입·배급하고 있는 회사에서 부담해야 합니다. 외국으로부터 영화를 수입·배급하고 있는 회사의 구매 직원은 도박에 가까운 심정으로 영화를 국내로 들여오고 있습니다. 이 밖에도 외국으로부터 영화를 수입·배급하고 있는 회사의 구매 직원은 영화제가 시작하기 전에 수백, 더 나아가 수천 편의 영화를 사전에 확인하고 영화제에 참석하여 아침부터 저녁까지 상영되고 있는 영화를 취사선택해 관람해야 합니다. 이처럼 어려운 환경 속에서 국내 관람객을 위해 고생하는 영화 수입·배급사의 구매 직원들이 보다 효과적으로, 그리고 효율적으로 영화를 선별할 수 있도록 도움을 드리기 위해 진행된 프로젝트입니다. 

추가적으로 영화진흥위원회에서 간행하고 있는 <월간 한국 영화>의 '팬데믹 시대, 신생 투자배급사를 점검하다'에서 팬데믹 이후 신생 투자·배급사, 그리고 중소 투자·배급사의 위기설에 대해 언급한 바 있습니다. 그 내용은 이들이 제작·투자한 영화들이 흥행에 실패했다는 내용입니다. 그러므로 투자·배급사는 영화의 투자·배급에 더욱 신중할 수밖에 없습니다.

<br/>

## 본문: 데이터

### 데이터: 개요

#### 1. IMDb
> Each dataset is contained in a gzipped, tab-separated-values (TSV) formatted file in the UTF-8 character set. The first line in each file contains headers that describe what is in each column. A ‘\N’ is used to denote that a particular field is missing or null for that title/name.

<div align="Right">
    Page Link: https://www.imdb.com/interfaces/
</div>

#### 2. KOBIS:KOREA Box-office Information System
> 이는 영화진흥위원회에서 매년 발표하는 한국영화연감(1971~2010)의 통계를 기준으로 정리한 데이터입니다. 한국영화연감은 2011년부터는 통합전산망을 기준으로 일정한 주기로 마감처리하여 산출되는 통계 정보입니다. 이 정보는 통계 마감 주기에 따라 공식통계 수치는 추후 변동될 수 있습니다. 추가적으로 전국 통계 데이터는 2004년 이후부터 배급사의 협조가 가능한 경우에만 부분적으로 집계되어 있습니다.

<div align="Right">
    Page Link: https://www.kobis.or.kr/kobis/business/main/main.do
</div>

### 데이터: 내용

#### 1. IMDb
공식 홈페이지에 있는 데이터에서 데이터의 범주가 '**영화**'인 데이터를 사용하였습니다. 전체 데이터는 약 61만 개이고, 전체 데이터의 컬럼은 11개입니다.

|Variable name|Variable description|
|------|---|
|tconst|alphanumeric unique identifier of the title|
|titleType|the type/format of the title (e.g. movie, short, tvseries, tvepisode, video, etc)|
|primaryTitle|the more popular title / the title used by the filmmakers on promotional materials at the point of release|
|originalTitle|original title, in the original language|
|isAdult|0: non-adult title; 1: adult title|
|startYear|represents the release year of a title. In the case of TV Series, it is the series start year|
|endYear|TV Series end year. ‘\N’ for all other title types|
|runtimeMinutes|primary runtime of the title, in minutes|
|genres|includes up to three genres associated with the title|
|averageRating|weighted average of all the individual user ratings|
|numVotes|number of votes the title has received|

#### 2. KOBIS:KOREA Box-office Information System
공식 홈페이지에서 '월별 박스오피스 조회 기간'을 설정하여 데이터를 수집하였습니다. 이 데이터는 2004년 01월 01일부터 2022년 05월 18일까지의 데이터를 포함하고 있습니다. 전체 데이터는 약 9만 개이고, 전체 데이터의 컬럼은 12개입니다.

|Variable name|Variable description|
|------|---|
|Daudience|Number of audiences on release day|
|A1audience|Number of audiences after release 1 week|
|A2audience|Number of audiences after release 2 weeks|
|Dscreen|Number of screens on release day|
|A1screen|Number of screens after release 1 week|
|A2screen|Number of screens after release 2 weeks|
|Nationality|Nationality(Domestic films, Foreign films)|
|Grade|Film rating(General, 12+, 15+, 18+)|
|Month|Release month(January-December)|
|Season|Release season(Spring, Summer, Autumn, Winter)|
|Dirscore|Director score|
|Actscore|Film star score|
|Distscore|Distributor score|

### 데이터: 분석

#### 1. IMDb
해당 데이터의 분석 내용을 작성해 주세요.

#### 2. KOBIS:KOREA Box-office Information System
해당 데이터의 분석 내용을 작성해 주세요.

<br/>

## 본문: 기계 학습

### 기계 학습: 의사결정나무
해당 모델의 결과를 작성해 주세요.

### 기계 학습: 다항 로지스틱 회귀분석
해당 모델의 결과를 작성해 주세요.

### 심화 학습: 다층 퍼셉트론
해당 모델의 결과를 작성해 주세요.

<br/>

## 결론

결론에 대해서 작성해 주세요.

<br/>

## 참고문헌

- Seonghyeon Jeona, Young Sook Sona(2016). Prediction of box office using data mining. The Korean Journal of Applied Statistics (2016), 29(7), 1257–1270
