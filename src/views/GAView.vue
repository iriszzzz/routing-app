<template>
    <div id="app">
      <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>GA - Travel Around Taiwan</title>
        <link rel="preconnect" href="https://fonts.googleapis.com">
        <link rel="shortcut icon" href="https://cdn-icons-png.flaticon.com/512/24/24170.png"/>
      </head>
      <body>
        <h1>🩴🗺️👩‍🎓 Let's Travel around Taiwan 🎒🌏🛵</h1>
        <div id="map" style="height: 400px;"></div>
    
        <div class="card">
          <br>
          <h2 contenteditable> &nbsp⚠️ 環島須知 </h2>
          <p contenteditable id="warn">
            &nbsp&nbsp&nbsp 1. 本路線僅供參考 🐸<br>
            &nbsp&nbsp&nbsp 2. 注意天氣變化 ☔<br>
            &nbsp&nbsp&nbsp 3. 請安全駕駛 ⛑️<br>
          </p>
        </div>
        <!-- <img src="ha.png" class="happy"> -->
        <div class="copyright">© 2024 GA group3. All Rights Reserved.</div>
      </body>
    </div>
  </template>
  
  <script>
  export default {
    name: 'App',
    mounted() {
      this.loadGoogleMaps();
    },
    methods: {
      loadGoogleMaps() {
        const script = document.createElement('script');
        script.src = `https://maps.googleapis.com/maps/api/js?key=AIzaSyA65CeniB1QhUdJEUJtJ9IJl4mojffBw5w&callback=initMap`;
        script.async = true;
        script.defer = true;
        window.initMap = this.initMap;
        document.head.appendChild(script);
      },
      initMap() {
        var map = new google.maps.Map(document.getElementById('map'), {
          center: { lat: 23.86928984365684, lng: 120.95915911801933 },
          zoom: 7
        });

        var locations = [
        // 新竹座標
        { lat: 24.78697718955756, lng:  120.99785893519154, name: '' },
        { lat: 24.801323410606095, lng:  120.96265989481958, name: '' },
        { lat: 24.799488896305647, lng:  120.95645286914106, name: '' },
        { lat: 24.80456650340949, lng:  120.96496948576976, name: '' },
        { lat: 224.80089754362506, lng:  120.9790074683623, name: '' },
        // 苗栗座標
        { lat: 24.55633970473704, lng:  120.80363523989513, name: '' },
        { lat: 24.55476417321401, lng:  120.81734843616167, name: '' },
        { lat: 24.564610920445343, lng:  120.82225631693073, name: '' },
        { lat: 24.571736034860756, lng:  120.85101119484756, name: '' },
        { lat: 24.47254789418804, lng:  120.83126207306478, name: '' },
        // 台中座標
        { lat: 24.322558553388415, lng:  120.6747295657879, name: '' },
        { lat: 24.27843905584624, lng:  120.73240778762738, name: '' },
        { lat: 24.190780442960865, lng:  120.74442408387715, name: '' },
        { lat: 24.177313239835687, lng:  120.75781367098526, name: '' },
        { lat: 24.14504881219574, lng:  120.66889307898668, name: '' },
        { lat: 24.13439663023246, lng:  120.67369959747035, name: '' },
        { lat: 24.125936912398178, lng:  120.69326899415384, name: '' },
        { lat: 24.117819977415486, lng:  120.66525170263402, name: '' },
        // 南投座標
        { lat: 23.938978926132286, lng:  120.70345302365146, name: '' },
        { lat: 23.949098240174454, lng:  120.7003631188384, name: '' },
        { lat: 23.95584400859394, lng:  120.69341083312001, name: '' },
        { lat: 23.926989901864523, lng:  120.70075534877381, name: '' },
        { lat: 23.949394585826756, lng:  120.71568779550213, name: '' },
        // 雲林座標
        { lat: 23.705718712987608, lng:  120.50492924643903, name: '' },
        { lat: 23.707304738369434, lng:  120.58807452064448, name: '' },
        { lat: 23.560251302514615, lng:  120.62271838489679, name: '' },
        // 嘉義座標
        { lat: 23.495003071309196, lng:  120.28243553268769, name: '' },
        { lat: 23.467615592878282, lng:  120.23461066136598, name: '' },
        { lat: 23.44623604996899, lng:  120.29360276141801, name: '' },
        // 台南座標
        { lat: 23.270757803167886, lng:  120.11462677630885, name: '' },
        { lat: 23.242431711724006, lng:  120.18163014931869, name: '' },
        { lat: 23.220346569901853, lng:  120.21658843105341, name: '' },
        { lat: 22.9764074572535, lng:  120.22281092051217, name: '' },
        // 高雄座標
        { lat: 22.99870373682153, lng:  120.23519507055735, name: '' },
        { lat: 22.975947422635425, lng:  120.15142431984204, name: '' },
        { lat: 22.974050890077734, lng:  120.26266089046403, name: '' },
        { lat: 22.819077715017094, lng:  120.31690588483045, name: '' },
        { lat: 22.7958953755387, lng:  120.30141222559051, name: '' }, 
        { lat: 22.75783077722962, lng:  120.30603140768278, name: '' },
        { lat: 22.61960453166032, lng:  120.29472665256002, name: '' },
        { lat: 22.616872151510037, lng:  120.29069486917057, name: '' },
        { lat: 22.620122735516315, lng:  120.28013057615551, name: '' }, 
        // 屏東座標
        { lat: 22.21919182376879, lng: 120.80741476800299, name: '' },
        { lat: 21.943689253262942, lng: 120.74544813587806376879, name: '' },
        { lat: 21.89781646569861, lng:  120.85843449354812, name: '' },
        { lat: 21.927464013677408, lng:  120.84835613666259, name: '' },
        { lat: 22.195817651837025, lng: 120.89075663989122, name: '' },
        // 台東座標
        { lat: 22.57159055936732, lng:   120.95468267614623, name: '' },
        { lat: 22.621574234242363, lng:  121.00688634013922, name: '' },
        { lat: 22.752095483324872, lng:  121.14743883220575, name: '' },
        { lat: 22.857191606714625, lng:  121.19894968988162, name: '' },
        { lat: 22.868562919060984, lng:  121.21919588749765, name: '' },
        { lat: 22.945442397226298, lng:  121.28054644443682, name: '' },
        // 花蓮座標
        { lat: 23.206638366024475, lng:  121.36495213457168, name: '' },
        { lat: 23.308835599981133, lng:  121.27980809286103, name: '' },
        { lat: 23.322708190142016, lng:  121.12874608337437, name: '' },
        { lat: 23.90148203166471, lng:   121.60153478483858, name: '' },
        { lat: 23.96652053250339, lng:  121.59818747086197, name: '' },
        { lat: 23.982935051175886, lng:  121.60022888014022, name: '' },
        // 宜蘭座標
        { lat: 24.648777800402478, lng:  121.7480569288341, name: '' },
        { lat: 24.688101002910553, lng:  121.73925487493888, name: '' },
        { lat: 24.693174143425175, lng:  121.72396062677721, name: '' },
        { lat: 24.685032529383978, lng:  121.77454731143526, name: '' },
        { lat: 24.692442758391664, lng:  121.7629993566141, name: '' },
        // 新北座標
        { lat: 25.122148323421758, lng:  121.86943211608113, name: '' },
        { lat: 25.117435063310825, lng:  121.86534929752459, name: '' },
        { lat: 25.101168299201603, lng:  121.85748987180322, name: '' },
        { lat: 24.959233967508112, lng:  121.66601191654405, name: '' },
        { lat: 24.94012435837916, lng:  121.63226686806718, name: '' },
        // 台北座標
        { lat: 25.030381636868164, lng:  121.53178127016331, name: '' },
        { lat: 25.035281034834924, lng:  121.524657323125, name: '' },
        { lat: 25.04282416977215, lng:  121.51307018035187, name: '' },
        { lat: 25.102579082712293, lng:  121.5468218571093, name: '' },
        { lat: 25.10224932746246, lng:  121.5259439945394, name: '' },
        // 桃園座標
        { lat: 24.895753784543206, lng:  121.29095741230664, name: '' },
        { lat: 24.88737360937491, lng:  121.28951391796278, name: '' },
        { lat: 24.883969000770097, lng:  121.29427744929747, name: '' },
        { lat: 24.790842686237273, lng:  121.38097362742604, name: '' },
        { lat: 24.78991604168184, lng:  121.36964380593163, name: '' },
    ];
    locations.forEach(function(location) {
        var marker = new google.maps.Marker({
        position: { lat: location.lat, lng: location.lng },
        map: map,
        title: location.name
        });
    });
  
        locations.forEach(function(location) {
          new google.maps.Marker({
            position: { lat: location.lat, lng: location.lng },
            map: map,
            title: location.name
          });
        });
  
        directionsService.route(request, function(response, status) {
          if (status === 'OK') {
            let directionsDisplay = new google.maps.DirectionsRenderer({
              map: map,
              directions: response,
            });
          }
        });
      }
    }
  }
  </script>
  
  <style scoped>
    h1 {
      margin-top: -25px;
      font-family: 'Noto Serif';
      color: rgb(17, 19, 139);
      text-align: center;
      margin-bottom: 15px;
    } 
    #map {
      height: 1100px;
      width: 800px;
      left: 150px;
    }
    ul {
      padding-top: 16px;
    }
    .fixed-bottom {
      left: 16px;
      bottom: 0;
      max-width: 320px;
    }
    .card {
      font-size: 12px;
      position: fixed;
      top : 150px;
      left: 1000px;
      width: 160px;
      height: 160px;
      padding-inline: 12px;
      position: in-line;
      background: linear-gradient(-135deg, transparent 1rem, #ffeaa7 0);
      border-radius: 0.5rem;
      filter:drop-shadow(4px 4px 8px rgba(92, 92, 92, 0.3));
    }
    p {
      font-size: 12px;
    }
    .happy {
      margin-top: 80px;
      margin-left: 500px;
      padding: block;
      width: 395.34 px; 
      height: 569.12px; 
      margin-bottom: 50px;
    }
    .copyright {
      margin-top: 200px;
      margin-left: 500px;
      font-size: 15px;
      font-family: 'Noto Serif';
      color: rgb(17, 19, 139);
    }
  </style>
  