<script>
  import {data} from './lib/movies'; // data 배열은 영화 정보를 담고 있음
  import Navbar from './lib/components/Navbar.svelte';
  import Modal from './lib/components/Modal.svelte'; // Modal 컴포넌트 추가
  import Movies from './lib/components/Movies.svelte'; // 영화 데이터 가져오기

  let likeCount = 0; // 좋아요 수 저장 변수
  const handleLike = (i) => {
    data[i].likeCount += 1;
  }

  let isModal = false; // 모달 상태 변수 추가
  let selectedMovie = 0; // 선택한 영화 정보 저장 변수 추가

  const closeModal = () => {
    isModal = false;
  }

  const handleMovieNumber = (i) => {
    selectedMovie = i;
  } 

  let isEvent = true; // 이벤트 창 표시 여부
</script>

<div class={isEvent ? 'event show' : 'event'}>
  <p>DFBFLEX 운명의 드라마, 경기크리처</p>
  <button>X</button>
</div>
<Movies {data} bind:isModal {handleMovieNumber} {handleLike} />

{#if isModal}
  <Modal 
    {data} 
    {selectedMovie}
    {closeModal}
  />
  <!-- Modal 컴포넌트 추가 -->
{/if}

<style>
  .event {
    width: 100%;
    background: #666;
    padding: 5px 1em;
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: #fff;
    text-align: center;
    margin-bottom: 1em;
    padding: 10px 20px;

    /* 창이 보이지 않게 */
    max-height: 0;
    opacity: 0;
    overflow: hidden;
    transition: all 0.4s;
  }

  /* 기본: 창이 보이게 */
  .show {
    opacity: 1;
    max-height: 100px;
  }

  .event button {
    padding: 2px;
  }

  .event p, .event button {
    margin: 0;
  }
  .event p {
    width: 100%;
  }
</style>
