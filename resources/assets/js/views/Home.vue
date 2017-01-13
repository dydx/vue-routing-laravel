<template>
  <div class="container">
    <div class="columns">
      <div class="column">
        <div class="box" v-for="status in statuses">
          <article class="media">
            <div class="media-left">
              <figure class="image is-64x64">
                <img src="http://bulma.io/images/placeholders/128x128.png" alt="Image">
              </figure>
            </div>
            <div class="media-content">
              <div class="content">
                <p>
                <strong>{{ status.user.name }}</strong> <small>said..</small> <small> {{ postedOn(status) }}</small>
                <br>
                {{ status.body }}
                </p>
              </div>
              <nav class="level">
                <div class="level-left">
                  <a class="level-item">
                    <span class="icon is-small"><i class="fa fa-reply"></i></span>
                  </a>
                  <a class="level-item">
                    <span class="icon is-small"><i class="fa fa-retweet"></i></span>
                  </a>
                  <a class="level-item">
                    <span class="icon is-small"><i class="fa fa-heart"></i></span>
                  </a>
                </div>
              </nav>
            </div>
          </article>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import moment from 'moment';
import Status from '../models/Status';

export default {
  name: 'home',

  data () {
    return {
      statuses: []
    }
  },

  created () {
    Status.all(statuses => this.statuses = statuses);
  },

  methods: {
    postedOn (status) {
      return moment(status.created_at).fromNow();
    }
  }
}
</script>
