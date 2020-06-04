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
