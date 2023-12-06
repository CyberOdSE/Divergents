<script>
    import NavBar from "$lib/components/NavBar.svelte";
    import { initializeApp } from "firebase/app";

    import {
        createUserWithEmailAndPassword,
        getAuth,
        onAuthStateChanged,
        signInWithEmailAndPassword,
        signOut,
    } from "firebase/auth";
    import { firebaseConfig } from "../key.js";

    const app = initializeApp(firebaseConfig);

    export const logout = async () => {
        const auth = getAuth(app);
        signOut(auth);
        window.location.href = "/";
    };

</script>

<svelte:head>
    <title>Forum</title>
    <meta name="description" content="Forum" />
</svelte:head>

<header>
    <NavBar />
</header>

<body class="bg-[#EEF5DB]">
    <div class="mt-28">
        <div class="h-full">
            <h2 class="text-6xl text-center font-bold text-[#3730A3]">Forum</h2>
        </div>
        <button on:click={logout}>logout</button>
    </div>
</body>

<style>
</style>
