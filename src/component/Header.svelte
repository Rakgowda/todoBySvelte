<script>
let src = 'images/time_managment.svg';

</script>

<style>
.header{
    
}
.headertext{
    text-transform: uppercase;
    /* text-decoration: black; */
    font-weight: bold;
    font-size: 5rem;
    overflow: hidden;
    text-decoration: underline;
}
.headerimage{
    width: 5rem;
    height:7rem;
    /* transform: rotate(20deg); */
}
@keyframes rotating {
  from {
    -ms-transform: rotate(0deg);
    -moz-transform: rotate(0deg);
    -webkit-transform: rotate(0deg);
    -o-transform: rotate(0deg);
    transform: rotate(0deg);
    
  }
  to {
    -ms-transform: rotate(360deg);
    -moz-transform: rotate(360deg);
    -webkit-transform: rotate(360deg);
    -o-transform: rotate(360deg);
    transform: rotate(360deg);
 
  }
}
.rotating {
  -webkit-animation: rotating 5s linear infinite;
  -moz-animation: rotating 5s linear infinite;
  -ms-animation: rotating 5s linear infinite;
  -o-animation: rotating 5s linear infinite;
  animation: rotating 5s linear infinite;
}
</style>

<div class="header">
    <div class="d-flex justify-content-center">
        <h1 class="text-center headertext">Task Managment</h1>
        <img {src} class="headerimage rotating" />
    </div>
</div>