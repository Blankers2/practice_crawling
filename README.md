# [ 데이터 수집 과제 제출 ]
- 스타벅스 사이트 -> 지점 정보 추출
- 데이터의 최종 형태 
    - [{'지점명':'GS타워','주소':'서울특별시 강남구 논현로 508 (역삼동)','시군구':'강남구','시도':'서울특별시','타입':'R|G|DT'},...]
- 이런 내용이 나오는 "데이터수집_본인이름.ipynb"  노트 파일 제출

## 워크플로우 설정
- html 구성을 확인하고 원하는 데이터를 어떻게 크롤링 할 것 인지 확인
- 원하는 데이터를 크롤링 할 방법을 확인 했으면 스텝별로 구분 후 코드 간소화 작업 시작
- 원하는 결과값?
    - dataframe : 리스트안의 딕셔너리 들 '[{ }, { }...]'
    - 데이터를 추출했을때 각 지점별 데이터가 있어야함
- level 4 웹크롤링으로 진행해야 될 것 같음
    - 지역검색을 해야하나 퀵검색을 해야하나???
    - 시도, 시군구 전부 ajax 스타일 확인 - 화면깜빡임 없음, 주소창X
    - 지역검색과 퀵검색이 따로 있음 검색종류를 바꿀때 깜빡임 발생
    - 일단 데이터를 추출해봐야 될것같음.
    - 원하는것은 지점별 정보
    - 이것저것 옵션을 바꿔봤으나 화면 깜빡임이 없었음. 주소창
- 페이지 html을 f12로 확인했을때
    - quickResultLstCon 클래스 안에 정보가 하나씩 들어가있음
    - 하위항목의 result_details 클래스에서 주소와 전화 번호 확인
    
- html 구성확인
    - class"loca_step1" 으로 시/도 를 구분
        - 시/도는 "sido_arae_box" 클래스 하위의 "set_sido_cd_btn" 클래스로 구분 되어있음
    - 시/도를 클릭했을때 clsss"loca_step2"로 구/군을 구분
        - 구/군은 "loca_step2_cont" 클래스 하위의 "set_gugun_cd_btn" 클래스로 구분 되어있음

### 최초 오류에 따른 변경사항
- 퀵검색? 지역검색? 퀵검색 url로 들어가면 시/도 선택 html 크롤링이 안됨
    - "~quick"에서 "https://www.starbucks.co.kr/store/store_map.do?disp=locale" 로 변경
- TODO를 활용하려 했으나 반응형은 하나씩 실행되어 먹히지 않음


# 오류없이 모든 지점정보 데이터 추출 완료!
    - 현재 모든 지점 데이터를 추출하는 것은 너무 오랜시간이 걸리기 때문에 3개 지역을 슬라이싱하여 테스트
    - for i in sido_click[2:5]: => for i in sido_click[:]: 로 변경해 모든 지점 추출 가능!
