<script>
import { todos } from './store.js';
</script>

<main>
  {#each $todos as { value, completed, id } (id)}
  <div class="card">
    <label class="card-body p-3 mb-2 bg-primary text-white">
        <input type="checkbox" bind:checked={completed}/>
        { value }
    </label>
  </div>
  {/each}

  <h4>{$todos.filter(todo => !todo.completed).length} left!</h4>
</main>
