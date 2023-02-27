## 한 번에 끝내는 프론트엔드 개발 강의 / ☕Starbucks 랜딩 페이지 만들기

강의를 통해 html, css, js로 메인화면, 로그인 스타벅스 랜딩 페이지(홈페이지)를 만드는 웹 페이지입니다. 
<br />
<br />
[DEMO+signin](https://dev-starbucks.netlify.app/)  


![스타벅스 메인이미지](/_assets/main_screenshot.PNG)

  
# 결론  
강의를 들으면서 모르는 부분을 알게되어서 좋았으며 내가 알고 있는 지식을 통해서 조금 더 수정과 보완을 해서 반응형으로 만들어볼예정이다.
몰랐던 부분은 나중에 까먹지 않기 위해 아래 목차에 적어놨다.
<br />

## 목차  
1. [오픈그래프(The Open Graph protocol)](#오픈-그래프(the-open-graph-protocol))  
2. [트위터 카드(Twitter Cards)](#트위터-카드(twitter-cards))  
3. [GSAP & ScrollToPlugin](#gsap-&-scrolltoplugin)  
4. [Youtube API](#4.-youtube-api)  
5. [ScrollMagic](#scrollmagic)  

## 1. 오픈 그래프(The Open Graph protocol)
웹페이지가 소셜 미디어(페이스북 등)로 공유될 때 우선적으로 활용되는 정보를 지정합니다.
<br />
KakaoTalk -  
![](/_assets/kakao_og_example.jpg)
<br />
[더 많은 오픈 그래프 속성 보기](https://ogp.me/)

```html
<meta property="og:type" content="website" />
<meta property="og:site_name" content="Starbucks" />
<meta property="og:title" content="Starbucks Coffee Korea" />
<meta property="og:description" content="스타벅스는 세계에서 가장 큰 다국적 커피 전문점으로, 64개국에서 총 23,187개의 매점을 운영하고 있습니다." />
<meta property="og:image" content="./images/starbucks_seo.jpg" />
<meta property="og:url" content="https://starbucks.co.kr" />
```

- ```og:type:``` 페이지의 유형(E.g, website, video.movie)
- ```og:site_name:``` 속한 사이트의 이름
- ```og:title:``` 페이지의 이름(제목)
- ```og:description:``` 페이지의 간단한 설명
- ```og:image:``` 페이지의 대표 이미지 주소(URL)
- ```og:url:``` 페이지 주소(URL)

## 2. 트위터 카드(Twitter Cards)
웹페이지가 소셜 미디어(트위터)로 공유될 때 우선적으로 활용되는 정보를 지정합니다.
<br />
[더 많은 트위터 카드 보기](https://developer.twitter.com/en/docs/twitter-for-websites/cards/guides/getting-started)
```html
<meta property="twitter:card" content="summary" />
<meta property="twitter:site" content="Starbucks" />
<meta property="twitter:title" content="Starbucks Coffee Korea" />
<meta property="twitter:description" content="스타벅스는 세계에서 가장 큰 다국적 커피 전문점으로, 64개국에서 총 23,187개의 매점을 운영하고 있습니다." />
<meta property="twitter:image" content="./images/starbucks_seo.jpg" />
<meta property="twitter:url" content="https://starbucks.co.kr" />
```

- ```twitter:card:``` 페이지(카드)의 유형(E.g. summary, player)
- ```twitter:site:``` 속한 사이트의 이름
- ```twitter:title:``` 페이지의 이름(제목)
- ```twitter:description:``` 페이지의 간단한 설명
- ```twitter:image:``` 페이지의 대표 이미지 주소(URL)
- ```twitter:url:``` 페이지 주소(URL)

## 3. GSAP & ScrollToPlugin
[GSAP(The GreenSock Animation Platform)](https://greensock.com/gsap/)은 자바스크립트로 제어하는 타임라인 기반의 애니메이션 라이브러리입니다.  
[ScrollToPlugin](https://greensock.com/scrolltoplugin/)은 스크롤 애니메이션을 지원하는 GSAP 플러그인입니다.

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/gsap.min.js" integrity="sha512-IQLehpLoVS4fNzl7IfH8Iowfm5+RiMGtHykgZJl9AWMgqx0AmJ6cRWcB+GaGVtIsnC4voMfm8f2vwtY+6oPjpQ==" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/ScrollToPlugin.min.js" integrity="sha512-nTHzMQK7lwWt8nL4KF6DhwLHluv6dVq/hNnj2PBN0xMl2KaMm1PM02csx57mmToPAodHmPsipoERRNn4pG7f+Q==" crossorigin="anonymous"></script>
```
[.to() 사용법 GSAP Easing](https://greensock.com/docs/v2/Easing)

```javascript
gsap.to(요소, 시간, 옵션)
// 또는
TweenMax.to(요소, 시간, 옵션)
```
```javascript
gsap.to(window, .7, {
  scrollTo: 0
});
```
## 4. Youtube API
[IFrame Player API](https://developers.google.com/youtube/iframe_api_reference?hl=ko)를 통해 YouTube 동영상을 제어할 수 있습니다.

유튜브 영상이 출력될 위치에 요소를 지정(생성)합니다.
```html
<!-- in HEAD -->
<script defer src="./js/youtube.js"></script>

<!-- in BODY -->
<div id="player"></div>
```
```onYouTubePlayerAPIReady``` 함수 이름은 Youtube IFrame Player API에서 사용하는 이름이기 때문에 다르게 지정하면 동작하지 않습니다!
그리고 함수는 전역(Global) 등록해야 합니다!

[플레이어 매개변수(playerVars)](https://developers.google.com/youtube/player_parameters.html?playerVersion=HTML5&hl=ko#Parameters)에서 더 많은 옵션을 확인할 수 있습니다.
```javascript
// Youtube IFrame API를 비동기로 로드합니다.
var tag = document.createElement('script');
tag.src = "https://www.youtube.com/iframe_api";
var firstScriptTag = document.getElementsByTagName('script')[0];
firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

function onYouTubePlayerAPIReady() {
  // <div id="player"></div>
  new YT.Player('player', {
    videoId: 'An6LvWQuj_8', // 재생할 유튜브 영상 ID
    playerVars: {
      autoplay: true, // 자동 재생 유무
      loop: true, // 반복 재생 유무
      playlist: 'An6LvWQuj_8' // 반복 재생할 유튜브 영상 ID 목록
    },
    events: {
      // 영상이 준비되었을 때,
      onReady: function (event) {
        event.target.mute(); // 음소거!
      }
    }
  });
}
```
## ScrollMagic
ScrollMagic은 스크롤과 요소의 상호 작용을 위한 자바스크립트 라이브러리입니다.
대표적으로 어떤 요소가 현재 화면에 보이는 상태인지를 확인할 때 사용합니다.

[ScrollMagic API](http://scrollmagic.io/docs/)
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.8/ScrollMagic.min.js"></script>
```
```javascript
new ScrollMagic
  .Scene({ // 감시할 장면(Scene)을 추가
    triggerElement: spyEl, // 보여짐 여부를 감시할 요소를 지정
    triggerHook: .8 // 화면의 80% 지점에서 보여짐 여부 감시
  })
  .setClassToggle(spyEl, 'show') // 요소가 화면에 보이면 show 클래스 추가
  .addTo(new ScrollMagic.Controller()) // 컨트롤러에 장면을 할당(필수!)
```

