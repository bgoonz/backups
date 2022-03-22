# Using Web Storage - SitePoint

[https://www.sitepoint.com/using-web-storage/](https://www.sitepoint.com/using-web-storage/)

Welcome to another article in the small and sweet functions series, in which I'd like to show you a neat abstraction called `domStorage()`, that provides a set of convenient functions for interacting with Web Storage, while discretely handling all the most common points of failure.

If you're not already familiar with Web Storage (aka DOM Storage), I'd recommend Colin Ihrig's article: [An Overview of the Web Storage API](https://www.sitepoint.com/an-overview-of-the-web-storage-api/).

Here's the `domStorage()` function's code:

```
function domStorage(persist)
{
try
{
var storage = window[persist ? 'localStorage' : 'sessionStorage'];
if(!storage) { return null; }
}
catch(ex) { return null; }

return {

read : function(key)
{
return storage.getItem(key);
}

, write : function(key, value)
{
try
{
return storage[key] = value.toString();
}
catch(ex) { return null; }
}

, erase : function(key)
{
storage.removeItem(key);
return true;
}

, keys : function()
{
for(var keys = [], n = storage.length, i = 0; i < n; i ++)
{
keys.push(storage.key(i));
}
return keys;
}

, clear : function()
{
try
{
storage.clear();
return true;
}
catch(ex) { return false; }
}
};
}
```

## How to Use the Function

The `domStorage()` function returns an object, containing methods that can then be used as shortcuts for things like reading and writing values. However if Web Storage is not supported, or is disabled in the browser, then the `domStorage()` function returns `null`. You start by calling `domStorage()` and saving the reference it returns, as shown below.

```
var storage = domStorage();
```

By default, the function creates a reference to *session storage* – data that is automatically deleted at the end of the browser session. You can also select persistent storage by passing in the Boolean value `true`, as shown below. In this case, the data will persist until you or the user deletes it.

```
var storage = domStorage(true);
```

Once you have the `storage` reference, you should test that it isn't `null` before attempting to use its methods:

```
var storage = domStorage();
if(storage !== null)
{
//storage is supported
}
```

The main methods are `read()`, which takes a single `key` argument, and `write()`, which takes a `key` and `value`. Storage interactions are **synchronous**, so you can read a value as soon as it's written:

```
storage.write("key", "value");
storage.read("key");
```

All stored values are strings, with any other data type silently converted (e.g. `123` is saved as `"123"`). If you need to store complex data, the best approach is to save it as a JSON string:

```
storage.write("key", JSON.stringify(data));
```

Both the `read()` and `write()` methods return a string if successful, or `null` for failure. A failure for `read()` means there was no storage value with that key, whereas a failure for `write()` means the value was not saved. This will only happen if the value is *too large* for the remaining storage space available, according to the quota set by browser preferences, which we'll discuss in the next section.

```
if(storage.write("key", "value") === null)
{
//value was not saved
}
```

There are also two deletion methods, one for erasing a single value:

```
storage.erase("key");
```

And another for clearing *every* value in the storage object (so careful there!):

```
storage.clear();
```

Finally, there's a `keys()` method that returns an array of string keys, for each of the values currently defined in the storage object:

```
var keys = storage.keys();
```

You could use this, for example, to inspect a storage object and find out how much data it contains:

```
var size = 0,
keys = storage.keys();

for(var n = keys.length, i = 0; i < n; i ++)
{
size += storage.read(keys[i]).length;
}

alert((size / 1000).toFixed(2) + 'K');
```

## How the Function Works

Essentially, all the `domStorage()` function does is define a set of shortcut methods, but it also handles several points of failure that could otherwise cause errors. The first, and most likely, failure occurs when getting a reference to the storage object itself (either `sessionStorage` or `localStorage` according to the `persist` argument). The storage object might not be supported, but even if it is, it might throw an error when referenced. This is because the specification allows the browser to throw a security error if the use of storage would violate a policy decision, such as being disabled by the user. So, that's the first place we need exception handling, catching any such error and returning `null` for failure:

```
try
{
var storage = window[persist ? 'localStorage' : 'sessionStorage'];
if(!storage) { return null; }
}
catch(ex) { return null; }
```

The next potential failure is when **saving a value**, because there's a limit to how much data we can store. Browsers set a quota, and most also provide user preferences for adjusting it. As far as I know, there's no reliable way of programatically determining what the quota is, but it's usually more than enough – somewhere from `2-5MB`, depending on the browser. If saving a value would exceed that quota, the browser will throw another error. So, we handle that and return `null` for failure:

```
try
{
return storage[key] = value.toString();
}
catch(ex) { return null; }
```

You'll notice that I've used square-bracket notation rather than the `setItem()` function, and this is simply for the convenience of saving and returning the value in a single expression, as an alternative to this:

```
try
{
storage.setItem(key, value);
return value.toString();
}
catch(ex) { return null; }
```

The final point of failure is when using the `clear()` function, because some early implementations don't support it (such as Firefox 3). To avoid raising errors in these implementations, we use exception handling again, and then return `true` or `false` to indicate success:

```
try
{
storage.clear();
return true;
}
catch(ex) { return false; }
```

If you do really need this functionality to work in older implementations, it's simple enough to do the same thing by using the `keys()` method – iterating through the keys it returns and erasing each value manually:

```
if(storage.clear() === false)
{
var keys = storage.keys();

for(var n = keys.length, i = 0; i < n; i ++)
{
storage.erase(keys[i]);
}
}
```

Note that Firefox 2-3 have limited support for Web Storage – in addition to missing support for `clear()`, they don't support `localStorage` at all, only `sessionStorage`. It's also worth noting that IE7 does not support Web Storage at all. IE8 does support it, even in Compatibility Mode – which gives the false impression that IE7 also supports it.

## Conclusion

What makes `domStorage()` a useful abstraction, is the way it handles these different points of failure in a seamless way. It saves on repeatedly having to check and test and handle exceptions, so that straightforward tasks, like reading and writing, are as simple as they should be!

[James Edwards](https://www.sitepoint.com/author/brothercake/)
James is a freelance web developer based in the UK, specialising in JavaScript application development and building accessible websites. With more than a decade's professional experience, he is a published author, a frequent blogger and speaker, and an outspoken advocate of standards-based development.
