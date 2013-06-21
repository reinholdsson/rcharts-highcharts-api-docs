<style>rChart {width: 600px; height: 400px;}</style>




## Highcharts

Highcharts is a JavaScript charting library based on SVG and VML rendering by Highsoft Solutions AS. It is not free for commercial use, so make sure you have a valid license. For more information, see [http://www.highcharts.com/](http://www.highcharts.com/).

### Class

#### Highcharts ([api](http://api.highcharts.com/highcharts#Highcharts))

To initialize a new chart object one simply write


```r
obj <- Highcharts$new()
```


*Hint: An alternative is to use the custom wrapper function `hPlot`.*

### Methods

The [Highcharts API Reference](http://api.highcharts.com/highcharts) has an extensive documentation of all methods in the Highcharts javascript library, those implemented in `rCharts` here follows with examples.

#### chart ([api](http://api.highcharts.com/highcharts#chart))

We set the `type` and `height` with the `chart` method.


```r
obj$chart(type = "column", height = 300)
```


As default, `line` is used as the chart type.

#### series ([api](http://api.highcharts.com/highcharts#series)|[docs](http://docs.highcharts.com/#series))


```r
obj$series(data = 1:3)
```

<script type='text/javascript' src=http://code.jquery.com/jquery-1.9.1.min.js></script>
<script type='text/javascript' src=http://code.highcharts.com/highcharts.js></script>
<script type='text/javascript' src=http://code.highcharts.com/highcharts-more.js></script>
<div id='/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db7487cb0a' class='rChart highcharts'></div>
<script type='text/javascript'>
    (function($){
        $(function () {
            var chart = new Highcharts.Chart({
 "dom": "/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db7487cb0a",
"width":    600,
"height":    400,
"credits": {
 "href": null,
"text": null 
},
"title": {
 "text": null 
},
"yAxis": {
 "title": {
 "text": null 
} 
},
"chart": {
 "type": "column",
"height":    300,
"renderTo": "/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db7487cb0a" 
},
"series": [
 {
 "data": [ 1, 2, 3 ] 
} 
],
"id": "/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db7487cb0a" 
});
        });
    })(jQuery);
</script>


It is possible to add another data series by re-using `series` on the same object. While we in the above example only provided the y-coordinates we could also specify the x-coordinates (otherwise starting from 0), as below:




```r
obj$series(data = list(c(0,2), c(1,1), c(2,3)), name = "foo")
```


We also named it by using the `name` argument.

The third alternative to add data is perhaps the most useful for more advanced charts, for example when using the `tooltip` method as one might be interested to show additional data in the chart, other than x- and y-values. 


```r
obj$series(data = list(
  list(x = 0, y = 0, foo = "a"),
  list(x = 1, y = 1, foo = "b"),
  list(x = 2, y = 3, foo = "c")
), type = "spline")
```


As noticed, the chart `type` may as well be included as an attribute, which makes it possible to combine several chart types within the same chart. The series are layered on each other in the same order as they are added, therefore the `spline` will be shown on top of the `columns`.

#### xAxis ([api](http://api.highcharts.com/highcharts#xAxis)|[docs](http://docs.highcharts.com/#axes))


```r
obj$xAxis(categories = c("apple", "orange", "pear"))
```


#### yAxis ([api](http://api.highcharts.com/highcharts#yAxis)|[docs](http://docs.highcharts.com/#axes))


```r
obj$yAxis(title = list(text = "Number"))
```



<div id='/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db7f23394a' class='rChart highcharts'></div>
<script type='text/javascript'>
    (function($){
        $(function () {
            var chart = new Highcharts.Chart({
 "dom": "/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db7f23394a",
"width":    600,
"height":    400,
"credits": {
 "href": null,
"text": null 
},
"title": {
 "text": null 
},
"yAxis": {
 "title": {
 "text": "Number" 
} 
},
"chart": {
 "type": "column",
"height":    300,
"renderTo": "/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db7f23394a" 
},
"series": [
 {
 "data": [ 1, 2, 3 ] 
},
{
 "data": [
 [      0,      2 ],
[      1,      1 ],
[      2,      3 ] 
],
"name": "foo" 
},
{
 "data": [
 {
 "x":      0,
"y":      0,
"foo": "a" 
},
{
 "x":      1,
"y":      1,
"foo": "b" 
},
{
 "x":      2,
"y":      3,
"foo": "c" 
} 
],
"type": "spline" 
} 
],
"id": "/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db7f23394a",
"xAxis": {
 "categories": [ "apple", "orange", "pear" ] 
} 
});
        });
    })(jQuery);
</script>


#### colors ([api](http://api.highcharts.com/highcharts#colors)|[docs](http://docs.highcharts.com/#colors))


```r
obj$colors(
  'rgba(223, 83, 83, .75)', 
  'rgba(60, 179, 113, .75)', 
  'rgba(238, 130, 238, .75)'
)
```


#### credits ([docs](http://docs.highcharts.com/#credits))


```r
obj$credits(text = "Created with rCharts", href = "http://rcharts.io")
```


#### tooltip ([api](http://api.highcharts.com/highcharts#tooltip)|[docs](http://docs.highcharts.com/#tooltip))


```r
obj$tooltip(useHTML = T, formatter = "#! function() { return this.x + ', ' + this.y; } !#")
```



<div id='/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db61866a7b' class='rChart highcharts'></div>
<script type='text/javascript'>
    (function($){
        $(function () {
            var chart = new Highcharts.Chart({
 "dom": "/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db61866a7b",
"width":    600,
"height":    400,
"credits": {
 "text": "Created with rCharts",
"href": "http://rcharts.io" 
},
"title": {
 "text": null 
},
"yAxis": {
 "title": {
 "text": "Number" 
} 
},
"chart": {
 "type": "column",
"height":    300,
"renderTo": "/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db61866a7b" 
},
"series": [
 {
 "data": [ 1, 2, 3 ] 
},
{
 "data": [
 [      0,      2 ],
[      1,      1 ],
[      2,      3 ] 
],
"name": "foo" 
},
{
 "data": [
 {
 "x":      0,
"y":      0,
"foo": "a" 
},
{
 "x":      1,
"y":      1,
"foo": "b" 
},
{
 "x":      2,
"y":      3,
"foo": "c" 
} 
],
"type": "spline" 
} 
],
"id": "/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db61866a7b",
"xAxis": {
 "categories": [ "apple", "orange", "pear" ] 
},
"colors": [
 "rgba(223, 83, 83, .75)",
"rgba(60, 179, 113, .75)",
"rgba(238, 130, 238, .75)" 
],
"tooltip": {
 "useHTML": true,
"formatter":  function() { return this.x + ', ' + this.y; }  
} 
});
        });
    })(jQuery);
</script>


#### labels ([docs](http://docs.highcharts.com/#labels))


```r
obj$labels(items = list(
  list(
    html = "An interactive example of Highcharts in rCharts", 
    style = list(left = "20px", top = "20px")
  )
))
```


The `items` argument takes an array of items, and that is why we use `list` twice.



<div id='/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db3fb8e342' class='rChart highcharts'></div>
<script type='text/javascript'>
    (function($){
        $(function () {
            var chart = new Highcharts.Chart({
 "dom": "/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db3fb8e342",
"width":    600,
"height":    400,
"credits": {
 "text": "Created with rCharts",
"href": "http://rcharts.io" 
},
"title": {
 "text": null 
},
"yAxis": {
 "title": {
 "text": "Number" 
} 
},
"chart": {
 "type": "column",
"height":    300,
"renderTo": "/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db3fb8e342" 
},
"series": [
 {
 "data": [ 1, 2, 3 ] 
},
{
 "data": [
 [      0,      2 ],
[      1,      1 ],
[      2,      3 ] 
],
"name": "foo" 
},
{
 "data": [
 {
 "x":      0,
"y":      0,
"foo": "a" 
},
{
 "x":      1,
"y":      1,
"foo": "b" 
},
{
 "x":      2,
"y":      3,
"foo": "c" 
} 
],
"type": "spline" 
} 
],
"id": "/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db3fb8e342",
"xAxis": {
 "categories": [ "apple", "orange", "pear" ] 
},
"colors": [
 "rgba(223, 83, 83, .75)",
"rgba(60, 179, 113, .75)",
"rgba(238, 130, 238, .75)" 
],
"tooltip": {
 "useHTML": true,
"formatter":  function() { return this.x + ', ' + this.y; }  
},
"labels": {
 "items": [
 {
 "html": "An interactive example of Highcharts in rCharts",
"style": {
 "left": "20px",
"top": "20px" 
} 
} 
] 
} 
});
        });
    })(jQuery);
</script>


#### legend ([docs](http://docs.highcharts.com/#legend))


```r
obj$legend(
  align = 'right', 
  verticalAlign = 'middle', 
  layout = 'vertical'
)
```



<div id='/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db35022bd' class='rChart highcharts'></div>
<script type='text/javascript'>
    (function($){
        $(function () {
            var chart = new Highcharts.Chart({
 "dom": "/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db35022bd",
"width":    600,
"height":    400,
"credits": {
 "text": "Created with rCharts",
"href": "http://rcharts.io" 
},
"title": {
 "text": null 
},
"yAxis": {
 "title": {
 "text": "Number" 
} 
},
"chart": {
 "type": "column",
"height":    300,
"renderTo": "/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db35022bd" 
},
"series": [
 {
 "data": [ 1, 2, 3 ] 
},
{
 "data": [
 [      0,      2 ],
[      1,      1 ],
[      2,      3 ] 
],
"name": "foo" 
},
{
 "data": [
 {
 "x":      0,
"y":      0,
"foo": "a" 
},
{
 "x":      1,
"y":      1,
"foo": "b" 
},
{
 "x":      2,
"y":      3,
"foo": "c" 
} 
],
"type": "spline" 
} 
],
"id": "/var/folders/l2/zqgw1zvx43q0dnylmjqzz3xh0000gn/T//RtmprBgyMW/file53db35022bd",
"xAxis": {
 "categories": [ "apple", "orange", "pear" ] 
},
"colors": [
 "rgba(223, 83, 83, .75)",
"rgba(60, 179, 113, .75)",
"rgba(238, 130, 238, .75)" 
],
"tooltip": {
 "useHTML": true,
"formatter":  function() { return this.x + ', ' + this.y; }  
},
"labels": {
 "items": [
 {
 "html": "An interactive example of Highcharts in rCharts",
"style": {
 "left": "20px",
"top": "20px" 
} 
} 
] 
},
"legend": {
 "align": "right",
"verticalAlign": "middle",
"layout": "vertical" 
} 
});
        });
    })(jQuery);
</script>


#### plotOptions

...

#### title

...

#### subtitle

...

### Additional methods

Although we have covered the most commonly used methods, there are still some that we have not described (that might be of interested to more advanced users):
  - exporting ([docs](http://docs.highcharts.com/#exporting))
  - loading ([docs](http://docs.highcharts.com/#loading))
  - navigation ([docs](http://docs.highcharts.com/#navigation))
  - pane ([docs](http://docs.highcharts.com/#pane))

For more information on how to use these, see the Highcharts API documentation page.
