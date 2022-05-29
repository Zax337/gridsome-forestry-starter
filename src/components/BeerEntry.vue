<template>
  <Layout>
    <div class="beer">
      <div class="container beer-container">

        <div class="beer-header">
          <h1 v-html="$page.post.name" class="beer-name" />
          <div class="beer-meta">
            <div class="beer-image">
              <g-image
                  :src="$page.post.thumbnail"
                  :alt="$page.post.title"
                  class="thumbnail"
              />
              <span class="label">Author</span>
              <span class="author-name" v-text="$page.post.author" />
            </div>
          </div>
        </div>

      </div>
    </div>
  </Layout>
</template>

<page-query>
query BeerEntry ($path: String!) {
  post: beerEntry (path: $path) {
    name
    thumbnail
    description
  }
}
</page-query>

<style scoped>
.beer-container {
  max-width: 840px;
}
.beer-header {
  padding: 2rem 0 4rem 0;
}
.beer-name {
  font-size: 4rem;
  margin: 0 0 4rem 0;
  padding: 0;
}
.beer-meta {
  display: flex;
  flex-wrap: wrap;
  font-size: 0.8rem;
}
.beer-meta > div {
  margin-right: 4rem;
}
.beer-meta > div:last-of-type {
  margin: 0;
}
</style>
