{% data src="fcq.clean.json" %}
{% enddata %}

# Warmup

Next, complete the following warmup exercises as a team.

## How many unique subject codes?

{% lodash %}
var result = _.size(_.uniq(_.pluck(data, "Subject")))
return result
//return 113
{% endlodash %}

They are {{ result }} unique subject codes.

## How many computer science (CSCI) courses?

{% lodash %}
var S = _.pluck(data, "Subject")
var result = _.size(_.filter(S, function(n){
    return n == "CSCI"
}))
return result
//return 63
{% endlodash %}

They are {{ result }} computer science courses.

## What is the distribution of the courses across subject codes?

{% lodash %}
// TODO: replace with code that computes the actual result
var groups = _.groupBy(data, "Subject")
var result = _.mapValues(groups, function(n){
    return n.length
})
return result
//return {"HIST": 78,"HONR": 20,"HUMN": 17,"IAFS": 20,"IPHY": 134}
{% endlodash %}

<table>
{% for key, value in result %}
    <tr>
        <td>{{key}}</td>
        <td>{{value}}</td>
    </tr>
{% endfor %}
</table>

## What subset of these subject codes have more than 100 courses?

{% lodash %}
// TODO: replace with code that computes the actual result

var grps = _.groupBy(data, 'Subject')
var result = _.pick(_.mapValues(grps, function(d){
    return d.length
}), function(x){
    return x > 100
})
return result
/*return {"IPHY": 134,"MATH": 232,"MCDB": 117,"PHIL": 160,"PSCI": 117}*/
{% endlodash %}

<table>
{% for key, value in result %}
    <tr>
        <td>{{key}}</td>
        <td>{{value}}</td>
    </tr>
{% endfor %}
</table>

## What subset of these subject codes have more than 5000 total enrollments?

{% lodash %}
// TODO: replace with code that computes the actual result

var groups = _.groupBy(data, 'Subject')
var result = _.pick(_.mapValues(groups, function(d){
    var a = _.pluck(d, 'N.ENROLL')
    return _.sum(a)
}), function(x){
        return x > 5000 
})
return result
/*return {"IPHY": 5507,"MATH": 8725,"PHIL": 5672,"PHYS": 8099,"PSCI": 5491}*/
{% endlodash %}

<table>
{% for key, value in result %}
    <tr>
        <td>{{key}}</td>
        <td>{{value}}</td>
    </tr>
{% endfor %}
</table>

## What are the course numbers of the courses Tom (PEI HSIU) Yeh taught? 

{% lodash %}
// TODO: replace with code that computes the actual result
var result = _.filter(data,function(d){
   x = _.where(d['Instructors'], { 'name': "YEH, PEI HSIU" });
  
   return _.size(x);
});
return _.pluck(result,"Course")
//return ['4830','4830']

{% endlodash %}

They are {{result}}.

