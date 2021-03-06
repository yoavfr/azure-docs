---
title: ARRAY_CONCAT in Azure Cosmos DB query language
description: Learn about SQL system function ARRAY_CONCAT in Azure Cosmos DB.
author: ginamr
ms.service: cosmos-db
ms.topic: conceptual
ms.date: 09/13/2019
ms.author: girobins
ms.custom: query-reference
---
# ARRAY_CONCAT (Azure Cosmos DB)
 Returns an array that is the result of concatenating two or more array values.  
  
## Syntax
  
```sql
ARRAY_CONCAT (<arr_expr1>, <arr_expr2> [, <arr_exprN>])  
```  
  
## Arguments
  
*arr_expr*  
   Is an array expression to concatenate to the other values. The `ARRAY_CONCAT` function requires at least two *arr_expr* arguments.  
  
## Return types
  
  Returns an array expression.  
  
## Examples
  
  The following example how to concatenate two arrays.  
  
```sql
SELECT ARRAY_CONCAT(["apples", "strawberries"], ["bananas"]) AS arrayConcat 
```  
  
 Here is the result set.  
  
```json
[{"arrayConcat": ["apples", "strawberries", "bananas"]}]  
```  
  

## Next steps

- [Array functions Azure Cosmos DB](sql-query-array-functions.md)
- [System functions Azure Cosmos DB](sql-query-system-functions.md)
- [Introduction to Azure Cosmos DB](introduction.md)
