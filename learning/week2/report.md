{% import '../../hackathons/classmates/data.html' as data %}

# Report

There are {{ data.comments.length }} students who gave a self-introduction. As a
class, we brainstormed and came up with a long list of further questions we can
ask based on this data. Our team chose to tackle on the following:


# (Question 1)
## "Who submitted on or before the deadlines?"
{% lodash %}

result = _.pluck(data.comments, "created_at")
var result = _.size(_.filter(result,function(n){
	n = n.split("T")[0].split("-")[2];
	return _.inRange(n,1,25);
}))
console.log(result)
return result
{% endlodash %}
The answer is {{result}}.

# (Question 2)
##"Who(name) has the User ID: 13950166?"
{% lodash %}
var text = _.filter(data.comments, function(n){
	return _.includes(n.user,13950166);
})
var text1 = _.pluck(text, "body")
console.log(text1)
var name = _.map(text1, function(n){
	var text2 = n.split("\r\n")[0]
	return _.last(text2.split("Name:"))
})
result = name
console.log(result)
return result
{% endlodash %}
The answer is {{result}}.

# (Question 3)
## "How many people are computer science major?"
{% lodash %}
result = _.pluck(data.comments, "body")
result = _.size(_.filter(result, function(n){
	return _.contains(n, "Computer")||_.contains(n,"cs\r")||_.contains(n,"CS");
}))
console.log(result)
return result
{% endlodash %}
The answer is {{result}}.
We included Susssant's Computer Engineering, because he thinks that computer Engineering is part of Computer Science.


# (Question 4)
## "How many people submit after deadline?"
{% lodash %}
result = _.pluck(data.comments, "created_at")
var result = _.size(_.filter(result,function(n){
	n = n.split("T")[0].split("-")[2];
	
	return _.inRange(n,25,40) ;
}))
console.log(result)
return result
{% endlodash %}
The answer is {{result}}.
