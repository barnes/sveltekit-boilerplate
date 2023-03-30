<script lang="ts">
  import { Auth } from '@supabase/auth-ui-svelte';
	import { ThemeSupa } from '@supabase/auth-ui-shared';
  import type { PageData } from './$types';

  export let data: PageData;
</script>

<div>
<Auth
			supabaseClient={data.supabase}
			view="magic_link"
			redirectTo={`${data.url}/logging-in?redirect=/`}
			showLinks={false}
			appearance={{ theme: ThemeSupa, style: { input: 'color: #fff' } }}
		/>
</div>