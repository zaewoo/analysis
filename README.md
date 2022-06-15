<img width="1440" alt="스크린샷 2022-06-06 오후 8 57 44" src="https://user-images.githubusercontent.com/97348375/172156376-1c7332a2-86a4-465a-947a-526c6e87e355.png">


<div align="Right">
    진행 기간: 2022.05.20-2022.05.26
    </br>
    </br>
    작성 일자: 2022.05.27
    </br>
    수정 일자: 2022.06.14
    </br>
    </br>
    박덕용 
    </br>
    한선아
    </br>
    박재우
</div>

## 목차

1. [개요](#1-개요)

    1.1. [주제](#11-주제)

    1.2. [목적](#12-목적)
    
    1.3. [결과](#13-결과)

2. [서론](#2-서론)

    2.1. [배경](#21-배경)

3. [본론: 데이터](#3-본론-데이터)

    3.1. [데이터: 개요](#31-데이터-개요)

    3.2. [데이터: 내용](#32-데이터-내용)

    3.3. [데이터: 전처리](#33-데이터-전처리)

    3.4. [데이터: 정리](#34-데이터-정리) 

4. [본론: 모델](#4-본론-모델)

    4.1. [모델: 개요](#41-모델-개요)
    
    4.2. [모델: 내용](#42-모델-내용)

    4.3. [모델: 실행](#43-모델-실행)
    
    4.4. [모델: 정리](#44-모델-정리)

5. [본론: 분석](#5-본론-분석)

    5.1. [분석: 정확도](#51-분석-정확도)

6. [결론](#5-결론)
    
    6.1. [결론: 데이터](#61-결론-데이터)
    
    6.2. [결론: 모델](#62-결론-모델)

    6.3. [결론: 결과](#63-결론-결과)

7. [참고](#참고)

8. [기타](#기타)

## 1. 개요

### 1.1. 주제
이 프로젝트는 국내에서 상영했었던 영화로 개봉이 예정되어 있는 영화의 관객 수를 예측하는 프로젝트입니다. 

### 1.2. 목적
이 프로젝트로 외국에서 상영했었던, 혹은 외국에서 개봉이 예정되어 있는 영화가 국내에서 개봉하였을 때의 영화 관객 수를 예측할 수 있습니다. 이를 활용하여 외국으로부터 영화를 수입·배급하고 있는 회사가 외국에서 상영했었던, 혹은 외국에서 개봉이 예정되어 있는 영화의 수익성을 분석할 수 있습니다. 

### 1.3. 결과
결과에 대해서 서술해 주세요.

## 2. 서론

### 2.1. 배경
![picture02 001](https://user-images.githubusercontent.com/97165359/169933472-fc638d5c-823c-4105-977b-4b1de44c8cb7.jpeg)

외국으로부터 영화를 수입·배급하고 있는 회사는 완성되지 않은 영화, 즉 영화의 감독, 배우, 시놉시스, 그리고 시나리오만을 갖고 영화를 구매합니다. 구매에 대한 위험은 온전히 영화를 수입·배급하고 있는 회사에서 부담해야 합니다. 그리고 외국으로부터 영화를 수입·배급하고 있는 회사는 영화제가 시작하기 전에 수백, 더 나아가 수천 편의 영화를 사전에 확인해야 합니다. 이들은 영화제에 참석하여 아침부터 저녁까지 상영하고 있는 영화를 선별해서 관람해야 합니다. 이처럼 국내 관객을 위해 외화를 수입·배급하고 있는 이들이 보다 효율적으로 영화를 선별할 수 있도록 도움을 드리기 위해 진행하는 프로젝트입니다. 

더 나아가 영화진흥위원회에서 간행하고 있는 <월간 한국 영화>의 ['팬데믹 시대, 신생 투자배급사를 점검하다'](https://www.kofic.or.kr/kofic/business/rsch/findPublishIndexInfoDetail.do?boardNumber=40&flag=1&pubSeqNo=2944&idxSeqNo=6896)에서는 팬데믹 이후 신생 투자·배급사, 그리고 중소 투자·배급사의 위기설에 대해 언급한 바 있습니다. 그 내용은 이들이 제작·투자한 영화들이 팬데믹으로 인해 흥행에 실패했다는 내용입니다. 그러므로 투자·배급사는 영화의 투자·배급에 더욱 신중할 수밖에 없습니다. [더보기](https://github.com/zaewoo/project/blob/master/CONTEXT.md)

## 3. 본론: 데이터

### 3.1. 데이터: 개요

#### 3.1.1. IMDb
> Each dataset is contained in a gzipped, tab-separated-values (TSV) formatted file in the UTF-8 character set. The first line in each file contains headers that describe what is in each column. A ‘\N’ is used to denote that a particular field is missing or null for that title/name.

<div align="Right">
    Page Link: https://www.imdb.com/interfaces/
</div>

#### 3.1.2. KOBIS:KOREA Box-office Information System
> 영화진흥위원회에서 매년 발표하는 한국영화연감(1971~2010)의 통계를 기준으로 정리한 데이터입니다. 한국영화연감은 2011년부터는 통합전산망을 기준으로 일정한 주기로 마감처리하여 산출되는 통계 정보입니다. 이 정보는 통계 마감 주기에 따라 공식통계 수치는 추후 변동될 수 있습니다. 추가적으로 전국 통계 데이터는 2004년 이후부터 배급사의 협조가 가능한 경우에만 부분적으로 집계되어 있습니다.

<div align="Right">
    Page Link: https://www.kobis.or.kr/kobis/business/main/main.do
</div>

#### 3.1.3. KOFIC:KOREA Film Council
> 영화진흥위원회 영화관 입장권 통합 전산망에서 제공하는 오픈API 서비스입니다. 이 사이에서 [영화 목록 조회 API 서비스](http://www.kobis.or.kr/kobisopenapi/homepg/apiservice/searchServiceInfo.do)를 이용하였습니다. 이는 영화진흥위원회 영화관 입장권 통합 전산망에서 사용되는 영화 목록을 영화 제목, 영화 감독 이름 등의 조건으로 조회할 수 있는 서비스입니다.

<div align="Right">
    Page Link: https://www.kobis.or.kr/kobisopenapi/homepg/main/main.do
</div>

### 3.2. 데이터: 내용

#### 3.2.1. IMDb
공식 홈페이지에 있는 데이터에서 데이터의 범주가 **영화**인 데이터를 사용하였습니다. 

#### 3.2.1.1. Details & Ratings
이 데이터는 1896년 01월 01일부터 2029년 12월 31일까지의 데이터를 포함하고 있습니다. 전체 데이터는 약 61만 개이고, 전체 데이터의 컬럼은 11개입니다.

<div align="Center">

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
    
</div>

#### 3.2.2. KOBIS:KOREA Box-office Information System
공식 홈페이지에서 **월별 박스오피스 조회 기간**을 설정하여 데이터를 수집하였습니다.

#### 3.2.2.1. Details
이 데이터는 2004년 01월 01일부터 2021년 12월 31일까지의 데이터를 포함하고 있습니다. 전체 데이터는 약 2만 개이고, 전체 데이터의 컬럼은 25개입니다.

<div align="Center">

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

</div> 

#### 3.2.2.2. Audience
이 데이터는 2004년 01월 01일부터 2022년 05월 18일까지의 데이터를 포함하고 있습니다. 전체 데이터는 약 2만 개이고, 전체 데이터의 컬럼은 6개입니다.

<div align="Center">
    
|Variable name|Variable description|
|------|---|
|movieNm|영화 제목|
|openDt|영화 개봉일자|
|acc_revenue|영화 매출액|
|acc_view|영화 관객 수|
|screen_cnt|영화 상영관 수|
|show_cnt|영화 상영 횟수|
    
</div>

### 3.3. 데이터: 전처리
영화의 누적 관객 수를 포함하고 있는 데이터(3.2.2.2. Audience), 그리고 영화의 정보를 포함하고 있는 데이터(3.2.2.1. Details) 모두 필요하므로 이 둘을 공통된 컬럼을 기준으로 병합하였습니다. 이 때 공통된 컬럼은 각 데이터에 존재하는 **movieNm**, **openDt**이고, 기준이 되는 데이터에 병합한 컬럼은 **acc_view**입니다. 이 과정에서 구글 클라우드에서 제공하는 SQL을 이용하였습니다. 이로써 국내에서 상영되었던 영화의 정보, 그리고 그 영화의 누적 관객 수가 포함되어 있는 전체 데이터를 구성할 수 있었습니다. 전체 데이터는 약 1만 5천 개이고, 전체 데이터의 컬럼은 11개입니다.

다음은 전체 데이터에서 각 컬럼을 기준으로 적용된 전처리에 관한 설명입니다.

#### 3.3.1. 영화 장르
이 컬럼에서는 범주, 즉 영화의 장르를 간소화하였습니다. 전체 데이터에는 여러 가지 영화 장르가 있습니다. 이 프로젝트에서 사용한 영화의 장르는 **드라마/가족**, **액션**, **스릴러**, **코미디**, **멜로/로맨스**, **공포(호러)**, **다큐멘터리**, **범죄**, **애니메이션**입니다. 

다음은 전체 데이터에서 영화의 장르를 기준으로 적용된 전처리에 관한 상세 설명입니다. 

네이버가 운영하는 영화 정보 서비스 상 상단에 노출되지 않는 영화 장르는 상단에 노출되는 영화 장르(이하 주요 장르)로 변환하였습니다. 단, 전체 데이터에서 영화의 장르가 **모험**인 영화는 주요 장르에 해당되지만 데이터의 수가 적고, 영화의 장르가 **다큐멘터리**인 영화, 그리고 영화의 장르가 **범죄**인 영화는 주요 장르에 해당되지 않지만 데이터의 수가 많습니다. 그러므로 영화의 장르가 **모험**인 영화는 그 외 주요 장르로 변환해 주었고, 영화의 장르가 **다큐멘터리**, 그리고 **범죄**인 영화는 주요 장르로 보았습니다. 전체 데이터에서 영화 장르를 나타내는 컬럼은 메인 장르, 그리고 서브 장르로 구성되어 있습니다. 그리고 이 두 컬럼을 갖고 데이터 전처리하였습니다. 그 방법은 전체 데이터에서 메인 장르가 주요 장르에 해당하지 않고 서브 장르가 주요 장르에 해당하는 경우에는 서브 장르를 메인 장르로 변환하였습니다. 메인 장르, 그리고 서브 장르 모두 주요 장르에 해당하지 않는 경우에는 [네이버 영화](https://movie.naver.com), [다음 영화](https://movie.daum.net/main), [왓챠피디아](https://pedia.watcha.com/ko-KR/), [IMDB](https://imdb.com), [Rotten Tomatoes](https://www.rottentomatoes.com), [Youtube](https://www.youtube.com) 등에서 영화의 장르를 확인하고 주요 장르로 변환하였습니다. 그 밖에 장르를 확인할 수 없는 영화는 제거하였습니다.

아래의 자료는 네이버의 [영화 정보 서비스](https://movie.naver.com/movie/sdb/browsing/bmovie_genre.naver) 상 상단에 노출되는 영화 장르입니다.

<details>
    <summary>더보기</summary>

<div align="Center">
    
![picture](https://user-images.githubusercontent.com/97165359/172034528-aaf26a95-7892-4c18-9e0b-bf581b62a51c.PNG)
    
</div>
    
</details>
    
#### 3.3.2. 영화 배급·수입사 · 영화 감독 · 영화 배우
이 컬럼에서는 필요하지 않은 컬럼을 제거하였습니다. 그 방법은 다음의 표와 함께 설명하고 있습니다.

</br>

<div align="Center">
    
||영화 제목|영화 배우|영화 배우|영화 배우|
|:--:|--|--|--|--|
|1|인터스텔라|매튜 맥커너히|앤 해서웨이|마이클 케인|
    
</div>

</br>

영화 제목이 **인터스텔라**인 영화의 영화 배우는 **매튜 맥커너히**, **앤 해서웨이**, **마이클 케인**으로 기재되어 있습니다. 이 중에서 가장 처음으로 등장하는 영화 배우 **매튜 맥커너히**를 해당 영화의 대표 배우로 하였습니다. 그 외에도 공동 배급·수입사, 다수의 영화 감독이 해당 영화를 제작하는 데에 관여하였다면 동일한 기준을 적용하였습니다.

#### 3.3.3. 영화 관객 수
이 컬럼에서는 영화의 관객 수가 1,000명이 되지 않는 영화는 모두 제거하였습니다. 그리고 영화의 관객 수를 카테고리 별로 분류하였습니다.

</br>

<div align="Center">

||1|2|3|4|5|6|7|8|
|:--:|--|--|--|--|--|--|--|--|
|영화 관객 수|< 10,000|< 100,000|< 500,000|< 1,000,000|< 3,000,000|< 7,000,000|< 10,000,000|≥ 10,000,000|
                                                                                 
</div>
    
</br>

#### 3.3.4. 영화 러닝 타임
이 컬럼에서는 영화의 러닝 타임이 제공되지 않는 영화는 모두 제거하였습니다. 

#### 3.3.5. 영화 배급·수입사
이 컬럼에서는 영화의 제작에 관여한 배급·수입사가 제공되지 않는 영화는 모두 제거하였습니다. 

#### 3.3.6. 영화 감독
이 컬럼에서는 영화의 제작에 관여한 영화 감독이 제공되지 않는 영화는 모두 제거하였습니다. 

#### 3.3.7. 영화 배우
이 컬럼에서는 영화의 제작에 관여한 영화 배우가 제공되지 않는 영화는 [네이버 영화](https://movie.naver.com), [다음 영화](https://movie.daum.net/main), [왓챠피디아](https://pedia.watcha.com/ko-KR/), [IMDB](https://imdb.com), [Rotten Tomatoes](https://www.rottentomatoes.com) 등에서 확인하고 추가하였습니다. 특히 애니메이션 장르의 영화는 영화 배우·성우 등이 포함되지 않은 경우가 많았기 때문에 이 역시 위의 사이트를 확인하고 추가하였습니다. 

#### 3.3.8. 국가
이 컬럼에서는 범주, 즉 영화 제작 국가를 간소화하였습니다. 전체 데이터에는 여러 국가가 포함되어 있습니다. 그 방법은 영화를 제작한 국가를 크게 **한국**, **미국**, **그 외 국가**로 분류하였습니다. 그 이유는 다음과 같습니다. 영화진흥위원회에 발간한 **한국영화연감**에 의하면 국내에서 상영된 영화 중에서 한국 영화의 관객 점유율은 51.4%로 가장 높았고, 미국 영화의 관객 점유율은 41.1%를 기록했습니다. 이 둘을 합한 점유율은 92.5%로 국내 관객의 다수를 차지하고 있습니다. 그 외 국가에서 개봉된 영화는 영화 관객 점유율이 현저히 낮습니다. 그러므로 **한국**, **미국**, 그리고 **그 외 국가**로 분류하였습니다. 이는 영화진흥위원회에서 발간한 **한국영화연감**의 자료를 기준으로 하였습니다. 이 자료는 가장 최신의 자료이고 그 기준년도는 2018년입니다.
    
아래에는 영화진흥위원회에서 발간한 **한국영화연감**의 자료를 일부 발췌한 내용입니다.
    
<details>
    <summary>더보기</summary>

<div align="Center">
    
![스크린샷 2022-06-01 오후 6 34 10](https://user-images.githubusercontent.com/97165359/171374273-98d83da1-6556-481f-9b4a-f0ce05b96737.png)
![스크린샷 2022-06-01 오후 6 36 26](https://user-images.githubusercontent.com/97165359/171374720-2fefdf20-4c47-4cad-b052-09063cbec7e7.png)
![스크린샷 2022-06-01 오후 6 36 44](https://user-images.githubusercontent.com/97165359/171374793-14f02119-a15a-4c5c-a63b-ea095f372dec.png)
    
</div>
    
<div align="Right">
    출처 : 연도별 한국영화연감(영화진흥위원회)
    </br>
    통계생산기관 : 문화체육관광부, 영상콘텐츠산업과
    </br>
    통계주기 : 매년
</div>

</details>

#### 3.3.9. 영상물 심의 등급
이 컬럼에서는 영상물 등급 위원회에서 정한 바에 따라 청소년 관람불가, 그 외로 분류하였습니다. 

#### 3.3.10. 영화 개봉 일자
이 컬럼에서는 별도의 전처리가 필요하지 않았습니다. 그 밖에 구체적인 데이터 분석을 위해서 이 데이터를 활용하여 **월 단위**의 컬럼을 새로이 만들었습니다.

### 3.4. 데이터: 정리
전체 데이터는 약 7천 개이고, 전체 데이터의 컬럼은 9개입니다. 그 중에서 학습 모델에 사용할 데이터는 아래의 표와 같습니다. 그리고 학습 모델이 예측해야 할 정답은 영화의 관객 수이고 그 형태는 범주형 데이터입니다.

</br>

<div align="Center">
 
|Variable name|Variable description|
|------|---| 
|runTm|영화 러닝타임|
|openMonth|영화 개봉월|    
|nations|영화 제작 국가|
|genre|영화 장르|
|directors|영화 감독|
|actors|영화 배우|
|is_adult|영상물 심의 등급|
|distributor|영화 배급·수입사| 

</br>

|Variable name|Variable description|
|------|---| 
|acc_view|영화 관객 수|

</div>

</br>

## 4. 본론: 모델

### 4.1. 모델: 개요
학습 모델은 학습 데이터로 구할 수 있는 정확도, 그리고 테스트 데이터로 구할 수 있는 정확도를 상호 비교하여 서로 간의 차이가 적고 정확도가 가장 우수한 모델을 채택하였습니다. 전체 데이터의 크기가 작았기 때문에 학습 모델을 사용하는 데에 소요되는 시간은 학습 모델의 성능 평가 요소로 적용시키지 않았습니다. 다음은 이 프로젝트에서 사용한 학습 모델입니다. 

- Logistic Regression
- Decision Tree Classifier
- Random Forrest Classifier
- LGBM
- GradientBoost
- GridSearchCV
- XGBoost
- AdaptiveBoost

학습 모델의 성능은 총 다섯 번의 시도를 거쳐 개선하였습니다. 학습 모델에서 성능이 가장 우수한 학습 모델은 **(1)GradientBoost**, **(2)GridSearchCV**입니다. 두 학습 모델의 성능은 약 75%의 정확도를 갖습니다. 학습 모델에서 가장 중요한 특성은 **영화 감독**입니다.

### 4.2. 모델: 내용
각 시도마다 동일한 특성을 사용하였습니다. 구체적으로 영화 상영 시간, 영화 수입·배급사, 영화 장르, 영상물 심의 등급, 영화 개봉일자(월), 영화 배우, 영화 감독을 특성으로 사용했습니다. 학습에 사용되는 데이터는 전체 데이터의 70%를 사용하였고, 테스트에 사용되는 데이터는 전체 데이터의 30%를 사용하였습니다. 
    
### 4.3. 모델: 실행

#### 4.3.1. 모델: 특성
아래의 표는 데이터의 특성을 처리하는 방법에 관한 표입니다.

</br>

|Features|Description|Trial 1|Trial 2|Trial 3|Trial 4|Trial 5|
|:--------:|:-----------:|:-------:|:-------:|:-------:|:-------:|:-------:|
|runTm|영화 러닝타임|MinMaxScaler|MinMaxScaler|MinMaxScaler|MinMaxScaler|MinMaxScaler|
|nation|영화 제작 국가|LabelEncoding|LabelEncoding|LabelEncoding|LabelEncoding|LabelEncoding|
|genre|영화 장르|LabelEncoding|LabelEncoding|장르 전체 관객 수의 중앙값 → MinMaxScaler|장르 전체 관객 수의 평균값 → MinMaxScaler|장르 전체 관객 수의 중앙값 → MinMaxScaler|
|director|영화 감독|LabelEncoding|영화 감독 전체 관객 수의 중앙값 → MinMaxScaler|영화 감독 전체 관객 수의 중앙값 → MinMaxScaler|영화 감독 전체 관객 수의 평균값 → MinMaxScaler|영화 감독 전체 관객 수의 중앙값 → MinMaxScaler|
|actor|영화 배우|LabelEncoding|영화 배우 전체 관객 수의 중앙값 → MinMaxScaler|영화 배우 전체 관객 수의 중앙값 → MinMaxScaler|영화 배우 전체 관객 수의 평균값 → MinMaxScaler|영화 배우 전체 관객 수의 중앙값 → MinMaxScaler|
|is_adult|영상물 심의 등급|-|-|-|-|-|
|distributor|영화 배급·수입사|LabelEncoding|영화 배급·수입사 전체 관객 수의 중앙값 → MinMaxScaler|영화 배급·수입사 전체 관객 수의 중앙값 → MinMaxScaler|영화 배급·수입사 전체 관객 수의 평균값 → MinMaxScaler|영화 배급·수입사 전체 관객 수의 중앙값 → MinMaxScaler|
|openMonth|영화 개봉일자(월)|LabelEncoding|LabelEncoding|영화 개봉일자(월) 전체 관객 수의 중앙값 → MinMaxScaler|영화 개봉일자(월) 전체 관객 수의 평균값 → MinMaxScaler|LabelEncoding|

</br>

위의 표에서 전체 관객 수의 중앙값, 혹은 평균값이 의미하는 바는 다음과 같습니다. 

</br>

<div align="Center">
    
||영화 제목|영화 감독|영화 배우|영화 배우|영화 배우|영화 관객 수|
|:--:|--|--|--|--|--|:--:|
|1|인터스텔라|크리스토퍼 놀란|매튜 맥커너히|앤 해서웨이|마이클 케인|1,032만 명|
|2|다크나이트 라이즈|크리스토퍼 놀란|크리스찬 베일|마이클 케인|게리 올드만|642만 명|
|3|인셉션|크리스토퍼 놀란|레오나르도 디카프리오|와타나베 켄|조셉 고든 레빗|599만 명|

</div>

</br>

영화 감독이 **크리스토퍼 놀란**인 영화 **인터스텔라**, **다크나이트 라이즈**, **인셉션**의 영화 관객 수는 **1,032만 명**, **642만 명**, **599만 명**으로 기재되어 있습니다. 영화 감독은 영화의 흥행을 어느 정도 예측할 수 있는 중요한 특성입니다. 그러므로 영화 감독에게 이전까지 제작에 관여하였던 영화의 관객 수를 가중치로 부여해야 합니다. 그 방법은 전체 관객 수의 중앙값을 사용하는 방법, 그리고 전체 관객 수의 평균값을 사용하는 방법입니다. 구체적으로 영화 관객 수의 가중치를 중앙값으로 설정한다면 크리스토퍼 놀란 감독은 642만 명의 관객 수를 가중치로 갖습니다. 영화 관객 수의 가중치를 평균값으로 설정한다면 약 758만 명의 관객 수를 가중치로 갖습니다. 그 외에도 공동 배급·수입사, 다수의 영화 배우가 해당 영화를 제작하는 데에 관여하였다면 동일한 기준을 적용하였습니다.

#### 4.3.2. 모델: 성능
아래의 표는 각 학습 모델의 매개변수, 그리고 학습 모델의 정확도에 관한 표입니다.

</br>

||Parameters|Trial 1|Trial 2|Trial 3|Trial 4|Trial 5|
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|LogisticRegression|solver = liblinear|0.51469|0.49608|0.46082|0.45935|0.45446|
|DecisionTree|max_depth = 8|0.46474|0.74535|0.75465|0.73947|0.74780|
|RandomForest|n_estimators = 100|0.50930|0.74780|0.74878|0.74878|0.74339|
|LGBM|-|-|0.74486|0.73898|0.73359|0.73800|
|GradientBoosting|n_estimators = 200, learning_rate = 0.01, max_depth = 4|-|-|0.75759|0.75465|0.75563|
|GridSearchCV|n_estimators = [100, 300], learning_rate = [0.01, 0.1], cv = 2, verbose = 1|-|-|0.75171|0.75612|0.75024|
|XGBoost|n_estimators = 200, learning_rate = 0.01, max_depth = 3|-|-|0.75220|0.75269|0.75416|
|AdaBoost|n_estimators = 200, learning_rate = 0.01, best_est = DecisionTree|-|-|0.73604|0.71596|0.72919|

</br>

#### 4.3.3. 모델: 첫 번째 실행
**영화 제작 국가, 영화 장르, 영화 감독, 영화 배우, 영화 배급·수입사, 영화 개봉일자**는 **sklearn.preprocessing.LabelEncoder**을 이용해서 문자로 된 데이터를 숫자로 변환하였습니다. **영화 러닝타임**은 **sklearn.preprocessing.MinMaxScaler**을 이용해서 값의 범위를 축소하였습니다. 

</br>

<div align="Center">
    
||LogisticRegression|DecisionTree|RandomForest|LBGM|
|--|--|--|--|--|
|Train Accuracy|0.86902|0.51050|0.99979|-|
|Test Accuracy|0.51469|0.46474|0.50930|-|
    
</div>

</br>

- 세 가지 학습 모델 모두 좋지 않은 성능을 보였습니다.
- 영화 러닝타임을 제외하고 모든 특성에 라벨 인코딩을 하면 매개변수가 너무 많아집니다. 그리고 모든 특성에 대해서 라벨 인코딩을 적용하는 것은 직접적으로 영화 관객 수를 예측하는 데에 영향을 미치지 않는 듯 보였습니다.

#### 4.3.4. 모델: 두 번째 실행
**영화 제작 국가, 영화 장르, 영화 개봉일자**는 **sklearn.preprocessing.LabelEncoder**을 이용해서 문자로 된 데이터를 숫자로 변환하였습니다. **영화 감독, 영화 배우, 영화 배급·수입사**는 영화의 제작에 관여한 모든 영화의 관객 수의 **중앙값**을 가중치로 하였습니다. 그리고 **영화 감독, 영화 배우, 영화 배급·수입사의 영화 관객 수에 대한 가중치, 그리고 영화 러닝타임**은 **sklearn.preprocessing.MinMaxScaler**을 이용해서 값의 범위를 축소하였습니다. 

</br>

<div align="Center">
    
||LogisticRegression|DecisionTree|RandomForest|LBGM|
|---|---|---|---|---|
|Train Accuracy|0.49748|0.82011|0.99979|0.99979|
|Test Accuracy|0.49608|0.74535|0.74780|0.74486|
</div>

</br>

- 이전의 시도와 비교하여 성능이 개선되었습니다.
- 그러나 학습 모델이 학습 데이터를 과하게 학습하는 듯한 모습을 보였습니다. 

#### 4.3.5. 모델: 세 번째 실행
**영화 제작 국가**는 **sklearn.preprocessing.LabelEncoder**을 이용해서 문자로 된 데이터를 숫자로 변환하였습니다. **영화 장르, 영화 감독, 영화 배우, 영화 배급·수입사, 영화 개봉일자**는 영화의 제작에 관여한 모든 영화의 관객 수의 **중앙값**을 가중치로 하였습니다. 그리고 **영화 장르, 영화 감독, 영화 배우, 영화 배급·수입사, 영화 개봉일자**의 영화 관객 수에 대한 가중치, 그리고 **영화 러닝타임**은 **sklearn.preprocessing.MinMaxScaler**을 이용해서 값의 범위를 축소하였습니다. 이 과정에서는 학습 모델이 일정 이상의 성능을 보인다는 점, 그리고 이전의 시도에서 학습 모델이 학습 데이터를 과하게 학습하는 듯한 모습을 보인다는 점을 들어 **부스팅 알고리즘**을 적용하였습니다.

</br>

<div align="Center">
    
||LogisticRegression|DecisionTree|RandomForest|LBGM|GradientBoost|GridSearchCV|XGBClassifier|AdaBoost|
|---|---|---|---|---|---|---|---|---|
|Train Accuracy|0.46704|0.81150|0.99979|0.99979|0.82347|0.80416|0.79975|0.96851|
|Test Accuracy|0.46082|0.75465|0.74878|0.73898|0.75759|0.75171|0.75220|0.73604|
    
</div>

</br>

- **부스팅 알고리즘**을 적용하여 학습 모델이 학습 데이터를 과하게 학습하는 듯한 모습을 개선하였습니다.
- 각 특성의 중요도를 확인해 본 결과 **영화 감독**, **영화 배우**, 그리고 **영화 배급·수입사**가 **영화 관객 수**를 예측하는 데 가장 많은 영향을 미쳤습니다.

#### 4.3.6. 모델: 네 번째 실행
**영화 제작 국가**는 **sklearn.preprocessing.LabelEncoder**을 이용해서 문자로 된 데이터를 숫자로 변환하였습니다. **영화 장르, 영화 감독, 영화 배우, 영화 배급·수입사, 영화 개봉일자**는 영화의 제작에 관여한 모든 영화의 관객 수의 **평균값**을 가중치로 하였습니다. 그리고 **영화 장르, 영화 감독, 영화 배우, 영화 배급·수입사, 영화 개봉일자**의 영화 관객 수에 대한 가중치, 그리고 **영화 러닝타임**은 **sklearn.preprocessing.MinMaxScaler**을 이용해서 값의 범위를 축소하였습니다. 이 과정에서도 학습 모델이 일정 이상의 성능을 보인다는 점, 그리고 이전의 시도에서 학습 모델이 학습 데이터를 과하게 학습하는 듯한 모습을 보인다는 점을 들어 **부스팅 알고리즘**을 적용하였습니다.

</br>

<div align="Center">
    
||LogisticRegression|DecisionTree|RandomForest|LBGM|GradientBoost|GridSearchCV|XGBClassifier|AdaBoost|
|---|---|---|---|---|---|---|---|---|
|Train Accuracy|0.46558|0.80877|0.99979|0.99979|0.81843|0.83312|0.78380|0.95403|
|Test Accuracy|0.45935|0.73947|0.74878|0.73359|0.75465|0.75612|0.75269|0.71596|
    
</div>

</br>

- **부스팅 알고리즘**을 적용하여 학습 모델이 학습 데이터를 과하게 학습하는 듯한 모습을 개선하였습니다.
- 이전의 시도에서는 각 특성의 전체 관객 수를 **중앙값**으로 치환하였습니다. 이번에는 각 특성의 전체 관객 수를 **평균값**으로 치환하였습니다. 그리고 이를 확인해 본 결과 중앙값으로의 치환이 더 적합해 보였습니다.

#### 4.3.7. 모델: 다섯 번째 실행
**영화 제작 국가, 그리고 영화 개봉일자**는 **sklearn.preprocessing.LabelEncoder**을 이용해서 문자로 된 데이터를 숫자로 변환하였습니다. **영화 장르, 영화 감독, 영화 배우, 영화 배급·수입사**는 영화의 제작에 관여한 모든 영화의 관객 수의 **중앙값**을 가중치로 하였습니다. 그리고 **영화 장르, 영화 감독, 영화 배우, 영화 배급·수입사**의 영화 관객 수에 대한 가중치, 그리고 **영화 러닝타임**은 **sklearn.preprocessing.MinMaxScaler**을 이용해서 값의 범위를 축소하였습니다. 이 과정에서도 학습 모델이 일정 이상의 성능을 보인다는 점, 그리고 이전의 시도에서 학습 모델이 학습 데이터를 과하게 학습하는 듯한 모습을 보인다는 점을 들어 **부스팅 알고리즘**을 적용하였습니다.

</br>

<div align="Center">
    
||LogisticRegression|DecisionTree|RandomForest|LBGM|GradientBoost|GridSearchCV|XGBClassifier|AdaBoost|
|---|---|---|---|---|---|---|---|---|
|Train Accuracy|0.47103|0.81297|0.99979|0.99979|0.82494|0.80353|0.79912|0.96620|
|Test Accuracy|0.45446|0.74780|0.74339|0.73800|0.75563|0.75024|0.75416|0.72919|
    
</div>

</br>

- 학습 모델의 결과에서 **영화 개봉일자**는 영화의 관객 수를 예측하는 데에 중요한 특성이 아니었습니다.
- 그러므로 **영화 개봉일자**를 **영화 개봉일자** 기준 전체 관객 수의 **중앙값**, 혹은 **평균값**으로 치환하지 않고 **라벨 인코딩**을 하였습니다.
- 학습 모델의 결과에서 각 특성의 전체 관객 수를 **중앙값**, 혹은 **평균값**으로 치환하여서 여러 차례 시도해 보았을 때, **중앙값**이 **평균값**보다 더 적합하게 예측하였습니다.
- 이를 바탕으로 다가오는 예측에서는 모든 특성을 각 특성 기준 전체 관객 수의 중앙값으로 치환하였습니다.  

### 4.4. 모델: 정리

</br>

<div align="Center">
    
||LogisticRegression|DecisionTree|RandomForest|LBGM|GradientBoost|GridSearchCV|XGBClassifier|AdaBoost|
|---|---|---|---|---|---|---|---|---|
|Trial 3|0.46082|0.75465|0.74878|0.73898|0.75759|0.75171|0.75220|0.72919|
|Trial 4|0.45935|0.73947|0.74878|0.73359|0.75465|0.75612|0.75269|0.71596|
|Trial 5|0.45446|0.74780|0.74339|0.73800|0.75563|0.75024|0.75416|0.72919|
    
</div>

</br>

- 학습 모델은 **GradientBoost**, 그리고 **XGBoost**가 테스트 환경에서의 정확도가 높았습니다.
- 두 학습 모델은 테스트 환경에서의 정확도가 학습 환경에서의 정확도와 큰 차이가 없었기 때문에 가장 적합한 학습 모델로 채택하였습니다.
- **GridSearchCV**는 테스트 환경에서의 정확도는 높았지만 위의 두 학습 모델과 비교하여 시간이 많이 소요되므로 대상에서 제외하였습니다.
- 마지막으로 학습 모델은 다섯 번째 시도에서 가장 높은 정확도를 보였습니다. 그러므로 다섯 번째 학습 모델에 새로운 데이터를 입력해 그 데이터의 범주를 예측해 보기로 하였습니다.

## 5. 본론: 분석

### 5.1. 분석: 정확도

#### 5.1.1. 영화 관객 수 
아래는 학습 모델이 영화 관객 수의 각 범주를 어느 정도 수준으로 예측하고 있는지를 나타낸 표입니다.

</br>

<div align="Center">
    
|범주|영화 관객 수|전체 데이터의 수|맞힌 데이터의 수|학습 모델의 정확도|
|:--------:|:-----------:|:-----------:|:-------------:|:--------:|
|1|1만 미만|2,421|2,205|0.910781|
|2|1만-10만|2,063|1,691|0.81968|
|3|10만-50만|1,143|798|0.698163|
|4|50만-100만|426|145|0.340376|
|5|100만-300만|521|346|0.664107|
|6|300만-700만|175|60|0.342857|
|7|700만-1000만|32|11|0.34375|
|8|1000만 이상|25|9|0.36|
    
</div>

</br>

일부 범주는 학습 모델의 정확도가 상대적으로 낮습니다. 그 이유에 대해서는 다음과 같이 생각해 보았습니다.

- 이들 범주는 범주의 범위에서 차이가 있고 데이터의 수에서도 차이가 있으므로 그 정확도가 낮게 나왔을 것으로 생각하였습니다. 
- 모든 특성에서 영화 관객 수의 가중치를 각 특성이 갖고 있는 영화 관객 수의 평균값, 혹은 중앙값을 사용하였으므로 대체로 보수적인 예측을 하였을 것으로 생각하였습니다. 즉, 영화 관객 수의 규모가 클수록 제대로 된 예측이 어렵습니다. 그러므로 위의 결과가 나왔다고 생각하였습니다. 

#### 5.1.2. 영화 감독
아래는 전체 데이터에서 영화 감독이 제작에 관여한 영화의 수가 열 개 이상이고 학습 모델의 정확도가 가장 높은 순으로 정렬한 표입니다.

</br>

<div align="Center">

|영화 감독|영화 관객 수의 중앙값|전체 데이터의 수|맞힌 데이터의 수|학습 모델의 정확도|
|:----------:|:-----------:|:-----------:|:-------------:|:--------:|
|조성규|1,524|11|9|0.818182|
|유야마 쿠니히코|288,230|16|13|0.8125|
|고레에다 히로카즈|42,286|12|9|0.75|
|이준익|1,648,634|12|9|0.75|
|홍상수|37,122|21|15|0.714286|
|프랑수아 오종|9,504|13|9|0.692308|
|뤽 베송|44,245|11|7|0.636364|
|론 하워드|213,980|11|4|0.363636|
|스티븐 스필버그|763,078|11|3|0.272727|
|리들리 스콧|589,899|13|3|0.230769|
    
</div>

</br>

세계적으로 저명한 영화 감독은 학습 모델의 정확도가 상대적으로 낮습니다. 그 이유에 대해서는 다음과 같이 생각해 보았습니다.

- 영화 감독의 특성 상 영화 관객 수의 분포가 골고루 분포해 있는 영화 감독, 즉 영화 관객 수의 편차가 큰 영화 감독이 있습니다. 반면 영화 관객 수의 분포가 밀집되어 있는 영화 감독, 즉 영화 관객 수의 편차가 작은 영화 감독이 있습니다. 이 학습 모델은 이처럼 분포가 고르지 않은 데이터를 학습하였으므로 학습 모델의 정확도에서 차이가 있을 것이라고 생각하였습니다.
- 예를 들어 영화 감독 **조성규**님이 제작에 관여한 영화에서 가장 많은 영화 관객을 동원하였던 영화는 **산타바바라**입니다. 이 영화의 관객 수는 약 **2만 명**입니다. 그리고 영화 감독 **조성규**님이 제작에 관여한 영화에서 가장 적은 영화 관객을 동원하였던 영화는 **딥**입니다. 이 영화의 관객 수는 약 **3백 명**입니다. 
- 반면 영화 감독 **리들리 스콧**님이 제작에 관여한 영화에서 가장 많은 영화 관객을 동원하였던 영화는 **로빈 후드**입니다. 이 영화의 관객 수는 약 **160만 명**입니다. 그리고 영화 감독 **리들리 스콧**님이 제작에 관여한 영화에서 가장 적은 영화 관객을 동원하였던 영화는 **차일드 44**입니다. 이 영화의 관객 수는 약 **2만 명**입니다. 
- 이처럼 영화 감독의 특성 상 영화 관객 수의 분포가 골고루 분포해 있는 영화 감독이 있고 그렇지 않은 영화 감독이 있습니다. 
- 그러므로 학습 모델에서의 정확도 차이는 위의 이유에서 기인하였다고 생각하였습니다.

#### 5.1.3. 영화 장르
아래는 학습 모델이 영화 장르의 각 범주를 어느 정도 수준으로 예측하고 있는지를 나타낸 표입니다.

</br>

<div align="Center">

|범주|영화 장르|영화 관객 수의 중앙값|전체 데이터의 수|맞힌 데이터의 수|학습 모델의 정확도|
|:------:|:----:|:-----------:|:-----------:|:-------------:|:--------:|
|1|드라마/가족|13,326|2,372|1,850|0.779933|
|2|액션|148,406|957|639|0.667712|
|3|스릴러|49,803|394|299|0.758883|
|5|코미디|31,655|715|552|0.772028|
|7|멜로/로맨스|17,246|540|423|0.783333|
|8|공포(호러)|74,600|328|258|0.786585|
|10|다큐멘터리|7,010|338|313|0.926036|
|11|범죄|81,724|240|160|0.666667|
|12|애니메이션|39,946|922|771|0.836226|
    
</div>

</br>

영화의 장르가 **액션**, 그리고 **범죄**에 해당하는 영화는 학습 모델의 정확도가 상대적으로 낮습니다. 반면 영화의 장르가 **다큐멘터리**에 해당하는 영화는 학습 모델의 정확도가 상대적으로 높습니다. 그 이유에 대해서는 다음과 같이 생각해 보았습니다.

- 영화 장르의 특성 상 영화 관객 수의 분포가 골고루 분포해 있는 영화, 즉 영화 관객 수의 편차가 큰 영화가 있습니다. 반면 영화 관객 수의 분포가 밀집되어 있는 영화, 즉 영화 관객 수의 편차가 작은 영화가 있습니다. 이 학습 모델은 이처럼 분포가 고르지 않은 데이터를 학습하였으므로 학습 모델의 정확도에서 차이가 있을 것이라고 생각하였습니다.
- 예를 들어 **안소니 루소** 감독의 영화 **어벤져스: 엔드게임**은 그 장르가 **액션**입니다. 이 영화의 관객 수는 약 **1,400만 명**입니다. **최동훈** 감독의 영화 **암살**은 그 장르가 **액션**입니다. 이 영화의 관객 수는 약 **1,300만 명**입니다. 반면 **다니엘 에스피노사** 감독의 영화 **모비우스**는 그 장르가 **액션**입니다. 이 영화의 관객 수는 약 **50만 명**입니다. 이처럼 영화의 장르가 **액션**인 영화는 영화의 장르 특성 상 영화 관객 수의 분포가 골고루 분포해 있습니다. 
- 반면 **진모영** 감독의 영화 **님아, 그 강을 건너지 마오**는 그 장르가 **다큐멘터리**입니다. 이 영화의 관객 수는 약 **480만 명**입니다. 이는 영화의 장르가 **다큐멘터리**인 영화 중에서 가장 많은 영화 관객을 동원하였습니다. **이충렬** 감독의 영화 **워낭소리**는 그 장르가 **다큐멘터리**입니다. 이 영화의 관객 수는 약 **300만 명**입니다. 이는 **님아, 그 강을 건너지 마오**를 이어 두 번째로 가장 많은 영화 관객을 동원하였습니다. 이처럼 영화의 장르가 **다큐멘터리**인 영화는 영화의 장르 특성 상 영화 관객 수의 분포가 상대적으로 밀집되어 있습니다.
- 그러므로 학습 모델에서의 정확도 차이는 위의 이유에서 기인하였다고 생각하였습니다.

#### 5.1.4. 영화 개봉일자(월)
아래는 학습 모델이 영화 개봉일자의 각 범주를 어느 정도 수준으로 예측하고 있는지를 나타낸 표입니다.

</br>

<div align="Center">
    
|영화 개봉일자 월|영화 관객 수의 중앙값|전체 데이터의 수|맞힌 데이터의 수|학습 모델의 정확도|
|:---------:|:-----------:|:-----------:|:-------------:|:--------:|
|1|41,439|520|403|0.775|
|2|51,487|538|398|0.739777|
|3|23,178|564|437|0.774823|
|4|29,048|579|456|0.787565|
|5|18,083|552|429|0.777174|
|6|30,576|518|412|0.795367|
|7|24,457|518|395|0.762548|
|8|36,139|584|461|0.789384|
|9|26,739|585|456|0.779487|
|10|19,616|615|485|0.788618|
|11|16,952|657|504|0.767123|
|12|27,025|576|429|0.744792|
    
</div>

</br>

영화 개봉일자는 개봉 월을 기준으로 큰 차이가 없었습니다. 이는 학습 모델의 각 특성 별 중요도를 분석했을 때에도 학습 모델의 성능에 큰 영향을 주지 않았습니다. 

#### 5.1.5. 영화 수입·배급사
아래는 전체 데이터에서 영화 수입·배급사가 제작에 관여한 영화의 수가 서른 개 이상이고 학습 모델의 정확도가 가장 높은 순으로 정렬한 표입니다.

</br>

<div align="Center">

|영화 수입·배급사|영화 관객 수의 중앙값|전체 데이터의 수|맞힌 데이터의 수|학습 모델의 정확도|
|:--------------:|:-----------:|:-----------:|:-------------:|:--------:|
|(주)소나무픽쳐스|1,657|79|76|0.962025|
|오드|14,459|44|41|0.931818|
|프리비젼엔터테인먼트|5,179|66|61|0.924242|
|(주)마운틴픽쳐스|4,030|78|72|0.923077|
|(주)영화사 백두대간|3,989|59|54|0.915254|
|(주)인디스토리|2,624|79|72|0.911392|
|(주)드림팩트엔터테인먼트|4,401|50|45|0.9|
|예지림엔터테인먼트|13,630|57|51|0.894737|
|(주)영화사오원|3,989|45|40|0.888889|
|(주)박수엔터테인먼트|18,017|108|95|0.87963|

</div>

</br>

아래는 전체 데이터에서 영화 수입·배급사가 제작에 관여한 영화의 수가 서른 개 이상이고 학습 모델의 정확도가 가장 낮은 순으로 정렬한 표입니다.
    
</br>

<div align="Center">

|영화 수입·배급사|영화 관객 수의 중앙값|전체 데이터의 수|맞힌 데이터의 수|학습 모델의 정확도|
|:--------------:|:-----------:|:-----------:|:-------------:|:--------:|
|CJ ENM|430,001|499|329|0.659319|
|(주)시너지하우스 (시너지)|185,331|41|27|0.658537|
|유니버셜픽쳐스인터내셔널 코리아(유)|173,887|223|141|0.632287|
|이십세기폭스코리아(주)|276,435|182|115|0.631868|
|소니픽쳐스릴리징코리아|282,862|177|111|0.627119|
|(주)넥스트엔터테인먼트월드(NEW)|340,936|181|112|0.618785|
|(주)메가박스|137,322|76|47|0.618421|
|워너브러더스 코리아(주)|528,537|185|108|0.583784|
|(주)쇼박스|708,108|206|113|0.548544|
|월트디즈니컴퍼니코리아 유한회사|969,543|112|60|0.535714|

</div>

</br>

대형 수입·배급사는 학습 모델의 정확도가 상대적으로 낮습니다. 그 이유에 대해서는 다음과 같이 생각해 보았습니다.

- 영화 수입·배급사의 특성 상 영화 관객 수의 분포가 골고루 분포해 있는 영화 수입·배급사, 즉 영화 관객 수의 편차가 큰 영화 수입·배급사가 있습니다. 반면 영화 관객 수의 분포가 밀집되어 있는 영화 수입·배급사, 즉 영화 관객 수의 편차가 작은 수입·배급사가 있습니다. 이 학습 모델은 이처럼 분포가 고르지 않은 데이터를 학습하였으므로 학습 모델의 정확도에서 차이가 있을 것이라고 생각하였습니다.

#### 5.1.6. 영화 제작 국가 

</br>

<div align="Center">

|영화 제작 국가|영화 관객 수의 중앙값|전체 데이터의 수|맞힌 데이터의 수|학습 모델의 정확도|
|:--------:|:-----------:|:-----------:|:-------------:|:--------:|
|한국|63,278|1,941|1,446|0.744977|
|미국|78,228|2,111|1,512|0.716248|
|그 외 국가|11,026|2,754|2,307|0.837691|

</div>

</br>
    
그 외 국가에서 제작한 영화는 학습 모델의 정확도가 상대적으로 높았습니다. 그 이유에 대해서는 다음과 같이 생각해 보았습니다.
- 그 외 국가는 영화 관객 수의 중앙값이 한국에서 제작한 영화, 그리고 미국에서 제작한 영화보다 영화 관객 수의 편차가 작습니다. 
- 그 외 국가에서 제작한 영화가 편차가 작고 이 데이터의 양이 타 국가와 비교하여 상대적으로 많으므로 학습 모델의 정확도가 높았을 것으로 생각하였습니다.

### 5.2. 모델


## 6. 결론       
                                                              
### 6.1. 결론: 데이터
데이터는 [인터넷 영화 데이터베이스](https://www.imdb.com) 공식 홈페이지에 있는 데이터를 사용하였습니다. 데이터의 범주는 **영화**입니다. 데이터는 영화 개봉일자를 기준으로 두 가지 종류로 분류하였습니다. 첫 번째 데이터는 **2004년** 이후 작품만을 추출하였습니다. 두 번째 데이터는 **2010년** 이후, 그리고 **2020년** 이전 작품만을 추출하였습니다. 그리고 **국내에서 개봉하지 않은 외국 영화**를 **별점**을 기준으로 정렬하여 상위 20개 데이터를 사용하였습니다. 데이터는 **국내에서 개봉하지 않은 외국 영화**이기 때문에 **영화 배급·수입사, 그리고 영화 개봉일자**는 임의로 선정하였습니다. 

### 6.2. 결론: 모델
학습 모델은 위에서 언급한 바 **GradientBoost**, 그리고 **XGBoost**를 사용하였습니다. 

### 6.3. 결론: 결과

#### 6.3.1. 결과: 국내에서 개봉하였던 외국 영화
데이터는 국내에서 개봉하였던 외국 영화를 임의로 선정하였습니다. 영화 배급·수입사는 해당 영화의 배급·수입을 맡은 배급·수입사로 하였습니다. 

</br>

||movieNm|runTm|nation|genre|director|actor|is_adult|distributor|view_cat|xgb_pred_1|gb_pred_1|xgb_pred_2|gb_pred_2|
|-|------|-----|------|-----|--------|-----|--------|-----------|--------|--------|-------|------|------|
|1|닥터 스트레인지: 대혼돈의 멀티버스|126|2|2|샘 레이미|베네딕트 컴버배치|0|월트디즈니컴퍼니코리아 유한책임회사|6|4|4|3|3|
|2|신비한 동물들과 덤블도어의 비밀|142|2|1|데이빗 예이츠|에디 레드메인|0|워너브러더스 코리아(주)|5|6|6|5|5|
|3|더 배트맨|176|2|2|맷 리브스|로버트 패틴슨|0|워너브러더스 코리아(주)|4|2|2|5|6|
|4|씽2게더|110|2|12|가스 제닝스|매튜 매커너히|0|유니버셜픽쳐스인터내셔널 코리아(유)|4|2|2|5|2|
|5|언차티드|116|2|2|루벤 플레셔|톰 홀랜드|0|소니픽쳐스릴리징코리아|4|5|5|5|8|
|6|모비우스|104|2|2|다니엘 에스피노사|자레드 레토|0|소니픽쳐스릴리징코리아|3|3|3|3|3|
|7|수퍼 소닉2|122|2|12|제프 파울러|제임스 마스던|0|롯데엔터테인먼트|3|3|3|1|1|
|8|나일 강의 죽음|126|2|11|케네스 브래너|케네스 브래너|0|월트디즈니컴퍼니코리아 유한책임회사|3|4|4|4|5|
|9|문폴|130|2|2|롤랜드 에머리히|할리 베리|0|(주)누리픽쳐스|3|2|2|4|4|
|10|하우스 오브 구찌|158|2|11|리들리 스콧|아담 드라이버|0|유니버셜픽쳐스인터내셔널 코리아(유)|3|2|2|5|5|

</br>

- 두 데이터 군집으로 분류하여도 학습 모델의 정확도는 상대적으로 낮습니다.
- 두 데이터 군집의 결과가 상이하게 나온다. 첫 번째 데이터 군집은 영화의 관객 수를 보수적으로 예측하는 경향이 있고, 두 번째 데이터 군집은 영화의 관객 수를 보수적이지 않게 예측하느 경향이 있습니다.
- 이는 현재까지 코로나 바이러스의 영향을 받고 있으므로 코로나 바이러스 이전 수준으로 영화 산업이 회복하지 못하였다고 생각하였습니다.

#### 6.3.2. 결과: 국내에서 개봉하지 않은 외국 영화
영화 배급·수입사는 **해리슨앤컴퍼니**, 영화 개봉일자(월)은 **4월**로 임의로 선정하였습니다. 

</br>

||movieNmEn|runTm|nation|genre|director|actor|is_adult|distributor|openMonth|xgb_pred_1|gb_pred_1|xgb_pred_2|gb_pred_2|
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
|0|Into the Wild|148|2|1|숀 펜|에밀 허쉬|0|주식회사 해리슨앤컴퍼니|4|1|1|3|3|
|1|Superbad|113|2|5|그렉 모톨라|조나 힐|1|주식회사 해리슨앤컴퍼니|4|2|2|2|2|
|2|Zombieland|88|2|5|루벤 플레셔|우디 해럴슨|1|주식회사 해리슨앤컴퍼니|4|5|3|5|3|
|3|Shaun of the Dead|99|3|5|에드가 라이트|사이먼 페그|1|주식회사 해리슨앤컴퍼니|4|2|2|4|4|
|4|21 Jump Street|109|2|2|필 로드|조나 힐|1|주식회사 해리슨앤컴퍼니|4|4|4|4|4|
|5|Crazy, Stupid, Love.|118|2|5|글렌 피카라|스티브 카렐|0|주식회사 해리슨앤컴퍼니|4|2|2|2|2|
|6|Scott Pilgrim vs. the World|112|2|2|에드가 라이트|마이클 세라|0|주식회사 해리슨앤컴퍼니|4|1|1|4|1|
|7|Anchorman: The Legend of Ron Burgendy|94|2|5|아담 맥케이|윌 퍼렐|0|주식회사 해리슨앤컴퍼니|4|3|3|3|3|
|8|Serenity|119|2|1|스티븐 나이트|매튜 매커너히|0|주식회사 해리슨앤컴퍼니|4|1|1|2|4|
|9|Forgetting Sarah Marshall|111|2|5|니콜라스 스톨러|제이슨 세걸|1|주식회사 해리슨앤컴퍼니|4|3|1|3|1|
|10|Gone Baby Gone|114|2|11|벤 애플렉|케이시 에플렉|1|주식회사 해리슨앤컴퍼니|4|3|3|3|3|
|11|Creed|133|2|1|라이언 쿠글러|마이클 B.조던|0|주식회사 해리슨앤컴퍼니|4|6|1|6|6|
|12|RocknRolla|114|2|2|가이 리치|제라드 버틀러|1|주식회사 해리슨앤컴퍼니|4|3|3|5|2|
|13|Kiss Kiss Bang Bang|103|2|2|세인 블랙|로버트 다우니 주니어|1|주식회사 해리슨앤컴퍼니|4|1|1|1|1|
|14|Thank You for Smoking|92|2|5|제이스 라이트먼|아론 에크하트|0|주식회사 해리슨앤컴퍼니|4|1|1|1|1|
|15|Garden State|102|2|5|잭 브라프|잭 브라프|1|주식회사 해리슨앤컴퍼니|4|1|2|1|1|
|16|The Boy in the Striped Pajamas|94|2|1|마크 허만|에이사 버터필드|0|주식회사 해리슨앤컴퍼니|4|1|1|1|1|
|17|War Dogs|114|2|5|토드 필립스|조나 힐|1|주식회사 해리슨앤컴퍼니|4|2|2|2|2|
|18|Facture|113|2|3|그레고리 호블릿|라이언 고슬링|1|주식회사 해리슨앤컴퍼니|4|3|3|1|1|
|19|The Lighthouse|109|2|1|로버트 에거스|로버트 패틴슨|1|주식회사 해리슨앤컴퍼니|4|1|1|1|1|

</br>

- 학습 모델의 결과에 의하면 위의 영화 중에서 **Zombieland**, 그리고 **Creed**가 국내에서 상영하였을 때 가장 많은 관객을 동원할 것으로 예상했습니다.
- 두 영화에 대한 관심을 확인하기 위해 네이버 영화에서 두 영화의 기대 지수를 살펴보았습니다. 두 영화 모두 **보고 싶어요**, 혹은 **글쎄요** 등 영화에 대한 반응을 표현한 사람은 700명 이상이었습니다. 그리고 두 영화 모두 **보고 싶어요**를 선택한 사람이 다수였습니다. 이는 영화에 대한 관심으로 해석할 수 있습니다. 
- 다음으로는 추가적인 검증을 위해 **Rotten Tomatoes**에서 US Box Office ($)를 살펴보았습니다. **Zombieland**, 그리고 **Creed**는 현지 기준 총 $100m 이상의 매출을 기록한 영화입니다. 현지에서 백만 이상의 관객을 동원한 영화는 일반적으로 $100m 이상의 매출을 기록하였습니다. 이는 곧 한국 관객의 관심으로 해석하기 어렵지만 흥행을 어느 정도 예상할 수 있는 하나의 지표였습니다.
- 학습 모델은 **XGBoost**, 그리고 **GradientBoost** 모두 비슷한 예측 값을 보여주었습니다. 그 중에서도 **XGBoost**는 보다 보수적인 예측 값을 보였습니다. 영화 산업은 **고위험 산업군**에 속하므로 영화 배급·수입사 측면에서는 보수적인 모델이 적합할 것으로 생각하였습니다.

#### 6.3.3. 결과: 국내에서 개봉이 예정되어 있는 외국 영화
데이터는 국내에서 개봉이 예정되어 있는 외국 영화를 임의로 선정하였습니다. 영화 배급·수입사는 해당 영화의 배급·수입을 맡은 배급·수입사로 하였습니다. 단 보고서 작성 일자 기준, 2022년 06월 15일을 기준으로 해당 영화의 배급·수입을 맡은 배급·수입사가 없을 때, 이 영화의 배급·수입사는 **롯데엔터테인먼트**로 하였습니다. 그리고 해당 영화의 러닝 타임이 제공되지 않을 때는 두 가지 방법으로 분류하여 데이터를 입력하였습니다. 해당 영화가 시리즈로 구성된 영화라면 전체 시리즈의 평균 러닝 타임을 이 영화의 러닝 타임으로 하였습니다. 해당 영화가 시리즈로 구성된 영화가 아니라면 해당 영화 감독의 필모그래피 상 전체 영화의 평균 러닝 타임으로 하였습니다.

</br>

||movieNm|runTm|nation|genre|director|actor|is_adult|distributor|view_cat|xgb_pred_1|gb_pred_1|xgb_pred_2|gb_pred_2|
|-|------|-----|------|-----|--------|-----|--------|-----------|--------|--------|-------|------|-----|
|1|존 윅4|120|2|2|채드 스타헬스키|키아누 리브스|1|롯데엔터테인먼트|3|3|3|3|3|
|2|토르: 러브 앤 썬더|133|2|2|타이카 와이티티|크리스 헴스워스|0|월트디즈니컴퍼니코리아 유한책임회사|7|6|6|6|6|
|3|미션 임파서블: 데드 레코닝 PART ONE|128|2|2|크리스토퍼 맥쿼리|톰 크루즈|0|롯데엔터테인먼트|7|6|6|6|6|
|4|스파이더맨: 어크로스 더 스파이더버스 (파트 원)|117|2|12|조아킹 도스 산토스|샤메익 무어|0|소니픽쳐스릴리징코리아|6|1|1|1|1|
|5|블랙 팬서: 와칸다 포에버|135|2|2|라이언 쿠글러|레티티아 라이트|0|월트디즈니컴퍼니코리아 유한책임회사|11|1|1|6|1|
|6|아바타: 물의 길|162|2|2|제임스 카메론|샘 워싱턴|0|월트디즈니컴퍼니코리아 유한책임회사|12|3|3|2|2|
|7|버즈 라이트이어|105|2|12|앤거스 맥클레인|크리스 에반스|0|월트디즈니컴퍼니코리아 유한책임회사|6|1|1|1|1|
|8|탑건: 매버릭|130|2|2|조셉 코신스키|톰 크루즈|0|롯데엔터테인먼트|6|3|3|3|3|
|9|바빌론|112|2|1|데이미언 셔젤|토비 맥과이어|0|롯데엔터테인먼트|12|5|5|5|2|
|10|노프|110|2|8|조던 필|다니엘 칼루야|0|유니버셜픽쳐스인터내셔널 코리아(유)|7|5|5|5|5|

</br>

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

[2] 정보 출처: https://www.youtube.com/watch?v=Hj4w4jukm4U

[3] 정보 출처: https://www.youtube.com/watch?v=b3tjkUeAVa8

[4] 정보 출처: https://www.youtube.com/watch?v=y1VVvnzQIx4

[5] 정보 출처: https://www.youtube.com/watch?v=rFADkXWicBE

[6] 정보 출처: https://www.youtube.com/watch?v=D6_hBNgEyeE

[7] 정보 출처: https://brunch.co.kr/@campuscine21/72
