<template>
  <main class="min-h-screen">
    <AppHeader class="mb-12" title="Projects" :description="description" />
    <div class="space-y-4">
      <AppProjectCard
        v-for="(project, id) in projects"
        :key="id"
        :project="project"
      />
    </div>
  </main>
</template>

<script setup>
const description =
  "Over the years, I've worked on many small projects, but these are the ones I'm really proud of. Some of them are open-source, which means anyone can check out the code and suggest improvements if they want to. So feel free to take a look and share your ideas if you have any!";
useSeoMeta({
  title: "Projects | Sujeet Singh",
  description,
});

const { data: projects } = await useAsyncData("projects-all", () =>
  queryContent("/projects").find()
);
</script>
