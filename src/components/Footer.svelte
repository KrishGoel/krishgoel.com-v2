<script>
    export let appearance
</script>

<style>
    footer {
        padding: 20px 0;
    }
    footer .width-restriction {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    footer .links, footer .links p{
        display: inline-block;
    }

    footer .links p {
        margin-left: 5px;
    }
    footer p {
        margin-bottom: 0
    }
</style>

<footer class="{appearance}">
    <div class="width-restriction">
        <p>&copy; Krish Goel<p>
        <div class="links">
            <!-- <p><a href="/about" aria-label="About">About</a></p> -->
            <p><a href="/colophon" aria-label="Colophon">Colophon</a></p>
            <p><a href="/thanks" aria-label="Thanks">Thanks</a></p>
        </div>
    </div>
</footer>