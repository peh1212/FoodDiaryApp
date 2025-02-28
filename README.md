### :bulb: 식당정보 CSV 파일과 이미지 파일을 DB에 저장하기 <br>
1. 식당 정보를 restaurantDB.csv 파일로 작성하여 `(프로젝트폴더)/src/main/resources/data` 폴더에 저장
### restaurantDB.csv
```Java
id,name,menu,price,rating,latitude,longitude
1,도담초밥,"활어초밥,생연어초밥,모듬초밥,민물장어초밥,한우초밥,초새우초밥,연어불초밥","19000,18000,18000,19000,19000,16000,19000",4.6,37.5442282023004,126.671411943773
2,국수궁전,"잔치국수,비빔국수,쫄면,냉국수,비빔밥,부추전","6000,7000,7000,7000,7000,7000,7000",4.5,37.547723285976,126.681652855522
3,감자탕마을,"감자탕(소),등뼈해물찜(소),삼계탕,뼈해장국,생고기김치찌개,양푼비빔밥,냉면","35000,45000,14000,10000,10000,10000,10000",4.4,37.5470754604579,126.676444921014
4,성원닭갈비,"닭갈비(소),닭갈비(중),닭갈비(대),치즈볶음밥,알밥,라면 떡사리,쫄면 우동사리","29000,36000,44000,4000,4000,2000,2000",4.5,37.5440877141166,126.675082992027
5,교동짬뽕,"교동짬뽕,찹쌀탕수육 미니,삼선짬뽕,짜장면,쟁반짜장,우동","9500,14000,13000,7000,9500,9500",4.4,37.542395856533,126.67346149477
6,촌장골,"소 왕 갈비,한우 설화꽃살,촌장 돼지양념구이,왕 갈비탕(2대),차돌 된장찌개,정통 함흥냉면","48000,62000,19000,17000,10000,11000",4.3,37.5440759399952,126.677163071146
7,태백산,"한돈왕갈비,한우 1++ 갈비살,소왕갈비,한우 1++ 등심,명품삼겹살,한우육회","21000,43000,45000,53000,18000,33000",4.5,37.5460050248938,126.673903592051
8,박군술상,"스지탕,육회물회,한근탕수육,차돌짬뽕파스타,쫄뱅이,생고기김치찌개,피꼬막초무침","26000,18000,14000,15000,15000,15000,15000",4.5,37.5439021680194,126.670487197643
9,잊지못회,"광어(1인),우럭(1인),연어(1인),광어+우럭(1인),광어+연어(1인),우럭+연어(1인)","23000,23000,25000,23000,25000,25000",4.4,37.5474120340164,126.676332342388
10,타코로와,"타코로와 타코앤후라이(6알),쭈꾸미 타코야끼(6알),마라 타코야끼(6알),오리지널 타코야끼(6알),두근두근 랜덤박스(10알),포테이토 모임","7000,8000,4500,4000,8000,5000",4.3,37.5442393571378,126.671826837611
```
2. 이미지 파일들을 `(프로젝트폴더)/src/main/resources/images` 폴더에 저장 <br>
![image](https://github.com/user-attachments/assets/4719ada6-9b15-41c7-9acf-eab2262435c7) <br>

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
    private Long id;

    @Column
    private String name;

    @ElementCollection
    private List<String> menu;

    @ElementCollection
    private List<Integer> price;

    @Column
    private Double rating;

    @Column
    private Double latitude;

    @Column
    private Double longitude;

    @Lob
    @Column
    private byte[] image;
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
                restaurant.setName(line[1]);
                restaurant.setMenu(Arrays.asList(line[2].split(",")));
                restaurant.setPrice(parsePrices(line[3]));
                restaurant.setRating(Double.parseDouble(line[4]));
                restaurant.setLatitude(Double.parseDouble(line[5]));
                restaurant.setLongitude(Double.parseDouble(line[6]));

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

7. DB에 저장된 식당 정보들과 이미지들을 조회할 수 있는 컨트롤러 구현 <br>
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
            htmlResponse.append("<p><strong>Menu:</strong> ").append(String.join(", ", restaurant.getMenu())).append("</p>");
            htmlResponse.append("<p><strong>Price:</strong> ").append(restaurant.getPrice()).append("</p>");
            htmlResponse.append("<p><strong>Rating:</strong> ").append(restaurant.getRating()).append("</p>");
            htmlResponse.append("<p><strong>Location:</strong> ")
                    .append(restaurant.getLatitude()).append(", ").append(restaurant.getLongitude())
                    .append("</p>");

            if (restaurant.getImage() != null) {
                String imageUrl = request.getScheme() + "://" + request.getServerName() + ":" + request.getServerPort()
                        + "/restaurants/image/" + restaurant.getId();
                htmlResponse.append("<img src=\"").append(imageUrl).append("\" alt=\"Image\" style=\"width:200px;\"/>");
            } else {
                htmlResponse.append("<p>No image available</p>");
            }

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
![db저장](https://github.com/user-attachments/assets/271e3274-51b3-4033-986c-5211b72c86f2) <br>
<br>
### :bulb: 안드로이드 스튜디오에서 구글맵을 띄우고 식당 정보 DB에 저장된 위도/경도에 맞게 지도에 위치 표시하기 <br>
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

        // SupportMapFragment를 얻고, 비동기적으로 지도를 초기화합니다.
        SupportMapFragment mapFragment = (SupportMapFragment) getSupportFragmentManager()
                .findFragmentById(R.id.map);
        mapFragment.getMapAsync(this);
    }

    // 지도가 준비되었을 때 호출됩니다.
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

6. 스프링부트에서 식당정보 DB를 가져와 위도, 경도에 맞는 위치에 마커 표시하기 <br>
