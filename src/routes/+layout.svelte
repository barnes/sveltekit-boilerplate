<script lang="ts">
  import '@picocss/pico'
  import { invalidate } from '$app/navigation'
  import { onMount } from 'svelte'
  import type { LayoutData } from './$types'

  export let data: LayoutData

  $: ({ supabase } = data)
  
  onMount(()=>{
    const { data } = supabase.auth.onAuthStateChage(()=>{
      invalidate('supabase:auth');
    })
    return () => data.subscription.unsubscribe();
  })
</script>

<svelte:head>
  <title>User MGMT</title>
</svelte:head>

<div class="container">
  <nav>
    <ul>
      <li>Sveltekit Boilerplate</li>
    </ul>
  </nav>
  <slot />
</div>