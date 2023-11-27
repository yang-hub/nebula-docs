# CREATE GRAPH

`CREATE GRAPH` is used to create a graph.

## Syntax

```
<create graph statement> ::=
  CREATE { [ PROPERTY ] GRAPH [ IF NOT EXISTS ] }
    <graph name> { <of graph type> }

<of graph type> ::=
   [ <typed> ] <graph type reference>  

```

## Prerequisites

To create a graph, you must have `CREATE` privilege in the used schema and `READ` privilege for the graph type specified by `of graph type`.

## Effects

The new graph is owned by the user issuing this statement.  

All indexes defined in the graph type specified by `of graph type` are automatically created in the new graph.


## Parameters

### `IF NOT EXISTS`

Checks if a graph with the same name already exists. If it does already exist, no exception is thrown and the execution ends.
 

### `<graph name>`

Specifies the name of the graph. The name must be xxx. Characters allowed? -> PDF

### `<typed>`

Specifies whether the graph is typed. Valid values: `::` and `TYPED`. If you do not specify this parameter, or set its value to either of the valid values, the graph is always typed.

### `<graph type reference>`

The `<graph type reference>` specifies the graph type referenced by the new
graph. 

The types of the graph elements such as nodes and edges in the new graph must be the same as those defined in the referenced graph type. 

 Graphs of the same graph type are stored in different physical locations. Even if the graph elements such as nodes or edges in different graphs have the same identifiers, they are NOT regarded as the same entity.

For more information about graph type, see [Create graph type]().

## Examples

The following examples use the XXX dataset to demonstrate GQL statements. For more information about the dataset, see [dataset introduction](../../overview/sample-dataset.md).

### Create a graph based on a graph type in the default schema
```
# Use either of the following statements to create a graph.

CREATE GRAPH graph_name TYPED graph_type_name
CREATE GRAPH IF NOT EXISTS graph_name :: graph_type_name
CREATE GRAPH IF NOT EXISTS graph_name graph_type_name
```
For more about how to create a graph type, see [Create graph type]().
