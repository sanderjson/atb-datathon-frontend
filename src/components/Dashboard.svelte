<script>
  import ChartDemo from "./ChartDemo.svelte";
  import "../../static/modal.css";
  import Modal from "./Modal.svelte";
  import axios from "axios";

  let showDashboard = false;
  let accountIds = [];
  let accountIdInput = "";
  let accountBalances = {};
  let balanceOverTime = [];
  let donationEst;
  let posMultiplier;
  let donationAmnt;
  let initialDonationAmnt;

  function modifier(donationEst) {
    if (donationEst > 0) {
      posMultiplier = [0.04, 0, 0.05];
    } else if (donationEst < 0) {
      posMultiplier = [0.01, 0, 0.02];
    } else if (donationEst > -5 || donationEst < 5) {
      value = "$5.00";
    }
  }

  const handleThumbsDown = () => {
    donationAmnt = donationAmnt * posMultiplier[0];
  };

  const handleThumbsSide = () => {
    donationAmnt = initialDonationAmnt;
  };

  const handleThumbsUp = () => {
    donationAmnt = donationAmnt * posMultiplier[2];
  };

  function handleAddId() {
    accountIds.push(accountIdInput);
    accountIdInput = "";
  }
  function handleConnectAccounts() {
    if (accountIds.length === 0) {
      accountIds.push(accountIdInput);
    }
    return axios({
      method: "put",
      url: "https://18.220.251.195/api/app/user/info",
      data: { accounts: accountIds },
      headers: {
        "Access-Control-Allow-Origin": "*"
      }
    })
      .then(response => {
        let data = response.data;
        let accounts = data.accounts;
        console.log(accounts);
        donationEst = accounts.donation_est;
        console.log(donationEst);
        for (let i = 0; i < accountIds.length; i++) {
          let accountInfo = accounts[accountIds[i]];
          if (accountBalances[accountInfo.label]) {
            accountBalances[accountInfo.label] += accountInfo.balance.amount;
          } else {
            accountBalances[accountInfo.label] = accountInfo.balance.amount;
          }
        }
        modifier(donationEst);
        balanceOverTime = [
          accounts.transaction_history[0].balance,
          accounts.transaction_history[1].balance,
          accounts.transaction_history[2].balance,
          accounts.transaction_history[3].balance
        ];
        showDashboard = true;
      })
      .catch(error => {
        console.error(error);
      });
  }
  const handleCloseModal = () => {
    showDashboard = true;
  };
</script>

<style>
  .content-wrapper {
    display: flex;
    flex-direction: column;
  }
</style>

{#if !showDashboard}
  <div
    class="modal-background absolute left-0 right-0 bottom-0 top-0 flex
    justify-center items-center">
    <Modal>
      <div class="ml-auto p-4 float-right">
        <button on:click={handleCloseModal}>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24">
            <path
              d="M23.954 21.03l-9.184-9.095 9.092-9.174-2.832-2.807-9.09
              9.179-9.176-9.088-2.81 2.81 9.186 9.105-9.095 9.184 2.81 2.81
              9.112-9.192 9.18 9.1z" />
          </svg>
        </button>
        <h1 class="text-white text-xl font-bold">Welcome to Finanthropy</h1>
        <div class="px-12 text-center py-10">
          <p class="text-md text-white">
            Find important causes to give to, tailored to where you are, and
            your own personal finances.
          </p>
          <p class="text-md mt-4 text-white">
            Let's get started! First connect your financial account.
          </p>
        </div>
        <div class="content-wrapper">
          <h2 class="text-md text-white font-semibold">Account ID</h2>
          <input
            class="px-1 mt-2 modal-input rounded border-solid"
            bind:value={accountIdInput} />
          <button on:click={handleAddId} class="modal-add-button my-4">
            + Add Another Account
          </button>
        </div>
        <button
          on:click={handleConnectAccounts}
          class="text-white modal-button mt-8 sm:mt-8 py-1 px-3 mt-4 rounded-sm">
          Connect Your Accounts
        </button>
      </div>
    </Modal>
  </div>
{:else}
  <div>
    <div class="flex justify-center p-4 flex-col">
      <h2 class="text-center text-md font-bold">
        How you feeling financially this month?
      </h2>
      <div class="mt-2 flex border-solid border justify-around">
        <button class="p-2 status-buttons flex justify-center flex-col">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
            class="thumbs-icon m-auto thumbs-up feather feather-thumbs-down">
            <path
              d="M10 15v4a3 3 0 0 0 3 3l4-9V2H5.72a2 2 0 0 0-2 1.7l-1.38 9a2 2 0
              0 0 2 2.3zm7-13h2.67A2.31 2.31 0 0 1 22 4v7a2.31 2.31 0 0 1-2.33
              2H17" />
          </svg>
          <p class="text-sm">Feeling Great!</p>
        </button>
        <button
          class="p-2 status-buttons border-l border-r flex justify-center
          flex-col">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
            class="thumbs-icon m-auto thumbs-side feather feather-thumbs-down">
            <path
              d="M10 15v4a3 3 0 0 0 3 3l4-9V2H5.72a2 2 0 0 0-2 1.7l-1.38 9a2 2 0
              0 0 2 2.3zm7-13h2.67A2.31 2.31 0 0 1 22 4v7a2.31 2.31 0 0 1-2.33
              2H17" />
          </svg>
          <p class="text-sm">Doing OK</p>
        </button>
        <button class="p-2 status-buttons flex justify-center flex-col">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
            class="thumbs-icon m-auto feather feather-thumbs-down">
            <path
              d="M10 15v4a3 3 0 0 0 3 3l4-9V2H5.72a2 2 0 0 0-2 1.7l-1.38 9a2 2 0
              0 0 2 2.3zm7-13h2.67A2.31 2.31 0 0 1 22 4v7a2.31 2.31 0 0 1-2.33
              2H17" />
          </svg>
          <p class="text-sm">Funds are tight</p>
        </button>
      </div>
      <div class="border-b py-2 flex flex-col justify-center items-center">
        <p class="text-center font-semibold">
          Your Suggested Giving Power for February:
        </p>
        <input
          class="my-4 border border-solid text-center font-semibold"
          bind:value={donationAmnt} />
        <button class="py-1 px-2 m-auto modal-button text-white">
          Find Causes to Give to
        </button>
      </div>
    </div>
    <ChartDemo {accountBalances} {balanceOverTime} />
  </div>
{/if}
