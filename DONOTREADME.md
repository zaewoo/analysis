# 프로젝트 기획안

## 임시 공간

- 전체적인 로직을 한눈에 확인할 수 있는 그림을 이곳에 넣으면 좋겠어요.
- 목차는 어디에 둘까?
- 기획 의도, 개발 동기, 주제 선정 이유 등은 어디에 둘까?

## 요약

### 주제
이 프로젝트의 주제는 머신러닝 모델을 이용하여 과거에 상영되었던 영화 데이터의 다양한 특성을 학습하고 앞으로 상영이 예정됭 있는 영화의 관객 수, 그리고 평점을 예측하는 것입니다. 

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

**IMDb Dataset Details** Each dataset is contained in a gzipped, tab-separated-values (TSV) formatted file in the UTF-8 character set. The first line in each file contains headers that describe what is in each column. A *‘\N’* is used to denote that a particular field is missing or null for that title/name. The available datasets are as follows: 

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
