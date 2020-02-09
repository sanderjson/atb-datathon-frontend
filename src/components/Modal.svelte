<script>
    import "../../static/modal.css"
    import axios from 'axios';
    // import closeModal from './Dashboard.svelte'

    let accountIds = [];
    let accountIdInput = "";

    function handleAddId() {
        accountIds.push(accountIdInput);
        accountIdInput = "";
    }

    function handleConnectAccounts() {
        // call callback
    }
</script>


<div class="bg-white w-full h-full modal-container flex flex-col items-center sm:rounded-lg">
    <slot/>
    <h1 class="text-white text-xl font-bold">Welcome to Finanthropy </h1>
    <div class="px-12 text-center py-10">
    <p class='text-md text-white'> 
        Find important causes to  give to, tailored to where you are, and your own
        personal finances.
    </p>
    <p class="text-md mt-4 text-white">
        Let's get started! First connect your financial account.
    </p>
    </div>
    <h2 class="text-md text-white font-semibold">Account ID</h2>
    <input class="px-1 mt-2 modal-input rounded border-solid" bind:value={accountIdInput}/>
    <button on:click={handleAddId} class='modal-add-button my-4'>+ Add Another Account</button>
    <button class="text-white modal-button mt-8 sm:mt-8 py-1 px-3 mt-4 rounded-sm"> Connect Your Accounts </button>
</div>