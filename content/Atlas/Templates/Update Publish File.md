
<%*
const dv = app.plugins.plugins["dataview"].api;

const fileAndQuery = new Map([
  [
    "book",
    'LIST where entity = [[book]]'
  ],
  [
    "podcast_episode",
    'LIST where entity = [[podcast_episode]]'
  ],
  [
    "youtube_video",
    'LIST from [[youtube_video]] where entity = [[youtube_video]]'
  ],
  [
    "entity",
    'LIST from [[entity]] where entity = [[entity]] and file.name != "entity"'
  ],
  [
    "howto",
    'LIST from [[howto]] where entity = [[howto]] and file.name != "howto"'
  ],

]);

await fileAndQuery.forEach(async (query, filename) => {
  if (!tp.file.find_tfile(filename)) {
    await tp.file.create_new("", filename);
    new Notice(`Created ${filename}.`);
  }
  var entity_link = 'up: [[entity]]'
  if (filename == 'entity') {
    entity_link = ' '
  }
  const tFile = tp.file.find_tfile(filename);
  const queryOutput = await dv.queryMarkdown(query);
  const fileContent = `---\nentity: "[[entity]]"\n---\n%% update via "Update Publish Files" template %% \n${entity_link}\n${queryOutput.value}`;
  try {
    await app.vault.modify(tFile, fileContent);
    new Notice(`Updated ${tFile.basename}.`);
  } catch (error) {
    new Notice("⚠️ ERROR updating! Check console. Skipped file: " + filename , 0);
  }
});
%>
