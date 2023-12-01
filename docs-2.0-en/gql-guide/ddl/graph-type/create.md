# CREATE GRAPH TYPE

`CREATE GRAPH TYPE` is used to create a graph type.

## Syntax

### `<create graph type statement>`

```
<create graph type statement> ::=
    CREATE
        { [ PROPERTY ] GRAPH TYPE [ IF NOT EXISTS ] }
        <graph type name> <graph type source>

<graph type source> ::=
    [ AS ] <nested graph type specification>

<nested graph type specification> ::=
    { <graph type specification body> }

<graph type specification body> ::=
    <element type definition list>

<element type definition list> ::=
    <element type definition> [ { , <element type definition> }... ]

<element type definition> ::=
    <node type definition>
    | <edge type definition>

```

### `<node type definition>`

```
<node type definition> ::=
    <node type pattern>

<node type pattern> ::=
    ( [ <node type name and primary key> ] [ <node type filler> ] )

<node type name and primary key> ::=
    <node type name> ( <primary key name> )

```

> Noticed that in current implementation, all node types require primary key property. See the `<node type name>` for detail differences.

 
### `<node type filler>`

```
<node type filler> ::=
    <node type label set definition>
    | <node type property type set definition>
    | <node type label set definition> <node type property type set definition>

<node type label set definition> ::=
    <label set definition>

<node type property type set definition> ::=
    <property type set definition>
```

### `<label set definition>`

```
<label set definition> ::=
    LABEL <label name>
    | LABELS <label set specification>
    | < IS | : > <label set specification>
```

### `<property type set definition>`

```
<property type set definition> ::=
    { [ <property type definition list> ] }

<property type definition list> ::=
    <property type definition> [ { , <property type definition> }... ]

<property type definition> ::=
    <property name> [ :: | TYPED ] <property value type>
```

> For details property value type, please refer to DataType doc.

### `<edge type definition>`

```
<edge type definition> ::=
    <edge type pattern>

<edge type pattern> ::=
    <full edge type pattern>

<full edge type pattern> ::=
    <full edge type pattern pointing right>
    | <full edge type pattern pointing left>

<full edge type pattern pointing right> ::=
    <source node type reference> <arc type pointing right> <destination node type reference>

<full edge type pattern pointing left> ::=
    <destination node type reference> <arc type pointing left> <source node type reference>


<arc type pointing right> ::=
    -[ <arc type filler> ]-> 

<arc type pointing left> ::=
    <-[ <arc type filler> ]-

<source node type reference> ::=
    ( <source node type name> )
    | ( [ <node type filler> ] )

<destination node type reference> ::=
    ( <destination node type name> )
    | ( [ <node type filler> ] )

```

### `<arc type filler>`

```
<arc type filler> ::=
    <edge type name> <edge type filler>

<edge type filler> ::=
    <edge type label set definition>
    | <edge type property type set definition>
    | <edge type label set definition> <edge type property type set definition>

<edge type label set definition> ::=
    <label set definition>
    
<edge type property type set definition> ::=
    <property type set definition>
```


## Description

## Prerequisites

To create a graph type, you must have `CREATE` privilege in the used schema.

## Parameters

### IF NOT EXISTS

### `<graph type name>`

The name of the graph type to be created.

### `<node type name>`

The name of a node type in the graph type to be created.

### `<edge type name>`

The name of an edge type in the graph type to be created.

### `<primary key name>`

The name of the property that functions as the primary key. The property must be defined in `<node type property type set definition>`.

### `<label name>`

The name of a single label of the node type or edge type in the graph type. To define multiple labels, refer to `<label set specification>`.

### `<label set specification>` 

The names of multiple labels of the node type or edge type in the graph type. Separate multiple names with ampersand (`&`). For example, `Label1&Label2`.

### `<property name>` 

The name of a property of a node type or edge type in the graph type.

### `<property value type>`

The value type of a property of a node type or edge type in the graph type. For details, refer to DataType doc.

### `<source node type name>` 

The name of the source node type of the edge type. The source node type must be one of the node types defined in the graph type.

### `<destination node type name>` 

The name of the destination node type of the edge type. The destination node type must be one of the node types defined in the graph type.

## Examples

### Scenario 1: Create a graph type

```
CREATE GRAPH TYPE gt1 AS {
    (Place(id) LABELS City&Country {id INT, name STRING, url STRING, kind STRING}),
    (Student(id) LABEL Person {id INT, firstName STRING, lastName STRING, gender STRING, birthday DATE}),
    (Student)-[Likes:Knows{since LOCALDATETIME}]->(Student),
    (Place)<-[Lives:Locates]-(Student)
}
```

Create a graph type named "gt1" with two node types and two edge types:
* node type Place with two labels (City/Country), four properties (id/name/url/kind) with value types respectively.
* node type Student with only one label Person, five properties (id/firstName/lastName/gender/birthday).
* edge type Likes with source node type Student and destination node type Student, one label Knows, one property since.
* edge type Lives with source node type Student and destination node type Place, one label Locates, no property.

### Scenario 2: Create a graph type with `IF NOT EXISTS`

```
CREATE GRAPH TYPE IF NOT EXISTS gt2 AS {
    (Student(id) : Person {id INT, firstName STRING, lastName STRING, gender STRING, birthday DATE}),
    (Student)-[Likes LABEL KNOWS {since LOCALDATETIME}]->(Student)
}
```

Create a graph type named "gt2" with one node type and one edge type if graph type `gt2` doest not exist. If graph type `gt2`, nothing happens.