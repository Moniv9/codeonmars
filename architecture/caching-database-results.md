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

Here you can see, I am making a synchronous request to the database, updating the user cache and then returning the user detail.

Instead of this, caching of user detail should be **asynchronous** request ****and the function should immediately return the user detail once it get from the database. Even if the cache fails, still the system can get it from the database next time and try to update the cache then.

{% hint style="info" %}
Asynchronous flow help reduce request times for expensive operations or task whose results are not demanded immediately.
{% endhint %}

Another way is to send the **cache updation process** into the queue system, which can be picked by another service to update the cache.

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



