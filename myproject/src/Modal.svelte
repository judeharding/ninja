<script>
   // export is declaring accepted props
  export let showModal = false; // will determine if this modal shows from App.svelte
  export let isPromo = false; // exporting b/c value may be passed in or set outside
  // export let message = "default value"; //  if msg is being passed in if not, default value
  
</script>

{#if showModal}
  <!-- CONDITIONALLY APPLY THE CLASS isPromo  -->
  <!-- on:click event is forwared to the parent calling this modal and the pipe is the event modifier -->
  <div class="backdrop" class:promo={isPromo} on:click|self>
    <div class="modal">
      <!-- <p> {message} </p> -->

      <!-- now using slots looking for child content from app and post it here-->
      <slot></slot>
    </div>
  </div>
{/if}

<style>
  .backdrop{
    width: 100%;
    height: 100%;
    position: fixed;
    background: rgba(0, 0, 0, 0.8);
  }
  .modal{
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background: white;
  }

  .promo .modal{
    background: crimson;
    color: white;
  }
</style>
