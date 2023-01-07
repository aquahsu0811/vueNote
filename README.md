# provide vs props & custom events


### Provide Props and emits

* Provide only use in parent and child components, so it can't use in neighbors.

* Props and custom events should be the default communication mechanism. 

* Provide use in some pass through case.
* It's hard to read the code, cause it have to dig into all the componetns to understand where those values here in App.vue 


App.vue
```
provide() {
    return {
      topics: this.topics,
      selectTopic: this.activateTopic
    };
  }
```
KnowledgeElements.vue
```
<template>
  <li>
    <h3>{{ topicName }}</h3>
    <p>{{ description }}</p>
    <button @click="selectTopic(id)">Learn More</button>
  </li>
</template>

<script>
export default {
  inject:['selectTopic'],
  props: ['id', 'topicName', 'description'],
};
</script>
```

