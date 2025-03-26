// 等待DOM加载完成
document.addEventListener('DOMContentLoaded', function() {
    // 初始化AOS动画库
    AOS.init({
        duration: 1000,
        once: true,
        offset: 100
    });
    
    // 初始化粒子背景
    initParticles();
    
    // 导航栏滚动效果
    initNavbar();
    
    // 初始化课程轮播
    initCourseSlider();
    
    // 初始化学员心声轮播
    initTestimonialSlider();
    
    // 数字计数动画
    initCounters();
    
    // 返回顶部按钮
    initBackToTop();
    
    // 表单提交处理
    initContactForm();
    
    // 移动端导航菜单
    initMobileNav();
});

// 初始化粒子背景
function initParticles() {
    particlesJS('particles-js', {
        "particles": {
            "number": {
                "value": 80,
                "density": {
                    "enable": true,
                    "value_area": 800
                }
            },
            "color": {
                "value": "#6a4ea3"
            },
            "shape": {
                "type": "circle",
                "stroke": {
                    "width": 0,
                    "color": "#000000"
                },
                "polygon": {
                    "nb_sides": 5
                }
            },
            "opacity": {
                "value": 0.3,
                "random": false,
                "anim": {
                    "enable": false,
                    "speed": 1,
                    "opacity_min": 0.1,
                    "sync": false
                }
            },
            "size": {
                "value": 3,
                "random": true,
                "anim": {
                    "enable": false,
                    "speed": 40,
                    "size_min": 0.1,
                    "sync": false
                }
            },
            "line_linked": {
                "enable": true,
                "distance": 150,
                "color": "#6a4ea3",
                "opacity": 0.2,
                "width": 1
            },
            "move": {
                "enable": true,
                "speed": 2,
                "direction": "none",
                "random": false,
                "straight": false,
                "out_mode": "out",
                "bounce": false,
                "attract": {
                    "enable": false,
                    "rotateX": 600,
                    "rotateY": 1200
                }
            }
        },
        "interactivity": {
            "detect_on": "canvas",
            "events": {
                "onhover": {
                    "enable": true,
                    "mode": "grab"
                },
                "onclick": {
                    "enable": true,
                    "mode": "push"
                },
                "resize": true
            },
            "modes": {
                "grab": {
                    "distance": 140,
                    "line_linked": {
                        "opacity": 0.5
                    }
                },
                "bubble": {
                    "distance": 400,
                    "size": 40,
                    "duration": 2,
                    "opacity": 8,
                    "speed": 3
                },
                "repulse": {
                    "distance": 200,
                    "duration": 0.4
                },
                "push": {
                    "particles_nb": 4
                },
                "remove": {
                    "particles_nb": 2
                }
            }
        },
        "retina_detect": true
    });
}

// 导航栏滚动效果
function initNavbar() {
    const navbar = document.querySelector('.navbar');
    const navLinks = document.querySelectorAll('.nav-links a');
    const sections = document.querySelectorAll('section');
    
    // 滚动时添加阴影和改变高度
    window.addEventListener('scroll', function() {
        if (window.scrollY > 50) {
            navbar.classList.add('scrolled');
        } else {
            navbar.classList.remove('scrolled');
        }
        
        // 更新活动导航链接
        let current = '';
        
        sections.forEach(section => {
            const sectionTop = section.offsetTop;
            const sectionHeight = section.clientHeight;
            
            if (window.scrollY >= (sectionTop - 200)) {
                current = section.getAttribute('id');
            }
        });
        
        navLinks.forEach(link => {
            link.classList.remove('active');
            if (link.getAttribute('href').substring(1) === current) {
                link.classList.add('active');
            }
        });
    });
    
    // 导航链接点击滚动
    navLinks.forEach(link => {
        link.addEventListener('click', function(e) {
            e.preventDefault();
            
            const targetId = this.getAttribute('href').substring(1);
            const targetSection = document.getElementById(targetId);
            
            window.scrollTo({
                top: targetSection.offsetTop - 100,
                behavior: 'smooth'
            });
            
            // 如果是移动菜单打开状态，点击后关闭
            document.querySelector('.nav-links').classList.remove('active');
        });
    });
}

// 课程轮播
function initCourseSlider() {
    const slider = document.querySelector('.course-slider');
    const prevBtn = document.getElementById('prevCourse');
    const nextBtn = document.getElementById('nextCourse');
    
    if (!slider || !prevBtn || !nextBtn) return;
    
    const cardWidth = 310; // 卡片宽度 + 外边距
    
    prevBtn.addEventListener('click', function() {
        slider.scrollBy({ left: -cardWidth, behavior: 'smooth' });
    });
    
    nextBtn.addEventListener('click', function() {
        slider.scrollBy({ left: cardWidth, behavior: 'smooth' });
    });
}

// 学员心声轮播
function initTestimonialSlider() {
    const slider = document.querySelector('.testimonial-slider');
    const prevBtn = document.getElementById('prevTestimonial');
    const nextBtn = document.getElementById('nextTestimonial');
    
    if (!slider || !prevBtn || !nextBtn) return;
    
    const testimonialWidth = 330; // 卡片宽度 + 外边距
    
    prevBtn.addEventListener('click', function() {
        slider.scrollBy({ left: -testimonialWidth, behavior: 'smooth' });
    });
    
    nextBtn.addEventListener('click', function() {
        slider.scrollBy({ left: testimonialWidth, behavior: 'smooth' });
    });
}

// 数字计数动画
function initCounters() {
    const counterElements = document.querySelectorAll('.stat-number');
    let countersStarted = false;
    
    function startCounters() {
        if (countersStarted) return;
        
        counterElements.forEach(counter => {
            const target = +counter.getAttribute('data-count');
            const duration = 2000; // 动画持续时间
            let startTime = null;
            
            function updateCounter(timestamp) {
                if (!startTime) startTime = timestamp;
                
                const progress = Math.min((timestamp - startTime) / duration, 1);
                const currentCount = Math.floor(progress * target);
                
                counter.textContent = currentCount.toLocaleString();
                
                if (progress < 1) {
                    requestAnimationFrame(updateCounter);
                } else {
                    counter.textContent = target.toLocaleString();
                }
            }
            
            requestAnimationFrame(updateCounter);
        });
        
        countersStarted = true;
    }
    
    // 监听滚动到统计区域时启动动画
    const statsSection = document.querySelector('.stats');
    if (!statsSection) return;
    
    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                startCounters();
                observer.unobserve(entry.target);
            }
        });
    }, { threshold: 0.5 });
    
    observer.observe(statsSection);
}

// 返回顶部按钮
function initBackToTop() {
    const backToTopBtn = document.getElementById('backToTop');
    
    if (!backToTopBtn) return;
    
    window.addEventListener('scroll', function() {
        if (window.scrollY > 300) {
            backToTopBtn.classList.add('active');
        } else {
            backToTopBtn.classList.remove('active');
        }
    });
    
    backToTopBtn.addEventListener('click', function() {
        window.scrollTo({
            top: 0,
            behavior: 'smooth'
        });
    });
}

// 联系表单提交
function initContactForm() {
    const contactForm = document.getElementById('contactForm');
    
    if (!contactForm) return;
    
    contactForm.addEventListener('submit', function(e) {
        e.preventDefault();
        
        // 获取表单数据
        const formData = {
            name: document.getElementById('name').value,
            phone: document.getElementById('phone').value,
            email: document.getElementById('email').value,
            interest: document.getElementById('interest').value,
            message: document.getElementById('message').value
        };
        
        // 简单的表单验证
        if (!formData.name || !formData.phone || !formData.email) {
            alert('请填写必填字段');
            return;
        }
        
        // 这里可以添加表单提交到服务器的代码
        // 示例：使用 fetch API 发送数据到后端
        
        // 模拟表单提交成功
        alert('感谢您的咨询！我们将尽快与您联系。');
        contactForm.reset();
    });
}

// 移动端导航菜单
function initMobileNav() {
    const navToggle = document.getElementById('navToggle');
    const navLinks = document.querySelector('.nav-links');
    
    if (!navToggle || !navLinks) return;
    
    navToggle.addEventListener('click', function() {
        navLinks.classList.toggle('active');
    });
}