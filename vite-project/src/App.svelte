<script>
  import logo1 from './assets/svelte.svg';
  let logo2 = '/vite.svg';

  let title = '제목';
  let openDate = 2024;
  let category = '액션';

  let textRed = 'color: red';

  const data = [
    { title: '물위의 하룻밤', openDate: 1998, category: '드라마' },
    { title: '파묘', openDate: 2024, category: '호러' },
    { title: '차인표', openDate: 2020, category: '코미디' },
  ] 
</script>

<main>

  <h1>영화정보</h1>
  <img src={logo1} alt="">
  <img src={logo2} alt="">
  {#each data as movie, i}
  <div>
    <h3 class="bg-yellow" style={textRed}>{movie.title}</h3>
    <h3>{movie.title}</h3>
    <p>개봉: {movie.openDate}</p>
    <p>장르: {movie.category}</p>
  </div>
  {/each}

</main>

<style>
  .bg-yellow {
    background-color: gold;
    padding: 10px;
  }
</style>
