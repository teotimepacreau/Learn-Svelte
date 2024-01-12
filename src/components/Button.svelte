<script>
    export let style
    export let type
    export let disabled
</script>

<button {type} class={style} {disabled}>
    <slot></slot>    
</button>

<style>
    button {
      color: #fff;
      border: 2px solid transparent;
      border-radius: 8px;
      width: 100px;
      height: 40px;
      cursor: pointer;
    }
  
    .primary {
      background-color: #202142;
    }
  
    .secondary {
      background: #ff6a95;
    }

  
    button:disabled{
      background-color: dimgrey;
      color: whitesmoke;
      cursor: not-allowed;
    }

    button:not(:disabled){
        background-color: #f1f1f1;
        border-color: #202142;
        color: #202142;
        font-weight: 600;
    }
  
  </style>