<script lang="ts">
  const projectsList = $state([
    {
      label: "Consider",
      projectLink: "https://github.com/jreydman/consider-desktop-app",
      logoLink:
        "https://github.com/jreydman/consider-desktop-app/raw/main/assets/consider-concept-1.jpeg",
    },
    {
      label: "NFCViewer",
      projectLink: "https://github.com/jreydman/nfcgate-mobile-app",
      logoLink:
        "https://f-droid.org/repo/de.tu_darmstadt.seemoo.nfcgate/en-US/icon_ju-kEhUQSmVVIIU6V1vUwU7hWm5KUkW5HY4B_CZVe6M=.png",
    },
    {
      label: "Teameights",

      projectLink: "https://github.com/nmashchenko/teameights",
      logoLink:
        "https://repository-images.githubusercontent.com/509949677/6a6e7bce-4bad-4c72-93d0-573bb5abb094",
    },
    {
      label: "FileBucket",
      projectLink: "https://github.com/jreydman/filebucket-frontend-app",
      logoLink:
        "https://github.com/user-attachments/assets/a93634fa-d8ac-4663-82a3-d71bb0995a54",
    },
  ]);
</script>

<h1 class="font-bold text-3xl lg:text-4xl">Portfolio</h1>

<hr class="max-w-10 my-4 bg-primary-foreground h-1 rounded-full" />

<div class="grid grid-flow-row grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
  {#each projectsList as project}
    <div class="border rounded-xl flex flex-col justify-evenly h-64">
      <img
        src={project.logoLink}
        alt="{project.label} logotype"
        class="size-3/5 mx-auto"
      />
      <h2 class="font-bold mx-2">{project.label}</h2>
    </div>
  {/each}
</div>
