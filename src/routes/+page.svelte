<!-- prettier-ignore -->
<script lang="ts">
    import "../app.css";

    let timeZoneToggle: boolean;

    $: timeFormatter = new Intl.DateTimeFormat('en-US', {
        hour: timeZoneToggle ? '2-digit' : 'numeric',
        minute: 'numeric',
        second: 'numeric',
        timeZoneName: timeZoneToggle ? 'short' : undefined,
        timeZone: undefined
    });

    let now = new Date()
    setInterval(() => {
        now = new Date();
    }, 100);

    $: time = timeFormatter.format(now);
</script>

<svelte:head>
  <title>Digital Clock</title>
  <link rel="preconnect" href="https://rsms.me/" />
  <link rel="stylesheet" href="https://rsms.me/inter/inter.css" />
  <link
    rel="shortcut icon"
    href="https://cdn.jsdelivr.net/gh/abysmal26/website/static/favicon.ico"
    type="image/x-icon"
  />
</svelte:head>

<div
  class="flex justify-center items-center h-screen font-sans text-4xl sm:text-6xl md:text-7xl 2xl:text-9xl bg-neutral-900 text-neutral-50"
>
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- prettier-ignore -->
  <span class="cursor-pointer hover:underline select-none" on:click={() => {timeZoneToggle = !timeZoneToggle}}>{time}</span>
</div>
