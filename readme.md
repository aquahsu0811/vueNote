1. componets can be registered globally or locally(Prefer local registration)

2. slots
   used to add placeholder for dynamic HTML, nultiple, named slots are possible, default fallbacks can be provided.
   Scoped slots allow adv. use-cases.

## Name slot

```
UserInfo:
<template #header>
  <h3>{{ fullName }}</h3>
  <base-badge :type="role" :caption="role.toUpperCase()"></base-badge>
</template>
  <template v-slot:default>
  <p>{{ infoText }}</p>
</template>

BaseCard:
<template>
  <div>
    <header v-if="$slots.header">
      <slot name="header"></slot>
    </header>
    <slot></slot>
  </div>
</template>

```

## Scoped slot

```
CourseGoals:
<template>
  <ul>
    <li v-for="goal in goals" :key="goal">
      <slot :item="goal" anotherProp="..."></slot>
    </li>
  </ul>
</template>

App:
<course-goals #default="slotProps">
  <h2>{{ slotProps.item }}</h2>
  <p>{{ slotProps.anotherProp}}</p>
</course-goals>

```

3. Dynamic Components

Components can be swapped dynamically via the built-in component

Component caching can be added via the "keep-alive"
