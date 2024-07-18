
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

<p class="m-4 mb-8 text-wrap">
Choose a file.
After the choice, a timeout will be triggered, but the accompanying change of the file picker value to an empty string won't have an effect on the string shown in the file picker.
Press the button to clear the file input. This works, because it is directly setting the value of the input, and not through Svelte bindings.
The question is why does it not work through the bindings. Is two layers of bindings too much?
</p>

<Fileupload on:change={handleFileChange} bind:files={pickedFiles} bind:value={filePickerValue} />

<p class="m-10">filePickerValue: {filePickerValue}</p>

<button class="w-36 h-16 border-4 rounded-lg" on:click={() => document.getElementsByTagName('input')[0].value = ''}>Clear file input using DOM query</button>

