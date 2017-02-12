vue-laravel-paginator
=============

A simple Vue Paginator component to be used in Laravel application.

## Installation
---------------
###npm
``` sh
npm install --save vue-laravel-paginator
```

##Example

```javascript
<template id="item-list">
  <div class="item-list">
      <paginator :maxPage="this.maxPage" @loadPage="loadPage"></paginator>
      <ul id="itemList">
        <li v-for="item in items">
            {{ item }}
        </li>
      </ul>
  </div>
</template>

<script>
  export default{
    data:function(){
      return {
        items:[],
        currentPage:1,
        maxPage:0
      }
    },
    created: function(){
      axios.get('/items?page='+ 1).then(response => {
        this.items = response.data.data;
        this.maxPage = response.data.last_page;
      });
    },
    methods: {
      loadPage:function(page_number){
            axios.get('/items?page='+page_number).then(response => {
              this.items = response.data.data;
            });
          }
    }
  }
</script>
```
