# background-image-mixin-for-compass
반응형 이미지/스프라이트이미지 쉽게 적용하는 compass 용 mixin

# 사용방법

## 스프라이트 이미지 사용하기

```scss
$sprite: sprite-map('../images/*.png');
@include background-image($sprite, filename);
```
```css
background-image:url('../images-spritedkey.png');
background-size:...;
background-position:...;
width:...;
height:...;
```

## 반응형 스프라이트 이미지 사용하기

```scss
$sprites: (
  1: sprite-map('../images/@1x/*.png'),
  2: sprite-map('../images/@2x/*.png')
);
@include background-image($sprites, filename);
```
```css
background-image:url('../images/@1x-spritedkey.png');
background-size:...;
background-position:...;
width:...;
height:...;

@media only screen and (min-device-pixel-ratio: 1.5), only screen and (min-resolution: 1.5dppx) {
	background-image:url('../images/@2x-spritedkey.png');
}
```

## 일반 이미지 사용하기

```scss
$image: '../images/*.png';
@include background-image($image, filename);
```
```css
background-image:url('../images/filename.png');
background-size:...;
width:...;
height:...;
```

## 반응형 일반 이미지 사용하기

```scss
$images: (
  1: '../images/@1x/*.png',
  2: '../images/@2x/*.png'
);
@include background-image($images, filename);
```
```css
background-image:url('../images/@1x/filename.png');
background-size:...;
width:...;
height:...;

@media only screen and (min-device-pixel-ratio: 1.5), only screen and (min-resolution: 1.5dppx) {
	background-image:url('../images/@2x/filename.png');
}
```

# 자동 사이즈 조정

스프라이트 이미지가 아닌 일반 이미지를 사용하는 경우, 다음과 같이 mix-in 의 세번째 인자를 사용해서 배경이미지가 지정된 엘리먼트의 width, height 를 설정하지 않도록 막을 수 있다.

## 일반 이미지 사용하기

```scss
$image: '../images/*.png';
@include background-image($image, filename, true);
```
```css
background-image:url('../images/filename.png');
background-size:...;
```

## 반응형 일반 이미지 사용하기

```scss
$images: (
  1: '../images/@1x/*.png',
  2: '../images/@2x/*.png'
);
@include background-image($images, filename, true);
```
```css
background-image:url('../images/@1x/filename.png');
background-size:...;

@media only screen and (min-device-pixel-ratio: 1.5), only screen and (min-resolution: 1.5dppx) {
	background-image:url('../images/@2x/filename.png');
}
```
