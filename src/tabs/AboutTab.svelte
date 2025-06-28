<script lang="ts">
  import coffeeImage from "../assets/coffee.png";
  import systemImage from "../assets/system.png";

  const workCards = $state([
    {
      image: coffeeImage,
      label: "Full Stack",
      desc: "Developing and maintaining web applications using some stacks.",
    },
    {
      image: systemImage,
      label: "Software Apps",
      desc: "Professional development of applications for different tasks",
    },
  ]);
</script>

<h1 class="font-bold text-3xl lg:text-4xl">About Me</h1>

<hr class="max-w-10 my-4 bg-primary-foreground h-1 rounded-full" />

<p>
  I’m professional Software Engineer with about two year of experience in App &
  System Development. Building innovative systems with architecture design for
  easy upgrades and bug fixes.
</p>

<br />

<ul class="[&>li]:my-2">
  <li>🤯 Developing for any OS since 2021.</li>
  <li>💻 Currently working on very cool projects.</li>
  <li>🌱 I’m currently learning cyber security.</li>
</ul>

<br />

<h2 class="font-semibold text-2xl lg:text-3xl">What i'm doing</h2>

<br />

<div class="flex flex-wrap gap-4 justify-start lg:justify-evenly">
  {#each workCards as workCard}
    <div
      class="lg:w-md md:w-10/12 w-full p-4 flex items-center gap-2 bg-secondary border rounded-xl"
    >
      <img src={workCard.image} class="size-12" alt="coffee" />
      <div>
        <h3 class="font-semibold">{workCard.label}</h3>
        <p>{workCard.desc}</p>
      </div>
    </div>
  {/each}
</div>

<br />

<h2 class="font-semibold text-2xl lg:text-3xl">Interests</h2>

<br />

<ul class="[&>li]:my-2">
  <li>
    I leaf through anything I can get my hands on, but I usually prefer
    journalism and documentation on circuitry and hardware systems.
  </li>
  <li>I also have a unique hobby, which is learning</li>
  <li>
    I'm not attracted to autobiographical topics and psychology because I think
    it's sophistry and a waste of time. In my spare time, I hang out on
    benchmarks for new developments and chat with coworkers.
  </li>
</ul>
