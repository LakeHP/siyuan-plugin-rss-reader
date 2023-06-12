<script lang="ts">
    const RSS_URL = "http://www.ruanyifeng.com/blog/atom.xml";
    let xmlText;
    let xmltestend;

    // // 拉取 RSS 数据
    // fetch(RSS_URL)
    //     .then((response) => {
    //         if (!response.ok) {
    //             throw new Error(`${response.status} ${response.statusText}`);
    //         }
    //         return response.text();
    //     })
    //     .then((data) => {
    //         xmlText = data;
    //         console.log(xmlText);

    //         // 解析 XML
    //         const parser = new DOMParser();
    //         const xmlDoc = parser.parseFromString(xmlText, "application/xml");
    //         const entries = Array.from(
    //             xmlDoc.getElementsByTagName("entry")
    //         ).map((entry) => ({
    //             title: entry.getElementsByTagName("title")[0].textContent,
    //             published:
    //                 entry.getElementsByTagName("published")[0].textContent,
    //             summary: entry.getElementsByTagName("summary")[0].textContent,
    //         }));
    //         console.log(xmltestend = entries[0]["published"]);
    //     })
    //     .catch((error) => {
    //         console.error(error);
    //     });

    import Parser from 'rss-parser';

interface Item {
  title: string;
  link: string;
  description: string;
  pubDate: Date;
}

async function getRssItems(url: string): Promise<Item[]> {
  const parser = new Parser();
  const feed = await parser.parseURL(url);
  return feed.items.map(item => ({
    title: item.title,
    link: item.link,
    description: item.contentSnippet ?? item.description ?? '',
    pubDate: new Date(item.pubDate),
  }));
}


getRssItems(RSS_URL)
  .then(items => {
    console.log(items);
  })
  .catch(err => {
    console.error(err);
  });



</script>

<div id="hello">
    {xmltestend}
    <!-- {xmltestend[0]['summary']}   {xmltestend[0]['title']}   
    {xmltestend[1]['published']}   {xmltestend[1]['summary']}   {xmltestend[1]['title']}   
    {xmltestend[2]['published']}   {xmltestend[2]['summary']}   {xmltestend[2]['title']}    -->
</div>
<!-- 
<style lang="scss">
    #hello {
        margin: 20px;
        div {
            margin-bottom: 10px;
        }
    }
    .__text-right {
        text-align: right;
    }
</style> -->
