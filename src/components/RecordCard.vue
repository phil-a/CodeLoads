<template>

    <b-col class="py-2" md="6" lg="6" sm="6">
    
      <a class="card-link zoom" :href="recordLink">
        <b-card border-variant="primary"
          header-bg-variant="primary"
          header-text-variant="white"
          align="center" bg-variant="light" text-variant="dark" :title="record.title" class="h-100" footer-class="border-0 ">

          <b-card-text>
            {{ record.excerpt }}
          </b-card-text>

          <div>
            <span class="badge-link" v-for="tag in record.tags" :key="tag.title">
              <b-badge :to="tag.path" variant="light">
                #{{ tag.title }}
              </b-badge>
            </span>
          </div>
          <template v-slot:footer footer-class="border-0 m-0 bg-white p-0">
              <span class="small">{{ record.createdAt }} <strong>&#183;</strong> {{ record.timeToRead }} min read</span>
          </template>

        </b-card>
      </a>

    </b-col>

</template>

<script>

export default {
  components: {
  },
  props: ['record'],
  computed: {
    recordLink() {
      if( this.record.recordType == 'Article') {
        return `/articles/${this.record.slug}`;
      }
      if( this.record.recordType == 'News') {
        return `/news/${this.record.slug}`;
      }

      return this.record.path;
    }
  }
}
</script>