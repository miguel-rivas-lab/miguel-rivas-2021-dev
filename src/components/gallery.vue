<template>
  <div class="gallery" v-if="db">
    <div class="container">
      <template v-for="(project, projectIndex) in db">
        <article v-bind:key="projectIndex" class="nano-box">
          <row :spacing="100" breakpoint="lg">
            <column size="100%-300">
              <img
                :src="project.image"
                :alt="`${project.client} ${project.date}`"
              />
            </column>
            <column size="300">
              <h1 v-html="project.client" />
              <h2 v-html="project.title" />
              <h3>
                <time v-html="project.date" />
              </h3>
              <ul class="skills">
                <template v-for="(tool, toolIndex) in project.tools">
                  <li v-bind:key="toolIndex">{{ tool }}</li>
                </template>
              </ul>
              <hr />
              <ul class="navigation">
                <template v-for="(link, linkIndex) in project.links">
                  <li v-bind:key="linkIndex">
                    <btn
                      tag="a"
                      size="md"
                      :color="
                        link.text == 'Github' ? 'charcoal' : 'royal-purple'
                      "
                      target="_blank"
                      :href="link.url"
                      :text="link.text"
                    />
                  </li>
                </template>
              </ul>
            </column>
          </row>
        </article>
      </template>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  components: {},
  props: {
    db: undefined,
  },
});
</script>