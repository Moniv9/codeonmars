# Caching Database Results

I mostly see developers using this pattern often while **caching** **database** results.

```javascript
class User {

    getUser(id) {
        const user = cache.getUser(id);

        if (user === null) {
            user = db.getUser(id);

            if (user !== null) {
                updateUserCache(id, user);
            }
        }

        return user;
    }
}
```

Here you can see, I am making a synchronous request to the database and then caching the user detail.

Instead caching the user detail should be **asynchronous** request ****and the function should immediately return the user detail once it get from the database. Even if the cache fails, still the system can get it from the database next time and try to update cache then.

Another way is to send the cache updation process into the queue system, which can be picked by another service to update the cache.

```javascript
class User {

    getUser(id) {
        const user = cache.getUser(id);

        if (user === null) {
            user = db.getUser(id);

            if (user !== null) {
                asyncUpdateUserCache(id, user);
            }
        }

        return user;
    }
}
```



