<script>
import ChartDemo from "./ChartDemo.svelte"
import Modal from "./Modal.svelte"
import axios from 'axios';

let showDashboard = false
// export let $dashboardInfo;

// export function sendRequest(accountIds) {
//   axios({
//     method: 'put',
//     url: 'http://18.220.251.195/api/app/user/info',
//     data: accountIds
//   }).then((response) => {
//       showDashboard = true
//       dashboardInfo = response.data;
//   }).catch((error) => {
//       console.error(error);
//   });

  const handleCloseModal = () => {
    showDashboard = true;
  }

</script>

{#if !showDashboard}
  <div  class='modal-background absolute left-0 right-0 bottom-0 top-0 flex justify-center items-center'>
      <Modal>
        <div class='ml-auto p-4 float-right'> 
          <button on:click = {handleCloseModal}> 
              <svg xmlns="http://www.w3.org/2000/svg" 
                  width="24" height="24" viewBox="0 0 24 24">
                  <path d="M23.954 21.03l-9.184-9.095 9.092-9.174-2.832-2.807-9.09 9.179-9.176-9.088-2.81 
                  2.81 9.186 9.105-9.095 9.184 2.81 2.81 9.112-9.192 9.18 9.1z"/>
              </svg> 
          </button>
      </div>
    </Modal>
  </div>
{:else}
  <div>
    <div class='flex justify-center p-4 flex-col'>
      <h2 class='text-center text-md font-bold'>How you feeling financially this month?</h2>
      <div class='mt-2 flex border-solid border justify-around'>
        <button class='p-2 status-buttons flex justify-center flex-col'>
          <svg xmlns="http://www.w3.org/2000/svg" 
            width="24" height="24" viewBox="0 0 24 24" fill="none" 
            stroke="currentColor" stroke-width="2" stroke-linecap="round" 
            stroke-linejoin="round" class="thumbs-icon m-auto thumbs-up feather feather-thumbs-down">
            <path d="M10 15v4a3 3 0 0 0 3 3l4-9V2H5.72a2 2 0 0 0-2 1.7l-1.38 9a2 2 0 0 0 2 
            2.3zm7-13h2.67A2.31 2.31 0 0 1 22 4v7a2.31 2.31 0 0 1-2.33 2H17">
            </path>
          </svg>
         <p class='text-sm'>Feeling Great!</p>
        </button>
        <button class='p-2 status-buttons border-l border-r flex justify-center flex-col'>
          <svg xmlns="http://www.w3.org/2000/svg" 
            width="24" height="24" viewBox="0 0 24 24" fill="none" 
            stroke="currentColor" stroke-width="2" stroke-linecap="round" 
            stroke-linejoin="round" class="thumbs-icon m-auto thumbs-side feather feather-thumbs-down">
            <path d="M10 15v4a3 3 0 0 0 3 3l4-9V2H5.72a2 2 0 0 0-2 1.7l-1.38 9a2 2 0 0 0 2 
            2.3zm7-13h2.67A2.31 2.31 0 0 1 22 4v7a2.31 2.31 0 0 1-2.33 2H17">
            </path>
          </svg>
         <p class='text-sm'>Doing OK</p>
        </button>
        <button class='p-2 status-buttons flex justify-center flex-col'>
          <svg xmlns="http://www.w3.org/2000/svg" 
            width="24" height="24" viewBox="0 0 24 24" fill="none" 
            stroke="currentColor" stroke-width="2" stroke-linecap="round" 
            stroke-linejoin="round" class="thumbs-icon m-auto feather feather-thumbs-down">
            <path d="M10 15v4a3 3 0 0 0 3 3l4-9V2H5.72a2 2 0 0 0-2 1.7l-1.38 9a2 2 0 0 0 2 
            2.3zm7-13h2.67A2.31 2.31 0 0 1 22 4v7a2.31 2.31 0 0 1-2.33 2H17">
            </path>
          </svg>
         <p class='text-sm'>Funds are tight</p>
        </button>
      </div>
      <div class='border-b py-2 flex flex-col justify-center items-center'>
        <p class='text-center font-semibold'> Your Suggested Giving Power for February:</p>
        <input class='my-4 border border-solid text-center font-semibold' value={'$50.00'}/>
        <button class='py-1 px-2 m-auto modal-button text-white'> Find Causes to Give to</button>
      </div>
    </div>
    <ChartDemo />
  </div>
{/if}
