<script lang="ts">
    import { getAuth, signOut } from "firebase/auth";
    import { user } from "$lib/stores/auth.store";

    export function logout() {
        const auth = getAuth();
        signOut(auth);
    }
</script>

<svelte:head>
	<title>Profile</title>
	<meta name="description" content="Profile settings of this app" />
</svelte:head>

<div class="text-column">
    {#if $user}
    <h1>
        <img width="32" src="{$user.photoURL}" alt="{$user.email}"/>
        {$user.displayName}
    </h1>
    <button class="clear" on:click={logout}>
        <i class="bx bx-log-out"></i>
        <span>Logout</span>
    </button>
    {/if}
</div>