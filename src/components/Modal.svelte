<script>
    import "../../static/modal.css"
    let accountIds = "";
</script>


<div class="bg-white w-full h-full modal-container flex flex-col items-center sm:rounded-lg">
    <div class='ml-auto p-4 float-right'> 
        <button> X </button>
    </div>
    <h1 class="p-4">Enter your account ids {accountIds} </h1>
    <input class="btn" value={accountIds}/>
    <div class="pt-6 w-full flex justify-around">
        <button class="btn">Add Account ID </button>
        <button>Get Dashboards</button>
    </div>
</div>