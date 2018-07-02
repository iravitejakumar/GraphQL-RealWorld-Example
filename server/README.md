# Some Important Notes of GraphQL

# Why we write query keyword infront of GraphQL query ?

In general a query with `query` keyword and a query without `query` keyword always works as same.
```
{
  company(id: "2") {
    description
    name
    users{
      firstName
    }
  }
}
```

```
query {
  company(id: "2") {
    description
    name
    users{
      firstName
    }
  }
}
```

Both these queries gives the same result. But main importance of `query` keyword comes when we name a query. We can name the query using `query` keyword , so that we can reuse it at frontend.

Query with name:

```
query commpanyWithUsers{
  company(id: "2") {
    description
    name
    users{
      firstName
    }
  }
}
```

