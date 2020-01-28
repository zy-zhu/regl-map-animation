# regl-map-animation

Animate x/y point data loaded from CSV files using [regl](https://github.com/regl-project/regl) and categorize them for vizualization. Point data in the csv file should be defined as x,y,value - with "value" being the numerical value with which the points will be categorized.

![alt text](https://github.com/eurostat/regl-map-animation/blob/master/preview.png)

## Installation & Usage

The project is built using UMD so it works both in browsers and in node.js

### Node

Within a node.js project simply run the following command:

`npm i regl-map-animation --save`

Then import:

```javascript
import mapAnimation from "regl-map-animation";

mapAnimation({
  csvURL: "./assets/pop_5km.csv", // xmin,ymin,value for a 5km population grid of Europe in EPSG 3035
  pointWidth: 1,
  pointMargin: 1,
  delayAtEnd: 1,
  colors: ["#005cff", "#55e238", "#ebff0a", "#ffce08", "#ff0f00", "#a6306f"],
  stops: [0, 100, 1000, 5000, 10000, 30000]
});
```

### Browsers

As a standalone script use:

```html
<script src="https://unpkg.com/regl-map-animation/dist/bundle.js"></script>
```

Then:

```javascript
mapAnimation({
  csvURL: "./assets/pop_5km.csv", // xmin,ymin,value for a 5km population grid of Europe in EPSG 3035
  pointWidth: 1,
  pointMargin: 1,
  delayAtEnd: 1,
  colors: ["#005cff", "#55e238", "#ebff0a", "#ffce08", "#ff0f00", "#a6306f"],
  stops: [0, 100, 1000, 5000, 10000, 30000]
});
```

## Parameters

### Required:

- **csvUrl** - _string_, (URL to csv file containing the points. The points in the CSV file must have three columns: "x", "y" and "value" and should be separated by a comma.)

### Optional:

- **numPoints** | _number_ (number of points to display. Defaults to the number of points in the csv file)
- **pointWidth** | _number_ (width of each point. Defaults to 1)
- **pointMargin** | _number_ (Margin applied to the bars in the bar chart. Defaults to 1)
- **duration** | _number_ (The duration of each transition animation in milliseconds. Defaults to 5000)
- **delayAtEnd** | _number_ (How long to stay at a final frame before animating again (in milliseconds). Defaults to 0)
- **screenWidth** | _number_ (Defaults to window.innerWidth)
- **screenHeight** | _number_ (Defaults to window.innerHeight)
- **stops** | _array_ (Stops used for categorizing points by their "value" attribute. Defaults to [0, 100, 1000, 5000, 10000] ),
- **colors** | _array_ (An array of Hex values which must correspond with the number of defined stops. Defaults to blue>red gradient: ["#005cff", "#55e238", "#ebff0a", "#ffce08", "#ff0f00"])
- **projection** | _string_ (Spatial refernce of the points x and y values. Accepted values: "EPSG:3035" or "EPSG:4326". Defaults to "EPSG:3035")

## Notes

Inspired by [Peter Beshai](https://peterbeshai.com/blog/2017-05-26-beautifully-animate-points-with-webgl-and-regl/)
