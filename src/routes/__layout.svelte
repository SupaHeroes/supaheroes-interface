<script>
  import Sbutton from "@comp/sbutton.svelte";
  import "../app.postcss";
  import { goto } from "$app/navigation";
  import { login, sUser, logout } from "@lib/moralis";
  import { onMount } from "svelte";

  let user;

  onMount(() => {
    // @ts-ignore
    sUser.set(Moralis.User.current());
    sUser.subscribe((value) => {
      user = value;
    });
  });

  let isExpanded = false;

  function toggle() {
    isExpanded = !isExpanded;
  }
</script>

<!-- Navbar -->
<div class="items-center bg-supadark text-white antialiased ">
  <div
    class="items-center pt-4 justify-between w-full px-5 overflow-y-auto whitespace-nowrap scroll-hidden pb-4 border-b border-supadark-light"
  >
    <!-- Tablet nav -->
    <div class=" flex-col mx-auto md:hidden flex overflow-hidden">
      <div class=" flex flex-row">
        <h1
          class=" flex-grow text-center p-2 text-2xl font-medium tracking-tighter text-transparent bg-clip-text bg-gradient-to-r from-supagreen-dark to-supagreen transition duration-500 ease-in-out transform cursor-pointer hover:text-green-500 lg:text-x lg:mr-8"
        >
          Supaheroes
        </h1>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          x="0px"
          y="0px"
          width="24"
          height="24"
          viewBox="0 0 172 172"
          class="h-5 w-5 text-white fill-current self-center"
          on:click={toggle}
          style=" fill:#000000;"
          ><g
            fill="none"
            fill-rule="nonzero"
            stroke="none"
            stroke-width="1"
            stroke-linecap="butt"
            stroke-linejoin="miter"
            stroke-miterlimit="10"
            stroke-dasharray=""
            stroke-dashoffset="0"
            font-family="none"
            font-weight="none"
            font-size="none"
            text-anchor="none"
            style="mix-blend-mode: normal"
            ><path d="M0,172v-172h172v172z" fill="none" /><g fill="#ecf0f1"
              ><path
                d="M14.33333,35.83333v14.33333h143.33333v-14.33333zM14.33333,78.83333v14.33333h143.33333v-14.33333zM14.33333,121.83333v14.33333h143.33333v-14.33333z"
              /></g
            ></g
          ></svg
        >
      </div>

      {#if isExpanded}
        <nav
          class="flex flex-wrap items-center justify-start text-base bg-supadark-dark w-full p-3"
        >
          <ul class="items-center inline-block list-none lg:inline-flex">
            <!-- <li>
              <a
                href="/"
                class="px-4 py-1 mr-1 text-base text-blueGray-500 transition duration-500 ease-in-out transform rounded-md focus:shadow-outline focus:outline-none focus:ring-2 ring-offset-current ring-offset-2 hover:text-supagreen "
                >How It Works</a
              >
            </li> -->
            <li>
              <a
                href="/discover"
                class="px-4 py-1 mr-1 text-base text-blueGray-500 transition duration-500 ease-in-out transform rounded-md focus:shadow-outline focus:outline-none focus:ring-2 ring-offset-current ring-offset-2 hover:text-supagreen "
                >Discover</a
              >
            </li>

            <li>
              <a
                href="/market"
                class="px-4 py-1 mr-1 text-base text-blueGray-500 transition duration-500 ease-in-out transform rounded-md focus:shadow-outline focus:outline-none focus:ring-2 ring-offset-current ring-offset-2 hover:text-supagreen "
                >Market</a
              >
            </li>
            <li>
              <a
                href="/protocol"
                class="px-4 py-1 mr-1 text-base text-blueGray-500 transition duration-500 ease-in-out transform rounded-md focus:shadow-outline focus:outline-none focus:ring-2 ring-offset-current ring-offset-2 hover:text-supagreen "
                >Protocol</a
              >
            </li>
            <li>
              <button
                on:click={login}
                class="px-4 py-1 mr-1 text-base text-blueGray-500 transition duration-500 ease-in-out transform rounded-md focus:shadow-outline focus:outline-none focus:ring-2 ring-offset-current ring-offset-2 hover:text-supagreen "
                >Connect Wallet</button
              >
            </li>
          </ul>
        </nav>
      {/if}
    </div>
    <!-- Desktop nav -->
    <div class=" flex-wrap mx-auto items-center flex-row md:flex hidden">
      <a href="/" class="pr-2 lg:pr-8 lg:px-6 focus:outline-none">
        <div class="inline-flex items-center">
          <h2
            class="block p-2 text-2xl font-medium tracking-tighter text-transparent bg-clip-text bg-gradient-to-r from-supagreen-dark to-supagreen transition duration-500 ease-in-out transform cursor-pointer hover:text-green-500 lg:text-x lg:mr-8"
          >
            Supaheroes
          </h2>
          <p>|</p>
        </div>
      </a>
      <nav class="flex flex-wrap items-center justify-start text-base ">
        <ul class="items-center  list-none inline-flex">
          <!-- <li>
            <a
              href="/"
              class="px-4 py-1 mr-1 text-base text-blueGray-500 transition duration-500 ease-in-out transform rounded-md focus:shadow-outline focus:outline-none focus:ring-2 ring-offset-current ring-offset-2 hover:text-supagreen "
              >How It Works</a
            >
          </li> -->
          <li>
            <a
              href="/discover"
              class="px-4 py-1 mr-1 text-base text-blueGray-500 transition duration-500 ease-in-out transform rounded-md focus:shadow-outline focus:outline-none focus:ring-2 ring-offset-current ring-offset-2 hover:text-supagreen "
              >Discover</a
            >
          </li>

          <li>
            <a
              href="/market"
              class="px-4 py-1 mr-1 text-base text-blueGray-500 transition duration-500 ease-in-out transform rounded-md focus:shadow-outline focus:outline-none focus:ring-2 ring-offset-current ring-offset-2 hover:text-supagreen "
              >Market</a
            >
          </li>
          <li>
            <a
              href="/protocol"
              class="px-4 py-1 mr-1 text-base text-blueGray-500 transition duration-500 ease-in-out transform rounded-md focus:shadow-outline focus:outline-none focus:ring-2 ring-offset-current ring-offset-2 hover:text-supagreen "
              >Protocol</a
            >
          </li>
        </ul>
      </nav>
      {#if user == null}
        <div class="flex">
         <div class="flex-grow"></div>
          <div><Sbutton on:click={login}>Connect Wallet</Sbutton></div>
        </div>
      {:else}
        <div class="flex-grow" />
        <button on:click={async () => goto("/profile")}
          ><img
            width="36px"
            height="36px"
            class="rounded-full bg-white object-contain"
            src={user["avatar"] != undefined
              ? user["avatar"]
              : "https://ui-avatars.com/api/?name=Supa+pol"}
            alt=""
          /></button
        >
      {/if}
    </div>
  </div>
</div>

<div class="min-h-screen bg-supadark">
  <slot />
</div>

<!-- Footer -->
<div class="items-center ">
  <footer
    class="text-gray-200 transition duration-500 ease-in-out transform bg-supadark border-t border-supadark-light"
  >
    <div class="flex flex-col flex-wrap justify-center p-5 md:flex-row">
      <nav
        class="flex flex-wrap items-center justify-center w-full mx-auto mb-6 text-base nprd"
      >
        <a
          href="/"
          class="px-4 py-1 mr-1 text-base text-blueGray-500 transition duration-500 ease-in-out transform rounded-md focus:shadow-outline focus:outline-none focus:ring-2 ring-offset-current ring-offset-2 hover:text-black "
          >Pricing</a
        >
        <a
          href="/"
          class="px-4 py-1 mr-1 text-base text-blueGray-500 transition duration-500 ease-in-out transform rounded-md focus:shadow-outline focus:outline-none focus:ring-2 ring-offset-current ring-offset-2 hover:text-black "
          >Contact</a
        >
        <a
          href="/"
          class="px-4 py-1 mr-1 text-base text-blueGray-500 transition duration-500 ease-in-out transform rounded-md focus:shadow-outline focus:outline-none focus:ring-2 ring-offset-current ring-offset-2 hover:text-black "
          >Services</a
        >
        <a
          href="/"
          class="px-4 py-1 mr-1 text-base text-blueGray-500 transition duration-500 ease-in-out transform rounded-md focus:shadow-outline focus:outline-none focus:ring-2 ring-offset-current ring-offset-2 hover:text-black "
          >Now</a
        >
      </nav>
      <span
        class="inline-flex justify-center w-full mx-auto mt-2 mr-2 sm:ml-auto sm:mt-0"
      >
        <a class="text-supagreen hover:text-black" href="/">
          <svg
            fill="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            class="w-5 h-5"
            viewBox="0 0 24 24"
          >
            <path
              d="M18 2h-3a5 5 0 00-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 011-1h3z"
            />
          </svg>
        </a>
        <a class="ml-3 text-supagreen hover:text-black" href="/">
          <svg
            fill="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            class="w-5 h-5"
            viewBox="0 0 24 24"
          >
            <path
              d="M23 3a10.9 10.9 0 01-3.14 1.53 4.48 4.48 0 00-7.86 3v1A10.66 10.66 0 013 4s-4 9 5 13a11.64 11.64 0 01-7 2c9 5 20 0 20-11.5a4.5 4.5 0 00-.08-.83A7.72 7.72 0 0023 3z"
            />
          </svg>
        </a>
        <a class="ml-3 text-supagreen hover:text-black" href="/">
          <svg
            fill="none"
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            class="w-5 h-5"
            viewBox="0 0 24 24"
          >
            <rect width="20" height="20" x="2" y="2" rx="5" ry="5" />
            <path
              d="M16 11.37A4 4 0 1112.63 8 4 4 0 0116 11.37zm1.5-4.87h.01"
            />
          </svg>
        </a>
        <a class="ml-3 text-supagreen hover:text-black" href="/">
          <svg
            fill="currentColor"
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="0"
            class="w-5 h-5"
            viewBox="0 0 24 24"
          >
            <path
              stroke="none"
              d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6zM2 9h4v12H2z"
            />
            <circle cx="4" cy="4" r="2" stroke="none" />
          </svg>
        </a>
      </span>
    </div>

    <p class="mx-auto pb-10 text-sm text-center text-gray-200  ">© 2021</p>
  </footer>
</div>

<style>
  button {
    outline: none;
  }
</style>
