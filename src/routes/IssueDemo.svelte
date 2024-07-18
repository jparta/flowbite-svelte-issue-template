
<script lang="ts">
    import { Fileupload } from 'flowbite-svelte';

    let pickedFiles: FileList | undefined;
	let filePickerValue: string | undefined;

    const handleFileChange = () => {
        setTimeout(() => {
            alert("Timeout triggered");
            filePickerValue = '';
        }, 1000)
    }
</script>

<Fileupload on:change={handleFileChange} bind:files={pickedFiles} bind:value={filePickerValue} />

<p class="m-10">filePickerValue: {filePickerValue}</p>

<button class="w-36 h-16 border-4 rounded-lg" on:click={() => document.getElementsByTagName('input')[0].value = ''}>Clear file input using DOM query</button>

