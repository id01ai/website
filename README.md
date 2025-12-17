<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>id01 ai | Corporate Intelligence</title>
    
    <!-- Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400&display=swap" rel="stylesheet">
    
    <!-- Tailwind CSS (via CDN for standalone usage) -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>

    <!-- Custom Tailwind Config for Animations -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        mono: ['JetBrains Mono', 'monospace'],
                    },
                    animation: {
                        'spin-slow': 'spin 12s linear infinite',
                        'spin-reverse': 'spin 15s linear infinite reverse',
                        fadeIn: 'fadeIn 0.5s ease-out forwards',
                        fadeInUp: 'fadeInUp 0.8s ease-out forwards',
                        pulse: 'pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite',
                    },
                    keyframes: {
                        fadeIn: {
                            '0%': { opacity: '0' },
                            '100%': { opacity: '1' },
                        },
                        fadeInUp: {
                            '0%': { opacity: '0', transform: 'translateY(20px)' },
                            '100%': { opacity: '1', transform: 'translateY(0)' },
                        }
                    }
                }
            }
        }
    </script>

    <style>
        html {
            scroll-behavior: smooth;
        }
        body {
            background-color: #050507;
            color: #e2e8f0; /* slate-200 */
        }
        ::selection {
            background-color: #334155; /* slate-700 */
            color: white;
        }
        /* Utility to hide scrollbar but keep functionality */
        .no-scrollbar::-webkit-scrollbar {
            display: none;
        }
        .no-scrollbar {
            -ms-overflow-style: none;
            scrollbar-width: none;
        }
    </style>
</head>
<body class="min-h-screen overflow-x-hidden antialiased">

    <!-- Canvas Background -->
    <canvas id="neural-bg" class="fixed top-0 left-0 w-full h-full pointer-events-none z-0 opacity-40"></canvas>

    <!-- Navigation -->
    <nav id="navbar" class="fixed w-full z-50 transition-all duration-500 py-6">
        <div class="max-w-7xl mx-auto px-6 flex justify-between items-center">
            <!-- Logo -->
            <div onclick="navigateToHome()" class="flex items-center gap-3 group cursor-pointer">
                <i data-lucide="hexagon" class="text-white fill-white/10 group-hover:rotate-90 transition-transform duration-700 w-6 h-6" stroke-width="1"></i>
                <span class="font-medium tracking-tight text-white text-lg">id01 ai</span>
            </div>

            <!-- Desktop Nav -->
            <div id="desktop-nav" class="hidden md:flex items-center gap-8 text-sm font-medium text-slate-400">
                <a href="#methodology" class="hover:text-white transition-colors">Methodology</a>
                <a href="#solutions" class="hover:text-white transition-colors">Solutions</a>
            </div>

            <!-- Mobile Menu Button -->
            <div class="md:hidden text-white cursor-pointer" onclick="toggleMenu()">
                <i id="menu-icon" data-lucide="menu" class="w-6 h-6"></i>
                <i id="close-icon" data-lucide="x" class="w-6 h-6 hidden"></i>
            </div>
        </div>
    </nav>

    <!-- Mobile Menu Overlay -->
    <div id="mobile-menu-overlay" class="fixed inset-0 z-40 bg-black hidden flex-col items-center justify-center space-y-8 animate-fadeIn">
        <button onclick="navigateToHomeMobile()" class="text-2xl text-slate-300 hover:text-white">Home</button>
        <div id="mobile-home-links" class="flex flex-col items-center space-y-8">
            <a href="#methodology" onclick="toggleMenu()" class="text-2xl text-slate-300 hover:text-white">Methodology</a>
            <a href="#solutions" onclick="toggleMenu()" class="text-2xl text-slate-300 hover:text-white">Solutions</a>
            <a href="#contact" onclick="toggleMenu()" class="text-2xl text-white font-bold">Inquire</a>
        </div>
        <button onclick="navigateToLegalMobile()" class="text-sm text-slate-500 hover:text-white mt-8">Legal & Compliance</button>
    </div>

    <!-- MAIN VIEW CONTAINER -->
    <main id="main-view">
        
        <!-- Hero Section -->
        <header class="relative z-10 min-h-screen flex items-center pt-20">
            <div class="max-w-7xl mx-auto px-6 w-full">
                <div class="max-w-4xl">
                    <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-white/5 border border-white/10 text-xs tracking-widest uppercase text-slate-400 mb-8 animate-fadeInUp">
                        <span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span>
                        System Operational
                    </div>
                    <h1 class="text-5xl md:text-7xl lg:text-8xl font-bold text-white tracking-tight leading-[1.1] mb-8 animate-fadeInUp" style="animation-delay: 0.1s;">
                        Architecting <br />
                        <span class="text-transparent bg-clip-text bg-gradient-to-r from-slate-200 to-slate-600">
                            Corporate Minds.
                        </span>
                    </h1>
                    <p class="text-lg md:text-xl text-slate-400 max-w-2xl leading-relaxed mb-12 animate-fadeInUp" style="animation-delay: 0.2s;">
                        We transform static professional research into dynamic, sovereign AI systems. 
                        The ultimate competitive advantage for the modern enterprise.
                    </p>
                    
                    <div class="flex flex-col sm:flex-row gap-4 animate-fadeInUp" style="animation-delay: 0.3s;">
                        <a href="#methodology" class="px-8 py-4 bg-white text-black font-semibold rounded-sm hover:bg-slate-200 transition-colors flex items-center justify-center gap-2 group">
                            Begin Transformation
                            <i data-lucide="arrow-right" class="w-5 h-5 group-hover:translate-x-1 transition-transform"></i>
                        </a>
                    </div>
                </div>
            </div>
            
            <!-- Scroll Indicator -->
            <div class="absolute bottom-10 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 opacity-50 animate-bounce">
                <span class="text-[10px] uppercase tracking-widest">Scroll</span>
                <div class="w-[1px] h-12 bg-gradient-to-b from-white to-transparent"></div>
            </div>
        </header>

        <!-- Methodology Section -->
        <section id="methodology" class="relative z-10 py-32 bg-[#050507]">
            <div class="max-w-7xl mx-auto px-6">
                <div class="grid md:grid-cols-2 gap-20 items-center">
                    <div>
                        <h2 class="text-3xl md:text-5xl font-bold text-white mb-6 leading-tight">
                            Your knowledge is dormant. <br />
                            <span class="text-slate-500">We wake it up.</span>
                        </h2>
                        <div class="space-y-8 mt-12">
                            <div class="flex gap-4">
                                <div class="w-12 h-12 rounded-sm bg-white/5 border border-white/10 flex items-center justify-center flex-shrink-0">
                                    <i data-lucide="file-text" class="text-slate-300 w-6 h-6"></i>
                                </div>
                                <div>
                                    <h3 class="text-xl font-semibold text-white mb-2">The Static Archive</h3>
                                    <p class="text-slate-400 leading-relaxed">
                                        Millions of dollars spent on research, PDFs, and reports that sit in folders, disconnected and unqueried.
                                    </p>
                                </div>
                            </div>
                            <div class="w-[1px] h-8 bg-white/10 ml-6"></div>
                            <div class="flex gap-4">
                                <div class="w-12 h-12 rounded-sm bg-blue-500/10 border border-blue-500/20 flex items-center justify-center flex-shrink-0">
                                    <i data-lucide="cpu" class="text-blue-400 w-6 h-6"></i>
                                </div>
                                <div>
                                    <h3 class="text-xl font-semibold text-white mb-2">The Active Intelligence</h3>
                                    <p class="text-slate-400 leading-relaxed">
                                        We ingest your proprietary corpus into a bespoke, private Large Language Model. It knows what you know—instantly.
                                    </p>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Visual Abstract Terminal -->
                    <div class="relative h-[500px] w-full bg-gradient-to-br from-slate-900 to-black rounded-sm border border-white/10 p-1 overflow-hidden group">
                        <!-- Pseudo texture -->
                        <div class="absolute inset-0 bg-white opacity-5" style="background-image: url('data:image/svg+xml,%3Csvg width=\'20\' height=\'20\' viewBox=\'0 0 20 20\' xmlns=\'http://www.w3.org/2000/svg\'%3E%3Cpath d=\'M1 1h2v2H1V1zm4 0h2v2H5V1zm4 0h2v2H9V1z\' fill=\'%23ffffff\' fill-opacity=\'0.4\' fill-rule=\'evenodd\'/%3E%3C/svg%3E');"></div>
                        <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-64 h-64 bg-blue-500/20 rounded-full blur-[100px] group-hover:bg-blue-500/30 transition-all duration-700"></div>
                        
                        <!-- Terminal Code Effect -->
                        <div class="relative z-10 h-full w-full bg-black/50 backdrop-blur-sm p-8 font-mono text-xs md:text-sm leading-6 text-slate-400 overflow-hidden">
                            <div class="flex gap-2 mb-4">
                                <div class="w-3 h-3 rounded-full bg-red-500/50"></div>
                                <div class="w-3 h-3 rounded-full bg-yellow-500/50"></div>
                                <div class="w-3 h-3 rounded-full bg-green-500/50"></div>
                            </div>
                            <p><span class="text-green-400">root@id01-core:~$</span> ingest --source=/secure/research_archive</p>
                            <p class="text-slate-500">[STATUS] Analyzing 45,000 documents...</p>
                            <p class="text-slate-500">[STATUS] Extracting semantic vectors...</p>
                            <p class="text-slate-500">[STATUS] Constructing knowledge graph...</p>
                            <br />
                            <p><span class="text-green-400">root@id01-core:~$</span> train --model=proprietary_v4</p>
                            <p class="text-slate-500">[PROCESS] Training initiated on NVIDIA H100 Cluster...</p>
                            <p class="text-blue-400">[INFO] Data remains fully sovereign. No external API calls.</p>
                            <br />
                            <div class="inline-block px-2 py-1 bg-white/10 text-white rounded-sm animate-pulse">
                                System Ready.
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Solutions Section -->
        <section id="solutions" class="relative z-10 py-32 bg-[#08080a]">
            <div class="max-w-7xl mx-auto px-6">
                <div class="mb-20">
                    <h2 class="text-4xl font-bold text-white mb-6">Built for the Enterprise.</h2>
                    <div class="w-20 h-1 bg-blue-600"></div>
                </div>

                <div class="grid md:grid-cols-3 gap-8">
                    <!-- Card 1 -->
                    <div class="group p-8 bg-white/5 border border-white/5 hover:border-white/20 transition-all duration-300 rounded-sm hover:-translate-y-2">
                        <i data-lucide="lock" class="text-slate-300 mb-6 w-8 h-8"></i>
                        <h3 class="text-xl font-bold text-white mb-4">Total Sovereignty</h3>
                        <p class="text-slate-400 text-sm leading-relaxed">
                            Your data never leaves your infrastructure. We deploy models on-premise or in your private VPC. Zero leakage. Zero external training.
                        </p>
                    </div>

                    <!-- Card 2 -->
                    <div class="group p-8 bg-white/5 border border-white/5 hover:border-white/20 transition-all duration-300 rounded-sm hover:-translate-y-2">
                        <i data-lucide="activity" class="text-slate-300 mb-6 w-8 h-8"></i>
                        <h3 class="text-xl font-bold text-white mb-4">Real-Time Synthesis</h3>
                        <p class="text-slate-400 text-sm leading-relaxed">
                            Our systems don't just search; they synthesize. Turn hours of manual cross-referencing into seconds of high-level analysis.
                        </p>
                    </div>

                    <!-- Card 3 -->
                    <div class="group p-8 bg-white/5 border border-white/5 hover:border-white/20 transition-all duration-300 rounded-sm hover:-translate-y-2">
                        <i data-lucide="terminal" class="text-slate-300 mb-6 w-8 h-8"></i>
                        <h3 class="text-xl font-bold text-white mb-4">Bespoke Engineering</h3>
                        <p class="text-slate-400 text-sm leading-relaxed">
                            We fine-tune base models (Llama 3, Mistral, Falcon) specifically for your taxonomy.
                        </p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section id="contact" class="relative z-10 py-40 flex items-center justify-center overflow-hidden">
            <!-- Background Elements -->
            <div class="absolute inset-0 bg-gradient-to-t from-blue-900/10 to-transparent"></div>
            <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[600px] border border-white/5 rounded-full animate-spin-slow opacity-20"></div>
            <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[400px] h-[400px] border border-white/10 rounded-full animate-spin-reverse opacity-20"></div>

            <div class="relative z-20 text-center max-w-3xl px-6">
                <h2 class="text-5xl md:text-7xl font-bold text-white mb-8 tracking-tight">
                    Ready to ascend?
                </h2>
                <p class="text-xl text-slate-400 mb-12">
                    We accept a limited number of enterprise partners per quarter to ensure white-glove deployment standards.
                </p>
                <div class="flex flex-col md:flex-row items-center justify-center gap-6">
                    <a href="mailto:info@id01.ai" class="w-full md:w-auto px-10 py-5 bg-white text-black font-bold text-lg rounded-sm hover:scale-105 transition-transform duration-300 inline-block">
                        Request Private Access
                    </a>
                </div>
                <p class="mt-8 text-xs text-slate-600 uppercase tracking-widest">
                    Minimum Engagement: $50k USD
                </p>
            </div>
        </section>
    </main>

    <!-- LEGAL VIEW CONTAINER (Hidden by default) -->
    <div id="legal-view" class="hidden min-h-screen pt-32 pb-20 px-6 animate-fadeIn relative z-20">
        <div class="max-w-3xl mx-auto">
            <button onclick="navigateToHome()" class="group flex items-center gap-2 text-white/50 hover:text-white mb-12 transition-colors">
                <i data-lucide="chevron-left" class="w-4 h-4 group-hover:-translate-x-1 transition-transform"></i>
                Return to Operational View
            </button>

            <h1 class="text-4xl md:text-5xl font-bold text-white mb-12">Legal & Compliance</h1>

            <div class="space-y-16">
                <section>
                    <h2 class="text-2xl font-bold text-white mb-6">Terms of Service</h2>
                    <div class="space-y-4 text-sm leading-relaxed text-slate-400">
                        <p><strong>1. Engagement & Sovereignty</strong><br/>
                        Engagement with id01 ai ("The Service") implies a strict adherence to data sovereignty protocols. All generated models, weights, and vectors derived from Client Data remain the sole intellectual property of the Client. id01 ai retains no rights to the synthesized intelligence produced within your private instance.</p>
                        
                        <p><strong>2. Liability & Deployment</strong><br/>
                        While The Service utilizes state-of-the-art probabilistic models, output accuracy cannot be mathematically guaranteed. id01 ai provides the architecture for intelligence but indemnifies itself against operational decisions made solely on the basis of AI-generated synthesis. Enterprise partners assume full responsibility for deployment outcomes.</p>
                    </div>
                </section>

                <div class="w-full h-[1px] bg-white/10"></div>

                <section>
                    <h2 class="text-2xl font-bold text-white mb-6">Privacy Policy</h2>
                    <div class="space-y-4 text-sm leading-relaxed text-slate-400">
                        <p><strong>1. Data Ingestion</strong><br/>
                        We operate on a "Zero-Retention" architecture for training data. Documents uploaded for ingestion are processed in-memory or within your designated VPC (Virtual Private Cloud). Once vectorization is complete, raw source files are expunged from the processing layer.</p>
                        
                        <p><strong>2. No External Learning</strong><br/>
                        Unlike public models, your interactions do not inform a global base model. Your system's learning is frozen to your environment. We do not aggregate cross-client insights.</p>
                        
                        <p><strong>3. Contact Information</strong><br/>
                        For legal inquiries or data controller requests, contact:<br/>
                        <a href="mailto:info@id01.ai" class="text-white hover:underline">info@id01.ai</a></p>
                    </div>
                </section>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer class="relative z-10 bg-black border-t border-white/10 py-16 text-sm">
        <div class="max-w-7xl mx-auto px-6">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-12 mb-16">
                <div class="col-span-1 md:col-span-2">
                    <div class="flex items-center gap-3 mb-6">
                        <i data-lucide="hexagon" class="text-slate-400 fill-slate-400/10 w-5 h-5" stroke-width="1"></i>
                        <span class="font-bold text-white text-lg">id01 ai</span>
                    </div>
                    <p class="text-slate-500 max-w-sm">
                        Hong Kong <br /><br />
                        Pioneering the intersection of corporate research and private artificial intelligence.
                    </p>
                </div>
                
                <div>
                    <h4 class="text-white font-bold mb-6">Company</h4>
                    <ul class="space-y-4 text-slate-500">
                        <li onclick="navigateToLegal()" class="hover:text-white cursor-pointer transition-colors">Legal</li>
                    </ul>
                </div>

                <div>
                    <h4 class="text-white font-bold mb-6">Connect</h4>
                    <ul class="space-y-4 text-slate-500">
                        <li class="hover:text-white cursor-pointer transition-colors">
                            <a href="mailto:info@id01.ai">info@id01.ai</a>
                        </li>
                    </ul>
                </div>
            </div>

            <div class="flex flex-col md:flex-row justify-between items-center pt-8 border-t border-white/10">
                <p class="text-slate-600">© 2024 id01 ai. All rights reserved.</p>
                <div class="flex gap-6 mt-4 md:mt-0">
                    <button onclick="navigateToLegal()" class="text-slate-600 hover:text-white cursor-pointer transition-colors">Privacy Policy</button>
                    <button onclick="navigateToLegal()" class="text-slate-600 hover:text-white cursor-pointer transition-colors">Terms of Service</button>
                </div>
            </div>
        </div>
    </footer>

    <!-- LOGIC SCRIPT -->
    <script>
        // Initialize Icons
        lucide.createIcons();

        // Canvas / Neural Network Animation
        const canvas = document.getElementById('neural-bg');
        const ctx = canvas.getContext('2d');
        let width = window.innerWidth;
        let height = window.innerHeight;
        
        canvas.width = width;
        canvas.height = height;

        const particles = [];
        const particleCount = width > 768 ? 60 : 30;

        class Particle {
            constructor() {
                this.x = Math.random() * width;
                this.y = Math.random() * height;
                this.vx = (Math.random() - 0.5) * 0.2;
                this.vy = (Math.random() - 0.5) * 0.2;
                this.size = Math.random() * 2 + 1;
            }

            update() {
                this.x += this.vx;
                this.y += this.vy;

                if (this.x < 0 || this.x > width) this.vx *= -1;
                if (this.y < 0 || this.y > height) this.vy *= -1;
            }

            draw() {
                ctx.fillStyle = 'rgba(100, 116, 139, 0.5)';
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }

        for (let i = 0; i < particleCount; i++) {
            particles.push(new Particle());
        }

        function animate() {
            ctx.clearRect(0, 0, width, height);
            
            particles.forEach((p, index) => {
                p.update();
                p.draw();

                for (let j = index + 1; j < particles.length; j++) {
                    const p2 = particles[j];
                    const dx = p.x - p2.x;
                    const dy = p.y - p2.y;
                    const distance = Math.sqrt(dx * dx + dy * dy);

                    if (distance < 150) {
                        ctx.beginPath();
                        ctx.strokeStyle = `rgba(148, 163, 184, ${0.15 - distance / 1000})`;
                        ctx.lineWidth = 1;
                        ctx.moveTo(p.x, p.y);
                        ctx.lineTo(p2.x, p2.y);
                        ctx.stroke();
                    }
                }
            });

            requestAnimationFrame(animate);
        }

        animate();

        window.addEventListener('resize', () => {
            width = window.innerWidth;
            height = window.innerHeight;
            canvas.width = width;
            canvas.height = height;
        });

        // UI Logic
        const navbar = document.getElementById('navbar');
        const mobileMenu = document.getElementById('mobile-menu-overlay');
        const menuIcon = document.getElementById('menu-icon');
        const closeIcon = document.getElementById('close-icon');
        const mainView = document.getElementById('main-view');
        const legalView = document.getElementById('legal-view');
        const desktopNav = document.getElementById('desktop-nav');
        const mobileHomeLinks = document.getElementById('mobile-home-links');

        // Scroll Handler
        window.addEventListener('scroll', () => {
            if (window.scrollY > 50) {
                navbar.classList.add('bg-[#050507]/90', 'backdrop-blur-md', 'border-b', 'border-white/5');
                navbar.classList.remove('py-6');
                navbar.classList.add('py-4');
            } else {
                navbar.classList.remove('bg-[#050507]/90', 'backdrop-blur-md', 'border-b', 'border-white/5');
                navbar.classList.remove('py-4');
                navbar.classList.add('py-6');
            }
        });

        // Menu Toggle
        function toggleMenu() {
            const isHidden = mobileMenu.classList.contains('hidden');
            if (isHidden) {
                mobileMenu.classList.remove('hidden');
                mobileMenu.classList.add('flex');
                menuIcon.classList.add('hidden');
                closeIcon.classList.remove('hidden');
                document.body.style.overflow = 'hidden';
            } else {
                mobileMenu.classList.add('hidden');
                mobileMenu.classList.remove('flex');
                menuIcon.classList.remove('hidden');
                closeIcon.classList.add('hidden');
                document.body.style.overflow = 'auto';
            }
        }

        // Navigation Logic
        function navigateToHome() {
            mainView.classList.remove('hidden');
            legalView.classList.add('hidden');
            desktopNav.classList.remove('hidden');
            window.scrollTo(0, 0);
        }

        function navigateToLegal() {
            mainView.classList.add('hidden');
            legalView.classList.remove('hidden');
            desktopNav.classList.add('hidden'); // Hide nav links on legal page
            window.scrollTo(0, 0);
        }

        function navigateToHomeMobile() {
            navigateToHome();
            toggleMenu();
        }

        function navigateToLegalMobile() {
            navigateToLegal();
            toggleMenu();
        }
    </script>
</body>
</html>
