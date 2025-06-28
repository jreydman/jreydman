<script lang="ts">
  import Timeline from "$lib/components/Timeline.svelte";
  import { Book } from "@lucide/svelte";
  import { Progress } from "$lib/components/ui/progress/index.js";

  const workList = $state([
    {
      label: "DistributedLab, Kharkiv",
      date: "2022",
      desc: "Frontend web developing (VueJS, SCSS, Blockchain-state)",
    },
    {
      label: "TeameightsTM",
      date: "2023-2024",
      desc: "Fullstack developing / bit DevOps (Next/Nest, K8S)",
    },
    {
      label: "OOO Rost, Kharkiv",
      date: "2024",
      desc: "Software developing",
    },
    {
      label: "Freelance",
      date: "2025",
      desc: "Software Engineering (Consider app on Java)",
    },
  ]);

  const educationList = $state([
    {
      label: "Kharkiv School №59",
      date: "2008 - 2020",
    },
    {
      label: "NURE University | Behaviour",
      date: "2020 - 2024",
      desc: "Computer Engineering",
    },
    {
      label: "NURE University | Master",
      date: "2024 - present",
      desc: "Computer Engineering",
    },
  ]);

  const expirienceList = $state([
    {
      label: "Blockchain client",
      date: "2022-2023",
      desc: "While working, I was learning about blockchain, making a web client to interact with transactions, while learning about planned roedmap. <br/> | VueJS, SCSS, Apollo, Chainstack |",
    },
    {
      label: "Fullstack",
      date: "2024",
      desc: "Worked at Teameights, dealing with security and deployment - AAA concept, sockets, archestration",
    },
    {
      label: "Freelance",
      date: "2024 - present",
      desc: "FileBucket, NFCViewer, Gate, Gazepass",
    },
  ]);

  const skillsList = $state([
    {
      label: "Typescript",
      progress: 85,
    },
    {
      label: "Java/FX",
      progress: 60,
    },
    {
      label: "Flutter/Dart",
      progress: 70,
    },
    {
      label: "Rust",
      progress: 70,
    },
    {
      label: "Virtualization | Lima/Cloud",
      progress: 80,
    },
    {
      label: "Unix",
      progress: 80,
    },
    {
      label: "Ukrainian",
      progress: 100,
    },
    {
      label: "English",
      progress: 65,
    },
  ]);
</script>

<h1 class="font-bold text-3xl lg:text-4xl">Resume</h1>

<hr class="max-w-10 my-4 bg-primary-foreground h-1 rounded-full" />

<Timeline title="Work" TitleIcon={Book} items={workList} />

<br class="my-4" />

<Timeline title="Education" TitleIcon={Book} items={educationList} />

<br class="my-4" />

<Timeline title="Expirience" TitleIcon={Book} items={expirienceList} />

<br class="my-2" />

<h2 class="font-semibold text-2xl lg:text-3xl my-4">My Skills</h2>

<div class="p-4 border rounded-xl">
  <h3>
    <strong>Stack maintenance:</strong>
    <a href="https://stackshare.io/jreydman/maintenance"
      >https://stackshare.io/jreydman/maintenance</a
    >
  </h3>

  {#each skillsList as skill}
    <div>
      <div class="flex items-center gap-2 mt-4 mb-2">
        <h3 class="text-1xl font-semibold">{skill.label}</h3>
        <p class="text-sm">{skill.progress}%</p>
      </div>
      <Progress value={skill.progress} />
    </div>
  {/each}
</div>
