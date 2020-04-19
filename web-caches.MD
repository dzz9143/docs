## target:
- browser
- proxy

## 2 kinds:
- shared cache: shared accros all users
- private cache: dedicated to single user

## cache policy
1. No caching
The cache should not store anything about the client request or server response. `A request is sent to the server and a full response is downloaded each and every time`.
```
Cache-Control: no-store
```

2. Cache but revalidate
A cache will send the request to the origin server for `validation` before releasing a cached copy

but how it validate?

```
Cache-Control: no-cache
```

3. Private and public caches
The "public" directive indicates that the response may be cached `by any cache`. This can be useful if pages with HTTP authentication, or response status codes that aren't normally cacheable, should now be cached.

What is means by `any cache`

On the other hand, "private" indicates that the response is intended for a single user only and must not be stored by a shared cache. A `private browser` cache may store the response in this case.