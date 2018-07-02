# Some Important Notes of GraphQL

## Why we write query keyword infront of GraphQL query ?

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

Both these queries gives the same result. But main importance of `query` keyword is it gives us ability to name the query, so that we can reuse it in frontend code.

##### Query with name:

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

## What is the use of fragments in GraphQL?

Lets say we are writing same properties repeatedly for querying a type like company shown below.

```
{
  pramati: company(id: "2") {
    id
    description
    name
  }
  apple: company(id: "1") {
    id
    description
    name
  }
}
```

we can use define `id`, `description` and `name` properties in a fragment and reuse them as follows:

```
{
  pramati: company(id: "2") {
    ...companyDetails
  }
  apple: company(id: "1") {
    ...companyDetails
  }
}

fragment companyDetails on Company {
  id
  description
  name
}
```

## What are mutations in GraphQL?

To make any modifications for the types we go for mutations in GraphQL. Generally we will use it for `POST`, `PUT` and `DELETE`
