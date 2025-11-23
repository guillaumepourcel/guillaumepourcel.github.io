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
    border: 1px solid #ccc;
    border-radius: 8px;
    display: block;
    transform-origin: 0 0;
}
</style>

<div id="iframe-container">
<iframe id="responsive-iframe" src="/assets/html/coupled_oscillators_v0.html" width="1500" height="1100" scrolling="no"></iframe>
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
    const iframe = document.getElementById('responsive-iframe');
    const container = document.getElementById('iframe-container');
    
    function resizeIframe() {
        if (!container || !iframe) return;
        
        const containerWidth = container.offsetWidth;
        const originalWidth = 1500;
        const originalHeight = 1100;
        
        // Calculate scale to fit container width
        const scale = Math.min(containerWidth / originalWidth, 1);
        
        // Apply scale transform
        iframe.style.transform = `scale(${scale})`;
        iframe.style.width = originalWidth + 'px';
        iframe.style.height = originalHeight + 'px';
        
        // Adjust container height to match scaled content
        container.style.height = (originalHeight * scale) + 'px';
        container.style.width = (originalWidth * scale) + 'px';
    }
    
    setTimeout(resizeIframe, 100);
    
    let resizeTimer;
    window.addEventListener('resize', function() {
        clearTimeout(resizeTimer);
        resizeTimer = setTimeout(resizeIframe, 250);
    });
    
    iframe.addEventListener('load', resizeIframe);
});
</script>
