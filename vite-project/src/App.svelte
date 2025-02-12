<script>
  const data = [
    { title: '쉬리', openDate: 1998, category: '액션', who:'한석규, 최민식', director:'강제규', likeCount: 0, imgUrl: 'images/쉬리.jpg'},
    { title: '물위의 하룻밤', openDate: 1998, category: '드라마', who:'이승희', director:'강정수', likeCount: 0, imgUrl: 'images/물위의하룻밤.jpg'},
    { title: '파묘', openDate: 2024, category: '호러', who:'최민식, 유해진, 김고은, 이도현', director:'장재현', likeCount: 0, imgUrl: 'images/파묘.jpg'},
    { title: '하얼빈', openDate: 2025, category: '드라마', who:'현빈', director:'우민호', likeCount: 0, imgUrl: 'images/하얼빈.jpg'},
  ] // 더미 데이터 목록

    let likeCount = 0; // 좋아요 수 저장 변수

    const handleLike = (i) => {
      data[i].likeCount += 1;
    }
</script>

<main>

  <h1>개밥그릇의 인생영화 목록</h1>
  {#each data as movie, i} 
  <!-- 반복문, data 배열을 순회하며 movie 객체와 인덱스 i를 반환 -->
  <div class="item">
    <figure>
      <img src={movie.imgUrl} alt={movie.title} />
    </figure>
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
