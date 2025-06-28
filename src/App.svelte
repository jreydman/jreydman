<script lang="ts">
  import avatarImage from "./assets/rounded_avatar.png";
  import * as Tabs from "$lib/components/ui/tabs/index.js";
  import * as Avatar from "$lib/components/ui/avatar/index.js";
  import * as Accordion from "$lib/components/ui/accordion/index.js";
  import { Badge } from "$lib/components/ui/badge/index.js";
  import {
    Mail,
    Phone,
    Calendar,
    MapPin,
    MessageCircle,
    Github,
    Linkedin,
  } from "@lucide/svelte";
  import Button from "$lib/components/ui/button/button.svelte";
  import AboutTab from "./tabs/AboutTab.svelte";
  import ResumeTab from "./tabs/ResumeTab.svelte";
  import PortfolioTab from "./tabs/PortfolioTab.svelte";

  const contacts = $state([
    { icon: Mail, label: "EMAIL", value: "pikj.reyderman@gmail.com" },
    { icon: Phone, label: "PHONE", value: "+380955804468" },
    { icon: Calendar, label: "BIRTHDAY", value: "August 26" },
    { icon: MapPin, label: "LOCATION", value: "Kyiv" },
  ]);

  const contactSocials = $state([
    { icon: MessageCircle, href: "" },
    { icon: Github, href: "" },
    { icon: Linkedin, href: "" },
  ]);

  const tabs = $state([
    { label: "About", value: "about", page: AboutTab },
    { label: "Resume", value: "resume", page: ResumeTab },
    { label: "Portfolio", value: "portfolio", page: PortfolioTab },
    { label: "Blog", value: "blog" },
  ]);

  let isXlScreen = $state(false);
  let accordionValue = $state<"contacts-cord" | undefined>();

  $effect(() => {
    const checkScreenSize = () => {
      isXlScreen = window.matchMedia("(min-width: 1280px)").matches;
      accordionValue = isXlScreen ? "contacts-cord" : undefined;
    };

    checkScreenSize();
    window.addEventListener("resize", checkScreenSize);

    return () => window.removeEventListener("resize", checkScreenSize);
  });
</script>

<main class="container mx-auto px-2 pt-4 flex xl:flex-row flex-col gap-4">
  <div
    class="h-fit bg-secondary rounded-3xl border xl:max-w-64 max-w-full xl:sticky xl:top-4"
  >
    <Accordion.Root type="single" value={accordionValue}>
      <Accordion.Item value="contacts-cord">
        <div class="flex gap-4 ml-4 xl:ml-0">
          <!-- --------------- -->
          <div
            class="w-full flex flex-row xl:flex-col items-center my-0 xl:my-2"
          >
            <Avatar.Root class="mx-auto size-20 my-2">
              <Avatar.Image src={avatarImage} alt="avatar" />
            </Avatar.Root>
            <!-- --------------- -->
            <div class="my-auto flex-1 basis-1">
              <div class="max-w-min">
                <h1 class="text-xl text-center">JReydman</h1>
                <Badge variant="outline">Software developer</Badge>
              </div>
            </div>
          </div>
          <!-- --------------- -->
          <div class="relative">
            <Accordion.Trigger
              class="xl:hidden absolute p-2 bg-accent-foreground rounded-none rounded-bl-xl rounded-tr-3xl right-0 top-0"
            >
              <span class="text-primary-foreground text-nowrap hidden md:block"
                >Show contacts</span
              >
            </Accordion.Trigger>
          </div>
          <!-- --------------- -->
        </div>
        <Accordion.Content class="py-0">
          <div class="mx-4">
            <hr />
            <div class="flex flex-col">
              {#each contacts as contact}
                <div class="flex items-center gap-4 my-2">
                  <div class="border p-3 rounded-xl">
                    <contact.icon class="size-4" />
                  </div>
                  <div class="max-w-full overflow-hidden">
                    <p class="text-[8pt]">
                      {contact.label}
                    </p>
                    {#if contact.label == "PHONE"}
                      <a href="tel:{contact.value}">
                        <p class="font-semibold truncate">{contact.value}</p>
                      </a>
                    {:else if contact.label == "EMAIL"}
                      <a href="mailto:{contact.value}">
                        <p class="font-semibold truncate">{contact.value}</p>
                      </a>
                    {:else}
                      <p class="font-semibold truncate">{contact.value}</p>
                    {/if}
                  </div>
                </div>
              {/each}
            </div>
            <hr />
            <div class="mt-2">
              {#each contactSocials as contactSocial}
                <Button variant="ghost" class="[&:hover>*]:text-accent">
                  <contactSocial.icon />
                </Button>
              {/each}
            </div>
          </div>
        </Accordion.Content>
      </Accordion.Item>
    </Accordion.Root>
  </div>
  <Tabs.Root value="portfolio" class="bg-secondary rounded-3xl border flex-1">
    <!-- --------------------------------- -->
    <div class="flex justify-end">
      <Tabs.List
        class="bg-accent-foreground p-2 rounded-none rounded-bl-xl rounded-tr-3xl"
      >
        {#each tabs as tab}
          <Tabs.Trigger value={tab.value}>
            <div class="text-accent">
              {tab.label}
            </div>
          </Tabs.Trigger>
        {/each}
      </Tabs.List>
    </div>
    {#each tabs as tab}
      <Tabs.Content class="min-h-48 px-4 pb-4" value={tab.value}>
        <tab.page />
      </Tabs.Content>
    {/each}
  </Tabs.Root>
</main>
