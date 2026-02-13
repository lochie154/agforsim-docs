---
name: fts5RowidCmp
source_tool: "[[forest_modeling_forestvegetationsimulator_bak]]"
source_file: dbsqlite/sqlite3.c
source_lines: 213773-213786
source_language: c
validated: false
inputs:
  - "[[error|error]]"
outputs:
  - "[[error|error]]"
assumes:
  - "[[error|error]]"
---

# fts5RowidCmp

## Pseudocode
_TODO: describe algorithm_

## Original Code
```c
static int fts5RowidCmp(
  Fts5Expr *pExpr,
  i64 iLhs,
  i64 iRhs
){
  assert( pExpr->bDesc==0 || pExpr->bDesc==1 );
  if( pExpr->bDesc==0 ){
    if( iLhs<iRhs ) return -1;
    return (iLhs > iRhs);
  }else{
    if( iLhs>iRhs ) return -1;
    return (iLhs < iRhs);
  }
}
```