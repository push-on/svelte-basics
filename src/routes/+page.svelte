<script lang="ts">
  let input = ""
  let count = 0
  let arr: number[] = [1, 2, 3]
  // run on update
  $: {
    console.log("hello", count)
  }

  let people = [
    { name: "Yoshi", beltColor: "black", age: 25, id: 1 },
    { name: "Mario", beltColor: "orange", age: 45, id: 2 },
    { name: "Luigi", beltColor: "brown", age: 35, id: 3 },
  ]
  let rest = people
  function del(id: number) {
    people = people.filter((person) => person.id != id)
  }

  let num = 15
</script>

<div class="wh-full m">
  <h1>This svelte kit</h1>

  <!-- button on click -->
  <button on:click={() => count++}> clicked {count}</button>

  <!-- input assign value -->
  <input bind:value={input} type="text" class="my" />
  <h1>Input Value: {input}</h1>

  <!-- Array input -->
  <div class="flex">
    <button
      on:click={() => {
        arr.push(arr.length + 1)
        arr = arr
        // arr[arr.length] = arr.length + 1
      }}>add</button>
    <h1 class="mx">{arr}</h1>
  </div>

  <!-- Loops -->
  <div class="flex">
    <h1>for each loop</h1>
    <button on:click={() => (people = rest)} class="mx">rest ↺</button>
  </div>

  <div class="flex">
    {#each people as person}
      <div class="mx">
        <h4>{person.name}</h4>
        <p>{person.age} years old.</p>
        <p>{person.beltColor} belt.</p>
        <button on:click={() => del(person.id)}>x</button>
      </div>
    {:else}
      <div>Array is empty</div>
    {/each}
  </div>

  <!-- Conditionals -->
  <h1>if - else - elif - condition</h1>
  <div class="flex">
    <p>number: {num}</p>
    {#if num < 20}
      <p class="mx">is less then 20</p>
    {:else if num > 20}
      <p class="mx">is Greater then 20</p>
    {:else}
      <p class="mx">is equal to 20</p>
    {/if}
  </div>
  <input type="range" min="15" max="25" step="1" bind:value={num} />
</div>
