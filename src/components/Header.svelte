<header>
    <a href="/">
        <img class="logoimage" src="logo.png" alt="Logo">
    </a>
	<h1>Ezan vakitleri</h1>
	<a style="font-size: 1.5em;" href="https://example.com">Link</a>
</header>
<style>
    :root{
        --logosize:4rem
    }
    .logoimage{
        width: var(--logosize);
        height: var(--logosize);
    }
    header {
        background-color: darkgreen;
    color: ivory;
    display: flex;
    flex-wrap: nowrap;
    padding: 20px;
    flex-direction: row;
    justify-content: space-evenly;        
    }

    h1 {
        align-self: center;
        margin: auto;
        text-align: center;
    }

    a {
        align-self: center;
        color: yellow;
        text-decoration: none;
        margin-left: auto;
    }

    @media screen and (min-width: 768px) {
        header {
            padding: 30px;
        }
        h1 {
            flex: 1 0 auto;
        }
    }
</style>