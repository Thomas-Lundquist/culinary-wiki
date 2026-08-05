```##dataviewjs##
let files = dv.pages('"culinary-1/cooking-techniques"')
    .where(p => p.file.name != "index")
    .sort(p => p.file.name);
let lines = files.map(p => `- [${p.title}](${p.file.name}.md)`).join("\n");
dv.paragraph("```\n" + lines + "\n```");
```

```dataviewjs
let files = dv.pages('"culinary-1/stocks-sauces/mother-sauces"')
    .where(p => p.file.name != "index")
    .sort(p => p.file.name);
let lines = files.map(p => `- **[${p.title}](${p.file.name}.md)**`).join("\n");
dv.paragraph("```\n" + lines + "\n```");
```
