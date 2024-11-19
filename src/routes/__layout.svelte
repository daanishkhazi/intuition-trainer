<script>
    import "../app.css";
</script>
<!-- src/routes/__layout.svelte -->
<nav>
    <div class="nav-container">
        <a href="/" class="nav-logo" title="Back to Homepage">Visual Intuition Trainer</a>
        <div class="nav-links">
            <a href="/about" class="link">Motivation & Scoring</a>
        </div>
    </div>
 </nav>
 
 <div class="container">
     <slot></slot>
 </div>
 
 <style>
     .container {
        max-width: 1400px;
        margin: 50px auto;
    }
 </style>
