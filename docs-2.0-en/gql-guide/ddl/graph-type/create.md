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

> Noticed that `<catalog object parent reference>` is removed from `<catalog graph type parent and name>`.


### `<node type definition>`

```
<node type definition> ::=
    <node type pattern>

<node type pattern> ::=
    ( [ <node type name and primary key> ] [ <node type filler> ] )

<node type name> ::=
    <element type name> ( <primary key name> )

```

> Noticed that in current implementation, all node types require primary key property. See the `<node type name>` for detail differences.

 
#### `<node type filler>`

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

##### `<label set definition>`

```
<label set definition> ::=
    LABEL <label name>
    | LABELS <label set specification>
    | <is or colon> <label set specification>
```

##### `<property type set definition>`

```
<property type set definition> ::=
    { [ <property type definition list> ] }

<property type definition list> ::=
    <property type definition> [ { , <property type definition> }... ]

<property type definition> ::=
    <property name> [ <typed> ] <property value type>
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
    <minus left bracket> <arc type filler> <bracket right arrow>

<arc type pointing left> ::=
    <left arrow bracket> <arc type filler> <right bracket minus>

<source node type reference> ::=
    ( <source node type name> )
    | ( [ <node type filler> ] )

<destination node type reference> ::=
    ( <destination node type name> )
    | ( [ <node type filler> ] )

```

#### `<arc type filler>`

```
<arc type filler> ::=
    <edge type name> <edge type filler>

<edge type name> ::=
    <element type name>

<edge type filler> ::=
    <edge type label set definition>
    | <edge type property type set definition>
    | <edge type label set definition> <edge type property type set definition>

<edge type label set definition> ::=
    <label set definition>
    
<edge type property type set definition> ::=
    <property type set definition>
```

> Noticed that in GQL, the `<edge type name>` and `<edge type filler>` is optional. However, in current implementation, they are both required. Check out the `<arc type filler>` in GQL standard for details.


## Description