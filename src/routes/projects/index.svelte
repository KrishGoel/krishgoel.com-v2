<script context="module">
	export function preload({ params, query }) {
		return this.fetch(`projects.json`).then(r => r.json()).then(projects => {
			return { projects };
		});
	}
</script>

<script>
    export let projects

    import { range } from '../../scripts/range'

    import Space from '../../components/space.svelte'

    let title= "Projects | krishgoel.com";
    let description = "Hi, I'm Krish, a technophile and maker from New Delhi and this is a comprehensive list of all my projects.";
    let url = "https://krishgoel.com/projects";
</script>

<svelte:head>
    <title>{title}</title>
    <meta name="title" content="{title}" />
    <meta name="description" content="{description}" />
    <meta property="og:title" content="{title}" />
    <meta property="og:url" content="{url}" />
    <meta property="og:description" content="{description}" />
    <meta name="twitter:title" content="{title}" />
    <meta name="twitter:url" content="{url}" />
    <meta name="twitter:description" content="{description}" />
</svelte:head>

<style>
    .card {
        padding-top: 0px
    }
</style>

<section>
    <div class="row">
        <div class="col-2">
            <h2>Projects Portfolio</h2>
            <p>This is a detailed list of all the projects I've worked on so far, it includes my hackathon submissions, side tinkers, failed startup ideas, and non-profits</p>
        </div>
    </div>
    <Space height={"25px"}/>
    <div class="large-view">
        <div class="row">
            {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each projects as project, p}
                        {#if p%3 == i}
                        <div class="card">
                            {#if project.cover != undefined && project.cover != ""}
                                <img src="{project.cover}" alt="Cover image for {project.title}" style="margin-bottom: 20px; width: calc(100% - 20px); margin-left: 10px; margin-top: 10px; "/>
                            {/if}
                            <div class="width-restriction">
                                {#if project.cover == undefined || project.cover == ""}
                                    <h3 style="padding-top: 30px; margin-bottom: 0px">{project.title}</h3>
                                {:else}
                                    <h3 style="margin-bottom: 0px">{project.title}</h3>
                                {/if}
                                <p class="mono" style="font-size: 14px; margin-bottom: 10px">{project.date} </p>
                                <p style="font-weight: bold; margin-bottom: 10px">{project.type}</p>
                                <p style="margin-bottom: 10px;">{@html project.description}</p>
                                <!-- Links -->
                                <div class="links">
                                    {#if project.link1 != undefined}
                                        {#if project.documentationAvailable == true}
                                            <p><a href="projects/{project.slug}" aria-label="Project Documentation">{project.link1}</a></p>
                                        {:else}
                                            <p><a href="{project.url1}" target="_blank" aria-label="{project.link1}">{project.link1}</a></p>
                                        {/if}
                                    {/if}
                                    {#if project.link2 != undefined}
                                        <p><a href="{project.url2}" target="_blank" aria-label="{project.link2}">{project.link2}</a></p>
                                    {/if}
                                    {#if project.link3 != undefined}
                                        <p><a href="{project.url3}" target="_blank" aria-label="{project.link3}">{project.link3}</a></p>
                                    {/if}
                                </div>
                            </div>
                        </div>
                        {/if}
                    {/each}
                </div>
            {/each}
        </div>
    </div>
    <div class="tablet-view">
        <div class="row">
            {#each range(0,2,1) as i, index}
                <div class="col-2">
                    {#each projects as project, p}
                        {#if p%2 == i}
                        <div class="card">
                            {#if project.cover != undefined && project.cover != ""}
                                <img src="{project.cover}" alt="Cover image for {project.title}" style="margin-bottom: 20px; width: calc(100% - 20px); margin-left: 10px; margin-top: 10px; "/>
                            {/if}
                            <div class="width-restriction">
                                {#if project.cover == undefined || project.cover == ""}
                                    <h3 style="padding-top: 30px; margin-bottom: 5px">{project.title}</h3>
                                {:else}
                                    <h3 style="margin-bottom: 5px">{project.title}</h3>
                                {/if}
                                <p class="mono" style="font-size: 14px; margin-bottom: 10px">{project.date} </p>
                                <p style="font-weight: bold; margin-bottom: 10px">{project.type}</p>
                                <p style="margin-bottom: 10px;">{@html project.description}</p>
                                <!-- Links -->
                                <div class="links">
                                    {#if project.link1 != undefined}
                                        {#if project.documentationAvailable == true}
                                            <p><a href="projects/{project.slug}" aria-label="Project Documentation">{project.link1}</a></p>
                                        {:else}
                                            <p><a href="{project.url1}" target="_blank" aria-label="{project.link1}">{project.link1}</a></p>
                                        {/if}
                                    {/if}
                                    {#if project.link2 != undefined}
                                        <p><a href="{project.url2}" target="_blank" aria-label="{project.link2}">{project.link2}</a></p>
                                    {/if}
                                    {#if project.link3 != undefined}
                                        <p><a href="{project.url3}" target="_blank" aria-label="{project.link3}">{project.link3}</a></p>
                                    {/if}
                                </div>
                            </div>
                        </div>
                        {/if}
                    {/each}
                </div>
            {/each}
        </div>
    </div>
    <div class="mobile-view">
        {#each projects as project, p}
            <div class="card">
                {#if project.cover != undefined && project.cover != ""}
                    <img src="{project.cover}" alt="Cover image for {project.title}" style="margin-bottom: 20px; width: calc(100% - 20px); margin-left: 10px; margin-top: 10px; "/>
                {/if}
                <div class="width-restriction">
                    {#if project.cover == undefined || project.cover == ""}
                        <h3 style="padding-top: 30px; margin-bottom: 5px">{project.title}</h3>
                    {:else}
                        <h3 style="margin-bottom: 5px">{project.title}</h3>
                    {/if}
                    <p class="mono" style="font-size: 14px; margin-bottom: 10px">{project.date} </p>
                    <p style="font-weight: bold; margin-bottom: 10px">{project.type}</p>
                    <p style="margin-bottom: 10px;">{@html project.description}</p>
                    <!-- Links -->
                    <div class="links">
                        {#if project.link1 != undefined}
                            {#if project.documentationAvailable == true}
                                <p><a href="projects/{project.slug}" aria-label="Project Documentation">{project.link1}</a></p>
                            {:else}
                                <p><a href="{project.url1}" target="_blank" aria-label="{project.link1}">{project.link1}</a></p>
                            {/if}
                        {/if}
                        {#if project.link2 != undefined}
                            <p><a href="{project.url2}" target="_blank" aria-label="{project.link2}">{project.link2}</a></p>
                        {/if}
                        {#if project.link3 != undefined}
                            <p><a href="{project.url3}" target="_blank" aria-label="{project.link3}">{project.link3}</a></p>
                        {/if}
                    </div>
                </div>
            </div>
        {/each}
    </div>
</section>