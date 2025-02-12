<script>
  const data = [
    { title: '물위의 하룻밤', openDate: 1998, category: '드라마' },
    { title: '파묘', openDate: 2024, category: '호러' },
    { title: '차인표', openDate: 2020, category: '코미디' },
  ] 

    // 글자색 스타일 변수 let textRed = 'color: red'; 
    let likeCount = 0; // 좋아요 수 저장 변수
</script>

<main>

  <h1>개밥그릇의 인생영화 목록</h1>
  {#each data as movie, i} 
  <div>
    <h3 class="bg-yellow">{movie.title}</h3>
    <h3>{movie.title}</h3>
    <p>개봉: {movie.openDate}</p>
    <p>장르: {movie.category}</p>
    <button on:click={() => likeCount += 1}>좋아요 {likeCount}</button>
  </div> 
  {/each}

</main>

<style>
  .bg-yellow {
    background-color: gold;
    padding: 10px;
    color: #333;
  }
</style>
