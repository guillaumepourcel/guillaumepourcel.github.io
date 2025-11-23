---
layout: wide
title: rhel interactif
permalink: /rhel-interactif/
nav: true
---

## Interactive Coupled Oscillators Demo

This interactive visualization demonstrates coupled harmonic oscillators. You can adjust the initial positions of the masses and observe how the system evolves over time.

<style>
#iframe-container {
    width: 100%;
    margin: 20px 0;
    position: relative;
    overflow: hidden;
}

#responsive-iframe {
    width: 100%;
    min-height: 800px;
    border: 1px solid #ccc;
    border-radius: 8px;
    display: block;
}
</style>

<div id="iframe-container">
<iframe id="responsive-iframe" src="/assets/html/coupled_oscillators_v0.html"></iframe>
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
    const iframe = document.getElementById('responsive-iframe');
    const container = document.getElementById('iframe-container');
    
    function resizeIframe() {
        if (!container || !iframe) return;
        
        // Get the container width
        const containerWidth = container.offsetWidth;
        
        // Set aspect ratio (1500:1100 from original dimensions)
        const aspectRatio = 1100 / 1500;
        
        // Calculate height based on width and aspect ratio
        const height = Math.max(containerWidth * aspectRatio, 800);
        
        // Set the iframe height
        iframe.style.height = height + 'px';
    }
    
    // Initial resize with a small delay to ensure layout is ready
    setTimeout(resizeIframe, 100);
    
    // Resize on window resize with debouncing
    let resizeTimer;
    window.addEventListener('resize', function() {
        clearTimeout(resizeTimer);
        resizeTimer = setTimeout(resizeIframe, 250);
    });
    
    // Also resize when iframe loads
    iframe.addEventListener('load', resizeIframe);
});
</script>
