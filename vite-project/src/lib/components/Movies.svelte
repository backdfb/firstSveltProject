<script>
    export let data=[];
    export let isModal = false;
    export let handleLike;
    export let handleMovieNumber; 
</script>

<main class="container">
    <h1>개밥그릇의 인생영화 목록</h1>
    {#each data as movie, i} 
    <!-- 반복문, data 배열을 순회하며 movie 객체와 인덱스 i를 반환 -->
    <div class="item">
      <figure>
        <img src={movie.imgUrl} alt={movie.title} />
      </figure>
      <div class="info">
        <h3 class="bg-yellow">{movie.title}</h3>
        <h3>{movie.title}</h3>
        <p>개봉: {movie.openDate}</p>
        <p>장르: {movie.category}</p>
        <p>주연: {movie.who}</p>
        <p>감독: {movie.director}</p>
        <button 
          on:click={() => {handleLike(i)}}>
          좋아요 {data[i].likeCount}</button>
          <!-- on:click은 클릭 이벤트 처리하는 svelte 문법으로, 좋아요 버튼 클릭 시 handleLike 함수 호출 -->
          <button on:click={() => {
            isModal = true;
            handleMovieNumber(i);
          }} class="btn btn-primary">상세보기</button>
      </div>
    </div> 
    {/each}
  </main>

  <style>
    .bg-yellow {
    background-color: gold;
    padding: 10px;
    color: #333;
    }

    .item {
    display: flex;
    width: 100%;
    margin-bottom: 20px;
    padding: 1rem;
    border: 1px solid #ccc;
    }

    .item figure {
    width: 30%;
    margin-right: 1rem;
    }

    .item img {
    width: 100%;
    }

    .item .info {
    width: 100%;
    }
  </style>