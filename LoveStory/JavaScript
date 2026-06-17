video.playbackRate = 0.6;
// ========================================
// КАРУСЕЛЬ ДЛЯ РАЗДЕЛА "НАШИ МОМЕНТЫ"
// ========================================

document.addEventListener('DOMContentLoaded', function() {

    const carousel = document.getElementById('carousel');
    const slides = document.querySelectorAll('.carousel-slide');
    const totalSlides = slides.length;
    const dots = document.querySelectorAll('.dot');

    let currentIndex = 0;
    let autoPlayInterval = null;
    const AUTO_PLAY_DELAY = 4000;

    // Функция переключения на слайд
    function goToSlide(index) {
        if (index < 0) {
            currentIndex = totalSlides - 1;
        } else if (index >= totalSlides) {
            currentIndex = 0;
        } else {
            currentIndex = index;
        }

        carousel.style.transform = 'translateX(-' + (currentIndex * 100) + '%)';

        dots.forEach(function(dot, i) {
            if (i === currentIndex) {
                dot.classList.add('active');
            } else {
                dot.classList.remove('active');
            }
        });
    }

    // Кнопка "назад"
    const prevBtn = document.getElementById('prevBtn');
    if (prevBtn) {
        prevBtn.addEventListener('click', function() {
            goToSlide(currentIndex - 1);
            resetAutoPlay();
        });
    }

    // Кнопка "вперед"
    const nextBtn = document.getElementById('nextBtn');
    if (nextBtn) {
        nextBtn.addEventListener('click', function() {
            goToSlide(currentIndex + 1);
            resetAutoPlay();
        });
    }

    // Клик по точечкам
    dots.forEach(function(dot, index) {
        dot.addEventListener('click', function() {
            goToSlide(index);
            resetAutoPlay();
        });
    });

    // Автопрокрутка
    function startAutoPlay() {
        if (autoPlayInterval) clearInterval(autoPlayInterval);
        autoPlayInterval = setInterval(function() {
            goToSlide(currentIndex + 1);
        }, AUTO_PLAY_DELAY);
    }

    function resetAutoPlay() {
        startAutoPlay();
    }

    // Запуск
    goToSlide(0);
    startAutoPlay();

    // Остановка автопрокрутки при наведении мыши
    const wrapper = document.querySelector('.carousel-wrapper');
    if (wrapper) {
        wrapper.addEventListener('mouseenter', function() {
            clearInterval(autoPlayInterval);
        });
        wrapper.addEventListener('mouseleave', function() {
            startAutoPlay();
        });

        // Свайп для телефонов
        let touchStartX = 0;
        let touchEndX = 0;

        wrapper.addEventListener('touchstart', function(e) {
            touchStartX = e.changedTouches[0].screenX;
        });

        wrapper.addEventListener('touchend', function(e) {
            touchEndX = e.changedTouches[0].screenX;
            const diff = touchStartX - touchEndX;
            if (Math.abs(diff) > 50) {
                if (diff > 0) {
                    goToSlide(currentIndex + 1);
                } else {
                    goToSlide(currentIndex - 1);
                }
                resetAutoPlay();
            }
        });
    }

});