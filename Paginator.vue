<template id="paginator">
    <div class="paginator">
      <ul class="pagination">
        <li :class="{ 'disabled': currentPage == 1 }" ><a @click="loadPrevPage">Prev</a></li>
        <li v-for="n in parseInt(this.maxPage)" :class="{ 'active': n == currentPage }"><a @click="loadPage(n)">{{ n }}</a></li>
        <li  :class="{ 'disabled': currentPage == maxPage }" ><a @click="loadNextPage">Next</a></li>
      </ul>
    </div>
</template>

<script>
export default{
   props:['maxPage'],
   data:function(){
     return { currentPage:1 }
   },
   methods:{
     loadPage(page_number){
       this.currentPage = page_number;
       this.$emit('loadPage',page_number);
     },
     loadNextPage(){
       this.currentPage++;
       if(this.currentPage >= this.maxPage )this.currentPage=this.maxPage;
       this.loadPage(this.currentPage);
     },
     loadPrevPage(){
       this.currentPage--;

       if(this.currentPage <= 1 )this.currentPage=1;
       this.loadPage(this.currentPage)
     }

   }
}
</script>
