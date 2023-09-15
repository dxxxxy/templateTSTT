<script lang="ts">
    import { invoke } from "@tauri-apps/api/tauri"
    
    let name = "";
    let greetMsg = ""
    
    async function greet(){
        //learn more about Tauri commands at https://tauri.app/v1/guides/features/command
        greetMsg = await invoke("greet", { name })
    }
</script>

<div class="flex flex-col items-center justify-center">
    <form class="flex gap-1" on:submit|preventDefault={greet}>
        <input class="px-4 py-2 font-semibold text-sm bg-gray-500 text-white rounded-l-lg shadow-sm" placeholder="dxxxxy was here" bind:value={name} />
        <button class="px-4 py-2 font-semibold text-sm bg-gray-500 text-white rounded-r-lg shadow-sm" type="submit">Greet</button>
    </form>

    <p class="text-white text-sm font-semibold">{greetMsg}</p>
</div>