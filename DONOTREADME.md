# 프로젝트 기획안

## 임시 공간

- 전체적인 로직을 한눈에 확인할 수 있는 그림을 이곳에 넣으면 좋겠어요.

## 메모장
- 목차는 어디에 둘까?
- 기획 의도, 개발 동기, 주제 선정 이유 등은 어디에 둘까?

## 읽을 목록
- https://www.yna.co.kr/view/AKR20200805055751005 
- https://www.econovill.com/news/articleView.html?idxno=302805
- https://brunch.co.kr/@campuscine21/72

## 요약

### 주제
이 프로젝트의 주제는 머신러닝 모델을 이용하여 과거에 상영되었던 영화 데이터의 다양한 특성을 학습하고 앞으로 상영이 예정됭 있는 영화의 관객 수, 그리고 평점을 예측하는 것입니다. 

### 주제 선정 이유
이 주제를 선정한 이유는 .........

외국으로부터 영화를 수입 및 배급하고 있는 회사가 상영 예정 작의 예상 관객 수, 그리고 예상되는 평점으로 영화의 수익성을 확인하기 위함입니다.


### 목적
이 프로젝트는 주제 외에도 세 가지 목적을 갖고 있습니다.

1. 온라인 동영상 서비스를 운영하고 있는 회사, 그리고 그것을 이용하는 이용자를 위해 가장 대중적이고 성공적인 영화를 추천할 수 있습니다.
2. 영화 상영관을 관리 및 운영하고 있는 회사는 상영 예정 작의 예상되는 관객 수로 상영 스케줄을 효율적으로 관리할 수 있습니다.
3. 외국으로부터 영화를 수입 및 배급하고 회사는 상영 예정 작의 예상 관객 수, 그리고 예상되는 평점으로 수익성을 확인할 수 있습니다. 

### 결과
1.
2.
3.

## 분석

### 데이터

#### 1. IMDb
**IMDb Dataset Details** Each dataset is contained in a gzipped, tab-separated-values (TSV) formatted file in the UTF-8 character set. The first line in each file contains headers that describe what is in each column. A *‘\N’* is used to denote that a particular field is missing or null for that title/name. The available datasets are as follows: 

**title.akas.tsv.gz: title_akas.tsv**

Contains the following information for titles:

- titleId (string) - a tconst, an alphanumeric unique identifier of the title
- ordering (integer) – a number to uniquely identify rows for a given titleId
- title (string) – the localized title
- region (string) - the region for this version of the title
- language (string) - the language of the title
- types (array) - Enumerated set of attributes for this alternative title. One or more of the following: "alternative", "dvd", "festival", "tv", "video", "working", "original", "imdbDisplay". New values may be added in the future without warning
- attributes (array) - Additional terms to describe this alternative title, not enumerated
- isOriginalTitle (boolean) – 0: not original title; 1: original title

**title.basics.tsv.gz: title_basics.tsv**

Contains the following information for titles:

- tconst (string) - alphanumeric unique identifier of the title
- titleType (string) – the type/format of the title (e.g. movie, short, tvseries, tvepisode, video, etc)
- primaryTitle (string) – the more popular title / the title used by the filmmakers on promotional materials at the point of release
- originalTitle (string) - original title, in the original language
- isAdult (boolean) - 0: non-adult title; 1: adult title
- startYear (YYYY) – represents the release year of a title. In the case of TV Series, it is the series start year
- endYear (YYYY) – TV Series end year. ‘\N’ for all other title types
- runtimeMinutes – primary runtime of the title, in minutes
- genres (string array) – includes up to three genres associated with the title

**title.crew.tsv.gz: title_crew.tsv**

Contains the director and writer information for all the titles in IMDb. Fields include:

- tconst (string) - alphanumeric unique identifier of the title
- directors (array of nconsts) - director(s) of the given title
- writers (array of nconsts) – writer(s) of the given title

**title.principals.tsv.gz: title_principals.tsv**

Contains the principal cast/crew for titles

- tconst (string) - alphanumeric unique identifier of the title
- ordering (integer) – a number to uniquely identify rows for a given titleId
- nconst (string) - alphanumeric unique identifier of the name/person
- category (string) - the category of job that person was in
- job (string) - the specific job title if applicable, else '\N'
- characters (string) - the name of the character played if applicable, else '\N'

**title.ratings.tsv.gz: title_ratings.tsv**

Contains the IMDb rating and votes information for titles

- tconst (string) - alphanumeric unique identifier of the title
- averageRating – weighted average of all the individual user ratings
- numVotes - number of votes the title has received

**name.basics.tsv.gz: name_basics.tsv**

Contains the following information for names:

- nconst (string) - alphanumeric unique identifier of the name/person
- primaryName (string)– name by which the person is most often credited
- birthYear – in YYYY format
- deathYear – in YYYY format if applicable, else '\N'
- primaryProfession (array of strings)– the top-3 professions of the person
- knownForTitles (array of tconsts) – titles the person is known for

<div align="Right">
    Page Link: https://www.imdb.com/interfaces/
</div>

#### 2. KOBIS:KOREA Box-office Information System

### 

## 정보

영화 제작사는 영화 제작 비용을 조달하기 위해 투자자들에게 시나리오를 제안한다. 여기에는 감독을 비롯한 제작진 구성, 배우 캐스팅, 예산 책정 등의 내용이 담겨있다. 투자사들은 제작사들이 제출한 기획안을 통해 시나리오의 수익성을 판단하고, 자금 투자 여부를 결정한다. 이를 픽업(Pick up)이라고 한다. 여기에서 투자를 주도하고 가장 많은 비용을 지원하는 업체들을 '메인 투자자(사)'라고 한다. 대표적으로 CJ엔터테인먼트, 롯데엔터테인먼트, 쇼박스, 뉴, 메가박스플러스M 등의 업체들이 있다. 그 외로는 소규모 투자사나 벤처캐피탈에서 조성하는 펀드 등을 통해 영화 제작비용이 모금된다. 일련의 과정을 통해 한 편의 영화가 제작되면, 이 시점부터 배급사의 본격적인 업무가 시작된다. 

- 배급사의 첫 번째 미션, 스크린(상영관)을 확보하라. 

업계에서는 배급을 디스트리뷰트(Distribute)라고 표현하기도 한다. 이는 제작사를 통해 만들어진 영화가 상영될 수 있는 스크린을 확보하는 일을 의미한다. 배급사는 영화에 투입된 예산과 BEP(손익분기점)를 계산하고 멀티플렉스 업체들과 조율을 통해 상영관 수를 확보한다. 절대 법칙은 아니지만, 상영관 수는 수익과 정비례한다고 보면 되기 때문에 배급사의 궁극적인 목표는 제작 예산을 넘어서는 수익을 가능한 빠른 시간에 거둘 수 있도록 많은 상영관을 확보하는 것이다. 업계에서는 영화의 상영을 스크린에 ‘건다’는 표현을 쓰는데 쉽게 말해 이 ‘거는’ 작업을 일선에서 주도하는 업체를 배급사라고 보면 된다. 특히 우리나라의 영화업계에서는 배급사가 곧 메인 투자자가 되는 경우가 많기 때문에, 다른 나라보다 배급사의 조율과 스크린 확보가 매우 중요하다.  

- 두 번째 미션, 원칙에 따른 수익 배분

영화 한 편으로 인한 수익은 철저한 자본 투자와 배분의 논리가 적용된다. 이를 통해 영화에 투자했던 메인 투자자들과 벤처캐피탈, 그리고 배급사, 제작사가 돈을 번다. 계산법은 다음과 같다. 관객이 영화 한 편을 보기위한 비용을 1만원으로 가정하면, 10% 세금을 제외한 9000원의 수익이 남는데 이를 멀티플렉스와 배급사가 50%, 즉 4500원씩으로 나눈다. 배급사는 여기서 배급수수료 10~12%, 약 500원을 제하고 나머지 4000원씩을 제작비용에 이를 때가지 적립한다. 이렇게 발생한 수익이 손익분기점을 넘으면, 배급사는 투자사와 제작사에 수익 배분을 시작한다. 투자비용 이상으로 발생하는 수익에 대해서는 투자사가 총 지분투자 비율 × 60%, 제작사가 나머지 40%를 가져가는 것으로 계산된다. 배급사가 메인 투자자일 경우에는 배급수수료와 수익을 동시에 가져가게 된다.

반대로 영화가 수익을 발생시키지 못했을  경우에는 그 손해의 100%를 투자자들이 감당한다. 여기서 제작사들은 수치상으로 손해를 보지는 않지만, 추후의 영화 제작에 있어 투자자들에 대한 제작 제안이 힘들어질 가능성이 있다.

업계에서는 통상적으로 100억 규모의 예산 투입을 가정할 때 관객수 200만 명~250만 명 정도를 손익분기점에 이르는 수준으로 본다.

출처 : 한겨레(https://www.hani.co.kr/arti/culture/culture_general/956608.html)

완성된 작품이 상영되는 것을 보고 영화를 사는 것이 아닌가 하고 많이들 착각하시기도 해요. 물론 그런 경우도 있습니다. 그러나 대부분은 완성 전에 영화가 없는 상황에서 계약이 진행됩니다. 특히 상업영화가 그렇고요. 예를 들어 '2019년에 <테이큰5>가 나온다'라는 프로젝트만 있습니다. 감독과 주인공만 정해져 있고 조연은 정해져 있지 않을 수 있죠. 이렇게 상품을 내놓습니다. 그 프로젝트만으로 많이들 구매하는 상황이고요. 정말 박한 프로젝트는 감독, 배우, 시놉시스 5줄 정도만 있는 경우도 있어요. 일반적인 케이스는 여기에 시나리오라고 하는 대본까진 나와 있습니다. 보통 감독, 배우, 시놉시스와 시나리오만 나온 상황에서 구매하는 경우가 80%이고, 완성작으로 보고 구매하는 건 15%, 남은 5%는 정말이지 프로젝트 소개 5줄만 보고 사야하는 경우도 있습니다.

공개된 정보가 적을수록 영화의 가격이 내려가지 않는다. 리스크는 구매자가 감수해야 할 부분이다. 영화업은 자율시장이기 때문에 좋은 상품이라고 할 때에는 시놉시스 5줄만 있어도 달려들어 경쟁할 때도 있습니다. 판매사와 구매사의 입장과는 별도로 자연적으로 경쟁이 커지면 가격도 올라갑니다. 판매사는 10만달러에 팔겠다는 생각으로 내놨는데 너무 경쟁이 붙어서 가격이 100만 달러까지 올라갈 수도 있다. 이렇게 가격이 높아져서 몇 십만 달러를 더 주고 사는 상황도 많이 일어난다.

영화 정보가 적으니 도박하는 심정으로 수입하는 회사들도 많다. 간혹 영화를 '숫자'로만 접근하는 회사도 있다. 개인적으로 그런 경우를 보면 마음이 좋지 않다. 최근 한국에서 그런 경향이 강해졌다. 높은 금액에 사면 그만큼 손익분기점이 높아지고, 수익 또한 내기 힘들다. 동시에 전반적인 업계의 시장 분위기에도 영향을 준다. 우선 계약은 땄는데, 금액이 많이 높아서 국내에 들어왔을 때, 큰 부담이 된다. 수입가 면에서 비용을 많이 써버리고 출발하는 개봉이 된다. 그만큼 마이너스가 난 상황에서 시작하는 거니까 영화가 흥행되면 좋겠지만 대부분이 그렇지 않다. IPTV나 DVD, 모바일에서 마이너스를 채울 수도 있지만 극장에서 손해 본 여화가 부가판권에서 잘되기란 쉽지 않다. 한국은 극장 흥행의 기준이 큰 나라라 수입할 때 과열 분위기에 휩쓸리지 않겠다는 마음을 잡아야 한다. 

수입업자들이 가는 마켓은 코엑스에 있는 박람회장 분위기를 떠올리시면 된다. 마켓 참여자만을 위한 상영이 따로 있습니다. 우리는 발부받은 배지를 들고 마켓 상영으로 영화를 봅니다. 물론 바이어들마다 스케줄이 있으니 마켓 상영 시간은 놓치면 페스티벌 상영으로 볼 수도 있습니다. 마켓 상영은 주로 아침 8시 반부터 오후 7시까지 하루 종일 꽉 잡혀 있어요. 그럼 계속 수백, 수천편의 영화들이 틀어지는 겁니다. 이번 베를린의 경우를 말씀드리면 극장 문 개수로 봤을 때, 한 30개관에서, 멀티플렉스 2개 정도와 3개 극장 5-6개가 동시에 돌아가는 거죠. 그러면 전 세계의 저 같은 바이어들이 마켓 상영 시간표를 보고 볼 영화를 선택해서 가는 겁니다. 누가 알려주지는 않죠. 알아서 잘 선택해서 가야 합니다. 동시간대에 여러 개가 상영되고 있으니 사고 싶은 영화 시간표를 확인해서 그 영화를 봐야겠죠. 완성된 영화만이 상영된다는 것이고, 완성되지 않은 영화는 상영할 수 없으니 그건 그거대로 따로 공부하고 판매사와 접촉해서 만나야 한다.

마켓 상영에는 프로모 상영이 있습니다. 아직 영화가 완전히 완성되지 않았지만 바이어에게 보여주고 싶을 때 하는 것을 프로모 상영이라고 부릅니다. 짧게는 1분, 길게는 15분 영상이 있습니다. 한 시간 동안 10편 정도 영화의 프로모를 모아서 틀어줍니다. 제가 타깃한 영화가 있다면 당연히 프로모 영상을 확인해야 합니다. 최초로 볼 수 있는 영상이니까요. 그 단계에서 너무 좋다면 바로 살 수 있습니다. 시간과 돈 싸움이기 때문에 판매자에게 빨리 연락해서 "관심이 있다"는 걸 보여줘야 합니다. 늦으면 다른 회사에 시간차로 계약을 빼앗길 수 있기 때문입니다.

출장 3주 전부터 사전 작업이 필요합니다. 얼마나 미리 준비가 되어 있는지가 중요합니다. 스케줄링이 잘되어 있고, 타깃 작품이 정해져 있어야 합니다. 지난 마켓에서부터 계속 주시하고 있는 작품, 새로 상품화된 영화들에 대한 취합, 종합, 타깃팅이 되어 있어야 출장 가서 좋은 구매를 할 수 있습니다. 수입을 한 다는 게 출장 가서 거기서 돌아보고, 영화를 보고 사면 된다고 생각할지 모르지만 그런 상황에서 얼마나 잘 구매할 수 있을까요.

수입은 사전 작업이 필수입니다. 몰랐던 영화가 현장에서 새로 발굴되는 케이스가 있지만, 그런 경우는 극소수입니다. 현장 가기 전에 정보를 통해 어떤 영화가 오는지 다 알고 있는 상황이죠. 이미 일반 관객도 어느 감독 신작이 언제 나오는지 스케줄을 알고 있잖아요. 한국에서도 같은 수입사 몇 십개가 같은 정보를 가지고 있습니다. 외신을 통해 정보를 업데이트하고 공부를 많이 한 사람들은 몇월에 어떤 감독이 촬영 들어가는지까지 압니다. 공부를 많이 하고 준비를 많이 한 사람과 아닌 사람이 마켓에서 차이가 있습니다. 또 거래처를 잘 활용해야 합니다. 언제 프로모 영상을 상영하는지, 언제 시작되고 이런 정보의 업데이트를 자신의 네트워킹을 통해 해두어야 합니다.

출처 : 캠퍼스씨네이십일(https://brunch.co.kr/@campuscine21/72)
