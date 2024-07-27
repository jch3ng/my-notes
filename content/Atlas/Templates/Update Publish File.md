<%*
const dv = app.plugins.plugins["dataview"].api;

const fileAndQuery = new Map([
  [
    "podcast",
    'LIST where entity = [[podcast]]'
  ],
  [
    "person",
    'LIST where entity = [[person]]'
  ],
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
    'LIST where entity = [[youtube_video]]'
  ],
  [
    "entity",
    'LIST where entity = [[entity]] and file.name != "entity"'
  ],
  [
    "howto",
    'LIST where entity = [[howto]] and file.name != "howto"'
  ],

]);

await fileAndQuery.forEach(async (query, filename) => {
  if (!tp.file.find_tfile(filename)) {
    await tp.file.create_new("", filename);
    new Notice(`Created ${filename}.`);
  }

  const tFile = tp.file.find_tfile(filename);
  const queryOutput = await dv.queryMarkdown(query);

  queryOutput.value = queryOutput.value.replace(/content\//g, '')
  const fileContent = `---\nentity: "[[entity]]"\n---\n\n${entity_link}\n${queryOutput.value}`;
  try {
    await app.vault.modify(tFile, fileContent);
    new Notice(`Updated ${tFile.basename}.`);
  } catch (error) {
    new Notice("⚠️ ERROR updating! Check console. Skipped file: " + filename , 0);
  }
});
%>







