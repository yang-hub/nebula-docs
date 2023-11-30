# Keywords and identifiers

Keywords and identifiers are two fundamental components in GQL statements.

## Keywords

Keywords are words with specific meanings in GQL, such as `CREATE` and `GRAPH` in the `CREATE GRAPH` statement.

## Identifiers

Identifiers are commonly used to identify objects like graphs and graph types.

### Rules for naming identifiers

In GQL statements, a identifier may be enclosed with double quotes (") or back quotes (`):

-  If quoted, the identifer can contain any character. 
-  If not quoted, the identifier must start with a Unicode letter or an underscore (\_). Subsequent characters can be Unicode letters, underscores (\_), or digits (0-9).