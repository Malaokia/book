{% data src="fcq.clean.json" %}
{% enddata %}

# Report

As a class, we brainstormed and came up with a long list of further questions we
can ask based on the FCQ data. Out of these questions, our team chose to tackle on
the following questions. Each member on our team is reponsible for one question.





# Which course has the highest enrollment?  by Andrew
{% lodash %}
//for course title
var group = _.groupBy(data, 'CourseTitle');
var coursesEnroll = _.mapValues(group, function(d){
   var enrollNumbers = _.pluck(d, 'N.ENROLL')
   return _.sum(enrollNumbers)
})
var max = _.max(coursesEnroll);
var bigClass =  _.pick(coursesEnroll, function(d){
   return d == max;
});
return bigClass 

{% endlodash %}
<table>
{% for key, value in result %}
    <tr>
        <td>{{key}}</td>
        <td>{{value}}</td>
    </tr>
{% endfor %}
</table>




# How many instructors have taught each subject?  by Kari 
{% lodash %}

var group = _.groupBy(data, "Subject")

var result = _.mapValues(group, function(n){
	var S = _.pluck(n, "Instructors")
	return _.size(_.uniq(_.flatten(_.map(S, function(x){
		return _.pluck(x,"name")
	}))))
})
return result 
{% endlodash %}

<table>
{% for key, value in result %}
    <tr>
        <td>{{key}}</td>
        <td>{{value}}</td>
    </tr>
{% endfor %}
</table>


# Does the instructors tends to give out higher grades if they teach more classes? or the reverse?  by Ming 
{% lodash %}

var graded = _.filter(data,function(d){
  return d.hasOwnProperty("AVG_GRD");
})
var smallData = _.map(graded, function(d){
  var avg_grd = d.AVG_GRD;
  var nameArr = _.pluck(d.Instructors, 'name');
  var objArray = _.map(nameArr, function(d){
    var obj = {name:d,AVG_GRD:avg_grd};
    return obj;
  })
  return objArray;
});

var groups = _.groupBy(_.flatten(smallData),'name');
var groups2 = _.map(groups, function(d){
  var avg = _.reduce(d, function(total,e){
    return total+e.AVG_GRD;
  },0)/_.size(d);
  var obj = {classcount:_.size(d),AVG_GRD:avg,name:_.first(d).name}
  return obj;
});
var groups3 = _.groupBy(groups2,'classcount');

var avgbyCount = _.mapValues(groups3, function(d){
  var avg = _.reduce(d, function(total,e){
    return total+e.AVG_GRD;
  },0)/_.size(d);
  var obj = {classcount:_.first(d).classcount,AVG_GRD:avg,instrCount:_.size(d)}
  return obj;
});
return avgbyCount

{% endlodash %}

{{result | json}}






# Which department has the lowest enrollment?  by John 
{% lodash %}
var group = _.groupBy(data, "CrsPBADept")
var sum = _.mapValues(group, function(n){
	var enroll = _.pluck(n, "N.ENROLL")
	return _.sum(enroll)
})
var min = _.min(sum)
var result = _.pick(sum, function(x){
	return x == min
})
return result
{% endlodash %}
<table>
{% for key, value in result %}
    <tr>
        <td>{{key}}</td>
        <td>{{value}}</td>
    </tr>
{% endfor %}
</table>


# Which subject is most in demand,based on the total number of enrollment?  by Sussant
{% lodash %}
var group = _.groupBy(data, "Subject")
var sum = _.mapValues(group, function(n){
	var enroll = _.pluck(n, "N.ENROLL")
	return _.sum(enroll)
})
var max = _.max(sum)
var result = _.pick(sum, function(x){
	return x == max
})
return result
{% endlodash %}

<table>
{% for key, value in result %}
    <tr>
        <td>{{key}}</td>
        <td>{{value}}</td>
    </tr>
{% endfor %}
</table>
