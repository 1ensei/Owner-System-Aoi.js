# Owner-System-Aoi.js
An owner system that's quick and easy to set up.

# Information :
- Only server owners can add users.
- This is not a bot owner system, but a permission owner system for the servers concerned.

# Aoi.js requirement
```
// Install
- aoi.js@6.4.0
- aoi.parser

// type
- hander

// Custom fuction (put it in your index.js)
bot.functionManager.createFunction({
    name: "$ifv6",
    type: "djs",
    code: async d => bot.functionManager.cache.get("if").code(d)
})
```

# Variables
```js
owner: "",
owner_count: 0,
owner_page: 0,
global: true
```
