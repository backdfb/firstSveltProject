<script>
  import {data} from './lib/movies'; // data 배열은 영화 정보를 담고 있음
  import Navbar from './lib/components/Navbar.svelte';
  import Modal from './lib/components/Modal.svelte'; // Modal 컴포넌트 추가
  let likeCount = 0; // 좋아요 수 저장 변수
  const handleLike = (i) => {
    data[i].likeCount += 1;
  }

  let isModal = false; // 모달 상태 변수 추가
  let selectedMovie = 0; // 선택한 영화 정보 저장 변수 추가

  const closeModal = () => {
    isModal = false;
  }
</script>

<Navbar />
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
        <!-- on:click은 클릭 이벤트 처리하는 svelte 문법으로, 좋아요 버튼 클릭 시 handleLike 함수 호출 -->
        좋아요 {data[i].likeCount}</button>
        <button on:click={() => {
          isModal = true;
          selectedMovie =i;
        }} class="btn btn-primary">상세보기</button>
    </div>
  </div> 
  {/each}
</main>

{#if isModal}
  <Modal 
    {data} 
    {selectedMovie}
    {closeModal}
  />
  <!-- Modal 컴포넌트 추가 -->
{/if}

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
