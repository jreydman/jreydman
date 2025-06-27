<script lang="ts">
  import coffeeImage from "../assets/coffee.png";
  import phoneImage from "../assets/phone.png";

  const workCards = $state([
    {
      image: coffeeImage,
      label: "Full Stack",
      desc: "Developing and maintaining web applications using MERN stack.",
    },
    {
      image: phoneImage,
      label: "Mobile Apps",
      desc: "Professional development of applications for iOS and Android.",
    },
  ]);
</script>

<h1 class="font-bold text-3xl lg:text-4xl">About Me</h1>

<hr class="max-w-10 my-4 bg-primary-foreground h-1 rounded-full" />

<p>
  I’m professional Mobile Software Engineer with about two year of experience in
  Mobile App Development. Building innovative Android and iOS apps with
  architecture design for easy upgrades and bug fixes.
</p>

<br />

<ul>
  <li>🤯 Developing for Android since 2021.</li>
  <li>💻 Currently working on very cool projects.</li>
  <li>🌱 I’m currently learning cyber security.</li>
</ul>

<br />

<h2 class="font-semibold text-2xl lg:text-3xl">What i'm doing</h2>

<br />

<div class="flex flex-wrap gap-4 justify-evenly">
  {#each workCards as workCard}
    <div
      class="lg:w-md w-10/12 p-4 flex items-center gap-2 bg-accent border rounded-xl"
    >
      <img src={workCard.image} class="size-12" alt="coffee" />
      <div>
        <h3>{workCard.label}</h3>
        <p>{workCard.desc}</p>
      </div>
    </div>
  {/each}
</div>
