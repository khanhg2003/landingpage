<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vân Hữu Gia Khánh - Digital Marketing Specialist</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #0a0a0a;
            color: #e5e7eb;
        }
        #hero-canvas {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: 0;
        }
        .hero-content {
            position: relative;
            z-index: 1;
        }
        .glass-effect {
            background: rgba(17, 24, 39, 0.6);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        .tech-glow {
            box-shadow: 0 0 15px rgba(59, 130, 246, 0.3), 0 0 5px rgba(59, 130, 246, 0.2);
        }
        .btn-primary {
            background-color: #1f2937;
            border: 1px solid #3b82f6;
            transition: all 0.3s ease;
        }
        .btn-primary:hover {
            background-color: #3b82f6;
            box-shadow: 0 0 20px rgba(59, 130, 246, 0.5);
        }
        .section-title {
            position: relative;
            display: inline-block;
            padding-bottom: 0.5rem;
            margin-bottom: 2rem;
        }
        .section-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 50%;
            height: 3px;
            background: linear-gradient(90deg, #3b82f6, #1e3a8a);
            border-radius: 2px;
        }
        .skill-card:hover .skill-icon {
            transform: scale(1.1);
            color: #3b82f6;
        }
        .project-card {
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .project-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
        }
        .timeline::before {
            content: '';
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            top: 0;
            bottom: 0;
            width: 2px;
            background-color: rgba(255, 255, 255, 0.1);
        }
        .timeline-item {
            position: relative;
        }
        .timeline-dot {
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            width: 16px;
            height: 16px;
            background-color: #0a0a0a;
            border: 3px solid #3b82f6;
            border-radius: 50%;
            z-index: 10;
        }
        .filter-btn {
            background-color: #1f2937;
            border: 1px solid #374151;
        }
        .filter-btn.active {
            background-color: #3b82f6;
            border-color: #3b82f6;
            color: white;
        }
        .project-card img {
            aspect-ratio: 16 / 10;
            object-fit: cover;
        }
        @media (max-width: 768px) {
            .timeline::before {
                left: 8px;
                transform: translateX(0);
            }
            .timeline-item > div {
                width: calc(100% - 40px);
                margin-left: 40px;
            }
            .timeline-dot {
                left: 8px;
            }
        }
    </style>
</head>
<body class="antialiased">

    <!-- Header -->
    <header class="fixed top-0 left-0 right-0 z-50 glass-effect">
        <div class="container mx-auto px-6 py-4 flex justify-between items-center">
            <a href="#" class="text-2xl font-bold text-white">Gia Khánh<span class="text-blue-500">.</span></a>
            <nav class="hidden md:flex space-x-8">
                <a href="#about" class="hover:text-blue-400 transition-colors">Giới thiệu</a>
                <a href="#skills" class="hover:text-blue-400 transition-colors">Kỹ năng</a>
                <a href="#experience" class="hover:text-blue-400 transition-colors">Kinh nghiệm</a>
                <a href="#projects" class="hover:text-blue-400 transition-colors">Dự án</a>
                <a href="#contact" class="hover:text-blue-400 transition-colors">Liên hệ</a>
            </nav>
            <button id="mobile-menu-button" class="md:hidden text-white focus:outline-none">
                <i class="fas fa-bars text-2xl"></i>
            </button>
        </div>
        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden md:hidden">
            <a href="#about" class="block py-2 px-6 hover:bg-gray-800">Giới thiệu</a>
            <a href="#skills" class="block py-2 px-6 hover:bg-gray-800">Kỹ năng</a>
            <a href="#experience" class="block py-2 px-6 hover:bg-gray-800">Kinh nghiệm</a>
            <a href="#projects" class="block py-2 px-6 hover:bg-gray-800">Dự án</a>
            <a href="#contact" class="block py-2 px-6 hover:bg-gray-800">Liên hệ</a>
        </div>
    </header>

    <main>
        <!-- Hero Section -->
        <section id="home" class="min-h-screen flex items-center relative overflow-hidden bg-[#0a0a0a]">
            <canvas id="hero-canvas"></canvas>
            <div class="container mx-auto px-6 text-center hero-content">
                <div class="max-w-4xl mx-auto">
                    <img src="https://i.imgur.com/T5w3P16.png" alt="Vân Hữu Gia Khánh" class="w-40 h-40 rounded-full mx-auto mb-6 border-4 border-gray-700 tech-glow">
                    <h1 class="text-4xl md:text-6xl font-bold text-white mb-4 leading-tight">Vân Hữu Gia Khánh</h1>
                    <p class="text-xl md:text-2xl text-blue-400 font-semibold mb-8">Digital Marketing Specialist</p>
                    <p class="text-lg text-gray-300 max-w-2xl mx-auto mb-10">
                        Chuyên gia về SEO & Social Media, giúp thương hiệu tăng trưởng đột phá trên nền tảng số.
                    </p>
                    <a href="#projects" class="btn-primary text-white font-bold py-3 px-8 rounded-full text-lg">
                        Xem các dự án của tôi
                    </a>
                </div>
            </div>
        </section>

        <!-- About Me Section -->
        <section id="about" class="py-20 md:py-32">
            <div class="container mx-auto px-6">
                <div class="grid md:grid-cols-5 gap-12 items-center">
                    <div class="md:col-span-2">
                        <div class="relative">
                             <img src="https://i.imgur.com/T5w3P16.png" alt="Vân Hữu Gia Khánh" class="rounded-lg w-full h-auto tech-glow">
                        </div>
                    </div>
                    <div class="md:col-span-3">
                        <h2 class="section-title text-3xl md:text-4xl font-bold mb-6">Về bản thân</h2>
                        <p class="text-gray-300 mb-4 text-lg leading-relaxed">
                           Tôi là một Junior Digital Marketing năng động và luôn chú trọng đến chi tiết, với kinh nghiệm thực chiến về Facebook Ads và SEO. Trong hơn một năm qua, tôi đã tích lũy kỹ năng vận hành các chiến dịch quảng cáo, tối ưu hóa nội dung website cho công cụ tìm kiếm và quản lý nội dung số.
                        </p>
                        <p class="text-gray-300 mb-6 text-lg leading-relaxed">
                            Với nền tảng về social media và sáng tạo nội dung, tôi hiểu rõ cách thu hút và tương tác với khán giả trực tuyến. Tôi mong muốn được áp dụng các kỹ năng của mình để đóng góp vào nỗ lực marketing của công ty bạn và tiếp tục phát triển trong ngành.
                        </p>
                        <div class="flex space-x-4">
                            <a href="mailto:khanhvhg2003.forwork@gmail.com" class="btn-primary text-white font-semibold py-3 px-6 rounded-lg">
                               <i class="fas fa-envelope mr-2"></i> Gửi Email
                            </a>
                            <a href="#" class="bg-gray-700 hover:bg-gray-600 text-white font-semibold py-3 px-6 rounded-lg transition-colors">
                               <i class="fas fa-download mr-2"></i> Tải CV
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Skills Section -->
        <section id="skills" class="py-20 md:py-32 bg-black">
            <div class="container mx-auto px-6">
                <h2 class="section-title text-3xl md:text-4xl font-bold text-center">Kỹ năng chuyên môn</h2>
                <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-8 mt-12">
                    <div class="skill-card glass-effect p-6 rounded-lg text-center transition-all duration-300"><i class="fas fa-search text-5xl mb-4 text-gray-400 skill-icon transition-all duration-300"></i><h3 class="font-semibold text-lg">SEO</h3></div>
                    <div class="skill-card glass-effect p-6 rounded-lg text-center transition-all duration-300"><i class="fab fa-facebook text-5xl mb-4 text-gray-400 skill-icon transition-all duration-300"></i><h3 class="font-semibold text-lg">Facebook Ads</h3></div>
                    <div class="skill-card glass-effect p-6 rounded-lg text-center transition-all duration-300"><i class="fas fa-bullhorn text-5xl mb-4 text-gray-400 skill-icon transition-all duration-300"></i><h3 class="font-semibold text-lg">Social Media</h3></div>
                    <div class="skill-card glass-effect p-6 rounded-lg text-center transition-all duration-300"><i class="fas fa-pen-nib text-5xl mb-4 text-gray-400 skill-icon transition-all duration-300"></i><h3 class="font-semibold text-lg">Content Marketing</h3></div>
                    <div class="skill-card glass-effect p-6 rounded-lg text-center transition-all duration-300"><i class="fas fa-tasks text-5xl mb-4 text-gray-400 skill-icon transition-all duration-300"></i><h3 class="font-semibold text-lg">Marketing Plan</h3></div>
                    <div class="skill-card glass-effect p-6 rounded-lg text-center transition-all duration-300"><i class="fab fa-figma text-5xl mb-4 text-gray-400 skill-icon transition-all duration-300"></i><h3 class="font-semibold text-lg">UI/UX Design</h3></div>
                </div>
            </div>
        </section>

        <!-- Experience Section -->
        <section id="experience" class="py-20 md:py-32">
            <div class="container mx-auto px-6">
                <h2 class="section-title text-3xl md:text-4xl font-bold text-center">Hành trình sự nghiệp</h2>
                <div class="relative mt-12">
                    <div class="timeline max-w-3xl mx-auto">
                        <div class="timeline-item md:grid md:grid-cols-2 md:gap-8"><div class="md:text-right mb-4 md:mb-0"><p class="font-bold text-lg text-blue-400">11/2024 - Hiện tại</p><p class="text-gray-400">Queen Cafe Bus</p></div><div class="glass-effect p-6 rounded-lg relative"><div class="timeline-dot"></div><h3 class="font-bold text-xl mb-2">Social media & SEO Project Manager</h3><p class="text-gray-300 text-sm">Dẫn dắt thiết kế UX/UI website, điều phối team IT. Thực thi chiến lược SEO, xây dựng và quản lý Fanpage, chạy Facebook Ads.</p></div></div>
                        <div class="timeline-item md:grid md:grid-cols-2 md:gap-8 mt-8"><div class="md:order-2 md:text-left mb-4 md:mb-0"><p class="font-bold text-lg text-blue-400">03/2025 - Hiện tại</p><p class="text-gray-400">SBS House - TechDictionary</p></div><div class="md:order-1 md:text-right glass-effect p-6 rounded-lg relative"><div class="timeline-dot"></div><h3 class="font-bold text-xl mb-2">SEO Specialist</h3><p class="text-gray-300 text-sm">Quản lý team content SEO, QC bài viết. Nghiên cứu từ khóa, tối ưu On-page và xây dựng backlink chiến lược.</p></div></div>
                        <div class="timeline-item md:grid md:grid-cols-2 md:gap-8 mt-8"><div class="md:text-right mb-4 md:mb-0"><p class="font-bold text-lg text-blue-400">05/2023 - 12/2023</p><p class="text-gray-400">Chiic Digital Agency</p></div><div class="glass-effect p-6 rounded-lg relative"><div class="timeline-dot"></div><h3 class="font-bold text-xl mb-2">Strategic Planner Intern</h3><p class="text-gray-300 text-sm">Hỗ trợ phát triển kế hoạch marketing chiến lược, nghiên cứu thị trường, và hợp tác với các KOLS/KOCs.</p></div></div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Projects Section -->
        <section id="projects" class="py-20 md:py-32 bg-black">
            <div class="container mx-auto px-6">
                <h2 class="section-title text-3xl md:text-4xl font-bold text-center">Các dự án nổi bật</h2>
                <!-- Filter Buttons -->
                <div id="filters" class="flex flex-wrap justify-center gap-2 md:gap-4 my-8">
                    <button class="filter-btn active px-4 py-2 rounded-md font-semibold transition-colors" data-filter="*">Tất cả</button>
                    <button class="filter-btn px-4 py-2 rounded-md font-semibold transition-colors" data-filter=".seo">SEO</button>
                    <button class="filter-btn px-4 py-2 rounded-md font-semibold transition-colors" data-filter=".social">Social Media & Ads</button>
                    <button class="filter-btn px-4 py-2 rounded-md font-semibold transition-colors" data-filter=".content">Content</button>
                    <button class="filter-btn px-4 py-2 rounded-md font-semibold transition-colors" data-filter=".design">UI/UX Design</button>
                    <button class="filter-btn px-4 py-2 rounded-md font-semibold transition-colors" data-filter=".plan">Marketing Plan</button>
                </div>

                <div id="project-grid" class="grid md:grid-cols-2 lg:grid-cols-3 gap-8 mt-12">
                    <!-- Project Items will be inserted here by JS -->
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section id="contact" class="py-20 md:py-32">
            <div class="container mx-auto px-6 text-center">
                <h2 class="section-title text-3xl md:text-4xl font-bold">Kết nối với tôi</h2>
                <p class="text-lg text-gray-300 max-w-2xl mx-auto mt-4 mb-8">
                    Tôi luôn sẵn sàng cho những cơ hội mới và các dự án thú vị. Đừng ngần ngại liên hệ!
                </p>
                <div class="flex justify-center items-center space-x-6 text-3xl">
                    <a href="mailto:khanhvhg2003.forwork@gmail.com" class="hover:text-blue-400 transition-colors"><i class="fas fa-envelope"></i></a>
                    <a href="tel:+84899245418" class="hover:text-blue-400 transition-colors"><i class="fas fa-phone"></i></a>
                    <a href="#" class="hover:text-blue-400 transition-colors"><i class="fab fa-linkedin"></i></a>
                    <a href="https://www.facebook.com/queenbus.com.vn" target="_blank" class="hover:text-blue-400 transition-colors"><i class="fab fa-facebook"></i></a>
                </div>
                 <p class="mt-8 text-gray-400">Email: khanhvhg2003.forwork@gmail.com</p>
                 <p class="text-gray-400">Phone: (+84) 899 245 418</p>
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer class="bg-black py-6">
        <div class="container mx-auto px-6 text-center text-gray-500">
            <p>&copy; 2025 Vân Hữu Gia Khánh. All Rights Reserved.</p>
        </div>
    </footer>

    <script>
        // --- Three.js Background ---
        let scene, camera, renderer, stars, starGeo;

        function init() {
            scene = new THREE.Scene();
            camera = new THREE.PerspectiveCamera(60, window.innerWidth / window.innerHeight, 1, 1000);
            camera.position.z = 1;
            camera.rotation.x = Math.PI / 2;

            renderer = new THREE.WebGLRenderer({
                canvas: document.getElementById("hero-canvas"),
                antialias: true,
            });
            renderer.setSize(window.innerWidth, window.innerHeight);
            renderer.setClearColor(0x0a0a0a, 1);

            starGeo = new THREE.BufferGeometry();
            const starVertices = [];
            for (let i = 0; i < 6000; i++) {
                const x = (Math.random() - 0.5) * 2000;
                const y = (Math.random() - 0.5) * 2000;
                const z = (Math.random() - 0.5) * 2000;
                starVertices.push(x, y, z);
            }
            starGeo.setAttribute('position', new THREE.Float32BufferAttribute(starVertices, 3));

            let sprite = new THREE.TextureLoader().load('https://threejs.org/examples/textures/sprites/disc.png');
            let starMaterial = new THREE.PointsMaterial({
                color: 0xaaaaaa,
                size: 0.7,
                map: sprite,
                transparent: true
            });

            stars = new THREE.Points(starGeo, starMaterial);
            scene.add(stars);

            window.addEventListener("resize", onWindowResize, false);
            animate();
        }

        function onWindowResize() {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        }

        function animate() {
            starGeo.attributes.position.needsUpdate = true;
            stars.rotation.y += 0.0002;
            renderer.render(scene, camera);
            requestAnimationFrame(animate);
        }
        init();


        // --- Mobile menu toggle ---
        const mobileMenuButton = document.getElementById('mobile-menu-button');
        const mobileMenu = document.getElementById('mobile-menu');
        mobileMenuButton.addEventListener('click', () => {
            mobileMenu.classList.toggle('hidden');
        });

        // --- Smooth scrolling ---
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                if(mobileMenu.classList.contains('hidden') === false) {
                   mobileMenu.classList.add('hidden');
                }
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });

        // --- Project Filtering ---
        const projects = [
            { category: 'seo', title: 'SEO Website Queen Bus', desc: 'Tăng trưởng traffic từ 0 lên 2,000/tháng và lợi nhuận tăng 461% trong 2 tháng.', img: 'https://placehold.co/600x400/111827/3b82f6?text=Ảnh+tăng+trưởng+Queen+Bus', url: 'https://queenbus.com.vn/' },
            { category: 'seo', title: 'SEO Website TechDictionary', desc: 'Phục hồi website sau án phạt Google, tăng traffic 19,200% (10 -> 1,900/ngày).', img: 'https://placehold.co/600x400/111827/3b82f6?text=Ảnh+tăng+trưởng+TechDictionary', url: 'https://techdictionary.io/' },
            { category: 'social', title: 'Quản lý Fanpage Queen Bus', desc: 'Xây dựng fanpage đạt 2.1K followers, reach trung bình 1,000/post (organic).', img: 'https://placehold.co/600x400/111827/3b82f6?text=Ảnh+Fanpage+Queen+Bus', url: 'https://www.facebook.com/queenbus.com.vn' },
            { category: 'social', title: 'Facebook Ads Queen Bus', desc: 'Tăng 45% doanh thu dịp lễ 30/4-1/5. Reach 132,000 người trong 8 tháng.', img: 'https://placehold.co/600x400/111827/3b82f6?text=Ảnh+Facebook+Ads', url: 'https://www.facebook.com/queenbus.com.vn' },
            { category: 'social', title: 'Fanpage Heading for the Future', desc: 'Thu về 246 đơn đăng ký. Seeding đạt 48 form (34.5%), email marketing 13 form (9.4%).', img: 'https://placehold.co/600x400/111827/3b82f6?text=Ảnh+dự+án+H4TF', url: '#' },
            { category: 'social', title: 'Fanpage Cửa hàng Mẹ & Bé', desc: 'Quản lý và sáng tạo nội dung cho fanpage sản phẩm mẹ và bé.', img: 'https://placehold.co/600x400/111827/3b82f6?text=Ảnh+Fanpage+Vian+Kids', url: '#' },
            { category: 'content', title: 'Content SEO Lalla Nail', desc: 'Viết bài chuẩn SEO cho website về dịch vụ làm đẹp, nail tại Đà Nẵng.', img: 'https://placehold.co/600x400/111827/3b82f6?text=Ảnh+Website+Lalla+Nail', url: 'https://lallanaildanang.com/' },
            { category: 'content', title: 'Content SEO MOR Software', desc: 'Viết các bài viết chuyên sâu (khoảng 2000 từ) về lĩnh vực công nghệ phần mềm.', img: 'https://placehold.co/600x400/111827/3b82f6?text=Ảnh+bài+viết+MOR+Software', url: '#' },
            { category: 'design', title: 'Thiết kế UX/UI (Cá nhân)', desc: 'Dự án cá nhân thiết kế giao diện người dùng và trải nghiệm người dùng bằng Figma.', img: 'https://placehold.co/600x400/111827/3b82f6?text=Ảnh+thiết+kế+Figma', url: '#' },
            { category: 'plan', title: 'Kế hoạch Marketing H4TF', desc: 'Thực hiện nghiên cứu thị trường và đóng góp vào kế hoạch IMC cho dự án.', img: 'https://placehold.co/600x400/111827/3b82f6?text=Ảnh+kế+hoạch+H4TF', url: '#' },
            { category: 'plan', title: 'Kế hoạch Marketing TEDx', desc: 'Xây dựng chiến lược marketing toàn diện cho sự kiện TEDxFPTUniversity Danang.', img: 'https://placehold.co/600x400/111827/3b82f6?text=Ảnh+kế+hoạch+TEDx', url: '#' },
            { category: 'plan', title: 'Strategic Planning (Agency)', desc: 'Hỗ trợ xây dựng kế hoạch cho các đối tác khách sạn lớn như A La Carte, Paracel.', img: 'https://placehold.co/600x400/111827/3b82f6?text=Ảnh+kế+hoạch+Agency', url: '#' },
        ];

        const projectGrid = document.getElementById('project-grid');
        const filters = document.getElementById('filters');

        function populateProjects(filter = '*') {
            projectGrid.innerHTML = '';
            const filteredProjects = filter === '*' ? projects : projects.filter(p => p.category === filter.substring(1));
            
            filteredProjects.forEach(p => {
                const projectEl = document.createElement('div');
                projectEl.className = `project-card glass-effect rounded-lg overflow-hidden ${p.category}`;
                projectEl.innerHTML = `
                    <img src="${p.img}" alt="${p.title}" class="w-full h-full">
                    <div class="p-6">
                        <h3 class="font-bold text-xl mb-2">${p.title}</h3>
                        <p class="text-gray-400 mb-4 text-sm">${p.desc}</p>
                        <a href="${p.url}" target="_blank" class="text-blue-400 font-semibold hover:underline">Xem chi tiết <i class="fas fa-arrow-right ml-1"></i></a>
                    </div>
                `;
                projectGrid.appendChild(projectEl);
            });
        }
        
        filters.addEventListener('click', (e) => {
            if (e.target.tagName === 'BUTTON') {
                document.querySelector('.filter-btn.active').classList.remove('active');
                e.target.classList.add('active');
                const filterValue = e.target.getAttribute('data-filter');
                populateProjects(filterValue);
            }
        });

        populateProjects();

    </script>
</body>
</html>
