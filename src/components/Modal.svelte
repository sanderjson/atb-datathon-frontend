<script>
    
    import axios from 'axios';

    let accountIds = [];
    let accountIdInput = "";
    let accountBalances = {}

    function handleAddId() {
        accountIds.push(accountIdInput);
        accountIdInput = "";
    }

    
</script>


<div class="bg-white w-full h-full modal-container flex flex-col items-center sm:rounded-lg">
    <slot/>
   
</div>