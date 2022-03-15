<template>
  <div class="container-fluid">
    <div class="row justify-content-center mt-4 mb-4">
      <div v-for="(course, index) in courses" :key="index" class="col-auto">
        <div class="card mt-3" style="width: 18rem;">
          <div class="card-header text-center">
            <img class="img-fluid mb-2"
                 :src="'https://asone.udea.edu.co/portafolioudea/files/images/catalog-' + course.image">
            <a :href="'http://link.udea.edu.co/portafolio?q=' + course.id" target="_blank"><h6>{{ course.name }}</h6>
            </a>
          </div>
          <div class="card-body">
            <span v-if="course.active" class="badge bg-success">Activo</span>
            <div class="col-12">{{ course.shortPresentation }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      courses: []
    }
  },
  mounted() {
    fetch("/data.json")
        .then(response => response.json())
        .then(data => this.courses = data.content);
  }
}
</script>

<style>

</style>
