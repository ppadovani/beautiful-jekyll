---
layout: page
title: KNQL Plugin
subtitle: Query Language
comments: true
---

## KNQL - Query Language ## 

- [Overview](#overview)
- [Language](#language)
  * [Any](#any)
  * [Field-Names](#field-names)
    + [Multi-Field-Names](#multi-field-names)
  * [Exists](#exists)
  * [Values](#values)
    + [Simple-Values](#simple-values)
    + [Sets](#sets)
    + [Range](#range)
  * [Operators](#operators)
    + [Equals](#equals)
    + [Like](#like)
    + [Greater-and-Less-than](#greater-and-less-than)
    + [In](#in)
  * [Basic-Expressions](#basic-expressions)
  * [Not](#not)
  * [Nested-Field-Support](#nested-field-support)
- [Error-Handling](#error-handling)
- [Reserved-Keywords](#reserved-keywords)

## Overview

The query language created for this plugin was designed based on two basic premises:
1. Make it easy clear for the end user
2. Support nested fields in Elasticsearch

The existing query language in Kibana isn't based on any standard, and isn't even parsed by Kibana. 
The language is the Lucene query language, and any expression entered is passed directly through to
the backend without being examined for syntactic correctness. If a syntax error was entered, 
the user either:
* Wasn't told there was an error in the query and no results were returned.
* An exception and stack trace is returned from Elasticsearch that the user has to read through 
  to try and determine what they did wrong. 

The KNQL language is loosely based on the SQL standard with a few constructs missing and added. 
The queries are parsed within Kibana and translated into an Elasticsearch query. The language is
not fully complete in that it doesn't support the full breadth of what one can do with an 
Elasticsearch query. However suggestions for enhancements are welcome as people find gaps
in functionality that they require.

## Language

### Any

A user can ask for all values from the index to be returned by simple using a lone '*' as the
query or the keyword 'ANY'. This will product a 'match all' Elasticsearch query equivalent.

### Field-Names

In Elasticsearch a field name is a string made up of numbers and letters and perhaps an underscore.
However, a dot ('.') is allowed within a field name when referencing a field within a sub-object.
Take this mapping snippet for example:
~~~
 "mappings": {
  "home": {
   "properties": {
    "address": {
     "properties": {
      "city": {
       "type": "keyword"
      },
      "postalCode": {
       "type": "keyword"
      },
      "street": {
       "type": "keyword"
      }
     }
    },
~~~

In order to reference the city of the address as part of a query, one would need to use the 
field name 'address.city'. Accessing nested fields is no different and the field name can
contain as many dots in the path as needed in order to properly identify the field name
required in the query.

#### Multi-Field-Names

One feature of this language is the ability to target multiple fields with one expression. In order
accomplish this, there is a special rule associated with specifying field names. A user can 
specify a star '*' as the last character of a field name in order to target all fields that
match the prefix string. Given the above mapping snippet then, the following are valid field
names:
* add*
* address.*
* address.c*

### Exists

The keyword 'EXISTS' is used to check if a field exists or contains a value, and to test for the 
existence of a nested object. The latter functionality will be discussed in the nested field 
support section.

In Elasticsearch if a field within a document does not have a value it doesn't exist in the 
document at all. The equivalent check in SQL would be something like ```field IS NULL```. In 
order to align a bit better with the underlying semantics of Elasticsearch, this keyword is
used as shown below:

```EXISTS address.city```

### Values

When defining a query expression, a value must always be present on the right hand side of a
comparison with a field. 

#### Simple-Values

A simple value is nothing more than single values that a user is attempting to match a 
field name to. The support simple values are:
* String - A string surrounded by double quotes: "simple value"
* Integer - An integer value: 12345 or -12345
* Decimal - A number containing a single dot with any number of places: 3.14159
* Boolean - Use of the boolean keywords: true or false or TRUE or FALSE
* Date - A date **without** time: 2018-02-04
* Datetime - A date **with** a time: 2018-02-04T10:05:34.000Z
* IPV4 - An IPV4 address: 192.168.1.1

**NOTE** A keyword exists called 'now' that allows the user to specify the current
instant in time to be used as the value.

#### Sets

A set is used to check if a field name contains a value within a set of values. For example
is the car.color within the set of colors: red, blue, green, white, silver. A set can contain
any number of the simple values defined above **as long as all of the values are of the same type**.
A set is surrounded by '{' and '}'. Examples:
* {'red', 'green', 'blue'}
* {2018-01-01, 2018-02-01}
* {1.0, 3.1415, 6.3}

Within Elasticsearch the query generated when using a set is equivalent to using a 'should' clause.

**NOTE** This value can only be used with the IN operator described below.

#### Range

A range value denotes a minimum and maximum value to match a field against. This could be a
price range, date range etc. Only two values are allowed within a range. The range value uses '[]' and '()' to surround the values used
within the query, and which is used depends on the intended range check. The square brackets '[]' 
indicate to the parser to **NOT** include either the upper or lower bound of the range. Whereas
the '()' indicate to the parser **TO** include either the upper or lower bound. Some examples:
* [3.14159, 6.3] - Match against values greater than 3.14159 and less than 6.3.
* (12, 24) - Match against values greater than or equal to 12 and less than or equal to 24.
* (3.14159, 24] - Match against values greater than or equal to 3.14159 and less than 24.
* [12, 6.3) - Match against values greater than 12 and less than or equal to 6.3.

**NOTE** This value can only be used with the IN operator described below.

### Operators

An operator is a symbol that is used to build an expression with a field name. This language has a 
basic set of operators that cover most required operations.

#### Equals

The equals operator '=' signifies an exact match to the value specified on the right hand side
of the expression. Only a simple value can be specified. Examples:
* cars.color = "red"
* cars.purchaseDate = 2017-01-01
* cars.purchaseDate > now
* cars.purchasePrice = 13299.40

#### Like

The link operator '~=' is used to indicate that a wildcard expression will be used. A wildcard
expression is one where the user is attempting to match against multiple values or does not
know the entire value being search upon. Examples:
* cars.color = "*white" - This might match 'metallic white', 'pearl white' etc.

#### Greater-and-Less-than

These operators contain the basic expected set of operators:
* &gt; - greater than
* &gt;= - greater than or equals to
* < - less than
* <= - less than or equals to

#### In

The 'IN' operator is used to test a field name against a set of possible values **OR** against
a range of values. Examples:
* cars.color IN {'red', 'green', 'blue'}
* cars.purchasePrice IN [13000, 14000]


### Basic-Expressions

The above discussed the basic atomic pieces needed to build a query. Expressions in KNQL look very 
similar to basic SQL. A comparison between a field name and value using an operator can be chained
together with AND and OR.
* ```cars.color = 'red' AND cars.purchasePrice IN [13000, 14000]``` - Find documents whose cars 
are the color red and whose purchase price is greater than 13000 and less than 14000.
* ```(cars.color = 'red' OR cars.make='Honda') AND cars.purchasePrice IN [13000, 14000]```

Notice in the last example that the '()' were used to scope out a portion of the query. This
will be needed by users to build more complex boolean expressions.

### Not

The 'NOT' keyword is used to negate an operation or expression. If one wanted to find all
cars that were not red, the expression might look like:
```NOT cars.color = 'red'```

This keyword can be used outside any expression or scoped set of expressions:
```NOT (cars.color = 'red' OR cars.make='Honda') AND cars.purchasePrice IN [13000, 14000]```

### Nested-Field-Support

In general you will never notice that nested queries are being generated, as this is done for you in the query parser. 
There are cases where a complex query requires that the nested fields be scoped correctly in order to return the correct 
results. This is where the unary EXISTS comes into play. The EXISTS provides a mechanism to scope a set of nested 
conditions together into a single condition. The thought here is that the use of EXISTS is checking for the existence 
of one or more nested objects within the parent.

Consider this query based on the simple home model defined above, where an home contains two car objects. car 
object #1 has a make of Honda, and car object #2 has a make of Acura.:

```roof="steel" AND ( cars_size=0 OR NOT car.make IN {"Lexus","Acura"})``` 

This query returns the wrong results because it was able to match one of the two nested car objects. What this query 
did was test each individual car against the "IN {"Lexus","Acura"}" rather than against the entire set of car objects. 
If the search was changed to use exists the correct result should be returned (no results in this case).

```roof="steel" AND ( cars_size=0 OR NOT EXISTS car.make IN {"Lexus","Acura"}) ```

When using EXISTS, whatever follows EXISTS as an expression, including surrounding the expression in parentheses, will 
be scoped to that one nested expression. You can use EXISTS multiple times within the same query as well.

```roof="steel" AND ( cars_size=0 OR NOT EXISTS car.make = "Lexus" OR NOT EXISTS car.make = "Acura")``` 

Please note that when saving a new style query, the next time it is loaded EXISTS unaries will be automatically injected for each scoped nested query. This happens because the query stored in the Kibana index is actually the Elasticsearch JSON query generated by the parser, and it must be reverse parsed back into the new style query language.


### Error-Handling

__NOTE:__ In order to avoid issues with native Kibana queries, indexPatterns that have nested support turned on can
only use the above query language.

When typing the query, the query is constantly parsed. In this example a single letter 'l' was typed which did not match any known field in the index. Please note that the existing type ahead still works.
![invalid field](img/invalid-field.png)

In this example, the query is not correctly formed as it doesn't contain a value:
![invalid syntax](img/syntax-error.png)

Finally, if the user attempts to put a value that doesn't match the type of the field, the parser will send an error.
![invalid value](img/invalid-value.png)

### Reserved-Keywords

* AND - Used to and two comparisons/expressions together
* OR - Used to or two comparisions/expressions together
* NOT - Negate a comparision/expression
* now - Use the current date/time as the value in a comparision
* ANY - Use a match-all query
* '*' - Equivalent to ANY or can be used to match multiple fields
* IN - Used for range or set comparisions
* EXISTS - Tests the existence of a field, or nested object
* TRUE or true - boolean true value used in a comparison
* FALSE or false - boolean false value used in a comparison


