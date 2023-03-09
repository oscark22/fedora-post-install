<script lang="ts">
    export let link: string;
</script>

<a class="hover:underline text-blue-500" href="{ link }"><slot /></a>
