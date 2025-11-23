---
layout: wide
title: rhel interactif
permalink: /rhel-interactif/
nav: true
---

## Interactive Coupled Oscillators Demo

This interactive visualization demonstrates coupled harmonic oscillators. You can adjust the initial positions of the masses and observe how the system evolves over time.

<div id="iframe-container" style="width: 100%; margin: 20px 0; position: relative;">
<iframe id="responsive-iframe" src="/assets/html/coupled_oscillators_v0.html" style="width: 100%; border: 1px solid #ccc; border-radius: 8px; display: block;"></iframe>
</div>

<script>
(function() {
    const iframe = document.getElementById('responsive-iframe');
    const container = document.getElementById('iframe-container');
    
    function resizeIframe() {
        // Get the container width
        const containerWidth = container.offsetWidth;
        
        // Set aspect ratio (1500:1100 from original dimensions)
        const aspectRatio = 1100 / 1500;
        
        // Calculate height based on width and aspect ratio
        const height = containerWidth * aspectRatio;
        
        // Set the iframe height
        iframe.style.height = height + 'px';
    }
    
    // Initial resize
    resizeIframe();
    
    // Resize on window resize
    window.addEventListener('resize', resizeIframe);
})();
</script>
