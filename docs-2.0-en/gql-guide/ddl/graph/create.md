# CREATE GRAPH

`CREATE GRAPH` is used to create a graph.

## Syntax

```
<create graph statement> ::=
  CREATE { [ PROPERTY ] GRAPH [ IF NOT EXISTS ] }
    <catalog graph parent and name> { <of graph type> }

<of graph type> ::=
   [ <typed> ] <graph type reference>  

<catalog graph parent and name> ::= [ <catalog object parent reference> ] <graph name>
```
## Prerequisites

To create a graph, you must have CREATE privilege in the used schema and READ privilege for the graph type specified by `of graph type`.

## Effects

The graph is owned by the user issuing this command.  


[Graphs of the same graph type are stored in different physical locations. Even if the graph elements such as nodes or edges in different graphs have the same IDs, they are NOT regarded as the same entity.]



## Parameters

### `IF NOT EXISTS`

Checks if a graph with the same name already exists. If it does already exist, no exception is thrown and the execution ends.
 

### `<graph name>`

Specifies the name of the graph. The name must be xxx. Characters allowed? -> PDF

### `<typed>`

Specifies whether the graph is typed. If not specified, the same effect.
Valid values: `::` and `TYPED`. The same effect. 

### `<graph type reference>`

The `<graph type reference>` specifies the graph type referenced by the new
graph. The schema of all graph element entities in new graph must conform to the
definitions from the referenced graph type. For more information about graph type, see [Create graph type](). 


## Examples

The following examples use the XXX dataset to demonstrate GQL statements. For more information about the dataset, see [dataset introduction](../../overview/sample-dataset.md).

### Create a graph based on a graph type in the default schema
```
nebula> CREATE GRAPH graph_name TYPED graph_type_name
nebula> CREATE GRAPH IF NOT EXISTS graph_name :: graph_type_name
nebula> CREATE GRAPH IF NOT EXISTS graph_name graph_type_name
```

