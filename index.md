---
layout: page
title: Home
---
<div class="homepage">
    <div class="full-width">
        <div class="homepage-banner">
            <h1 class="homepage-banner-text-heading">SAMA RHINOPLASTY</h1>
            <h2 class="homepage-banner-text-subheading">Prof. Ansul Sama</h2>
            <img src="home-banner-theatre.jpg" width="100%" class="home-banner">
            <img src="home-banner-sama.png" class="home-banner-over">
        </div>
        <h1 class="homepage-quote quote-text">
            <div class="page-width">
                “A smile is happiness you will find right under your nose. Let’s find you a nose that puts a smile on your face”
            </div>
        </h1>
    </div>
    <div class="page-width">
        <div class="spacer-50"></div>
        <h2 class="page-subheading">The Nose you always wanted.</h2>
        <p class="page-text">
            Noses come in all shapes and sizes. In Rhinoplasty surgery, there is no “one size fits all”. It must be a “made to measure” procedure that successfully addresses your concerns, improves breathing and is in harmony with your facial features.
            <br><br>
            Rhinoplasty Can Help To:
            <ul>
                <li>Reduce a nasal hump</li>
                <li>Correct a drooping or hooked nose</li>
                <li>Change the size of your nose</li>
                <li>Improve the shape, size and angle of the nasal tip</li>
                <li>Change the shape and size of the nostrils</li>
                <li>Improve breathing and correct the septum</li>
                <li>Repair injuries to the nose</li>
            </ul>
        </p>
        <div class="spacer-25"></div>
        <div class="blue-line-small"></div>
        <div class="spacer-50"></div>
    </div>
    <div class="full-width homepage-comparison-pictures-container">
        <div class="page-width">
            <div class="homepage-comparison-pictures">
                <button class="homepage-comparison-button prev">
                    <img src="button-prev.png" width="100%">
                </button>
                <div class="homepage-comparison-pictures-inner" id="homepage-carousel">
                    <div class="comparison-row" name="slide1">
                        <div class="before"><img src="1a.jpg" width="100%"></div>
                        <div class="after"><img src="1b.jpg" width="100%"></div>
                    </div>
                    <div class="comparison-row" name="slide2">
                        <div class="before"><img src="2a.jpg" width="100%"></div>
                        <div class="after"><img src="2b.jpg" width="100%"></div>
                    </div>
                    <div class="comparison-row" name="slide3">
                        <div class="before"><img src="3a.jpg" width="100%"></div>
                        <div class="after"><img src="3b.jpg" width="100%"></div>
                    </div>
                    <div class="comparison-row" name="slide4">
                        <div class="before"><img src="4a.jpg" width="100%"></div>
                        <div class="after"><img src="4b.jpg" width="100%"></div>
                    </div>
                    <div class="comparison-row" name="slide5">
                        <div class="before"><img src="5b.jpg" width="100%"></div>
                        <div class="after"><img src="5a.jpg" width="100%"></div>
                    </div>
                </div>
                <button class="homepage-comparison-button next">
                    <img src="button-next.png" width="100%">
                </button>
            </div>
        </div>
    </div>
    <div class="spacer-50"></div>
    <div class="page-width">
        <div class="homepage-logos">
            <div class="homepage-logo"><img src="BRS.png" width="100%"></div>
            <div class="homepage-logo"><img src="bsfps.png" width="100%"></div>
            <div class="homepage-logo"><img src="BSRS 2.jfif" width="100%"></div>
            <div class="homepage-logo"><img src="BSRS.jfif" width="100%"></div>
            <div class="homepage-logo"><img src="ENT UK 2.png" width="100%"></div>
            <div class="homepage-logo"><img src="ERS logo.png" width="100%"></div>
            <div class="homepage-logo"><img src="logo-eafps.png" width="100%"></div>
            <div class="homepage-logo"><img src="RCOS 1.png" width="100%"></div>
            <div class="homepage-logo"><img src="RCOS 2.png" width="100%"></div>
            <div class="homepage-logo"><img src="RCOS 3.png" width="100%"></div>
            <div class="homepage-logo"><img src="RCOS 4.png" width="100%"></div>
            <div class="homepage-logo"><img src="RSM.png" width="100%"></div>
        </div>
    </div>
    <div class="spacer-50"></div>
</div>
<script>
    const nextBtn = document.querySelector('.homepage-comparison-button.next');
    const prevBtn = document.querySelector('.homepage-comparison-button.prev');
    const inner = document.querySelector('.homepage-comparison-pictures-inner');
    const slideWidth = inner.offsetWidth;
    let slides = Array.from(document.querySelectorAll('#homepage-carousel .comparison-row'));
    const slidesLength = slides.length;
    let firstSlideDupe = slides[0].cloneNode(true);
    let lastSlideDupe = slides[slidesLength - 1].cloneNode(true);
    firstSlideDupe.dataset.clone = 'last';
    lastSlideDupe.dataset.clone = 'first';
    inner.appendChild(firstSlideDupe);
    inner.insertBefore(lastSlideDupe, slides[0]);
    slides = Array.from(inner.querySelectorAll('#homepage-carousel .comparison-row'));
    let currentSlide = 1;
    let isTransitioning = false;
    let transition_duration = 500;
    function scrollToIndex(index, smooth = true) {
        inner.scrollTo({
            left: index * slideWidth,
            behavior: smooth ? 'smooth' : 'auto'
        });
    }
    scrollToIndex(1, false);
    function nextSlide() {
        if (isTransitioning) return;
        isTransitioning = true;
        currentSlide += 1;
        if (slides[currentSlide].dataset.clone == 'last') {
            scrollToIndex(currentSlide, true);
            setTimeout(() => {
                currentSlide = 1;
                scrollToIndex(1, false);
                isTransitioning = false;
            }, transition_duration);
        } else {
            scrollToIndex(currentSlide, true);
            setTimeout(() => {
                isTransitioning = false;
            }, transition_duration);
        }
    }
    function prevSlide() {
        if (isTransitioning) return;
        isTransitioning = true;
        currentSlide -= 1;
        if (slides[currentSlide].dataset.clone == 'first') {
            scrollToIndex(currentSlide, true);
            setTimeout(() => {
                currentSlide = slidesLength;
                scrollToIndex(slidesLength, false);
                isTransitioning = false;
            }, transition_duration);
        } else {
            scrollToIndex(currentSlide, true);
            setTimeout(() => {
                isTransitioning = false;
            }, transition_duration);
        }
    }
    nextBtn.addEventListener('click', nextSlide);
    prevBtn.addEventListener('click', prevSlide);
    let autoScroll;
    const element = document.querySelector('#homepage-carousel');
    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                autoScroll = setInterval(nextSlide, 4000);
            } else {
                clearInterval(autoScroll);
            }
        });
    });
    observer.observe(element);
</script>
