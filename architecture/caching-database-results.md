# Caching Database Results

I mostly see developers using this pattern often while **caching** **database** results.

```javascript
class User {

    getUser(id) {
        const user = cache.getUser(id);

        if (user === null) {
            user = db.getUser(id);

            if (user !== null) {
                updateUserCache(id);
            }
        }

        return user;
    }
}
```

Here you can see, I am making a synchronous request to the database and then caching the user detail.

Instead caching the user detail should be **asynchronous** request ****and the function should immediately return the user detail once it get from the database. Even if the cache fails, still the system can get it from the database next time and try to update cache then.

```javascript
class User {

    getUser(id) {
        const user = cache.getUser(id);

        if (user === null) {
            user = db.getUser(id);

            if (user !== null) {
                asyncUpdateUserCache(id);
            }
        }

        return user;
    }
}
```



