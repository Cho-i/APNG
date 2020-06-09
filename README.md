# APNG

![](https://media.vlpt.us/images/suji5358/post/773f4514-a536-4fb1-9563-17f2fa005cf9/mozilla_apng.png)

### 개념

APNG (Animated Portable Network Graphics)

PNG를 확장한 이미지 파일 포맷. 애니메이션 이미지에 대한 지원이 추가됨.
한마디로,애니메이션이 되는 PNG.

2004년 모질라 코퍼레이션의 Stuart Parmenter와 Vladimir Vukićević가 인터페이스에 필요한 애니메이션을 저장하기 위해 만들었다. 대중에게 발표는 2008년에 되었으며 오픈 포맷.



### 장점

- GIF, VIDEO(MP4) 보다 낮은 용량, 더 선명한 애니메이션

- 기존 PNG 파일과의 하위호환성을 유지 (APNG 파일의 첫 프레임은 PNG로 저장하기 때문에 APNG를 지원하지 않는 브라우저도 APNG 파일의 첫 프레임을 보여 줄 수 있음)



### 웹 브라우저 서포트

**PC**

- 불가능 : IE/Edge (CANIUSE에서 Edge79+ 가능하다고 했지만, 확인해보니 Edge ver.44에서 불가)
- 가능 : 이외 나머지 브라우저(Chrome 59+, safari 8+, FF3+, Opera 46+) 가능

(apng-canvas.js 플러그인을 사용하면 IE10+ 까진 지원)

**MOBILE**

- 불가능 : Opera Mini

- 가능 : 이외 모바일 웹브라우저(iOS safari 8+, Android Chrome 80+, Samsung Internet 7.2+) 가능
  (App에서는 불가. Android/iOS App에서 따로 플러그인을 사용)

  ![](https://media.vlpt.us/images/suji5358/post/2b6f9e57-9deb-45c2-badf-168c38ee6904/image.png)

[CANIUSE에서 APNG 지원범위 확인하기](https://caniuse.com/#search=APNG)



### APNG 제작 방법

#### 준비물

APNG로 사용할 PNG 파일



#### APNG Assembler 로 apng 파일 생성

1. APNG Assembler

아래 링크를 통해 APNG Assembler를 다운

[APNG Assembler 다운링크](https://sourceforge.net/projects/apngasm/)

![](https://media.vlpt.us/images/suji5358/post/875a5971-5e15-4158-95a2-98432f6c7a7f/image.png)

1번. loop 설정 : play Infinity 로 설정

2번. Delays : 모든 프레임에 대한 딜레이 설정

3번. Compression settings : 압축설정

4번. Delays - selected Frames : 선택된 프레임에 대한 딜레이 설정

5번. 추출할 파일의 위치 선택 ( [...]버튼을 눌러서 풀 경로가 나와야 추출됨)

Make Animated PNG를 누르면 변환!

*만들어진 apng가 웹에서 잘 나오는지 확인해보려면,
(크롬, 파이어폭스) 브라우저를 열고 apng 파일을 드래그 하면 정상적으로 동작하는걸 볼 수 있음.



2. EZGIF 사이트

[EZGIF 사이트](https://ezgif.com/apng-maker)

다운받을 필요 없이 사이트에서 apng 변환



### Web 사이트에 표시하는 방법

html에서 apng를 사용하는 방법은 png와 같다. 그냥 img 태그에 넣으면 됨.

```html
<img src="./src/apng_animated.png" alt="apng">
```

하지만, apng를 모든 브라우저에서 지원되지 않기 때문에, apng가 지원되지 않는 브라우저에서는 canvas로 보여주게끔 해주는 플러그인이 있음.

[davidmz/apng-canvas github](https://github.com/davidmz/apng-canvas)



```html
<script src="https://code.jquery.com/jquery-2.1.3.min.js"></script>
<script src="./apng-canvas.min.js"></script>
...
<div class="source apng-image"><img src="./src/apng_animated.png" alt="apng"></div>
...
<script>
        APNG.ifNeeded()
        .then(function () {
            $(".apng-image").find("img").each(function () { APNG.animateImage(this); });
            var msg = '<p>canvas 로 로드됩니다.</p>'
            $('.info').append(msg);
            //msg는 apng, canvas 중 어떤 것으로 로드되는지 알려줌. 필요없으면 제거
        })
        .catch(function () {
            var msg = '<p>apng 로 로드됩니다.</p>'
            $('.info').append(msg);
        });
</script>
```

하지만, 이 플러그인도 모든 브라우저에서 지원되는 것은 아님, 대부분 IE10이상에서만 지원되는 기술들.

- PC : IE10+, FF, Safari 8+, 그리고 그외 모든 브라우저.



** 테스트 [Web test](https://cho-i.github.io/APNG/sample/)

------

**참고**

[https://velog.io/@suji5358/APNG-%EC%A0%9C%EC%9E%91%ED%95%98%EA%B3%A0-%EC%9B%B9%EC%97%90%EC%84%9C-%EC%82%AC%EC%9A%A9%ED%95%B4%EB%B3%B4%EA%B8%B0](https://velog.io/@suji5358/APNG-제작하고-웹에서-사용해보기)