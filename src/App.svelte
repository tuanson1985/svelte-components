<script>
  import Greet from "./components/Greet.svelte";
  const name = "Bui Tuan Son";
  const channel = "HQGROUP";
  const obj = {
    name: "HQPLAY",
    heroName: "HQGROUP",
  };
</script>

<main>
  <Greet name="Sonbt" heroName="Nhan vien" />
  <Greet name="Truongdv" heroName="Pho phong" />
  <Greet name="Phuongdt" heroName="Nhan vien" />
  <Greet {name} heroName={channel} />
  <Greet name={obj.name} heroName={obj.heroName} />
  <Greet {...obj} />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
