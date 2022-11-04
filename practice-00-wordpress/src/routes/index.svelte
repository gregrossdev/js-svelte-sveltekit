<script context="module">
  export const load = async ({fetch}) => {
    // const endpoint = "https://jsonplaceholder.typicode.com/posts";
    const endpoint = "http://localhost:8000/wp-json/wp/v2/posts";
    const res = await fetch(endpoint);
    const posts = await res.json();

    return {
      props: {
        posts,
      }
    }
  }
</script>

<script>
  export let posts; 
</script>

{#each posts as post}
<h2>{post.title.rendered}</h2>
<p>{@html post.excerpt.rendered}</p>
{/each}