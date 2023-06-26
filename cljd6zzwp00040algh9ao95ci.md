---
title: "Client-side data fetching in Nextjs"
datePublished: Mon Jun 26 2023 18:28:47 GMT+0000 (Coordinated Universal Time)
cuid: cljd6zzwp00040algh9ao95ci
slug: client-side-data-fetching-in-nextjs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1687659356340/ee093301-91ae-4891-ab26-fa841747da80.png
tags: web-development, nextjs

---

📔In this blog post, I will compare and contrast three awesome client-side data-fetching libraries: SWR, Tanstack Query and Apollo Client. These libraries allow you to fetch data from APIs or other sources on the client side, instead of on the server side. This can have some advantages, such as faster rendering, better user experience and offline support. However, it also comes with some challenges, such as caching, error handling and authentication. Let's see how these libraries handle these aspects and what are their pros and cons.

![](https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExMzgzZWkzdm1jcGRobXhod3VuejUwajY1OHUzc3Q5MzdndHV1ZmlyZiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/BpGWitbFZflfSUYuZ9/giphy.gif align="center")

---

### 1️⃣ SWR

[SWR](https://swr.vercel.app/) stands for Stale-While-Revalidate, which is a caching strategy that optimistically renders stale data while fetching fresh data in the background. SWR is a React hook library that makes data fetching easy and fast. It supports features such as automatic revalidation, focus tracking, reflecting on intervals, pagination, suspense and more. SWR works with any data source and has built-in support for JSON and GraphQL APIs. SWR is lightweight and flexible, and you can customize its behavior with various options and plugins.

```javascript
import useSWR from 'swr'
 
function Profile() {
  const { data, error, isLoading } = useSWR('/api/user', fetcher)
 
  if (error) return <div>failed to load</div>
  if (isLoading) return <div>loading...</div>
  return <div>hello {data.name}!</div>
}
```

---

### 2️⃣ TanStack Query

[Tanstack Query](https://tanstack.com/query/latest) is another React hook library that simplifies data fetching and caching. Tanstack Query uses an in-memory cache to store and manage the data you fetch from your APIs. It handles features such as background fetching, caching, deduplication, pagination, mutations, optimistic updates and more. Tanstack Query also works with any data source and has built-in support for JSON and GraphQL APIs. Tanstack Query is powerful and scalable, and you can configure its cache with various options and plugins.

```javascript
import { useQuery } from '@tanstack/react-query'

function Example() {
  const { isLoading, error, data } = useQuery({
    queryKey: ['repoData'],
    queryFn: () =>
      fetch('https://api.github.com/repos/tannerlinsley/react-query').then(
        (res) => res.json(),
      ),
  })

  if (isLoading) return 'Loading...'

  if (error) return 'An error has occurred: ' + error.message

  return (
    <div>
      <h1>{data.name}</h1>
      <p>{data.description}</p>
      <strong>👀 {data.subscribers_count}</strong>{' '}
      <strong>✨ {data.stargazers_count}</strong>{' '}
      <strong>🍴 {data.forks_count}</strong>
    </div>
  )
}
```

---

### 3️⃣ Apollo Client

[Apollo Client](https://www.apollographql.com/docs/react) is a comprehensive state management library that integrates GraphQL with React. Apollo Client allows you to fetch data from GraphQL APIs on the client side and store it in a normalized cache. It handles features such as optimistic UI, prefetching, pagination, subscriptions, mutations, error handling and more. Apollo Client also works with any GraphQL API and has built-in support for JSON APIs. Apollo Client is robust and reliable, and you can extend its functionality with various options and plugins.

---

```javascript
// app/page.tsx
import { getClient } from "@/lib/client";

import { gql } from "@apollo/client";

export const revalidate = 5;
const query = gql`query Now {
    now(id: "1")
}`;

export default async function Page() {
  const client = getClient();
  const { data } = await client.query({ query });

  return <main>{data.now}</main>;
}
```

### 🐱 Takeaway

If you need to fetch data from APIs on the client side, you might want to use one of these three libraries: SWR, Tanstack Query or Apollo Client. They all offer different features and benefits for data fetching and caching. SWR is a lightweight and flexible library that uses a stale-while-revalidate strategy. Tanstack Query is a powerful and scalable library that uses an in-memory cache. Apollo Client is a comprehensive and integrated library that uses GraphQL.  

![](https://media.giphy.com/media/fbqQLgp22TFOvPby68/giphy.gif align="center")