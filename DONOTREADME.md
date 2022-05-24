<h1 align="center">프로젝트 기획안</h1>

<div align="Right">
    작성일자: 2022.05.18
    </br>
    수정일자: 2022.05.24
    </br>
    </br>
    박덕용 
    </br>
    한선아
    </br>
    박재우
</div>

</br>

## 개요

### 주제
이 프로젝트는 국내에서 상영되었던 영화로 개봉이 예정되어 있는 영화의 관객 수를 예측하는 프로젝트입니다. 

### 목적
이 프로젝트로 외국에서 상영되었던, 혹은 외국에서 개봉이 예정되어 있는 영화가 국내에서 개봉하였을 때의 영화 관객 수를 예측할 수 있습니다. 이를 활용하여 외국으로부터 영화를 수입·배급하고 있는 회사의 구매 직원이 외국에서 상영되었던, 혹은 외국에서 개봉이 예정되어 있는 영화의 수익성을 분석할 수 있습니다. 

## 배경
외국으로부터 영화를 수입·배급하고 있는 회사의 구매 직원은 완성되지 않은 영화, 즉 영화의 감독, 배우, 시놉시스, 그리고 시나리오만을 보고 영화를 구매합니다. 구매에 대한 위험은 온전히 영화를 수입·배급하고 있는 회사에서 부담해야 합니다. 그리고 외국으로부터 영화를 수입·배급하고 있는 회사의 구매 직원은 영화제가 시작하기 전에 수백, 더 나아가 수천 편의 영화를 사전에 확인해야 합니다. 이들은 영화제에 참석하여 아침부터 저녁까지 상영하고 있는 영화를 선별해서 관람해야 합니다. 이처럼 국내 관람객을 위해 노력하는 외화 수입·배급사의 구매 직원이 보다 효율적으로 영화를 선별할 수 있도록 도움을 드리기 위해 진행하는 프로젝트입니다. 

더 나아가 영화진흥위원회에서 간행하고 있는 <월간 한국 영화>의 '**팬데믹 시대, 신생 투자배급사를 점검하다**'에서는 팬데믹 이후 신생 투자·배급사, 그리고 중소 투자·배급사의 위기설에 대해 언급한 바 있습니다. 그 내용은 이들이 제작·투자한 영화들이 팬데믹으로 인해 흥행에 실패했다는 내용입니다. 그러므로 투자·배급사는 영화의 투자·배급에 더욱 신중할 수밖에 없습니다. [더보기](https://github.com/zaewoo/project/blob/master/INFORMATION.md)

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

#### 3. Kaggle

### 데이터: 내용

#### 1. IMDb
공식 홈페이지에 있는 데이터에서 데이터의 범주가 **영화**인 데이터를 사용하였습니다. 

#### 1.1. MoviesWithRating
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

#### 1.2. Movieawards
이 데이터는 1886년 01월 01일부터 2020년 12월 31일까지의 데이터를 포함하고 있습니다. 전체 데이터는 약 22만 개이고, 전체 데이터의 컬럼은 21개입니다.
|Variable name|Variable description|
|------|---|
|eventId|영화제 고유 아이디|
|eventName|영화제 명칭|
|awardName|영화제 수상 부문|
|year|영화제 개최년도|
|categoryName|영화제 수상 내역|
|nomeneeNote|영화제 노미네이트 구분|
|name|영화제 수상자·수상작 이름|
|originalName|영화·드라마 명칭|
|characterNames|영화·드라마 내 극중 인물의 이름|
|isWinner|영화제 수상 여부|
|isPerson|영화제 수상자 구분|
|isTitle|영화제 수상작 구분|
|const|영화제 수상자·수상작 고유 번호|
|~~episodeNames~~|~~드라마 시리즈 에피소드 제목~~|
|~~songNames~~|~~음악 명칭~~|
|~~notes~~|~~기타~~|
|~~occurrence~~|-|
|~~winAnnouncementTime~~|-|
|~~isPrimary~~|-|
|~~isSecondary~~|-|
|~~isCompany~~|-|

#### 2. KOBIS:KOREA Box-office Information System
공식 홈페이지에서 **월별 박스오피스 조회 기간**을 설정하여 데이터를 수집하였습니다.

#### 2.1. Moviedetails
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

#### 2.2. Movieview
이 데이터는 2004년 01월 01일부터 2022년 05월 18일까지의 데이터를 포함하고 있습니다. 전체 데이터는 약 2만 개이고, 전체 데이터의 컬럼은 6개입니다.
|Variable name|Variable description|
|------|---|
|movieNm|영화 제목|
|openDt|영화 개봉일자|
|acc_revenue|영화 매출액|
|acc_view|영화 관객 수|
|screen_cnt|영화 상영관 수|
|show_cnt|영화 상영 횟수|

### 데이터: 분석

#### 1. IMDb
해당 데이터의 분석 내용을 작성해 주세요.

#### 2. KOBIS:KOREA Box-office Information System
해당 데이터의 분석 내용을 작성해 주세요.

## 본문: 모델
이 프로젝트에서는 영화 관객 수 분류에 의해 영화의 관객 수를 예측해야 하므로 데이터 마이닝에서의 주요 분류 기법에 해당하는 의사결정나무, 다항 로지스틱 회귀분석, 다층 퍼셉트론을 사용하겠습니다. 

### 기계 학습

#### 1. 기계 학습: 의사결정나무
> 의사결정나무 알고리즘은 의사결정 규칙을 도표화하여 관심대상이 되는 집단을 몇 개의 소집단으로 분류하거나 예측을 수행하는 방법으로서 고객세분화, 고객 분류, 문제 예측 등의 여러 분야에서 유용하게 활용되고 있다 (조광현, 박희창, 2011). [8]

> 의사결정나무모형은 분석의 목적과 자료구조에 따라 적절한 분리기준과 정지규칙을 지정하고 의사결정가지치기와 같은 특징선택을 통해 분류에 가장 필요한 특징들만을 추출함으로써 원자료에 비해 줄어든 자료를 얻을 수 있으며, 분류의 기준이 되기에 기여도가 떨어지는 잡음, 중복자료 그리고 규칙을 제거할 수 있다 (Woosik Lee, 2017). [2]

#### 2. 기계 학습: 다항 로지스틱 회귀분석
> 다항 로짓모형은 확률선택모형의 구체화된 모형으로 3개 이상의 대안 중 하나를 선택해야 하는 상황에서 개인 'A'가 대안 'B'를 선택 할 확률을 분석한다. 기준대안에 대한 선택대안의 승산이 없는 다른 대안에 대해 독립적이라는 것은 다항 로짓모형의 기본 가정이며, 이러한 특성으로 인해 설문조사에서 개인들의 여러 가지 특성과 이들이 하는 선택들을 기록하고 분석해야 하는 사회과학분야에서 일반적으로 활용된다 (Mu-Seon Lee, 2016). [4]

### 심화 학습

#### 1. 심화 학습: 다층 퍼셉트론
> 신경망모형은 매우 유연한 비선형모형으로서 예측변수들을 결합하여 각 은닉마디에 전달하고 은닉마디 들의 결합을 출력마디에 전달함으로서 목표변수의 범주를 분류하는 분류모형이다. multilayer percep- tron(MLP) 신경망모형의 구조는 예측변수들로 구성되는 입력층, 은닉마디들로 구성되는 은닉층, 그리 고 목표변수의 범주들로 구성되는 출력층으로 이루어진다 (Lee, 2016). [1]

## 참고문헌
[1] Seonghyeon Jeona, Young Sook Sona(2016). Prediction of box office using data mining. The Korean Journal of Applied Statistics (2016), 29(7), 1257–1270.

[2] Woosik Lee(2017). A deep learning analysis of the KOSPI's directions. Journal of the Korean Data & Information Science Society (2017), 28(2), 287-295.

[3] Kwak, M. and Rhee, S(2016). Finding factors on employment by adult life cycle using decision tree model. Journal of the Korean Data & Information Science Society, 27, 1537-1545.

[4] Mu-Seon Lee(2016). Analysis on the Factors Affecting Housing Tenure of Single-Person Households of Young Generation Employing the Multinomial Logit Model. Journal of the Korean Academia-Industrial cooperation Society Vol 17. No.6. pp.469-481.

[5] Y.Choi, Y.K.Kang, Analysis on the Preference against the Residential-building Forms in Multi-familiy Attached House Employing The Multinomial Logit Model, Journal of Architectual Institute of Korea, Vol 24. No.12. pp.57-65, 2008.

[6] 최종후, 서두성(1999). 데이터마이닝 의사결정나무의 응용. 통계청 「통계분석연구」 제4권 제1호(99.봄). 61-83.

[7] 이용규, 고형일, 이일병(2014). 객체의 분류를 위한 효율적인 다층 퍼셉트론의 설계 및 구조에 관한 연구. 2014년 추계학습발표대회 논문집 제21권 제2호 (2014.11). 803-805.

[8] 왕빈신, 전범수(2016). 한국 개봉 미국 제외 외국 영화 흥행 결정 요인. The Journal of the Korea Contents Association Vol 16. Issue 2. pp.96-105.

[9] 조광현, 박희창(2011). 매개 변수를 이용한 의사결정나무 생성에 관한 연구. Journal of the Korean Data & Information Science Society, 22(4), 671-678.
