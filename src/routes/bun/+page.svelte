<script lang="ts">
  // Svelte 5 新特性演示 - Bun（兔子）主题
  
  // 1. $state - 响应式状态
  let count = $state(0);
  let name = $state("小白");
  
  // 2. $derived - 派生状态（自动计算）
  let emoji = $derived(count > 5 ? "🐰" : "🐇");
  let message = $derived(`${name}跳了${count}次 ${emoji}`);
  
  // 3. $effect - 副作用
  $effect(() => {
    console.log(`${name} 跳跃次数: ${count}`);
  });
  
  // 事件处理
  function jump() {
    count += 1;
  }
  
  function reset() {
    count = 0;
  }
</script>

<main class="container">
  <h1>🐰 Svelte 5 Bun 特性演示</h1>
  
  <div class="bun-card">
    <div class="bun-emoji">{emoji}</div>
    <h2>{name}</h2>
    <p class="message">{message}</p>
    
    <div class="controls">
      <input 
        type="text" 
        bind:value={name} 
        placeholder="给兔子起个名字"
      />
      
      <div class="buttons">
        <button onclick={jump} class="btn-jump">
          跳一下！
        </button>
        <button onclick={reset} class="btn-reset">
          重置
        </button>
      </div>
    </div>
    
    <div class="counter">
      <span class="count">{count}</span>
      <span class="label">跳跃次数</span>
    </div>
  </div>

  <div class="features">
    <h3>Svelte 5 新特性</h3>
    <ul>
      <li><code>$state</code> - 响应式状态声明</li>
      <li><code>$derived</code> - 自动计算派生值</li>
      <li><code>$effect</code> - 响应式副作用</li>
      <li><code>onclick</code> - 简化事件处理器（无需 <code>on:</code> 前缀）</li>
      <li><code>bind:value</code> - 双向绑定</li>
    </ul>
  </div>
</main>

<style>
  .container {
    max-width: 600px;
    margin: 2rem auto;
    padding: 1rem;
    text-align: center;
    font-family: system-ui, sans-serif;
  }
  
  h1 {
    color: #e67e22;
    margin-bottom: 2rem;
  }
  
  .bun-card {
    background: linear-gradient(135deg, #fff9e6, #fff3cc);
    border-radius: 16px;
    padding: 2rem;
    box-shadow: 0 4px 20px rgba(0,0,0,0.1);
    margin-bottom: 2rem;
  }
  
  .bun-emoji {
    font-size: 4rem;
    margin-bottom: 1rem;
  }
  
  h2 {
    color: #d35400;
    margin: 0.5rem 0;
  }
  
  .message {
    color: #666;
    font-size: 1.1rem;
    margin: 1rem 0;
  }
  
  .controls {
    margin: 1.5rem 0;
  }
  
  input {
    padding: 0.8rem 1rem;
    border: 2px solid #e67e22;
    border-radius: 8px;
    font-size: 1rem;
    width: 200px;
    text-align: center;
  }
  
  .buttons {
    margin-top: 1rem;
    display: flex;
    gap: 1rem;
    justify-content: center;
  }
  
  button {
    padding: 0.8rem 1.5rem;
    border: none;
    border-radius: 8px;
    font-size: 1rem;
    cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s;
  }
  
  button:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(0,0,0,0.2);
  }
  
  button:active {
    transform: translateY(0);
  }
  
  .btn-jump {
    background: linear-gradient(135deg, #e67e22, #f39c12);
    color: white;
  }
  
  .btn-reset {
    background: linear-gradient(135deg, #95a5a6, #7f8c8d);
    color: white;
  }
  
  .counter {
    margin-top: 1.5rem;
    padding: 1rem;
    background: rgba(230, 126, 34, 0.1);
    border-radius: 12px;
  }
  
  .count {
    display: block;
    font-size: 3rem;
    font-weight: bold;
    color: #e67e22;
  }
  
  .label {
    color: #888;
    font-size: 0.9rem;
  }
  
  .features {
    background: #f8f9fa;
    border-radius: 12px;
    padding: 1.5rem;
    text-align: left;
  }
  
  .features h3 {
    color: #333;
    margin-top: 0;
  }
  
  .features ul {
    list-style: none;
    padding: 0;
  }
  
  .features li {
    padding: 0.5rem 0;
    color: #555;
  }
  
  .features code {
    background: #e67e22;
    color: white;
    padding: 0.2rem 0.5rem;
    border-radius: 4px;
    font-size: 0.9rem;
  }
</style>
