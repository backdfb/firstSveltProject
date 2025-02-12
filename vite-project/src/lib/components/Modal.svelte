<script>
    export let data; // 부모 컴포넌트에서 전달받은 data 속성, 영화 데이터(props 변수 선언)
    export let selectedMovie; // 부모 컴포넌트에서 전달받은 selectedMovie 속성, 선택한 영화 정보 저장 변수(props 변수 선언)
    export let closeModal; // 부모 컴포넌트에서 전달받은 isModal 속성, 모달 상태 변수(props 변수 선언)
</script>

<div class="modal">
    <div class="inner">
      <h3>{data[selectedMovie].title}</h3>
      <p>{@html data[selectedMovie].story}</p>
      <button 
        on:click={closeModal}
        class="btn-close"
      >닫기</button>
    </div>
</div>

<style>
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