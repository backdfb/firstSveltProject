<script>
  const data = [
    { 
      title: '쉬리', 
      openDate: 1998, 
      category: '액션', 
      who:'한석규, 최민식', 
      director:'강제규', 
      likeCount: 0, 
      imgUrl: 'images/쉬리.jpg',
      story: '토종 물고기 다큐멘터리',
    },
    { 
      title: '물위의 하룻밤', 
      openDate: 1998, 
      category: '드라마', 
      who:'이승희', 
      director:'강정수', 
      likeCount: 0, 
      imgUrl: 'images/물위의하룻밤.jpg',
      story: '수상도시를 건설하는 휴먼 드라마'
    },
    { 
      title: '파묘', 
      openDate: 2024, 
      category: '호러', 
      who:'최민식, 유해진, 김고은, 이도현', 
      director:'장재현', 
      likeCount: 0, 
      imgUrl: 'images/파묘.jpg',
      story: '전설의 무기를 찾아 모험을 떠나는 4명의 용사 이야기'
    },
    { 
      title: '하얼빈', 
      openDate: 2025, 
      category: '드라마', 
      who:'현빈', 
      director:'우민호', 
      likeCount: 0, 
      imgUrl: 'images/하얼빈.jpg',
      story: '차마 드립 칠 수 없는 역사적 이야기'
    },
  ] // 더미 데이터 목록

    let likeCount = 0; // 좋아요 수 저장 변수

    const handleLike = (i) => {
      data[i].likeCount += 1;
    }

    let isModal = false; // 모달 상태 저장 변수 추가가
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
        <!-- on:click은 클릭 이벤트 처리하는 svelte 문법으로, 좋아요 버튼 클릭 시 handleLike 함수 호출 -->
        좋아요 {data[i].likeCount}</button>
        <button on:click={() => {isModal = true}} class="btn btn-primary">상세보기</button>
    </div>
  </div> 
  {/each}
</main>

{#if isModal}
  <div class="modal">
    <div class="inner">
      <h3>자세히</h3>
      <button class="btn-close" on:click={() =>isModal = false}>닫기</button>
    </div>
  </div>
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

  .modal {
    background: rgba(0, 0, 0, 0.7);
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100vh;
    display: flex;  
    justify-content: center;
    align-items: center; 
  } 

  .modal .inner {
    background: #fff;
    width: 80%;
    padding: 20px;
    border-radius: 10px;
  }
</style>
