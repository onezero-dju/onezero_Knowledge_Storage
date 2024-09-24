# DELELT란?
| Method  | 의미                | CRUD | 멱등성 | 안전성 | Path Variable | Query Parameter | DataBody |
|---------|---------------------|------|--------|--------|---------------|-----------------|----------|
| **DELETE** | 리소스 삭제          | D    | O      | X      | O             | X               | X        |

```
 @DeleteMapping(path = {"/user/{userName}/delete/", "/user/{userName}/del"})
    public void delete(@PathVariable String userName) {
        log.info("user-name : {}",userName);

    }
```