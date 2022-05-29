<template>
  <Layout>
    <div class="beers">
      <div class="container beer-container"
           v-for="item in $page.posts.edges"
      >

        <div class="beer-image">
          <g-image
              :src="item.node.thumbnail"
              :alt="item.node.title"
              class="thumbnail"
          />
        </div>
        <div class="beer-tile">
          <span class="beer-name">{{ item.node.name}} </span>
          <p> {{ item.node.description }}</p>
        </div>

      </div>
    </div>
  </Layout>
</template>

<page-query>
query BeerEntry {
  posts: allBeerEntry {
    edges {
      node {
        id
        path
        name
        thumbnail
        description
      }
    }
  }
}
</page-query>

<script>
import Hero from "@/components/Hero"

export default {
  // components: {
  //   Hero,
  // }
}
</script>

<style scoped>
.beers {
}

.thumbnail {
  height: 560px;
  object-fit: cover;
  transition: all 0.15s ease;
  box-shadow: 0 0 40px -20px rgba(0,0,0,0.25);
}
.beer-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 4rem;
}
.beer-name {
  font-size: 4rem;
  margin: 0 0 4rem 0;
  padding: 0;
}

.beer-meta > div {
  margin-right: 4rem;
}
.beer-meta > div:last-of-type {
  margin: 0;
}
</style>
