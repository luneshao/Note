# vue+threejs

[参考项目](https://github.com/AlbanCrepel/vue-displacement-slideshow)

主要内容是 最近项目中机缘巧合要使用 threejs 的一个效果。然后，把它强行绑定到 vue 中踩过的坑。

取用 这个 [github](https://github.com/Mamboleoo/DecorativeBackgrounds/) 中 <i>demo1</i> 和 <i>demo5</i>。

## demo5

这里 <i>demo5</i> 很顺利的完成了。把 `html` 拷到 `template` 中，`js` 拷到 `template` 中，其中需要先安装依赖，分别是 

<b>three</b> 、<b>gsap</b> 、 <b>noise-library</b>、 <b>enquire.js</b>

```javascript
import * as THREE from 'three'
import { TweenMax, Power0 } from 'gsap/TweenMax'
import noise from 'noise-library'
import enquire from 'enquire.js'
```

## demo1

<i>demo1</i> 比较复杂，因为它使用的 `ShaderMaterial` (着色器材质)，原例着色器是写在 html 文件中的，我最初也写在了 template 

中, 有位大佬说在 template 中会被编译， 我就单独提出来了，最终测试写在 template 中是可行的。

我的出错原因： 

* <b>着色器没加分号！</b><b>着色器没加分号！</b><b>着色器没加分号！</b> 因为着色器是 `glsl语言` ，语句末尾必须要有 <b>分号</b>，

和 js 不同，所以需要注意哦。

```glsl
// 错误写法 

attribute float size
attribute vec3 color
varying vec3 vColor
void main() {
  vColor = color;
  vec4 mvPosition = modelViewMatrix * vec4( position, 1.0 );
  gl_PointSize = size * ( 350.0 / - mvPosition.z );
  gl_Position = projectionMatrix * mvPosition;
}

// 正确写法 

attribute float size;
attribute vec3 color;
varying vec3 vColor;
void main() {
  vColor = color;
  vec4 mvPosition = modelViewMatrix * vec4( position, 1.0 );
  gl_PointSize = size * ( 350.0 / - mvPosition.z );
  gl_Position = projectionMatrix * mvPosition;
}

```

* THREE.TextureLoader().load(url) 一直没有拿到图片，下面是写法。 [参考文章](https://segmentfault.com/q/1010000016802820)

```javascript
// 错误写法

var loader = new THREE.TextureLoader()
loader.crossOrigin = ''
var dotTexture = loader.load('../../assets/plugins/img/dotTexture.png')

// 正确写法

var loader = new THREE.TextureLoader()
loader.crossOrigin = ''
var dotTexture = loader.load(require('../../assets/plugins/img/dotTexture.png'))
```

目前是以上内容，都是小问题，困了我两天。 等待遇到相同问题的民那桑;）
