<script>
    import NavBar from "$lib/components/NavBar.svelte";
</script>

<svelte:head>
    <title>Chat & Activities</title>
    <meta name="description" content="Forum" />
</svelte:head>

<header>
    <NavBar />
</header>

<body class="bg-[#EEF5DB]">
    <div class="grid grid-cols-2 mt-28">
        <div class="flex h-full border-r-8">
            <h2 class="text-6xl text-left ml-6 font-bold text-[#3730A3]">
                Chat
            </h2>
        </div>

        <div class="flex h-full">
            <h2 class="text-6xl text-right ml-6 font-bold text-[#3730A3]">
                Activities
            </h2>
        </div>
    </div>
</body>

<style>
</style>
