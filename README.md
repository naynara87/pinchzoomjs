# PinchZoom.js

PinchZoom은 모든 DOM 요소에서 확대/축소 및 끌기를 위한 멀티 터치 제스처를 제공하는 Javascript 라이브러리입니다.
미리보기 (https://naynara87.github.io/pinchzoomjs/demo/zooms.html)


## Installation

- Use the [NPM package](https://www.npmjs.com/package/pinch-zoom-js).
- Link directly to the [minified script](https://unpkg.com/pinch-zoom-js/dist/pinch-zoom.min.js) via [UNPKG](https://unpkg.com). Make sure you specify a version.
- Compile from source. 👾

## Usage

### Requirements
* No dependencies, built with vanilla JS.
* A modern browser (ECMA 5 support, http://caniuse.com/use-strict).

### Initialisation

```Javascript

let el = document.querySelector('#my-id');
let pz = new PinchZoom(el, options);

```

### Options

```Text

tapZoomFactor:      두 번 탭하여 확대/축소하는 확대/축소 비율입니다. (default 2)
zoomOutFactor:      확대/축소 비율이 이 값보다 낮으면 원래 크기로 크기가 조정됩니다. (default 1.3)
animationDuration:  애니메이션 지속 시간(밀리초)입니다. (default 300)
maxZoom:            Maximum zoom factor. (default 4)
minZoom:            Minimum zoom factor. (default 0.5)
draggableUnzoomed:  이미지가 확대/축소되지 않은 경우에도 드래그 이벤트를 캡처합니다. (default true)
                    (using `false` allows other libs (e.g. swipe) to pick up drag events)
lockDragAxis:       단일 축으로 요소의 이동을 잠급니다. (default false)
setOffsetsOnce:     오프셋(컨테이너 내부 이미지 위치)을 한 번만 계산합니다. (기본값은 거짓)
                    ('true'를 사용하면 연속적인 'load' 및 'resize'에서 오프셋을 유지합니다)
use2d:              유휴 상태일 때 2D 변환으로 폴백합니다. (default true)
                    (진실 값은 애니메이션 중에 3D 변환을 계속 사용합니다.)
verticalPadding:    이미지 주위에 적용할 수직 패딩입니다. (default 0)
horizontalPadding:  이미지 주위에 적용할 수평 패딩입니다. (default 0)

onZoomStart:        Callback for zoomstart event (params: Pinchzoom object, Event event) (default null)
onZoomEnd:          Callback for zoomend event (params: Pinchzoom object, Event event) (default null)
onZoomUpdate:       Callback for zoomupdate event (params: Pinchzoom object, Event event) (default null)
onDragStart:        Callback for dragstart event (params: Pinchzoom object, Event event) (default null)
onDragEnd:          Callback for dragend event (params: Pinchzoom object, Event event) (default null)
onDragUpdate:       Callback for dragupdate event (params: Pinchzoom object, Event event) (default null)
onDoubleTap:        Callback for doubletap event (params: Pinchzoom object, Event event) (default null)
```

### Methods

```Javascript
let pz = new PinchZoom(myElement);

pz.enable(); // Enables all gesture capturing (is enabled by default)
pz.disable(); // Disables all gesture capturing

```

### Example with callback

```Javascript
var myElement = document.getElementById("myElement");
var pz = new PinchZoom.default(myElement, {
    draggableUnzoomed: false,
    minZoom: 1,
    onZoomStart: function(object, event){
        // Do something on zoom start
        // You can use any Pinchzoom method by calling object.method()
    },
    onZoomEnd: function(object, event){
        // Do something on zoom end
    }
})
```

### Events (deprecated)

*Events are deprecated in favour of callbacks (see above).*

Pinchzoom emits custom events you can listen to:

```Text

pz_zoomstart  Started to zoom
pz_zoomend    Stopped zooming
pz_zoomupdate Zoom factor updated
pz_dragstart  Started to drag the element
pz_dragend    Stopped to drag the element
pz_dragupdate Drag position updated
pz_doubletap  Resetting the zoom with double-tap

```

_(if need be, the event names can be customized via `options`)_


## Release a New Version

1. Make a bump commit (update package.json, package-lock.json and src)
2. Create a new tag `git tag -m "v2.2.0" v2.2.0`
3. Release new NPM version (`npm whoami; npm publish`)
4. Push the code + the tag to Github (`git push origin v2.2.0`)
4. Make a new Github release (https://github.com/manuelstofer/pinchzoom/releases)

## Troubleshooting

- 보이지 않는 이미지에 문제가 있는 경우 이미지가 절대 위치에 있지 않은지 확인하십시오.
  어떤 경우에는 문제를 일으킬 것입니다.

## License

Licensed under the [MIT License](http://opensource.org/licenses/MIT).

## Github Page with demo

https://manuelstofer.github.com/pinchzoom/
