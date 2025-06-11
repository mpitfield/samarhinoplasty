---
layout: page
title: Home
---

<div class="page-width">
    <div class="carousel" id="home-carousel">
        <span class="carousel-buttons">
            <button class="button-blank prev-button" onclick="nextCarousel()"><</button>
            <button class="button-blank next-button">></button>
        </span>
        <div><img src="/images/car1.jpg"></div>
        <div><img src="/images/car2.jpg"></div>
        <div><img src="/images/car3.jpg"></div>
        <div><img src="/images/car4.jpg"></div>
    </div>
</div>

<script>
    let carousels = document.getElementById('home-carousel').querySelectorAll('div');
    carousels[0].classList.add('current');
    function nextCarousel() {
        let current = '';
        let next = '';
        for (let i=0; i<carousels.length; i++) {
            if (carousels[i].classList.contains('current')) {
                current = carousels[i];
                next = carousels[i + 1];
                break;
            }
        }
        current.classList.remove('current');
        current.classList.add('previous');
        next.classList.add('current');
    }
</script>
