<script type="ts">
    import { Button } from "$lib/components/ui/button/";
    import * as Accordion from "$lib/components/ui/accordion";
    import { JsonView } from '@zerodevx/svelte-json-view'

    let docContent = "";

    function selectedDoc(doc) {
        docContent = doc;
    }

    const json = {
        "name": "mathadventure's library!",
        "consoles": [
            {
                "name": "NES",
                "folder": "nes"
            },
            {
                "name": "GBA",
                "folder": "gba"
            }
        ]
    }

    const json2 = {
        "games": [
            {
                "title": "Fake Racing",
                "file": "fake.nes"
            },
            {
                "title": "Real Racing",
                "file": "real.nes"
            },
        ]
    }
</script>
    
<svelte:head>
    <title>Documentation - {docContent}</title> 
</svelte:head>
    
    <div class="flex ml-2">
        <aside class="ml-40 w-1/5 mt-8">
            <div class="flex flex-col ml-2 justify-start">
                <h4 class="scroll-m-20 font-bold text-xl tracking-tight mt-4">General</h4>
                {#each [
                    {name: "Intro", selected: docContent === "Intro"},
                    {name: "Library", selected: docContent === "Library"},
                ] as doc}
                    <Button
                        variant="link"
                        class={`pl-0 ml-2 scroll-m-20 text-lg tracking-tight ${doc.selected ? 'font-bold' : 'text-muted-foreground'} mt-4 w-max`}
                        on:click={() => selectedDoc(doc.name)}
                        style="font-weight: {doc.selected ? 'bold' : 'normal'}"
                    >{doc.name}</Button>
                {/each}
            </div>
        </aside>
    
        <div class="ml-4 float-left mt-12">
            {#if docContent === "Intro" || !docContent}
                <h1 class="scroll-m-20 text-3xl font-bold tracking-tight lg:text-3xl mt-4">
                    GBA2.0 Documentation
                </h1>
                <p class="text-lg text-muted-foreground">
                    Welcome to the GBA2.0 documentation. This is where you can find all the information you need to know about GBA2.0.
                </p>
                <p class="mt-3 font-medium">
                    Including, information on how to self-host, add a library, and community information. This is NOT developer documentation.
                </p>    

                <p class="mt-3 font-medium">
                    This site was created by Cattn & the MSG team, you can view more information about us at our <Button class="px-0 font-bold underline" variant="link" href="https://mathstudy.dev">site</Button>
                </p>


                <h3 class="mt-12 font-bold text-2xl">FAQ</h3>
                <Accordion.Root class="w-3/5">
                    <Accordion.Item value="item-1">
                      <Accordion.Trigger class="font-bold text-lg">Do you provide games?</Accordion.Trigger>
                      <Accordion.Content>
                        No, we do not, and will not provide any games or ROMs to you directly. You are expected to be a legal owner of any games you play here.
                      </Accordion.Content>
                    </Accordion.Item>
                    <Accordion.Item value="item-2">
                        <Accordion.Trigger class="font-bold text-lg">What happened to the old site?</Accordion.Trigger>
                        <Accordion.Content>
                          There's been a lot of stir involving nintendo and their policy towards emulators and sites. We are just ensuring all of our bases are covered.
                        </Accordion.Content>
                      </Accordion.Item>
                      <Accordion.Item value="item-3">
                        <Accordion.Trigger class="font-bold text-lg">How do I host my own Library?</Accordion.Trigger>
                        <Accordion.Content>
                          Please view our "Library" section of our Docs.
                        </Accordion.Content>
                      </Accordion.Item>
                  </Accordion.Root>
            {:else if docContent === "Library"}
                <h1 class="scroll-m-20 text-3xl font-bold tracking-tight lg:text-3xl mt-4">
                    Library Info
                </h1>
                <p class="text-lg text-muted-foreground">
                    General information about creation of libraries, as well as common questions and answers.
                </p>

                <Accordion.Root class="mt-12">
                    <Accordion.Item value="item-1">
                      <Accordion.Trigger class="font-bold text-lg">Library Creation Tool</Accordion.Trigger>
                      <Accordion.Content>
                        You can find details regarding our library creation tool <Button class="px-0 font-bold underline" variant="link" href="https://github.com/Cattn/GBAv3/wiki">here</Button> on our github wiki!
                      </Accordion.Content>
                    </Accordion.Item>
                    <Accordion.Item value="item-2">
                        <Accordion.Trigger class="font-bold text-lg">Custom Values</Accordion.Trigger>
                        <Accordion.Content>
                          In the future we may add support for custom options regarding theme, images, etc with your library.
                        </Accordion.Content>
                      </Accordion.Item>
                  </Accordion.Root>
            {/if}
        </div>
    </div>

