<div class="card">
    <slot></slot>
</div>

<style>
    .card {
        position: relative;
        background-color: #f1f1f1;
        color: #333;
        border-radius: calc(0.5*var(--rythme));
        padding: var(--rythme);
        margin-block: calc(0.5*var(--rythme));
    }
</style>