<script lang="ts">

const RSS_URL = "http://www.ruanyifeng.com/blog/atom.xml";
let blog ;

// fetch(RSS_URL)
//   .then(response => response.text())
//   .then(str => new window.DOMParser().parseFromString(str, "text/html"))
// //   .then(data => console.log(blog_type=typeof(data)))
//   .then(data => console.log(blog = data))

const url = RSS_URL;

fetch(url)
  .then(response => response.text())
  .then(data => {
    console.log(blog = data); // This should output the response body as text
  })
  .catch(error => {
    console.error(error);
  });



</script>

<div id="hello">
    {blog}
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
