<template>
  <div class="rounded-lg bg-white h-80 w-64 inline-flex flex-col items-center m-4">
    <img
      class="h-20 w-20 mt-6 rounded-full shadow-2xl"
      src="https://images.unsplash.com/photo-1492681290082-e932832941e6?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1171&q=80&auto=format&fit=facearea&facepad=2.25&w=256&h=256&q=80"
      alt=""
    />
    <p class="mt-4 font-bold">{{ user.name }}</p>
    <p class="text-gray-400 text-sm">@{{ user.username }}</p>

    <span class="mt-4 text-xs"
      >Website: <a class="text-blue-600" :href="user.website">{{ user.website }}</a></span
    >

    <span class="mt-2 text-xs"
      >Email: <a class="text-blue-600" :href="`mailto:${user.email}`">{{ user.email }}</a></span
    >

    <span class="mt-2 text-xs text-center">Address: {{ fullAddress }}</span>

    <button
      class="
        bg-gradient-to-r
        from-yellow-400
        via-red-500
        to-pink-500
        rounded-3xl
        px-8
        py-2
        mt-4
        text-white
        capitalize
        font-semibold
      "
    >
      Hire Me
    </button>
  </div>
</template>

<script>
export default {
  props: {
    user: {
      type: Object,
    },
  },
  computed: {
    fullAddress() {
      return `${this.user.address.city} - ${this.user.address.street}`;
    },
  },
};
</script>

<style></style>
