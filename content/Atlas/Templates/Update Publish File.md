<%*
dv = this.app.plugins.plugins["dataview"].api;
const fileTitle = tp.file.title;
const query = `LIST from [[youtube_video]]`; 
const queryOutput = await dv.queryMarkdown(query);

// write to file
const filename = "youtube_video";
const tFile = tp.file.find_tfile(filename);
await app.vault.modify(tFile, queryOutput.value);
%>







