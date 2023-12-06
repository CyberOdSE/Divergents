<script>
    import { initializeApp } from "firebase/app";
    import { getAuth, sendPasswordResetEmail } from "firebase/auth";
    import { firebaseConfig } from "../key.js";

    let email = "";

    // Initialize Firebase
    const app = initializeApp(firebaseConfig);

    const resetPassword = () => {
        const auth = getAuth(app);
        sendPasswordResetEmail(auth, email)
            .then(() => {
                setTimeout(() => {
                    window.location.href = "/";
                }, 2000);
                // Password reset email sent!
                // ..
            })
            .catch((error) => {
                const errorCode = error.code;
                const errorMessage = error.message;
                console.log(errorCode, errorMessage);
            });
    };
</script>

<svelte:head>
    <title>Forgot your password?</title>
    <meta name="description" content="Forgot your password" />
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
                Forgot your password?
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
                <br />
                <p>
                    Enter your email address and we will send you a link to
                    reset your password.
                </p>
                <br />
                <input
                    type="email"
                    id="email"
                    name="email"
                    class="mt-4 border rounded-md border-[#3730A3] w-full py-2 px-3"
                    placeholder="Email"
                    bind:value={email}
                />
            </div>
            <div class="flex items-center justify-between">
                <button
                    class="mt-8 px-4 py-2 bg-[#3730A3] font-bold w-full text-white rounded-md hover:bg-[#DFC2F2] hover:text-[#3730A3]"
                    type="button"
                    on:click={resetPassword}
                >
                    Reset Password
                </button>
            </div>
        </form>
    </div></body
>
