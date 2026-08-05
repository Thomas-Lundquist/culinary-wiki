
## Level 1 Indexes

### core

#### equipment
```dataviewjs
const targetDirectory = "core/equipment"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```

#### measurement
```dataviewjs
const targetDirectory = "core/measurement"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```

#### professionalism
```dataviewjs
const targetDirectory = "core/professionalism"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```

#### safety-sanitation
```dataviewjs
const targetDirectory = "core/safety-sanitation"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```

#### strands-and-standards
```dataviewjs
const targetDirectory = "core/strands-and-standards"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```

### culinary-1
#### cooking-methods
```dataviewjs
const targetDirectory = "culinary-1/cooking-methods"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```
#### culinary-math
```dataviewjs
const targetDirectory = "culinary-1/culinary-math"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```
#### knives
```dataviewjs
const targetDirectory = "culinary-1/knives"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```
#### stocks-sauces
```dataviewjs
const targetDirectory = "culinary-1/stocks-sauces"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```
#### yeast-breads
```dataviewjs
const targetDirectory = "culinary-1/yeast-breads"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```

### culinary-2

#### appetizers-salads-sandwiches
```dataviewjs
const targetDirectory = "culinary-2/appetizers-salads-sandwiches"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```
#### commercial equipment
```dataviewjs
const targetDirectory = "culinary-2/commercial-equipment"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```
#### customer-service
```dataviewjs
const targetDirectory = "culinary-2/customer-service"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```
#### dining-room-management
```dataviewjs
const targetDirectory = "culinary-2/dining-room-management"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```
#### quantity-food-prep
```dataviewjs
const targetDirectory = "culinary-2/quantity-food-prep"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```

### food-nutrition
#### cooking-methods
```dataviewjs
const targetDirectory = "food-nutrition/cooking-methods"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```
#### nutrition-guidelines
```dataviewjs
const targetDirectory = "food-nutrition/cooking-methods"; // e.g., "core/equipment"

const parent = app.vault.getAbstractFileByPath(targetDirectory);

if (parent && parent.children) {
    const folderLinks = parent.children
        .filter(item => item.children) // Filter for folders only
        .map(folder => {
            // Check for index.md inside the subfolder
            const indexPage = dv.page(`${folder.path}/index.md`);
            
            // Extract frontmatter title, or fallback to folder.name
            const title = indexPage?.title || folder.name;
            
            return `- **[${title}](${folder.name}/index.md)**`;
        });

    // Renders output in a standard code block for easy copy-pasting
    dv.paragraph("```markdown\n" + folderLinks.join("\n") + "\n```");
} else {
    dv.paragraph("Directory not found. Please check the path.");
}
```
## Level 2 Index Names
```dataviewjs
let files = dv.pages('"culinary-1/cooking-techniques/combination"')
    .where(p => p.file.name != "index")
    .sort(p => p.file.name);

let lines = files.map(p => `- **[${p.title || p.file.name}](${p.file.name}.md)**`).join("\n");

dv.paragraph("\n" + lines + "\n");
```

