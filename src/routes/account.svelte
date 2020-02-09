<style>
  .profile-img {
    border: 1px solid var(--cl-grey);
    border-radius: 50%;
    width: 180px;
  }

  .account header {
    display: grid;
    grid-row-gap: 4rem;
    grid-template-areas:
      "title button"
      "img details";
  }

  .account header h1 {
    grid-area: title;
  }

  .account header button {
    grid-area: button;
    justify-self: center;
  }

  .profile-img {
    grid-area: img;
  }
  .profile-details {
    grid-area: details;
  }

  .account-card {
    border: 1px solid var(--cl-grey);
  }
</style>

<article class="account px-2 mt-6">
  <header class="">
    <h1 class="my-2 ml-2">Your Profile</h1>
    <button
      class="my-4 btn btn-pri text-white py-2 px-6 mx-auto rounded text-lg
      sm:text-2xl shadow-xl hover:shadow-2xl trans-shadow ">
      Sign Out
    </button>

    <div class="profile-img p-8 mx-4">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512">
        <path
          d="M224 256c70.7 0 128-57.3 128-128S294.7 0 224 0 96 57.3 96 128s57.3
          128 128 128zm89.6 32h-16.7c-22.2 10.2-46.9 16-72.9
          16s-50.6-5.8-72.9-16h-16.7C60.2 288 0 348.2 0 422.4V464c0 26.5 21.5 48
          48 48h352c26.5 0 48-21.5 48-48v-41.6c0-74.2-60.2-134.4-134.4-134.4z" />
      </svg>

    </div>

    <div class="profile-details mx-4">
      <div class="name">
        First Name:
        <span>test</span>
      </div>
      <div class="name">
        Last Name:
        <span>test</span>
      </div>
      <div class="name">
        Email:
        <span>test</span>
      </div>

      <div>
        <button
          class="my-4 btn btn-sec py-2 px-6 rounded text-sm sm:text-md shadow-xl
          hover:shadow-2xl trans-shadow ">
          Sign Out
        </button>
      </div>
    </div>

  </header>

  <hr class="hr mx-4 my-12" />
  <section class="my-8 mx-auto">
    <h2 class="my-2 ml-2">Your Connected Accounts</h2>
    <div class="account-card p-4 rounded my-6">
      <h3>ATB Unlimited Cheqing Account (701)</h3>
      <button
        class="my-4 btn btn-sec py-2 px-6 rounded text-sm sm:text-md shadow-xl
        hover:shadow-2xl trans-shadow ">
        Disconnect
      </button>
    </div>
    <div class="account-card p-4 rounded my-6">
      <h3>ATB Springboard Savings Account (832)</h3>
      <button
        class="my-4 btn btn-sec py-2 px-6 rounded text-sm sm:text-md shadow-xl
        hover:shadow-2xl trans-shadow ">
        Disconnect
      </button>
    </div>
    <div>
      <button
        class="center-button my-4 btn btn-pri text-white py-2 px-6 mx-auto
        rounded text-lg sm:text-2xl shadow-xl hover:shadow-2xl trans-shadow ">
        Connect Another Account
      </button>
    </div>
  </section>
  <hr class="hr mx-4 my-12" />
  <section class="my-8 mx-auto">
    <h2 class="my-2 ml-2">Tax Receipts</h2>
    <div class="center-button">
      <button
        class="center-button my-4 btn btn-pri text-white py-2 px-6 mx-auto
        rounded text-lg sm:text-2xl shadow-xl hover:shadow-2xl trans-shadow ">
        View All Tax Receipts
      </button>
    </div>
  </section>
</article>
