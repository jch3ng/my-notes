```
const fileTitle2 = tp.file.title;
const query2 = `LIST from [[entity]] where entity = [[entity]]`; 
const queryOutput2 = await dv.queryMarkdown(query2);
const fileContent2 = `---\nentity: entity\n---\n\n${queryOutput2.value}`;

// write to file
const filename2 = "entity";
const tFile2 = tp.file.find_tfile(filename2);
await app.vault.modify(tFile2, fileContent2.value);
```