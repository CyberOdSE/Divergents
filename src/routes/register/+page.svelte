<script>
    import { initializeApp } from "firebase/app";
    import {
        createUserWithEmailAndPassword,
        getAuth,
    } from "firebase/auth";
    import { firebaseConfig } from "../key.js";

    let email = "";
    let password = "";

    // Initialize Firebase
    const app = initializeApp(firebaseConfig);

    const register = () => {
        const auth = getAuth(app);
        createUserWithEmailAndPassword(auth, email, password)
            .then((userCredential) => {
                const user = userCredential.user;
                window.location.href = "/";
            })
            .catch((error) => {
                const errorCode = error.code;
                const errorMessage = error.message;
                console.log(errorCode, errorMessage);
            });
    };
</script>

<svelte:head>
    <title>Register</title>
    <meta name="description" content="Register" />
</svelte:head>

<header>
    <nav class="bg-[#3730A3] p-4 fixed top-0 w-full z-10">
        <div class="container mx-auto flex justify-between items-center">
            <a href="/home" class="text-[#DFC2F2] text-6xl font-bold">Anxietr</a
            >
        </div>
    </nav>
</header>

<body class="bg-[#EEF5DB]">
    <div class="mt-28">
        <div class="h-full">
            <h2 class="text-6xl text-center font-bold text-[#3730A3]">
                Register
            </h2>
        </div>
    </div>
    <div class="flex items-center justify-center">
        <form
            class="mt-12 bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4 w-1/4"
        >
            <div class="mb-4">
                <label for="email" class="text-2xl text-[#3730A3] font-bold"
                    >Email</label
                >
                <br />
                <input
                    class="mt-4 border rounded-md border-[#3730A3] w-full py-2 px-3"
                    type="email"
                    id="email"
                    placeholder="Email"
                    bind:value={email}
                />
            </div>
            <div class="mt-8">
                <label for="password" class="text-2xl text-[#3730A3] font-bold"
                    >Password</label
                >
                <br />
                <input
                    class="mt-4 border rounded-md border-[#3730A3] w-full py-2 px-3"
                    type="password"
                    id="password"
                    placeholder="New Password"
                    bind:value={password}
                />
            </div>
            <div class="text-center">
                <button
                    on:click={register}
                    class="mt-8 px-4 font-bold py-2 bg-[#3730A3] w-full text-white rounded-md hover:bg-[#DFC2F2] hover:text-[#3730A3]"
                    >Register</button
                >
            </div>
        </form>
    </div>
</body>

<style>
</style>
