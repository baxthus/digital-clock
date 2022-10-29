<script>
  import '$lib/app.css';

  let timeZoneToggler = false;

  $: timeFormatter = new Intl.DateTimeFormat('en-US', {
    hour: timeZoneToggler ? '2-digit' : 'numeric',
    minute: 'numeric',
    second: 'numeric',
    timeZoneName: timeZoneToggler ? 'short' : undefined,
    timeZone: undefined
  });

  let now = new Date();
  setInterval(() => {
    now = new Date();
  }, 100);

  $: time = timeFormatter.format(now);
</script>

<svelte:head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Digital Clock</title>
  <link rel="stylesheet" href="https://rsms.me/inter/inter.css">
  <link rel="shortcut icon" href="https://cdn.jsdelivr.net/gh/abysmal26/website/static/favicon.ico" type="image/x-icon">
</svelte:head>

<div class="flex justify-center items-center h-screen font-sans text-4xl sm:text-6xl md:text-7xl 2xl:text-9xl bg-neutral-900 text-neutral-50">
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <span class="cursor-pointer hover:underline select-none" on:click={() => {timeZoneToggler = !timeZoneToggler}}>{time}</span>
</div>

<style>
</style>