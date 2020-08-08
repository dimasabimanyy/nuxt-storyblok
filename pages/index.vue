<template>
  <div id="posts">
      <PostPreview v-for="post in posts"
    :key="post.id" :title="post.title" :excerpt="post.previewText" :thumbnailImage="post.thumbnailUrl" :id="post.id" />
  </div>
</template>

<script>
import PostPreview from '../components/Blog/PostPreview.vue';

export default {
  components: {
    PostPreview
  },
  asyncData(context) {
    return context.app.$storyapi.get('cdn/stories', {
      version: 'draft',
      starts_with: 'blog/'
    }).then(res => {
        return {
          posts: res.data.stories.map(bp => {
          return {
            id : bp.slug,
            title: bp.content.title,
            previewText: bp.content.summary,
            thumbnailUrl: bp.content.thumbnail
          }
        })
      };
    });
  }
  // data(){
  //   return {
  //     posts: [
  //       {
  //         title : 'A New Beginning',
  //         previewText : 'This will be awesome, dont miss it.',
  //         thumbnailUrl : 'https://images.unsplash.com/photo-1555099962-4199c345e5dd?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=750&q=80',
  //         id : 'a-new-beginning'
  //       },
  //       {
  //         title : 'A Second Beginning',
  //         previewText : 'This will be awesome, dont miss it.',
  //         thumbnailUrl : 'https://images.unsplash.com/photo-1555099962-4199c345e5dd?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=750&q=80',
  //         id : 'a-second-beginning'
  //       }
  //     ]
  //   }
  // }
}
</script>

<style scoped>
#posts{
  padding-top: 2rem;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
@media (min-width: 35rem){
  #posts{
    flex-direction: row;
  }
}
</style>
