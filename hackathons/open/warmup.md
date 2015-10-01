# Warmup

Complete this warmup exercise to get an idea how to put all the different pieces
together to generate an end-to-end data analysis viz report.

<a name="top"/>
<div id="autonav"></div>

{% data src="../fcq/fcq.clean.json" %}
{% enddata %}

{% viz %}

{% title %}

What is the distribution of courses across colleges?

{% solution %}
var groups = _.groupBy(data, function(d){
    return d['CrsPBAColl']
})
var map = _.map(groups,function(x, value){
    return {"name": value, "count": _.pluck(x,'Course').length};
});
console.log(map);

// TODO: add real code to convert groups (which is an object) into an array like below
// This array should have a lot more elements.
/*var counts = {"name": "AS","count": 3237},
    {"name": "BU","count": 378},
    {"name": "EB","count": 139},
    {"name": "EN","count": 573}

console.log(counts)*/

// TODO: modify the code below to produce a nice vertical bar charts

function computeX(d, i) {
    return i*10;
}

function computeHeight(d, i) {

    return d.count/10 ;
}

function computeWidth(d, i) {
    return 10;
}

function computeY(d, i) {
    return 0;
}

function computeColor(d, i) {
    return 'green'
}

var viz = _.map(map, function(d, i){
            return {
                x: computeX(d, i),
                y: computeY(d, i),
                height: computeHeight(d, i),
                width: computeWidth(d, i),
                color: computeColor(d, i)
            }
         })
console.log(viz)

var result = _.map(viz, function(d){
         // invoke the compiled template function on each viz data
         return template({d: d});
     })
return result.join('\n')

{% template %}

<rect x="${d.x}"
      y="${d.y}"
      height="${d.height}"
      width="${d.width}"
      style="fill:${d.color};
             stroke-width:3;
             stroke:rgb(0,0,0)" />

{% endviz %}
