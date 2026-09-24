<!DOCTYPE html>
<html lang="pt-BR" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ofertas Especiais - Mercado Livre & Shopee</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: { sans: ['Inter', 'sans-serif'] },
                    colors: {
                        mercadolivre: { 400: '#ffe600', 500: '#ffd100', 600: '#e6bd00', text: '#2d3277' },
                        shopee: { 500: '#ee4d2d', 600: '#d73211' }
                    }
                }
            }
        }
    </script>
    <style>
        .crisp-img {
            image-rendering: -webkit-optimize-contrast;
            image-rendering: crisp-edges;
            object-fit: cover;
        }
    </style>
</head>
<body class="bg-slate-950 text-slate-100 font-sans antialiased min-h-screen pb-24 selection:bg-amber-500 selection:text-slate-950">

    <!-- Barra Superior do Administrador (Invisível por Padrão) -->
    <div id="adminBar" class="hidden sticky top-0 z-50 bg-emerald-950/90 border-b border-emerald-600/40 py-2 px-4 shadow-xl backdrop-blur-md">
        <div class="max-w-7xl mx-auto flex items-center justify-between gap-3">
            <div class="flex items-center gap-2 text-emerald-300 text-xs md:text-sm font-bold">
                <i class="fa-solid fa-user-shield text-emerald-400"></i>
                <span>Modo Administrador Ativo</span>
            </div>
            <div class="flex items-center gap-2">
                <button onclick="openAddProductModal()" class="px-3 py-1 rounded-lg bg-emerald-500 hover:bg-emerald-400 text-slate-950 font-black text-xs transition flex items-center gap-1.5 shadow">
                    <i class="fa-solid fa-plus-circle"></i>
                    <span>+ Adicionar Produto</span>
                </button>
                <button onclick="logoutAdmin()" class="px-2.5 py-1 rounded-lg bg-slate-900 hover:bg-slate-800 text-slate-300 text-xs font-semibold border border-slate-700 transition">
                    <i class="fa-solid fa-right-from-bracket"></i> Sair
                </button>
            </div>
        </div>
    </div>

    <!-- Banner de Urgência -->
    <div class="bg-gradient-to-r from-amber-600 via-amber-500 to-yellow-500 text-slate-950 font-extrabold text-center py-2 px-4 text-xs md:text-sm tracking-wide shadow-md">
        <i class="fa-solid fa-bolt mr-1"></i>
        DESCONTO EXCLUSIVO DE AFILIADO - FRETE GRÁTIS EM PRODUTOS SELECIONADOS NA SHOPEE E MERCADO LIVRE!
        <span class="ml-2 bg-slate-950 text-amber-400 px-2 py-0.5 rounded font-mono text-xs" id="countdownTimer">14:59</span>
    </div>

    <!-- Hero Section: Produto Destaque -->
    <header class="relative overflow-hidden py-10 md:py-16 px-4 border-b border-slate-800/80 bg-gradient-to-b from-slate-900 via-slate-950 to-slate-950">
        <div class="max-w-6xl mx-auto">
            <div class="text-center mb-8">
                <span class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-amber-500/10 border border-amber-500/30 text-amber-400 text-xs font-bold uppercase tracking-wider mb-4">
                    <i class="fa-solid fa-fire text-amber-400"></i> Produto Campeão em Vendas
                </span>
                <h1 class="text-2xl md:text-5xl font-black text-white tracking-tight mb-3 leading-tight max-w-4xl mx-auto" id="heroTitle">
                    Fone De Ouvido Gamer Kapbom KA-999 Bluetooth 5.0 In-Ear Preto
                </h1>
                <p class="text-slate-400 text-sm md:text-base max-w-2xl mx-auto">
                    Alta fidelidade sonora, baixa latência para jogos, microfone HD integrado e bateria de longa duração com case de carregamento.
                </p>
            </div>

            <!-- Card Destaque -->
            <div class="bg-slate-900/90 border border-slate-800 rounded-3xl p-6 md:p-8 shadow-2xl backdrop-blur-md max-w-4xl mx-auto">
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
                    <div class="relative bg-slate-950 rounded-2xl p-4 border border-slate-800 flex items-center justify-center overflow-hidden group">
                        <span class="absolute top-3 left-3 z-10 bg-red-600 text-white font-extrabold text-xs px-2.5 py-1 rounded-md uppercase tracking-wider" id="heroBadge">
                            OFERTA 42% OFF
                        </span>
                        <img id="heroProductImg" src="https://images.unsplash.com/photo-1590658268037-6bf12165a8df?auto=format&fit=crop&w=1000&q=95" alt="Produto Físico Afiliado" class="w-full h-64 md:h-80 object-contain crisp-img transition duration-300 group-hover:scale-105">
                    </div>

                    <div class="flex flex-col justify-between space-y-5">
                        <div class="flex items-center gap-2">
                            <div class="flex text-amber-400 text-xs">
                                <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i>
                            </div>
                            <span class="text-xs text-slate-400 font-semibold">(4.9/5 - 1.240 avaliações verificadas)</span>
                        </div>

                        <div class="bg-slate-950/80 p-4 rounded-xl border border-slate-800/80">
                            <span class="text-xs text-slate-500 line-through block mb-0.5" id="heroOldPrice">De R$ 129,90</span>
                            <div class="flex items-baseline gap-3">
                                <span class="text-3xl md:text-4xl font-black text-emerald-400" id="heroPrice">R$ 74,90</span>
                                <span class="text-xs bg-emerald-500/10 text-emerald-400 border border-emerald-500/30 px-2 py-0.5 rounded font-bold">Menor Preço do Mês</span>
                            </div>
                        </div>

                        <ul class="space-y-2 text-xs text-slate-300">
                            <li class="flex items-center gap-2"><i class="fa-solid fa-circle-check text-emerald-400"></i> Conexão Bluetooth rápida</li>
                            <li class="flex items-center gap-2"><i class="fa-solid fa-circle-check text-emerald-400"></i> Baixa latência para jogos</li>
                            <li class="flex items-center gap-2"><i class="fa-solid fa-circle-check text-emerald-400"></i> Case de carregamento com LED</li>
                        </ul>

                        <div class="space-y-2.5 pt-2">
                            <a id="heroAffiliateBtn" href="https://meli.la/2ajKx5K" target="_blank" rel="noopener noreferrer" class="w-full py-4 bg-mercadolivre-400 hover:bg-mercadolivre-500 text-slate-950 font-black rounded-xl text-sm md:text-base transition shadow-lg flex items-center justify-center gap-2 uppercase tracking-wide">
                                <i class="fa-solid fa-cart-shopping text-slate-950"></i>
                                <span>Comprar no Mercado Livre</span>
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <!-- Vitrine de Outros Produtos -->
    <section class="py-16 px-4">
        <div class="max-w-6xl mx-auto">
            <div class="text-center mb-12">
                <span class="text-amber-400 font-bold text-xs uppercase tracking-widest block mb-2">Mais Achadinhos e Ofertas</span>
                <h2 class="text-2xl md:text-4xl font-extrabold text-white">Confira Outros Produtos Recomendados</h2>
            </div>
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6" id="productsGrid"></div>
        </div>
    </section>

    <!-- Rodapé com Acesso Restrito -->
    <footer class="py-8 bg-slate-950 border-t border-slate-900 text-center text-xs text-slate-600">
        <p>© 2026 Vitrine de Ofertas de Afiliados. Todos os direitos reservados.</p>
        <button onclick="openLoginModal()" class="mt-3 text-slate-700 hover:text-slate-500 text-[11px] underline flex items-center gap-1 mx-auto">
            <i class="fa-solid fa-lock"></i> Área do Administrador
        </button>
    </footer>

    <!-- Modal de Login Admin -->
    <div id="loginModal" class="fixed inset-0 bg-slate-950/90 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="bg-slate-900 border border-slate-800 rounded-2xl w-full max-w-xs p-6 shadow-2xl relative text-center">
            <h3 class="font-bold text-white text-base mb-4"><i class="fa-solid fa-shield-halved text-amber-400 mr-1"></i> Acesso Restrito</h3>
            <form onsubmit="handleLogin(event)" class="space-y-3">
                <input type="password" id="adminPasswordInput" placeholder="Senha do Administrador" required class="w-full bg-slate-950 border border-slate-800 rounded-xl px-3 py-2 text-xs text-white text-center focus:border-amber-500 focus:outline-none">
                <div class="flex gap-2">
                    <button type="button" onclick="closeLoginModal()" class="w-1/2 py-2 rounded-xl border border-slate-800 text-slate-400 text-xs">Cancelar</button>
                    <button type="submit" class="w-1/2 py-2 rounded-xl bg-amber-500 hover:bg-amber-400 text-slate-950 font-bold text-xs">Entrar</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Modal: Adicionar Produto (Apenas Admin) -->
    <div id="productModal" class="fixed inset-0 bg-slate-950/80 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="bg-slate-900 border border-slate-800 rounded-2xl w-full max-w-lg p-6 shadow-2xl relative max-h-[90vh] overflow-y-auto">
            <div class="flex items-center justify-between pb-4 border-b border-slate-800 mb-5">
                <span class="text-amber-400 font-bold text-base"><i class="fa-solid fa-plus-circle mr-1"></i> Cadastrar Novo Produto</span>
                <button onclick="closeModal()" class="text-slate-400 hover:text-white text-lg"><i class="fa-solid fa-xmark"></i></button>
            </div>

            <form id="productForm" onsubmit="handleProductSubmit(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold text-slate-300 uppercase mb-1">Nome do Produto *</label>
                    <input type="text" id="pName" required placeholder="Ex: Mouse Gamer RGB" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-3.5 py-2 text-xs text-slate-100 focus:border-amber-500 focus:outline-none">
                </div>
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-semibold text-slate-300 uppercase mb-1">Preço Atual (R$) *</label>
                        <input type="number" step="0.01" id="pPrice" required placeholder="49.90" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-3.5 py-2 text-xs text-slate-100 focus:border-amber-500 focus:outline-none">
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-slate-300 uppercase mb-1">Preço Antigo (R$)</label>
                        <input type="number" step="0.01" id="pOldPrice" placeholder="89.90" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-3.5 py-2 text-xs text-slate-100 focus:border-amber-500 focus:outline-none">
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-300 uppercase mb-1">Plataforma *</label>
                    <select id="pPlatform" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-3.5 py-2 text-xs text-slate-100 focus:border-amber-500 focus:outline-none">
                        <option value="mercadolivre">Mercado Livre</option>
                        <option value="shopee">Shopee</option>
                    </select>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-300 uppercase mb-1">Link de Afiliado *</label>
                    <input type="url" id="pAffiliateLink" required placeholder="https://..." class="w-full bg-slate-950 border border-slate-800 rounded-xl px-3.5 py-2 text-xs text-slate-100 focus:border-amber-500 focus:outline-none">
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-300 uppercase mb-1">URL da Imagem *</label>
                    <input type="url" id="pImg" required placeholder="https://..." class="w-full bg-slate-950 border border-slate-800 rounded-xl px-3.5 py-2 text-xs text-slate-100 focus:border-amber-500 focus:outline-none">
                </div>
                <div class="pt-3 flex gap-3">
                    <button type="button" onclick="closeModal()" class="w-1/2 py-2.5 rounded-xl border border-slate-800 text-slate-300 text-xs">Cancelar</button>
                    <button type="submit" class="w-1/2 py-2.5 rounded-xl bg-emerald-600 hover:bg-emerald-500 text-white text-xs font-bold">Salvar Produto</button>
                </div>
            </form>
        </div>
    </div>

    <script>
        const ADMIN_PASSWORD = "1234"; // Altere aqui a sua senha
        let isAdminLoggedIn = false;

        let affiliateProducts = JSON.parse(localStorage.getItem('my_affiliate_products')) || [
            { id: '1', name: 'Fone Headset Bluetooth Over-Ear Cowin', price: 29.99, oldPrice: 39.90, platform: 'mercadolivre', affiliateLink: 'https://meli.la/2FLn4WD', img: 'https://images.unsplash.com/photo-1505740420928-5e560c06d30e?auto=format&fit=crop&w=800&q=95' },
            { id: '2', name: 'Mouse Gamer RGB 7200 DPI', price: 49.90, oldPrice: 89.90, platform: 'shopee', affiliateLink: 'https://shopee.com.br', img: 'https://images.unsplash.com/photo-1615663245857-ac93bb7c39e7?auto=format&fit=crop&w=800&q=95' }
        ];

        window.onload = function() {
            renderGridProducts();
            startCountdown();
            // Atalho de teclado: Ctrl + Shift + A
            document.addEventListener('keydown', (e) => {
                if (e.ctrlKey && e.shiftKey && e.key === 'A') openLoginModal();
            });
        };

        function openLoginModal() { document.getElementById('loginModal').classList.remove('hidden'); }
        function closeLoginModal() { document.getElementById('loginModal').classList.add('hidden'); }

        function handleLogin(e) {
            e.preventDefault();
            const pass = document.getElementById('adminPasswordInput').value;
            if (pass === ADMIN_PASSWORD) {
                isAdminLoggedIn = true;
                document.getElementById('adminBar').classList.remove('hidden');
                closeLoginModal();
                renderGridProducts();
            } else {
                alert('Senha incorreta!');
            }
        }

        function logoutAdmin() {
            isAdminLoggedIn = false;
            document.getElementById('adminBar').classList.add('hidden');
            renderGridProducts();
        }

        function renderGridProducts() {
            const grid = document.getElementById('productsGrid');
            grid.innerHTML = '';

            affiliateProducts.forEach(p => {
                const card = document.createElement('div');
                card.className = 'bg-slate-900 border border-slate-800 rounded-2xl p-5 flex flex-col justify-between relative group';

                const isML = p.platform === 'mercadolivre';
                const platformName = isML ? 'Mercado Livre' : 'Shopee';
                const btnBgClass = isML ? 'bg-mercadolivre-400 hover:bg-mercadolivre-500 text-slate-950 font-bold' : 'bg-shopee-500 hover:bg-shopee-600 text-white font-bold';

                card.innerHTML = `
                    <div>
                        <div class="relative w-full h-48 bg-slate-950 rounded-xl overflow-hidden mb-4 border border-slate-800/80 p-2">
                            <img src="${p.img}" alt="${p.name}" class="w-full h-full object-contain crisp-img">
                        </div>
                        <h3 class="text-sm font-bold text-white mb-2">${p.name}</h3>
                        <div class="mb-4">
                            <span class="text-2xl font-black text-emerald-400">R$ ${p.price.toFixed(2)}</span>
                        </div>
                    </div>
                    <div class="space-y-2">
                        <a href="${p.affiliateLink}" target="_blank" rel="noopener noreferrer" class="w-full py-2.5 ${btnBgClass} rounded-xl text-xs flex items-center justify-center gap-1.5 uppercase">
                            <span>Ver no ${platformName}</span>
                        </a>
                        ${isAdminLoggedIn ? `
                            <button onclick="deleteProduct('${p.id}')" class="w-full text-[11px] text-red-400 py-1 flex items-center justify-center gap-1">
                                <i class="fa-solid fa-trash"></i> Remover
                            </button>
                        ` : ''}
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        function openAddProductModal() { document.getElementById('productModal').classList.remove('hidden'); }
        function closeModal() { document.getElementById('productModal').classList.add('hidden'); }

        function handleProductSubmit(e) {
            e.preventDefault();
            const newProd = {
                id: 'prod-' + Date.now(),
                name: document.getElementById('pName').value,
                price: parseFloat(document.getElementById('pPrice').value),
                oldPrice: parseFloat(document.getElementById('pOldPrice').value) || 0,
                platform: document.getElementById('pPlatform').value,
                affiliateLink: document.getElementById('pAffiliateLink').value,
                img: document.getElementById('pImg').value
            };
            affiliateProducts.push(newProd);
            localStorage.setItem('my_affiliate_products', JSON.stringify(affiliateProducts));
            renderGridProducts();
            closeModal();
        }

        function deleteProduct(id) {
            affiliateProducts = affiliateProducts.filter(p => p.id !== id);
            localStorage.setItem('my_affiliate_products', JSON.stringify(affiliateProducts));
            renderGridProducts();
        }

        function startCountdown() {
            let duration = 899;
            const display = document.getElementById('countdownTimer');
            setInterval(() => {
                let m = parseInt(duration / 60, 10);
                let s = parseInt(duration % 60, 10);
                display.textContent = (m < 10 ? "0" + m : m) + ":" + (s < 10 ? "0" + s : s);
                if (--duration < 0) duration = 899;
            }, 1000);
        }
    </script>
</body>
</html>
