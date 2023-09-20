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
```
```js
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
interaction: false // put "true" if you use discord slash commands
```

# [prefix]owner <member>
```js
module.exports = [{
    name: "owner",
    
    usage: "owner <membre>",
    description: "Ajouter les permissions owner à un utilisateur sur le serveur.",

    $if: "old",

    code: `
    $sendlogs[$getGuildVar[owner_logs];<@$findMember[$message;false]> a désormais les permissions __owner__.;$getGuildVar[color]]

    $sendMessage[$nonEscape[$ifv6[$getGuildVar[delafter]!=false;{extraOptions:{delete:$getGuildVar[delafter]}}]{options:{mention:false}}> <@$findMember[$message;false]> a désormais les permissions __owner__.]]

    $setGuildVar[owner_page;$get[page]]
    
    $let[page;$round[$replaceText[$replaceText[$replaceText[$replaceText[$replaceText[$divide[$getGuildVar[owner_count];10];.1;.6];.2;.6];.3;.6];.4;.6];.5;.6]]]
    
    $setGuildVar[owner;$nonEscape[$ifv6[$getGuildVar[owner_count]==1;$findMember[$message;false];$getGuildVar[owner], $findMember[$message;false]]]]
    $setGuildVar[owner_count;$sum[$getGuildVar[owner_count];1]]
    
    $onlyIf[$checkContains[$getGuildVar[owner];$findMember[$message;false]]==false;$nonEscape[{options:{mention:false}}$replaceText[$getGuildVar[error];,,error,,;<@$findMember[$message;false]> a déjà les permissions __owner__.]]]
    $onlyIf[$findMember[$message;false]!=;$nonEscape[$replaceText[$getGuildVar[error];,,error,,;Le membre donné est invalide]]]
    $onlyIf[$authorID==$ownerID||$checkContains[$getVar[dev];$authorID]==true;$nonEscape[$replaceText[$getGuildVar[noperm];,,require_perms,,;\`Propriétaire du serveur\`]]]
    $onlyIf[$guildID!=;]
    `
}]
```

# ⚠️ THIS SYSTEM ISN'T FINISHED ⚠️
