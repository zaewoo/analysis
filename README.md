![âPngtreeâpure stage banner background_976453](https://user-images.githubusercontent.com/97165359/171340263-21df96d7-def2-4ec8-98bb-85408456122e.png)

<div align="Right">
    진행 기간: 2022.05.20-2022.05.26
    </br>
    </br>
    작성 일자: 2022.05.27
    </br>
    수정 일자: 2022.06.02
    </br>
    </br>
    박덕용 
    </br>
    한선아
    </br>
    박재우
</div>

## 목차

1. [개요](#개요)

    1.1. [주제](#주제)

    1.2. [목적](#목적)
    
    1.3. [결과](#결과)

2. [서론](#서론)

    2.1. [배경](#배경)

3. [본론: 데이터](#본론-데이터)

    3.1. [데이터: 개요](#데이터-개요)

    3.2. [데이터: 내용](#데이터-내용)

    3.3. [데이터: 전처리](#데이터-전처리)

4. [본론: 모델](#본론-모델)

    4.1. [모델: 개요](#모델-개요)
    
    4.2. [모델: 내용](#모델-내용)

    4.3. [모델: 실행](#모델-실행)

5. [결론](#결론)

6. [참고](#참고)

7. [기타](#기타)

## 개요

### 주제
이 프로젝트는 국내에서 상영되었던 영화로 개봉이 예정되어 있는 영화의 관객 수를 예측하는 프로젝트입니다. 

### 목적
이 프로젝트로 외국에서 상영되었던, 혹은 외국에서 개봉이 예정되어 있는 영화가 국내에서 개봉하였을 때의 영화 관객 수를 예측할 수 있습니다. 이를 활용하여 외국으로부터 영화를 수입·배급하고 있는 회사가 외국에서 상영되었던, 혹은 외국에서 개봉이 예정되어 있는 영화의 수익성을 분석할 수 있습니다. 

### 결과
결과에 대해서 서술해 주세요.

## 서론

### 배경

![picture02 001](https://user-images.githubusercontent.com/97165359/169933472-fc638d5c-823c-4105-977b-4b1de44c8cb7.jpeg)

외국으로부터 영화를 수입·배급하고 있는 회사는 완성되지 않은 영화, 즉 영화의 감독, 배우, 시놉시스, 그리고 시나리오만을 갖고 영화를 구매합니다. 구매에 대한 위험은 온전히 영화를 수입·배급하고 있는 회사에서 부담해야 합니다. 그리고 외국으로부터 영화를 수입·배급하고 있는 회사는 영화제가 시작하기 전에 수백, 더 나아가 수천 편의 영화를 사전에 확인해야 합니다. 이들은 영화제에 참석하여 아침부터 저녁까지 상영하고 있는 영화를 선별해서 관람해야 합니다. 이처럼 국내 관람객을 위해 외화를 수입·배급하고 있는 이들이 보다 효율적으로 영화를 선별할 수 있도록 도움을 드리기 위해 진행하는 프로젝트입니다. 

더 나아가 영화진흥위원회에서 간행하고 있는 <월간 한국 영화>의 ['팬데믹 시대, 신생 투자배급사를 점검하다'](https://www.kofic.or.kr/kofic/business/rsch/findPublishIndexInfoDetail.do?boardNumber=40&flag=1&pubSeqNo=2944&idxSeqNo=6896)에서는 팬데믹 이후 신생 투자·배급사, 그리고 중소 투자·배급사의 위기설에 대해 언급한 바 있습니다. 그 내용은 이들이 제작·투자한 영화들이 팬데믹으로 인해 흥행에 실패했다는 내용입니다. 그러므로 투자·배급사는 영화의 투자·배급에 더욱 신중할 수밖에 없습니다. [더보기](https://github.com/zaewoo/project/blob/master/CONTEXT.md)

## 본론: 데이터

### 데이터: 개요

#### 1. IMDb
> Each dataset is contained in a gzipped, tab-separated-values (TSV) formatted file in the UTF-8 character set. The first line in each file contains headers that describe what is in each column. A ‘\N’ is used to denote that a particular field is missing or null for that title/name.

<div align="Right">
    Page Link: https://www.imdb.com/interfaces/
</div>

#### 2. KOBIS:KOREA Box-office Information System
> 영화진흥위원회에서 매년 발표하는 한국영화연감(1971~2010)의 통계를 기준으로 정리한 데이터입니다. 한국영화연감은 2011년부터는 통합전산망을 기준으로 일정한 주기로 마감처리하여 산출되는 통계 정보입니다. 이 정보는 통계 마감 주기에 따라 공식통계 수치는 추후 변동될 수 있습니다. 추가적으로 전국 통계 데이터는 2004년 이후부터 배급사의 협조가 가능한 경우에만 부분적으로 집계되어 있습니다.

<div align="Right">
    Page Link: https://www.kobis.or.kr/kobis/business/main/main.do
</div>

#### 3. KOFIC:KOREA Film Council
> 영화진흥위원회 영화관 입장권 통합 전산망에서 제공하는 오픈API 서비스입니다. 이 사이에서 [영화 목록 조회 API 서비스](http://www.kobis.or.kr/kobisopenapi/homepg/apiservice/searchServiceInfo.do)를 이용하였습니다. 이는 영화진흥위원회가 제공하는 통합전산망에서 제공하는 영화 목록을 영화명, 감독명등의 조건으로 조회할 수 있는 서비스입니다.

<div align="Right">
    Page Link: https://www.kobis.or.kr/kobisopenapi/homepg/main/main.do
</div>

### 데이터: 내용

#### 1. IMDb
공식 홈페이지에 있는 데이터에서 데이터의 범주가 **영화**인 데이터를 사용하였습니다. 

#### 1.1. Details & Ratings
이 데이터는 1896년 01월 01일부터 2029년 12월 31일까지의 데이터를 포함하고 있습니다. 전체 데이터는 약 61만 개이고, 전체 데이터의 컬럼은 11개입니다.

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
공식 홈페이지에서 **월별 박스오피스 조회 기간**을 설정하여 데이터를 수집하였습니다.

#### 2.1. Audience
이 데이터는 2004년 01월 01일부터 2022년 05월 18일까지의 데이터를 포함하고 있습니다. 전체 데이터는 약 2만 개이고, 전체 데이터의 컬럼은 25개입니다.

|Variable name|Variable description|
|-----|-----|
|movieCd|영화 고유번호|
|movieNm|영화 제목|
|movieNmEn|영화 제목(영문)|
|prdtYear|영화 제작년도|
|openDt|영화 개봉일자|
|showTm|영화 러닝타임|
|prdtStatNm|영화 제작 상태|
|typeNm|영화 분류|
|nationNm|영화 제작 국가|
|genres_1|영화 장르|
|genres_2|영화 장르|
|directorNmEn|영화 감독(영문)|
|actor_1|영화 배우|
|actor_2|영화 배우|
|actor_3|영화 배우|
|prod_companyCd|영화 제작 회사 고유번호|
|prod_companyNm|영화 제작 회사 명칭|
|prod_companyNmEn|영화 제작 회사 명칭(영문)|
|dist_companyCd|영화 배급 회사 고유번호|
|dist_companyNm|영화 배급 회사 명칭|
|dist_companyNmEn|영화 배급 회사 명칭(영문)|
|imp_companyCd|영화 수입 회사 고유번호|
|imp_companyNm|영화 수입 회사 명칭|
|imp_companyNmEn|영화 수입 회사 명칭(영문)|
|is_adult|영상물 심의 등급|

#### 2.2. Details
이 데이터는 2004년 01월 01일부터 2021년 12월 31일까지의 데이터를 포함하고 있습니다. 전체 데이터는 약 2만 개이고, 전체 데이터의 컬럼은 6개입니다.

|Variable name|Variable description|
|------|---|
|movieNm|영화 제목|
|openDt|영화 개봉일자|
|acc_revenue|영화 매출액|
|acc_view|영화 관객 수|
|screen_cnt|영화 상영관 수|
|show_cnt|영화 상영 횟수|

### 데이터: 전처리
처음으로는 영화의 누적 관객 수를 포함하고 있는 데이터(2.1. Audience), 그리고 영화의 정보를 포함하고 있는 데이터(2.2. Details) 모두 필요하므로 이 둘을 공통된 컬럼을 기준으로 병합하였습니다. 이 때 공통된 컬럼은 각 데이터 테이블에 존재하는 **movieNm**, **openDt**이고, 기준이 되는 데이터 테이블에 병합한 컬럼은 **acc_view**입니다. 이 과정에서 구글 클라우드에서 제공하는 SQL을 활용하였습니다. 이로써 국내에서 상영되었던 영화의 정보, 그리고 그 영화의 누적 관객 수가 포함되어 있는 데이터 테이블을 구성할 수 있었습니다. 전체 데이터는 약 1만 5천 개이고, 전체 데이터의 컬럼은 11개입니다.

다음으로는 전체 데이터에서 각 컬럼을 기준으로 적용된 전처리 기준에 대해서 설명하겠습니다.

#### genreNm
이 컬럼은 해당 영화의 장르를 나타내는 컬럼입니다. 이 컬럼에서는 범주, 즉 영화의 장르를 간소화하였습니다. 전체 데이터는 여러 가지 영화 장르가 포함되어 있습니다. 

우선 영화의 장르가 **공연**으로 되어 있는 영화는 모두 제거하였습니다. 그 이유는 이 장르의 영화는 대부분 무대에서 펼쳐지는 연극이었습니다. 그리고 이 프로젝트에서 다루고 있는 수입·배급사가 관심을 갖고 있는 장르가 아니라고 생각했기 때문입니다. 이 과정에서 제거된 데이터는 263개입니다. 

다음으로 네이버가 운영하는 영화 정보 서비스 상 상단에 노출되지 않는 영화 장르는 상단에 노출되는 영화 장르(이하 주요 장르)로 변환하였습니다. 전체 데이터에서 영화 장르를 나타내는 컬럼은 메인 장르, 그리고 서브 장르로 구성되어 있습니다. 그리고 이 두 컬럼을 갖고 데이터 전처리를 실행하였습니다. 그 방법은 전체 데이터에서 서브 장르가 주요 장르에 해당하는 경우에는 서브 장르를 메인 장르로 변환하였습니다. 메인 장르, 그리고 서브 장르 모두 주요 장르에 해당하지 않는 경우에는 [네이버 영화](https://movie.naver.com), [다음 영화](https://movie.daum.net/main), [왓챠피디아](https://pedia.watcha.com/ko-KR/), [IMDB](https://imdb.com), [Rotten Tomatoes](https://www.rottentomatoes.com), [Youtube](https://www.youtube.com) 등에서 장르를 확인하고 주요 장르로 변환하였습니다. 그 밖에 장르를 확인할 수 없는 영화는 제거하였습니다.

#### companys·directorNm·actor
해당 컬럼을 기준으로는 각 컬럼마다 가장 먼저 등장하는 데이터를 추출하였습니다. 구체적으로 영화 배우가 '매튜 맥커너히', '앤 해서웨이', '마이클 케인'으로 기재되어 있으면, 그 중에서 가장 먼저 등장하는 배우 '매튜 맥커너히'를 대표 배우로 선정하였습니다. 그 외 공동 배급·수입사, 다수의 영화 감독이 영화를 감독했다면 동일한 기준으로 전처리하였습니다. 

#### acc_view
해당 컬럼을 기준으로는 영화의 관객 수가 1,000명이 되지 않는 영화는 제거하였습니다. 그리고 관객 수를 카데고리 별로 분류하였습니다. 

||1|2|3|4|5|6|7|8|
|--|--|--|--|--|--|--|--|--|
|영화 관객 수|<10,000|<100,000|<200,000|<400,000|<600,000|<800,000|<1,000,000|≥1,000,000|

#### showTm
해당 컬럼을 기준으로는 영화의 러닝 타임이 제공되지 않는 영화는 제거하였습니다.

#### companys
해당 컬럼을 기준으로는 영화 배급·수입사가 제공되지 않는 영화는 제거하였습니다.

#### directorNm
해당 컬럼을 기준으로는 영화 감독이 제공되지 않는 영화는 제거하였습니다.

#### actor
해당 컬럼을 기준으로는 영화 배우가 제공되지 않는 영화는 네이버 영화 등을 확인하고 추가하였습니다. 그 밖에 애니메이션 장르의 영화는 영화 배우, 혹은 성우가 포함되지 않은 경우가 많았기 때문에 네이버 영화 등을 확인하고 추가하였습니다. 

#### nations
해당 컬럼을 기준으로는 영화 제공 국가를 **한국**, **미국**, **그 외**로 분류하였습니다. 그 이유는 영화진흥위원회에서 발간한 **한국영화연감**에 의하면 국내에서 상영된 영화 중에서 한국 영화의 관객 점유율은 51.4%로 가장 높았고, 미국 영화의 관객 점유율은 41.1%를 기록했습니다. 이 둘을 합한 점유율은 92.5%로 국내 대다수를 차지하고 있습니다. 그러므로 그 외 국가에서 개봉된 영화는 **그 외**로 분류하였습니다. 이는 2018년 자료를 기준으로 하였습니다.

<details>
    <summary>더보기</summary>
    
![스크린샷 2022-06-01 오후 6 34 10](https://user-images.githubusercontent.com/97165359/171374273-98d83da1-6556-481f-9b4a-f0ce05b96737.png)
![스크린샷 2022-06-01 오후 6 36 26](https://user-images.githubusercontent.com/97165359/171374720-2fefdf20-4c47-4cad-b052-09063cbec7e7.png)
![스크린샷 2022-06-01 오후 6 36 44](https://user-images.githubusercontent.com/97165359/171374793-14f02119-a15a-4c5c-a63b-ea095f372dec.png)
    
<div align="Right">
    출처 : 연도별 한국영화연감(영화진흥위원회)
    </br>
    통계생산기관 : 문화체육관광부, 영상콘텐츠산업과
    </br>
    통계주기 : 매년
</div>

</details>

#### audits
해당 컬럼을 기준으로는 영상물 등급 위원회에서 정한 바에 따라 청소년 관람불가, 그 외로 분류하였습니다.

#### openDt
해당 컬럼을 기준으로는 별도의 전처리가 필요하지 않았습니다. 그 밖에 구체적인 데이터 분석을 위해서 이 데이터를 활용하여 **월 단위**의 컬럼을 새로이 만들었습니다.

## 본론: 모델

### 모델: 개요
이 과정에서 총 다섯 번의 시도를 하였습니다. 다섯 번의 시도 끝에 성능이 가장 좋은 모델은 **(1)Decision Tree Classifier, (2)XGB Classifier**이고, 모델의 성능은 약 74%의 정확도를 갖습니다. 

#### 특성
각 시도마다 동일한 특성을 사용하였습니다. 구체적으로 영화 상영 시간, 영화 수입·배급사, 영화 장르, 영상물 심의 등급, 영화 개봉 월, 영화 배우, 영화 감독을 특성으로 선정했습니다. 

#### 데이터 분류
학습에 사용되는 데이터는 전체 데이터의 70%를 사용하였고, 테스트에 사용되는 데이터는 전체 데이터의 30%를 사용하였습니다. 

#### 학습 모델
학습 모델은 학습에 사용되는 데이터로 구할 수 있는 정확도, 그리고 테스트에 사용되는 데이터로 구할 수 있는 정확도를 비교하여 우수한 모델로 채택했습니다. 데이터의 크기가 작았기 때문에 모델을 사용하는 데에 소요되는 시간은 학습 모델의 성능 평가 요소로 적용시키지 않았습니다. 아래는 이 프로젝트에서 사용한 학습 모델입니다.

- Logistic Regression
- Decision Tree Classifier
- Random Forrest Classifier
- LGBM
- Boosting → 3가지 방법

### 모델: 내용

### 모델: 실행

## 결론
결론에 대해서 서술해 주세요.

## 참고
[1] Seonghyeon Jeona, Young Sook Sona(2016). Prediction of box office using data mining. The Korean Journal of Applied Statistics (2016), 29(7), 1257–1270.

[2] Woosik Lee(2017). A deep learning analysis of the KOSPI's directions. Journal of the Korean Data & Information Science Society (2017), 28(2), 287-295.

[3] Kwak, M. and Rhee, S(2016). Finding factors on employment by adult life cycle using decision tree model. Journal of the Korean Data & Information Science Society, 27, 1537-1545.

[4] Mu-Seon Lee(2016). Analysis on the Factors Affecting Housing Tenure of Single-Person Households of Young Generation Employing the Multinomial Logit Model. Journal of the Korean Academia-Industrial cooperation Society Vol 17. No.6. pp.469-481.

[5] Y.Choi, Y.K.Kang, Analysis on the Preference against the Residential-building Forms in Multi-familiy Attached House Employing The Multinomial Logit Model, Journal of Architectual Institute of Korea, Vol 24. No.12. pp.57-65, 2008.

[6] 최종후, 서두성(1999). 데이터마이닝 의사결정나무의 응용. 통계청 「통계분석연구」 제4권 제1호(99.봄). 61-83.

[7] 이용규, 고형일, 이일병(2014). 객체의 분류를 위한 효율적인 다층 퍼셉트론의 설계 및 구조에 관한 연구. 2014년 추계학습발표대회 논문집 제21권 제2호 (2014.11). 803-805.

[8] 왕빈신, 전범수(2016). 한국 개봉 미국 제외 외국 영화 흥행 결정 요인. The Journal of the Korea Contents Association Vol 16. Issue 2. pp.96-105.

[9] 조광현, 박희창(2011). 매개 변수를 이용한 의사결정나무 생성에 관한 연구. Journal of the Korean Data & Information Science Society, 22(4), 671-678.

[10] 홍수민. [COVER STORY] 팬데믹 시대, 신생 투자배급사를 점검하다. <월간 한국영화>. September 30, 2021.

## 기타
[1] 사진 출처: https://pngtree.com/free-backgrounds
