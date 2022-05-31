<h1 align="center">결과 보고서</h1>

<div align="Right">
    작성일자: 2022.05.27
    </br>
    수정일자: 2022.05.31
    </br>
    </br>
    박덕용 
    </br>
    한선아
    </br>
    박재우
</div>

## 개요

### 목적
- 개봉 예정 영화 관객 수 예측

### 결론
결론에 대해서 서술해 주세요.

## 서론

### 배경
외국으로부터 영화를 수입·배급하고 있는 회사는 완성되지 않은 영화, 즉 영화의 감독, 배우, 시놉시스, 그리고 시나리오만을 보고 영화를 구매합니다. 구매에 대한 위험은 온전히 영화를 수입·배급하고 있는 회사에서 부담해야 합니다. 그리고 외국으로부터 영화를 수입·배급하고 있는 회사는 영화제가 시작하기 전에 수백, 더 나아가 수천 편의 영화를 사전에 확인해야 합니다. 이들은 영화제에 참석하여 아침부터 저녁까지 상영하고 있는 영화를 선별해서 관람해야 합니다. 이처럼 국내 관람객을 위해 노력하는 외화 수입·배급사가 보다 효율적으로 영화를 선별할 수 있도록 도움을 드리기 위해 진행하는 프로젝트입니다. 

더 나아가 영화진흥위원회에서 간행하고 있는 <월간 한국 영화>의 '**팬데믹 시대, 신생 투자배급사를 점검하다**'에서는 팬데믹 이후 신생 투자·배급사, 그리고 중소 투자·배급사의 위기설에 대해 언급한 바 있습니다. 그 내용은 이들이 제작·투자한 영화들이 팬데믹으로 인해 흥행에 실패했다는 내용입니다. 그러므로 투자·배급사는 영화의 투자·배급에 더욱 신중할 수밖에 없습니다. [더보기](https://github.com/zaewoo/project/blob/master/CONTEXT.md)

## 본론: 데이터

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

#### 3. KOFIC:KOREA Film Council
> 이는 영화진흥위원회가 제공하는 통합전산망 

<div align="Right">
    Page Link: https://www.kobis.or.kr/kobisopenapi/homepg/main/main.do
</div>

### 수집
데이터 수집에 대해서 서술해 주세요.

### 전처리
데이터 전처리에 대해서 서술해 주세요.

## 본론: 모델
데이터 모델링에 대해서 서술해 주세요.

## 결론
결론에 대해서 서술해 주세요.
