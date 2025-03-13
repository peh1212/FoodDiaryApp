## :blue_book:  [1. 식당정보 CSV 파일과 이미지 파일을 DB에 저장하기](https://github.com/peh1212/HannipmanApp/blob/main/1.%20HannipmanApp.zip) <br>
1. 식당 정보를 restaurantDB.csv 파일로 작성하여 `(프로젝트폴더)/src/main/resources/data` 폴더에 저장
### restaurantDB.csv
```Java
id,diary,name,menu,price,rating,kategorie,phonenumber,businesshours,closeddays,breaktime,kiosk,place,latitude,longitude
1,1,도담초밥,"활어초밥,생연어초밥,모듬초밥,민물장어초밥,한우초밥,초새우초밥,연어불초밥","19000,18000,18000,19000,19000,16000,19000",4.6,일식,0507-1332-0720,11:30~22:30,없음,14:30~15:30,없음,인천 서구 탁옥로 17,37.5442282023004,126.671411943773
2,0,국수궁전,"잔치국수,비빔국수,쫄면,냉국수,비빔밥,부추전","6000,7000,7000,7000,7000,7000,7000",4.5,한식,0507-1349-9569,08:00~20:00,월요일,없음,없음,인천 서구 심곡로 165,37.547723285976,126.681652855522
3,0,감자탕마을,"감자탕(소),등뼈해물찜(소),삼계탕,뼈해장국,생고기김치찌개,양푼비빔밥,냉면","35000,45000,14000,10000,10000,10000,10000",4.4,한식,0507-1448-0645,09:30~21:30,수요일,없음,없음,인천 서구 대평로 5,37.5470754604579,126.676444921014
4,0,성원닭갈비,"닭갈비(소),닭갈비(중),닭갈비(대),치즈볶음밥,알밥,라면 떡사리,쫄면 우동사리","29000,36000,44000,4000,4000,2000,2000",4.5,한식,032-567-8996,10:30~24:30,없음,없음,없음,인천 서구 탁옥로 49,37.5440877141166,126.675082992027
5,1,교동짬뽕,"교동짬뽕,찹쌀탕수육 미니,삼선짬뽕,짜장면,쟁반짜장,우동","9500,14000,13000,7000,9500,9500",4.4,중식,0507-1442-8894,11:00~21:00,월요일,없음,있음,인천 서구 심곡로 35,37.542395856533,126.67346149477
6,0,촌장골,"소 왕 갈비,한우 설화꽃살,촌장 돼지양념구이,왕 갈비탕(2대),차돌 된장찌개,정통 함흥냉면","48000,62000,19000,17000,10000,11000",4.3,한식,032-562-4343,11:00~22:00,없음,없음,없음,인천 서구 서곶로 296,37.5440759399952,126.677163071146
7,0,태백산,"한돈왕갈비,한우 1++ 갈비살,소왕갈비,한우 1++ 등심,명품삼겹살,한우육회","21000,43000,45000,53000,18000,33000",4.5,한식,032-567-3331,11:00~22:00,없음,없음,없음,인천 서구 서곶로315번길 26,37.5460050248938,126.673903592051
8,0,박군술상,"스지탕,육회물회,한근탕수육,차돌짬뽕파스타,쫄뱅이,생고기김치찌개,피꼬막초무침","26000,18000,14000,15000,15000,15000,15000",4.5,한식,0507-1405-9355,17:00~23:50,일요일,없음,없음,인천 서구 탁옥로 10,37.5439021680194,126.670487197643
9,0,잊지못회,"광어(1인),우럭(1인),연어(1인),광어+우럭(1인),광어+연어(1인),우럭+연어(1인)","23000,23000,25000,23000,25000,25000",4.4,한식,0507-1360-7715,14:00~24:00,없음,없음,없음,인천 서구 대평로8번길 2,37.5474120340164,126.676332342388
10,1,타코로와,"타코로와 타코앤후라이(6알),쭈꾸미 타코야끼(6알),마라 타코야끼(6알),오리지널 타코야끼(6알),두근두근 랜덤박스(10알),포테이토 모임","7000,8000,4500,4000,8000,5000",4.3,일식,0507-1492-5279,12:00~24:00,없음,없음,없음,인천 서구 탁옥로 21,37.5442393571378,126.671826837611
11,0,처비스,"마르게리타,페퍼로니 피자,하와이안 피자,고르곤졸라,치즈크러스트 피자,BBQ 치킨 피자,불고기 피자","18000,17000,24000,19000,21000,22000,20000",4.5,양식,070-4792-8285,00:00~24:00,없음,없음,없음,인천 서구 청라커낼로 270,37.5325339360697,126.644964478604
12,0,구루멘,"쇼유라멘,돈코츠라멘,미소라멘,카라이라멘,츠케멘,탄탄멘,야끼소바","12500,13000,11000,14000,15000,13000,13500",4.6,일식,0507-1315-5948,11:30~20:00,없음,15:30~17:00,없음,인천 서구 청라커낼로 270,37.5325338360697,126.644964578604
13,0,레이중화요리,"짜장면,짬뽕,탕수육,볶음밥,깐풍기,양장피,유린기","8000,9000,18000,12000,19000,22000,21000",4.2,중식,0507-1392-3889,11:00~21:30,월요일,15:30~17:00,없음,인천 서구 청라루비로42번길 5-21,37.5294772752587,126.642327230062
14,0,진심낙곱새,"낙곱새,낙새볶음,곱창볶음,소곱창전골,버섯불고기,우삼겹볶음","22000,24000,23500,19000,21000,22000",4.1,한식,032-563-7683,11:30~23:00,월요일,없음,없음,인천 서구 중봉대로612번길 10-8,37.5333635711451,126.650734729401
15,1,고복샤브샤브,"한우샤브샤브,해물샤브샤브,버섯샤브샤브,월남쌈,칼국수,볶음밥,매운 샤브샤브","27000,26000,25000,22000,10000,7000,28000",4.6,일식,0507-1310-3008,11:00~22:00,없음,없음,없음,인천 서구 청라루비로42번길 6-4,37.5285351965312,126.640962603598
16,0,모락핌,"가케우동,카레우동,붓가케우동,냉우동,유부우동,텐푸라우동","9000,9500,8500,8800,7500,10000",4.8,일식,032-710-1025,11:30~01:00,월요일,15:00~17:00,없음,인천 서구 청라커낼로260번길 7-15,37.532612112787,126.646185435766
17,0,육미관,"갈비구이,박포구이,한우등심,소고기차돌박이,된장찌개,육회비빔밥","29000,31000,45000,37000,9000,12000",4.8,한식,0507-1348-0696,16:00~24:00,없음,없음,없음,인천 서구 청라커낼로233번길 12,37.5294868260845,126.643399916794
18,0,구공숙성돼지,"숙성삼겹살,목살,항정살,가브리살,차돌박이,된장찌개,계란찜","18000,19000,20000,21000,22000,8000,5000",4.4,한식,0507-1489-0994,12:00~22:00,없음,없음,없음,인천 서구 청라커낼로233번길 14-1,37.5294864043422,126.64323044474
19,0,동대문엽기떡볶이,"엽기떡볶이,로제떡볶이,치즈떡볶이,엽기오뎅,엽기닭발,주먹밥","13000,14000,15000,11000,20000,9000",4.0,한식,0507-1488-2622,11:00~22:30,없음,없음,없음,인천 서구 중봉대로 610,37.533887048764,126.650277577612
20,1,미분당,"소고기 쌀국수,닭고기 쌀국수,매운 쌀국수,분짜,월남쌈,반미","15000,14000,16000,17000,11000,8000",4.3,중식,010-3941-0516,11:00~21:00,없음,없음,없음,인천 서구 청라라임로 85,37.5346639378439,126.652614505895
21,0,써브웨이,"안창비프,에그 슬라이스,이탈리안 비엠티,터키 베이컨 아보카도,로티세리 바비큐 치킨,스파이시 쉬림프","10400,5200,6900,8400,7500,7900",4.3,양식,032-565-2481,08:00~22:00,없음,없음,없음,인천 서구 탁옥로 50,37.5437286275368,126.675035780574
22,0,어푸키친,"알리오 올리오,쉬림프 오일 파스타,바질 오일 파스타,봉골레 파스타,베이컨 토마토 파스타,청양 베이컨 크림 파스타","14000,17000,16000,21000,16000,15000",4.5,양식,0507-1363-0291,11:00~21:00,월요일,없음,있음,인천 서구 승학로 243,37.5442217804822,126.672473261192
23,0,폰더스트,"폰더스트 하우스스테이크 정식,프라임채끝스테이크 정식,목살스테이크 정식,투움바파스타,알리오올리오,바질크림뇨끼","21900,36900,15900,15900,13900,14900",4.4,양식,0507-1314-8320,11:00~22:00,없음,없음,없음,인천 서구 탁옥로 16,37.543890871844,126.671380382949
24,0,비스트로 페르레이,"니도 디 루꼴라 샐러드,깔라마리 감바스,살치살 스테이크 200g,카펠리니 안젤로 파스타,콰트로 풍기 샐러드,리코타 치즈 샐러드","18000,23000,40000,20000,18000,18000",4.6,양식,0507-1398-3666,11:30~22:00,없음,15:00~17:00,있음,인천 서구 크리스탈로 100,37.5338603917033,126.636936327482
25,0,프로포레,"뚝배기 토마토 파스타,스테이크 피자,리코타 치즈 샐러드,해물 스파이시 필라프,전복리조또","16000,23000,14000,12500,16000",4.3,양식,0507-1315-8181,08:00~22:00,없음,없음,있음,인천 서구 중봉대로 490,37.5227614575062,126.650465263705
26,0,식가짬뽕,"짜장면,홍합짬뽕,삼선짬뽕,게살볶음밥,잡탕밥","8500,11000,14000,10000,14000",4.4,중식,0507-1379-8973,11:00~21:00,수요일,15:00~17:00,있음,인천 서구 승학로 278,37.5470039273843,126.673827157665
27,0,이비가짬뽕,"국민짬뽕,이비가짬뽕,백짬뽕,한우짜장,고기짬뽕,볶음짬뽕","9000,11000,11000,9000,11000,12000",4.4,중식,032-566-7484,11:00~21:00,없음,없음,있음,인천 서구 서곶로 322,37.5463926279011,126.677345564302
28,0,고구려짬뽕,"옛날짬뽕,옛날짜장,군만두,탕수육(소),옛날볶음밥,불짬뽕","9000,6500,6500,19000,8500,9500",4.4,중식,032-569-6253,09:30~21:00,없음,없음,없음,인천 서구 중봉대로 763,37.5479910532792,126.649761198111
29,0,한신우동,"즉석우동,어묵우동,김치우동,왕돈까스,매운돈까스,치즈 감자채전","8000,9000,9000,13000,13000,12000",4.3,일식,0507-1484-2737,11:30~04:00,없음,14:00~17:00,없음,인천 서구 서곶로301번길 13,37.5444239179483,126.675098393164
30,0,라쿤카츠,"생등심카츠정식,생안심카츠정식,치즈롤카츠정식,고구마치즈롤카츠정식,생선카츠정식","9300,9800,9800,9900,9300",4.4,일식,032-203-6667,10:00~21:00,토요일,없음,없음,인천 서구 용두산로13번길 5,37.5447424631365,126.67140210512
```
`참고(위도 경도 찾기)` : https://www.findlatlng.org/ <br>

2. 이미지 파일들을 `(프로젝트폴더)/src/main/resources/images` 폴더에 저장 <br>
![image](https://github.com/user-attachments/assets/b8c88cad-9c7e-4ba0-8072-3b93e8cfc337) <br>
`사진출처` : 네이버지도 리뷰 <br>

3. dependencies 설정 <br>
### build.gradle
```Java
implementation 'com.opencsv:opencsv:5.6'
implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
implementation 'org.springframework.boot:spring-boot-starter-mustache'
implementation 'org.springframework.boot:spring-boot-starter-web'
compileOnly 'org.projectlombok:lombok'
runtimeOnly 'com.h2database:h2'
runtimeOnly 'org.postgresql:postgresql'
annotationProcessor 'org.projectlombok:lombok'
testImplementation 'org.springframework.boot:spring-boot-starter-test'
testRuntimeOnly 'org.junit.platform:junit-platform-launcher'
```
4. H2 DB 설정 <br>
### application.properties
```Java
spring.application.name=HannipmanApp
spring.datasource.url=jdbc:h2:mem:testdb
spring.h2.console.enabled=true
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=password
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.jpa.hibernate.ddl-auto=update
```
5. 식당정보 엔티티와 레포지토리 구현 <br>
### Restaurant.java
```Java
@Entity
@Getter
@Setter
@NoArgsConstructor
@AllArgsConstructor
@ToString
public class Restaurant {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;  // 식당 DB 기본키, 자동증가

    @Column
    private boolean diary;  // 일기 작성 여부

    @Column
    private String name;  // 식당 이름

    @ElementCollection
    private List<String> menu;  // 식당 메뉴 리스트

    @ElementCollection
    private List<Integer> price;  // 식당 메뉴 가격 리스트

    @Column
    private String kategorie;  // 카테고리(한식, 중식, 일식, 양식)

    @Column
    private String phoneNumber;  // 연락처

    @Column
    private String businessHours;  // 영업시간

    @Column
    private String closedDays;  // 휴무일

    @Column
    private String breakTime;  // 브레이크타임

    @Column
    private String kiosk;  // 키오스크 유무

    @Column
    private String place;  // 주소

    @Column
    private Double rating;  // 별점

    @Column
    private Double latitude;  // 위도

    @Column
    private Double longitude;  // 경도

    @Lob
    @Column(columnDefinition = "LONGBLOB")  // MySQL DB 저장시 LONGLOB타입으로 저장
    private byte[] image;  // 식당 이미지
}

interface RestaurantRepo extends JpaRepository<Restaurant, Long> {
}
```

6. 식당정보 csv파일 데이터와 이미지 데이터를 DB(H2)에 저장 <br>
### CSVDataLoader.java
```Java
@Service
public class CSVDataLoader {

    @Autowired
    private RestaurantRepo restaurantRepo;

    @PostConstruct
    public void loadDataFromCSVAndImages() {
        String csvFilePath = "src/main/resources/data/restaurantDB.csv";
        String imageDirectoryPath = "src/main/resources/images/";

        try (CSVReader reader = new CSVReader(new FileReader(csvFilePath))) {
            String[] line;
            reader.readNext(); // 헤더 건너뛰기

            while ((line = reader.readNext()) != null) {
                Restaurant restaurant = new Restaurant();
                restaurant.setDiary(line[1].equals("1"));
                restaurant.setName(line[2]);
                restaurant.setMenu(Arrays.asList(line[3].split(",")));
                restaurant.setPrice(parsePrices(line[4]));
                restaurant.setRating(Double.parseDouble(line[5]));
                restaurant.setKategorie(line[6]);
                restaurant.setPhoneNumber(line[7]);
                restaurant.setBusinessHours(line[8]);
                restaurant.setClosedDays(line[9]);
                restaurant.setBreakTime(line[10]);
                restaurant.setKiosk(line[11]);
                restaurant.setPlace(line[12]);
                restaurant.setLatitude(Double.parseDouble(line[13]));
                restaurant.setLongitude(Double.parseDouble(line[14]));

                // 이미지 파일 읽어오기
                String imageFileName = line[0] + ".jpg"; // 예: "1.jpg"
                File imageFile = new File(imageDirectoryPath + imageFileName);
                if (imageFile.exists()) {
                    byte[] imageData = FileCopyUtils.copyToByteArray(new FileInputStream(imageFile));
                    restaurant.setImage(imageData);
                } else {
                    System.out.println(imageFileName + " 파일을 찾을 수 없습니다.");
                }

                restaurantRepo.save(restaurant);
            }
            System.out.println("CSV 데이터와 이미지를 성공적으로 저장했습니다!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    private List<Integer> parsePrices(String priceData) {
        String[] prices = priceData.split(",");
        List<Integer> priceList = new ArrayList<>();
        for (String price : prices) {
            priceList.add(Integer.parseInt(price));
        }
        return priceList;
    }
}
```

7. DB에 저장된 식당 정보들과 이미지들을 html에서 조회할 수 있는 컨트롤러 구현 <br>
(DB 내용 확인용) <br>
### RestaurantController.java
```Java
@RestController
@RequestMapping("/restaurants")
public class RestaurantController {

    @Autowired
    private RestaurantRepo restaurantRepo;

    @GetMapping
    public ResponseEntity<?> getAllRestaurants(HttpServletRequest request) {
        List<Restaurant> restaurants = restaurantRepo.findAll();

        // HTML 형태로 데이터를 반환
        StringBuilder htmlResponse = new StringBuilder();
        htmlResponse.append("<html><head><title>Restaurants</title></head><body>");
        htmlResponse.append("<h1>Restaurant List</h1>");
        htmlResponse.append("<ul>");

        for (Restaurant restaurant : restaurants) {
            htmlResponse.append("<li>");
            htmlResponse.append("<h2>").append(restaurant.getName()).append("</h2>");
            if (restaurant.getImage() != null) {
                String imageUrl = request.getScheme() + "://" + request.getServerName() + ":" + request.getServerPort()
                        + "/restaurants/image/" + restaurant.getId();
                htmlResponse.append("<img src=\"").append(imageUrl).append("\" alt=\"Image\" style=\"width:200px;\"/>");
            } else {
                htmlResponse.append("<p>No image available</p>");
            }
            htmlResponse.append("<p><strong>id:</strong> ").append(restaurant.getId()).append("</p>");
            htmlResponse.append("<p><strong>Menu:</strong> ").append(String.join(", ", restaurant.getMenu())).append("</p>");
            htmlResponse.append("<p><strong>Price:</strong> ").append(restaurant.getPrice()).append("</p>");
            htmlResponse.append("<p><strong>Rating:</strong> ").append(restaurant.getRating()).append("</p>");
            htmlResponse.append("<p><strong>Location:</strong> ")
                    .append(restaurant.getLatitude()).append(", ").append(restaurant.getLongitude())
                    .append("</p>");
            htmlResponse.append("<p><strong>Category:</strong> ").append(restaurant.getKategorie()).append("</p>");
            htmlResponse.append("<p><strong>Phone Number:</strong> ").append(restaurant.getPhoneNumber()).append("</p>");
            htmlResponse.append("<p><strong>Business Hours:</strong> ").append(restaurant.getBusinessHours()).append("</p>");
            htmlResponse.append("<p><strong>Closed Days:</strong> ").append(restaurant.getClosedDays()).append("</p>");
            htmlResponse.append("<p><strong>Break Time:</strong> ").append(restaurant.getBreakTime()).append("</p>");
            htmlResponse.append("<p><strong>Kiosk:</strong> ").append(restaurant.getKiosk()).append("</p>");
            htmlResponse.append("<p><strong>Place:</strong> ").append(restaurant.getPlace()).append("</p>");

            htmlResponse.append("</li>");
        }

        htmlResponse.append("</ul></body></html>");
        return ResponseEntity.ok(htmlResponse.toString());
    }

    @GetMapping("/image/{id}")
    public ResponseEntity<byte[]> getImage(@PathVariable Long id) {
        Optional<Restaurant> restaurantOpt = restaurantRepo.findById(id);

        if (restaurantOpt.isPresent() && restaurantOpt.get().getImage() != null) {
            byte[] imageData = restaurantOpt.get().getImage();
            return ResponseEntity.ok()
                    .contentType(MediaType.IMAGE_JPEG)
                    .body(imageData);
        } else {
            return ResponseEntity.notFound().build();
        }
    }
}
```
![image](https://github.com/user-attachments/assets/31e24725-66d2-4dad-b08c-c46c158764cc) <br>
<br>


## :blue_book:  [2. MySQL DB 연동하기](https://github.com/peh1212/HannipmanApp/blob/main/2.%20HannipmanApp.zip) <br>
1. 설치하기 <br>
`참고 링크` : https://code-angie.tistory.com/158 <br>
설치 시 입력한 비밀번호를 기억해야한다<br>

2. 스프링부트와 연동하기 <br>
MySQL Workbench에서 커넥션을 추가한다. <br>
![image](https://github.com/user-attachments/assets/9942a091-6043-41f6-8d7d-53ad5bae3b49) <br><br>
DB를 생성한다. <br>
![image](https://github.com/user-attachments/assets/c87d4edf-cb4b-402b-8dd5-e32cb6a72e3f) <br><br>

`application.properties`에 설정을 추가한다. <br>
H2 DB와 겹치는 설정은 지워준다. <br>
### application.properties
```Java
spring.datasource.url=jdbc:mysql://[서버주소:포트번호]/[DB이름]?useSSL=false&serverTimezone=UTC
spring.datasource.username=[사용자이름]
spring.datasource.password=[비밀번호]
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.hibernate.ddl-auto=update
spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect
```
`[서버주소:포트번호]` : 커넥션 추가에서 입력한 서버주소와 포트번호 <br>
`[DB이름]` : 위에서 생성한 DB 이름 <br>
`[사용자이름]` : 따로 설정 안했을 시 기본값 root <br>
`[비밀번호]` : 설치할때 입력한 비밀번호 <br><br>

`build.gradle` dependencies에 mysql 의존성 추가 후 Gradle Sync하기 <br>
### build.gradle
```Java
implementation 'mysql:mysql-connector-java:8.0.29'
```

<br>
Restaurant 엔티티에서 image의 컬럼을 `LONGBLOB` 타입으로 설정해준다. <br>
(그냥 실행하면 H2 DB에서는 잘 되지만 MySQL에서는 오류가 뜨는데 둘이 데이터 처리방식이 달라서 그렇다고 함) <br>

### Restaurant.java
```Java
@Lob
@Column(columnDefinition = "LONGBLOB")
private byte[] image;
```
스프링부트에서 실행을 한다. <br>
![image](https://github.com/user-attachments/assets/4bb1d1ce-bd47-4e86-98cd-642c782fbb18) <br>
MySQL DB에서 데이터가 잘 저장된 것을 확인한다. <br><br>

3. 중복저장 피하기 <br>
스프링부트 서버를 실행할때마다 똑같은 데이터가 30개씩 늘어나므로 CSVDataLoader에 중복저장을 피하는 로직을 추가한다. <br>
### CSVDataLoader.java
```Java
@Service
public class CSVDataLoader {

    @Autowired
    private RestaurantRepo restaurantRepo;

    @PostConstruct
    public void loadDataFromCSVAndImages() {
        String csvFilePath = "src/main/resources/data/restaurantDB.csv";
        String imageDirectoryPath = "src/main/resources/images/";

        try (CSVReader reader = new CSVReader(new FileReader(csvFilePath))) {
            String[] line;
            reader.readNext(); // 헤더 건너뛰기

            while ((line = reader.readNext()) != null) {

                // 식당 이름으로 중복검사
                String restaurantName = line[2];
                if (restaurantRepo.existsByName(restaurantName)) {
                    System.out.println("중복된 레스토랑: " + restaurantName);
                    continue; // 이미 존재하면 해당 데이터를 건너뛰고 다음 데이터로 넘어감
                }

                Restaurant restaurant = new Restaurant();
                restaurant.setDiary(line[1].equals("1"));
                restaurant.setName(line[2]);
                restaurant.setMenu(Arrays.asList(line[3].split(",")));
                restaurant.setPrice(parsePrices(line[4]));
                restaurant.setRating(Double.parseDouble(line[5]));
                restaurant.setKategorie(line[6]);
                restaurant.setPhoneNumber(line[7]);
                restaurant.setBusinessHours(line[8]);
                restaurant.setClosedDays(line[9]);
                restaurant.setBreakTime(line[10]);
                restaurant.setKiosk(line[11]);
                restaurant.setPlace(line[12]);
                restaurant.setLatitude(Double.parseDouble(line[13]));
                restaurant.setLongitude(Double.parseDouble(line[14]));

                // 이미지 파일 읽어오기
                String imageFileName = line[0] + ".jpg"; // 예: "1.jpg"
                File imageFile = new File(imageDirectoryPath + imageFileName);
                if (imageFile.exists()) {
                    byte[] imageData = FileCopyUtils.copyToByteArray(new FileInputStream(imageFile));
                    restaurant.setImage(imageData);
                } else {
                    System.out.println(imageFileName + " 파일을 찾을 수 없습니다.");
                }

                restaurantRepo.save(restaurant);
            }
            System.out.println("CSV 데이터와 이미지를 성공적으로 저장했습니다!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    private List<Integer> parsePrices(String priceData) {
        String[] prices = priceData.split(",");
        List<Integer> priceList = new ArrayList<>();
        for (String price : prices) {
            priceList.add(Integer.parseInt(price));
        }
        return priceList;
    }
}
```

<br>

### RestaurantRepo
```Java
interface RestaurantRepo extends JpaRepository<Restaurant, Long> {
    boolean existsByName(String name);
}
```

<br><br>

## :blue_book:  [3. 안드로이드 스튜디오에서 구글맵을 띄우고 식당 정보 DB에 저장된 위도/경도에 맞게 지도에 위치 표시하기]() <br>
[안드로이드스튜디오](https://github.com/peh1212/HannipmanApp/blob/main/3.%20Android%20Studio%20-%20HannipmanApp.zip) [스프링부트](https://github.com/peh1212/HannipmanApp/blob/main/3.%20Spring%20Boot%20-%20HannipmanApp.zip)
1. dependencies 추가 <br>
### build.gradle.kts
```Java
implementation("com.google.android.gms:play-services-maps:17.0.1")
```

2. Manifest에 permission 추가 <br>
### AndroidManifest.xml
```Java
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>

<application
(...)
android:usesCleartextTraffic="true"
(...)
</application>
```

3. 구글맵 API Key 추가 <br>
```Java
<application
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name">
    
    <!-- Google Maps API Key 설정 -->
    <meta-data
        android:name="com.google.android.geo.API_KEY"
        android:value="API_KEY" />
    
</application>
```

4. 구글맵을 띄울 레이아웃 만들기 <br>
### activity_main.xml
```Java
<fragment
        android:id="@+id/map"
        android:name="com.google.android.gms.maps.SupportMapFragment"
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="1"/>
```

5. 액티비티 구현 <br>
예시로 서울에 마커를 찍어본다. <br>
```Java
public class MainActivity extends FragmentActivity implements OnMapReadyCallback {

    private GoogleMap mMap;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // SupportMapFragment를 얻고, 지도를 비동기적으로 초기화
        SupportMapFragment mapFragment = (SupportMapFragment) getSupportFragmentManager()
                .findFragmentById(R.id.map);
        mapFragment.getMapAsync(this);
    }

    // 지도가 준비되었을 때 호출
    @Override
    public void onMapReady(GoogleMap googleMap) {
        mMap = googleMap;

        // 위도, 경도 데이터 (예시: 서울)
        LatLng location = new LatLng(37.5665, 126.9780); // 서울의 위도, 경도

        // 지도에 마커 추가
        mMap.addMarker(new MarkerOptions().position(location).title("서울"));
        mMap.moveCamera(CameraUpdateFactory.newLatLngZoom(location, 10)); // 10은 줌 레벨
    }
}
```
![image](https://github.com/user-attachments/assets/fb1d2697-eb63-4b77-8adb-16dcbe48f087) <br>

6. 스프링부트에서 식당정보 DB를 가져와 위도, 경도에 맞는 위치에 마커 표시하기 <br><br>
dependencies에 retrofit 추가 <br>
### build.gradle.kts
```Java
implementation("com.squareup.retrofit2:retrofit:2.9.0")
implementation("com.squareup.retrofit2:converter-gson:2.9.0")
```
스프링부트에서 RestaurantController에 위치정보를 반환하는 엔드포인트 정의 <br>
### RestaurantController.java
```Java
@RestController
@RequestMapping("/restaurants")
public class RestaurantController {

    @Autowired
    private RestaurantRepo restaurantRepo;

    (...)

    @GetMapping("/locations")
        public List<RestaurantDTO> getRestaurantLocations() {
            return restaurantRepo.findAll().stream()
                    .map(r -> new RestaurantDTO(r.getLatitude(), r.getLongitude(), r.getName()))
                    .collect(Collectors.toList());
        }
```

RestaurantDTO 정의 <br>
### Restaurant.java
```Java
@Data
@AllArgsConstructor
@NoArgsConstructor
class RestaurantDTO {
    private Double latitude;
    private Double longitude;
    private String name;
}
```

<br>

안드로이드 스튜디오에서 RestaurantDTO 정의 <br>
안드로이드에서는 Lombok이 없으므로 Constructor와 Getter Setter를 직접 작성해준다. <br>
### RestaurantDTO.java
```Java
public class RestaurantDTO {
    private Double latitude;
    private Double longitude;
    private String name;

    // 기본 생성자
    public RestaurantDTO() {
    }

    // 파라미터가 있는 생성자
    public RestaurantDTO(Double latitude, Double longitude, String name) {
        this.latitude = latitude;
        this.longitude = longitude;
        this.name = name;
    }

    // Getter와 Setter 메서드
    public Double getLatitude() {
        return latitude;
    }

    public void setLatitude(Double latitude) {
        this.latitude = latitude;
    }

    public Double getLongitude() {
        return longitude;
    }

    public void setLongitude(Double longitude) {
        this.longitude = longitude;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```
레트로핏 설정을 위한 인터페이스와 서비스 클래스 작성 <br>
### RestaurantService.java
```Java
public interface RestaurantService {
    @GET("/restaurants/locations")
    Call<List<RestaurantDTO>> getRestaurantLocations();
}
```

### RetrofitClient.java
```Java
public class RetrofitClient {
    private static final String BASE_URL = "http://10.0.2.2:8080"; // 안드로이드 에뮬레이터 주소

    private static Retrofit retrofit;

    public static Retrofit getInstance() {
        if (retrofit == null) {
            retrofit = new Retrofit.Builder()
                    .baseUrl(BASE_URL)
                    .addConverterFactory(GsonConverterFactory.create())
                    .build();
        }
        return retrofit;
    }
}
```
메인액티비티 수정 <br>
### MainActivity.java
```Java
public class MainActivity extends FragmentActivity implements OnMapReadyCallback {

    private GoogleMap mMap;
    private RestaurantService restaurantService;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Retrofit 초기화
        restaurantService = RetrofitClient.getInstance().create(RestaurantService.class);

        // SupportMapFragment를 얻고, 지도를 비동기적으로 초기화
        SupportMapFragment mapFragment = (SupportMapFragment) getSupportFragmentManager()
                .findFragmentById(R.id.map);
        mapFragment.getMapAsync(this);
    }

    // 지도가 준비되었을 때 호출
    @Override
    public void onMapReady(GoogleMap googleMap) {
        mMap = googleMap;

        // 서버에서 레스토랑 위치 데이터 가져오기
        restaurantService.getRestaurantLocations().enqueue(new Callback<List<RestaurantDTO>>() {
            @Override
            public void onResponse(Call<List<RestaurantDTO>> call, Response<List<RestaurantDTO>> response) {
                if (response.isSuccessful() && response.body() != null) {
                    for (RestaurantDTO restaurant : response.body()) {
                        LatLng location = new LatLng(restaurant.getLatitude(), restaurant.getLongitude());
                        mMap.addMarker(new MarkerOptions().position(location).title(restaurant.getName()));
                    }
                    if (!response.body().isEmpty()) {
                        LatLng firstLocation = new LatLng(response.body().get(0).getLatitude(), response.body().get(0).getLongitude());
                        mMap.moveCamera(CameraUpdateFactory.newLatLngZoom(firstLocation, 10));
                    }
                }
            }

            @Override
            public void onFailure(Call<List<RestaurantDTO>> call, Throwable t) {
                // 실패 시 처리
                Log.e("Retrofit", "Failed", t);
            }
        });
    }
}
```
<br>

![image](https://github.com/user-attachments/assets/07f84a33-e757-4d03-ab3c-7fc92ba04dfb) <br>
