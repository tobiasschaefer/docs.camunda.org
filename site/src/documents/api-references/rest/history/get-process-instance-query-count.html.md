---

title: 'Get Process Instances Count'
category: 'History'

keywords: 'historic get query list'

---


Query for the number of historic process instances that fulfill the given parameters.
Takes the same parameters as the [Get Activity Instances](ref:#history-get-activity-instances-historic) method.


Method
------

GET `/history/process-instance/count`


Parameters
----------

#### Query Parameters

<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>processInstanceIds</td>
    <td>Filter by process instance ids. Must be a comma-separated list of process instance ids.</td>
  </tr>
  <tr>
    <td>processInstanceBusinessKey</td>
    <td>Filter by process instance business key.</td>
  </tr>
  <tr>
    <td>superProcessInstanceId</td>
    <td>Restrict query to all process instances that are sub process instances of the given process instance. Takes a process instance id.</td>
  </tr>
  <tr>
    <td>processDefinitionId</td>
    <td>Filter by the process definition the instances run on.</td>
  </tr>
  <tr>
    <td>processDefinitionKey</td>
    <td>Filter by the key of the process definition the instances run on.</td>
  </tr>
  <tr>
    <td>processDefinitionKeyNotIn</td>
    <td>Exclude instances that belong to a set of process definitions. Must be a comma-separated list of process definition keys.</td>
  </tr>
  <tr>
    <td>finished</td>
    <td>Only include finished process instances. Values may be `true` or `false`.</td>
  </tr>
  <tr>
    <td>unfinished</td>
    <td>Only include unfinished process instances. Values may be `true` or `false`.</td>
  </tr>
  <tr>
    <td>startedBy</td>
    <td>Only include process instances that were started by the given user.</td>
  </tr>
  <tr>
    <td>startedBefore</td>
    <td>Restrict to instances that were started before the given date. The date must have the format `yyyy-MM-dd'T'HH:mm:ss`, so for example `2013-01-23T14:42:45` is valid.</td>
  </tr>
  <tr>
    <td>startedAfter</td>
    <td>Restrict to instances that were started after the given date. The date must have the format `yyyy-MM-dd'T'HH:mm:ss`, so for example `2013-01-23T14:42:45` is valid.</td>
  </tr>
  <tr>
    <td>finishedBefore</td>
    <td>Restrict to instances that were finished before the given date. The date must have the format `yyyy-MM-dd'T'HH:mm:ss`, so for example `2013-01-23T14:42:45` is valid.</td>
  </tr>
  <tr>
    <td>finishedAfter</td>
    <td>Restrict to instances that were finished after the given date. The date must have the format `yyyy-MM-dd'T'HH:mm:ss`, so for example `2013-01-23T14:42:45` is valid.</td>
  </tr>
  <tr>
    <td>variables</td>
    <td>Only include process instances that have/had variables with certain values.
    Variable filtering expressions are comma-separated and are structured as follows:<br/>
    A valid parameter value has the form `key_operator_value`.
    `key` is the variable name, `op` is the comparison operator to be used and `value` the variable value.<br/>
    <strong>Note:</strong> Values are always treated as `String` objects on server side.<br/>
    <br/>
    Valid operator values are: `eq` - equals; `neq` - not equals; `gt` - greater than;
    `gteq` - greater than or equals; `lt` - lower than; `lteq` - lower than or equals;
    `like`.<br/>
    `key` and `value` may not contain underscore or comma characters.
    </td>
  </tr>
</table>


Result
------

A json object that contains the count as the only property.

<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Value</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>count</td>
    <td>Number</td>
    <td>The number of matching historic process instances.</td>
  </tr>
</table>


Response codes
--------------

<table class="table table-striped">
  <tr>
    <th>Code</th>
    <th>Media type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>200</td>
    <td>application/json</td>
    <td>Request successful.</td>
  </tr>
  <tr>
    <td>400</td>
    <td>application/json</td>
    <td>Returned if some of the query parameters are invalid. See the <a href="ref:#overview-introduction">Introduction</a> for the error response format.</td>
  </tr>
</table>


Example
-------

#### Request

GET `/history/process-instance/count?variables=myVariable_eq_camunda`

#### Response

    {"count": 1}
