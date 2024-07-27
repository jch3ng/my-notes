---
entity: "[[howto]]"
---
## Remove GitHub and Discord Links

go to `quartz.layout.ts` and comment out these lines: 

```
GitHub: "https://github.com/jackyzha0/quartz",
"Discord Community": "https://discord.gg/cRFFHYye7t",
```

You should then have:
```javascript
// components shared across all pages
export const sharedPageComponents: SharedLayout = {
  head: Component.Head(),
  header: [],
  afterBody: [],
  footer: Component.Footer({
    links: {
     // GitHub: "https://github.com/jackyzha0/quartz",
     // "Discord Community": "https://discord.gg/cRFFHYye7t",
    },
  }),
}
```

## Remove Footer

`vi quartz/components/Footer.tsx`

add `return false`:
```
  //return Footer
  return false
```


