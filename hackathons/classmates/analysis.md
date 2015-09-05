# Analysis

{% import './data.html' as data %}

After completing the warmup exercises, your task is to do four more slightly
more challenges analyses.

## How many students like sushi as their favorite food?

{% lodash %}
result = _.pluck(data.comments, "body")
result = _.size(_.filter(result, function(n){
	return _.contains(n, "Sushi")}))
return result

{% endlodash %}

The answer is {{result}}.

## Who are the students liking Python the most?

{% lodash %}
var array;
result = _.pluck(data.comments, "body")
result = _.filter(result, function(n){
	return _.contains(n, "Python")})

_.forEach(result, function(n){
	n = _.trimLeft(n,"Name: ");
	n=_.first(n.split('\r'));
	console.log(n);
	array = _(array).concat(n);
});
return array


{% endlodash %}

Their names are {{result}}.

## Are there more Javascript lovers or Java lovers?

{% lodash %}
var array
result = _.pluck(data.comments, "body")
jv0 = _.size(_.filter(result, function(n){
	return _.contains(n, "Java")}))

var js0 = _.size(_.filter(result, function(n){
	return _.contains(n,"javascript")}))
var js1= _.size(_.filter(result, function(n){
	return _.contains(n, "Javascript");}))
var js = _.add(js0,js1)
var r = _.gte(js,jv0)
if(r == true) {return "Javascript"}
else{return "Java"}

{% endlodash %}

The answer is {{result}}.

## Who like the same food as `kjblakemore`?

{% lodash %}

//var body = _.filter(data.comments, _.matchesProperty("user.login","kjblakemore"))
//var kjbody = _.first(_.pluck(body,"body"))
//var vegan = _.last(kjbody.split("Food: "))

var text = _.filter(data.comments, function(n){
	return _.includes(n.body,"Vegan");
})

var text1 = _.pluck(text, "body")
console.log(text1)
var name = []
var finalName = []
for(i = 0; i < _.size(text1);i++){
	name.push(_.first(text1[i].split("\r\n")))
	finalName.push(_.last(name[i].split('Name:')))
}
console.log(name)
return finalName



//_.forEach(_.pluck(data.comments,"body"), function(n){
//	array = _(array).concat(_.filter(n,_.contains(vegan)));	
//});
//console.log(array)
//return result

{% endlodash %}

Their names are {{result}}.
