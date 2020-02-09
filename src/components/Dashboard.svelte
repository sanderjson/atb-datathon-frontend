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
    <ChartDemo />
  </div>
{/if}
