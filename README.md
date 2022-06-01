![âPngtreeâpure stage banner background_976453](https://user-images.githubusercontent.com/97165359/171340263-21df96d7-def2-4ec8-98bb-85408456122e.png)

<div align="Right">
    진행 기간: 2022.05.20-2022.05.26
    </br>
    </br>
    작성 일자: 2022.05.27
    </br>
    수정 일자: 2022.06.01
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
    
    1.3. [결론](#결론)

2. [서론](#서론)

    2.1. [배경](#배경)

3. [본론: 데이터](#본론-데이터)

    3.1. [데이터: 개요](#데이터-개요)

    3.2. [데이터: 내용](#데이터-내용)

    3.3. [데이터: 전처리](#데이터-전처리)

4. [본론: 모델](#본론-모델)

5. [결론](#결론)

6. [참고](#참고)

7. [기타](#기타)

## 개요

### 주제
이 프로젝트는 국내에서 상영되었던 영화로 개봉이 예정되어 있는 영화의 관객 수를 예측하는 프로젝트입니다. 

### 목적
이 프로젝트로 외국에서 상영되었던, 혹은 외국에서 개봉이 예정되어 있는 영화가 국내에서 개봉하였을 때의 영화 관객 수를 예측할 수 있습니다. 이를 활용하여 외국으로부터 영화를 수입·배급하고 있는 회사가 외국에서 상영되었던, 혹은 외국에서 개봉이 예정되어 있는 영화의 수익성을 분석할 수 있습니다. 

### 결론
결론에 대해서 서술해 주세요.

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
> 영화진흥위원회 영화관 입장권 통합 전산망에서 제공하는 오픈API 서비스입니다. 
> 그 중에서 [영화 목록 조회 API 서비스](http://www.kobis.or.kr/kobisopenapi/homepg/apiservice/searchServiceInfo.do)를 이용하였습니다. 이는 영화진흥위원회가 제공하는 통합전산망에서 제공하는 영화 목록을 영화명, 감독명등의 조건으로 조회할 수 있는 서비스입니다.

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
영화의 누적 관객 수를 포함하고 있는 데이터(2.1. Audience), 그리고 영화의 정보를 포함하고 있는 데이터(2.2. Details) 모두 필요하므로 이 둘을 공통된 컬럼으로 병합하였습니다. 이 때 공통된 컬럼은 각 테이블에 존재하는 **movieNm**, **openDt**이고, 기준이 되는 테이블에 병합한 컬럼은 **acc_view**입니다. 이 과정에서 구글 클라우드에서 제공하는 SQL을 활용하였습니다. 이로써 국내에서 상영되었던 영화의 정보, 그리고 그 영화의 누적 관객 수가 포함되어 있는 테이블을 구할 수 있습니다. 전체 데이터는 약 1만 5천 개이고, 전체 데이터의 컬럼은 11개입니다.

1. genreNm 컬럼에서 “공연" 데이터는 프로젝트에서 중점으로 다루려는 일반적인 영화의 장르와는 다소 다른 면이 있으므로 제거 → 총 263개의 데이터 삭제
2. genreNm 컬럼 단순화 작업
    1. 기존의 데이터에서는 16개의 장르가 제공되었다. 너무 세분화 되어 있어서 마이너 장르를 제외한 주요 장르 9개만 유지하도록 하였다
    2. 데이터에서 마이너 장르의 영화들은 서브 장르가 메이저 장르인 경우 치환하였다
    3. 메인과 서브 장르가 모두 마이너 장르인 경우, 100,000 이상의 관객수 영화는 네이버 영화 혹은 IMBD, Rotten Tomatoes, Youtube 조사 후 장르를 메이저 장르중 하나로 업데이트 하였다.
3. companys, directorNm, actor 컬럼에서는 각 한개의 데이터만 추출 → 예를 들어, actor 컬럼에 3명의 배우의 이름이 제공되면, 그중에서 처음 등장하는 배우명을 컬럼 값으로 지정.
4. acc_view 컬럼에서 1,000 미만 관객수의 영화는 프로젝트 목적과는 맞지 않는 데이터라 판단되어 제거
5. showTm컬럼 정보가 제공되지 않는 경우 제거
6. companys 컬럼에서 배급사 정보가 제공되지 않는 경우 제거
7. 애니메이션 장르의 데이터에서 배우 정보가 누락된 경우가 많았기에 100,000 이상의 관객수 영화는 네이버 영화를 참고하여 수작업으로 배우 정보를 업데이트 하였다.
8. directorNm 컬럼에서 감독명이 없는 경우 제거
9. nations 컬럼은 주요 국가인 한국, 미국, 제 3국으로 다시 분류하였다 → 비슷한 수의 데이터 그루핑
10. audits 컬럼은 18세 이상의 영화 심의 등급은 is_adult = 1로 치환하였다.
11. openDt에서 월 정보만 추출하여 openMonth 컬럼을 만들어 개봉 월 단위로 분석을 가능하게 하였다.
12. acc_view 컬럼을 범주형 데이터로 변환 → 캐터고리 지정

## 본론: 모델

### 기계 학습
데이터 모델링에 대해서 서술해 주세요.

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
