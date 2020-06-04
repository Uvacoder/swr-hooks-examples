# SWR Examples

[SWR](https://swr.now.sh/) is a React Hooks library for remote data fetching.

## Basic Example

```js
import useSWR from "swr";

const fetcher = (url) => fetch(url).then((r) => r.json());

const Profile = () => {
  const { data, error } = useSWR("/api/user", fetcher);

  if (error) return <div>failed to load</div>;
  if (!data) return <div>loading...</div>;
  return (
    <>
      <p>hello {data.name}!</p>
    </>
  );
};

export default Profile;
```

[![Edit gregrickaby/swr-examples: example-basic](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/github/gregrickaby/swr-examples/tree/master/example-basic?fontsize=14&hidenavigation=1&theme=dark)

---

## GraphQL

```js
import { request } from "graphql-request";

const API = "https://api.graph.cool/simple/v1/movies";
const fetcher = (query) => request(API, query);

function App() {
  const { data, error } = useSWR(
    `{
      Movie(title: "Inception") {
        releaseDate
        actors {
          name
        }
      }
    }`,
    fetcher
  );
  // ...
}
```

[![Edit gregrickaby/swr-examples: example-graphql](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/github/gregrickaby/swr-examples/tree/master/example-graphql?fontsize=14&hidenavigation=1&theme=dark)

---
