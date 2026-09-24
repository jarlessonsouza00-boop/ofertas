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
        .glow-ml { box-shadow: 0 0 25px -5px rgba(255, 230, 0, 0.3); }
        .glow-shopee { box-shadow: 0 0 25px -5px rgba(238, 77, 45, 0.3); }
    </style>
</head>
<body class="bg-slate-950 text-slate-100 font-sans antialiased min-h-screen pb-24 selection:bg-amber-500 selection:text-slate-950">

    <!-- Barra Superior de Controle do Afiliado -->
    <div class="sticky top-0 z-50 bg-slate-900/95 backdrop-blur-md border-b border-slate-800 py-2.5 px-4 shadow-xl">
        <div class="max-w-7xl mx-auto flex flex-wrap items-center justify-between gap-3">
            <div class="flex items-center gap-2 text-amber-400 text-xs md:text-sm font-semibold">
                <i class="fa-solid fa-store text-emerald-400"></i>
                <span>Painel de Afiliado | Vitrine de Produtos Físicos</span>
            </div>
            <div class="flex items-center gap-2">
                <button onclick="openAddProductModal()" class="px-3.5 py-1.5 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-white font-bold text-xs shadow-lg shadow-emerald-950/50 transition flex items-center gap-1.5">
                    <i class="fa-solid fa-plus-circle"></i>
                    <span>+ Adicionar Produto / Link</span>
                </button>
            </div>
        </div>
    </div>

    <!-- Banner de Urgência e Oferta Limitada -->
    <div class="bg-gradient-to-r from-amber-600 via-amber-500 to-yellow-500 text-slate-950 font-extrabold text-center py-2 px-4 text-xs md:text-sm tracking-wide shadow-md">
        <i class="fa-solid fa-bolt mr-1"></i>
        DESCONTO EXCLUSIVO DE AFILIADO - FRETE GRÁTIS EM PRODUTOS SELECIONADOS NA SHOPEE E MERCADO LIVRE!
        <span class="ml-2 bg-slate-950 text-amber-400 px-2 py-0.5 rounded font-mono text-xs" id="countdownTimer">14:59</span>
    </div>

    <!-- Hero Section: Produto Destaque (Físico) -->
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

            <!-- Card Destaque do Produto Físico -->
            <div class="bg-slate-900/90 border border-slate-800 rounded-3xl p-6 md:p-8 shadow-2xl backdrop-blur-md max-w-4xl mx-auto">
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
                    
                    <!-- Imagem Principal Nítida em Alta Definição -->
                    <div class="relative bg-slate-950 rounded-2xl p-4 border border-slate-800 flex items-center justify-center overflow-hidden group">
                        <span class="absolute top-3 left-3 z-10 bg-red-600 text-white font-extrabold text-xs px-2.5 py-1 rounded-md uppercase tracking-wider" id="heroBadge">
                            OFERTA 42% OFF
                        </span>
                        <img id="heroProductImg" src="https://images.unsplash.com/photo-1590658268037-6bf12165a8df?auto=format&fit=crop&w=1000&q=95" alt="Produto Físico Afiliado" class="w-full h-64 md:h-80 object-contain crisp-img transition duration-300 group-hover:scale-105">
                    </div>

                    <!-- Detalhes da Oferta de Afiliado -->
                    <div class="flex flex-col justify-between space-y-5">
                        
                        <!-- Avaliações -->
                        <div class="flex items-center gap-2">
                            <div class="flex text-amber-400 text-xs">
                                <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i>
                            </div>
                            <span class="text-xs text-slate-400 font-semibold">(4.9/5 - 1.240 avaliações verificadas)</span>
                        </div>

                        <!-- Preço e Desconto -->
                        <div class="bg-slate-950/80 p-4 rounded-xl border border-slate-800/80">
                            <span class="text-xs text-slate-500 line-through block mb-0.5" id="heroOldPrice">De R$ 129,90</span>
                            <div class="flex items-baseline gap-3">
                                <span class="text-3xl md:text-4xl font-black text-emerald-400" id="heroPrice">R$ 74,90</span>
                                <span class="text-xs bg-emerald-500/10 text-emerald-400 border border-emerald-500/30 px-2 py-0.5 rounded font-bold">Menor Preço do Mês</span>
                            </div>
                            <div class="mt-2 flex items-center gap-2 text-xs text-slate-400">
                                <i class="fa-solid fa-truck-fast text-emerald-400"></i>
                                <span>Envio imediato com Rastreamento Oficial</span>
                            </div>
                        </div>

                        <!-- Recursos Rápidos -->
                        <ul class="space-y-2 text-xs text-slate-300">
                            <li class="flex items-center gap-2"><i class="fa-solid fa-circle-check text-emerald-400"></i> Bluetooth 5.0 com conexão rápida automática</li>
                            <li class="flex items-center gap-2"><i class="fa-solid fa-circle-check text-emerald-400"></i> Baixa latência perfeita para jogos e vídeos</li>
                            <li class="flex items-center gap-2"><i class="fa-solid fa-circle-check text-emerald-400"></i> Case recarregável com display de bateria LED</li>
                            <li class="flex items-center gap-2"><i class="fa-solid fa-circle-check text-emerald-400"></i> Design ergonômico in-ear para esportes e treino</li>
                        </ul>

                        <!-- Botão de Ação Direto para Afiliado (Mercado Livre / Shopee) -->
                        <div class="space-y-2.5 pt-2">
                            <a id="heroAffiliateBtn" href="https://meli.la/2ajKx5K" target="_blank" rel="noopener noreferrer" class="w-full py-4 bg-mercadolivre-400 hover:bg-mercadolivre-500 text-slate-950 font-black rounded-xl text-sm md:text-base transition shadow-lg shadow-amber-500/20 flex items-center justify-center gap-2 group uppercase tracking-wide">
                                <i class="fa-solid fa-cart-shopping text-slate-950 group-hover:scale-110 transition duration-200"></i>
                                <span>Comprar no Mercado Livre</span>
                            </a>

                            <a id="heroShopeeBtn" href="https://shopee.com.br" target="_blank" rel="noopener noreferrer" class="w-full py-3 bg-shopee-500 hover:bg-shopee-600 text-white font-bold rounded-xl text-xs md:text-sm transition shadow-lg shadow-shopee-500/20 flex items-center justify-center gap-2 uppercase tracking-wide">
                                <i class="fa-solid fa-bag-shopping"></i>
                                <span>Ver Opção na Shopee (Frete Grátis)</span>
                            </a>
                        </div>

                    </div>
                </div>
            </div>

        </div>
    </header>

    <!-- Especificações e Benefícios -->
    <section class="py-16 px-4 bg-slate-900/40 border-b border-slate-800/80">
        <div class="max-w-5xl mx-auto">
            <h2 class="text-2xl md:text-3xl font-extrabold text-white text-center mb-10">Por Que Este Produto Está Sendo Tão Vendido?</h2>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <div class="bg-slate-900 p-6 rounded-2xl border border-slate-800 hover:border-slate-700 transition">
                    <div class="w-12 h-12 bg-amber-500/10 rounded-xl flex items-center justify-center text-amber-400 text-xl mb-4 border border-amber-500/20">
                        <i class="fa-solid fa-gamepad"></i>
                    </div>
                    <h3 class="text-lg font-bold text-white mb-2">Modo Gamer Sem Atraso</h3>
                    <p class="text-slate-400 text-xs leading-relaxed">Áudio sincronizado perfeitamente com a imagem para ouvir passos e tiros em tempo real nos seus jogos favoritos.</p>
                </div>

                <div class="bg-slate-900 p-6 rounded-2xl border border-slate-800 hover:border-slate-700 transition">
                    <div class="w-12 h-12 bg-emerald-500/10 rounded-xl flex items-center justify-center text-emerald-400 text-xl mb-4 border border-emerald-500/20">
                        <i class="fa-solid fa-battery-full"></i>
                    </div>
                    <h3 class="text-lg font-bold text-white mb-2">Bateria para o Dia Todo</h3>
                    <p class="text-slate-400 text-xs leading-relaxed">Até 5 horas contínuas de reprodução + 20 horas extras fornecidas pela case de carregamento portátil.</p>
                </div>

                <div class="bg-slate-900 p-6 rounded-2xl border border-slate-800 hover:border-slate-700 transition">
                    <div class="w-12 h-12 bg-blue-500/10 rounded-xl flex items-center justify-center text-blue-400 text-xl mb-4 border border-blue-500/20">
                        <i class="fa-solid fa-shield-halved"></i>
                    </div>
                    <h3 class="text-lg font-bold text-white mb-2">Garantia Mercado Livre / Shopee</h3>
                    <p class="text-slate-400 text-xs leading-relaxed">Compra 100% garantida pelas maiores plataformas do Brasil com devolução grátis em até 7 dias.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Seção de Outros Produtos de Afiliado (Grade de Links) -->
    <section class="py-16 px-4">
        <div class="max-w-6xl mx-auto">
            <div class="text-center mb-12">
                <span class="text-amber-400 font-bold text-xs uppercase tracking-widest block mb-2">Mais Achadinhos e Ofertas</span>
                <h2 class="text-2xl md:text-4xl font-extrabold text-white">Confira Outros Produtos Recomendados</h2>
                <p class="text-slate-400 text-sm max-w-xl mx-auto mt-2">Clique nos botões abaixo para acessar diretamente a página oficial do vendedor com desconto ativo.</p>
            </div>

            <!-- Grade Dinâmica de Produtos Físicos -->
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6" id="productsGrid">
                <!-- Inserido dinamicamente via JS -->
            </div>
        </div>
    </section>

    <!-- Depoimentos e Avaliações da Plataforma -->
    <section class="py-16 bg-slate-900/50 border-t border-slate-800 px-4">
        <div class="max-w-5xl mx-auto text-center">
            <h2 class="text-2xl font-extrabold text-white mb-8">Avaliações de Quem Já Comprou</h2>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 text-left">
                <div class="bg-slate-900 p-5 rounded-2xl border border-slate-800">
                    <div class="flex items-center justify-between mb-3">
                        <div class="flex text-amber-400 text-xs">
                            <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i>
                        </div>
                        <span class="text-[10px] bg-emerald-500/10 text-emerald-400 px-2 py-0.5 rounded font-bold">Compra Verificada ML</span>
                    </div>
                    <p class="text-slate-300 text-xs mb-4">"Chegou em 2 dias úteis via Mercado Livre Full! O fone tem um grave excelente e não fica a cair da orelha na corrida."</p>
                    <div class="text-xs font-bold text-slate-200">Lucas M. - São Paulo/SP</div>
                </div>

                <div class="bg-slate-900 p-5 rounded-2xl border border-slate-800">
                    <div class="flex items-center justify-between mb-3">
                        <div class="flex text-amber-400 text-xs">
                            <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i>
                        </div>
                        <span class="text-[10px] bg-shopee-500/10 text-shopee-500 px-2 py-0.5 rounded font-bold">Compra Verificada Shopee</span>
                    </div>
                    <p class="text-slate-300 text-xs mb-4">"Apanhei com o cupão de frete grátis da Shopee pelo link da página. Valeu muito a pena, produto 100% original!"</p>
                    <div class="text-xs font-bold text-slate-200">Fernanda R. - Curitiba/PR</div>
                </div>

                <div class="bg-slate-900 p-5 rounded-2xl border border-slate-800">
                    <div class="flex items-center justify-between mb-3">
                        <div class="flex text-amber-400 text-xs">
                            <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i>
                        </div>
                        <span class="text-[10px] bg-emerald-500/10 text-emerald-400 px-2 py-0.5 rounded font-bold">Compra Verificada ML</span>
                    </div>
                    <p class="text-slate-300 text-xs mb-4">"O encaixe do fone é perfeito e a bateria dura muito mais do que esperava. Recomendo demais o vendedor!"</p>
                    <div class="text-xs font-bold text-slate-200">Rodrigo S. - Belo Horizonte/MG</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Dúvidas Frequentes -->
    <section class="py-16 px-4">
        <div class="max-w-3xl mx-auto">
            <h2 class="text-2xl font-bold text-white text-center mb-8">Perguntas Frequentes sobre a Compra</h2>
            <div class="space-y-4">
                <div class="bg-slate-900 p-4 rounded-xl border border-slate-800">
                    <h3 class="font-bold text-white text-sm mb-1">Como funciona a entrega?</h3>
                    <p class="text-slate-400 text-xs">Ao clicar nos botões de compra, é redirecionado para o anúncio oficial no Mercado Livre ou Shopee. O envio é feito diretamente pelos vendedores oficiais das plataformas com código de rastreamento.</p>
                </div>
                <div class="bg-slate-900 p-4 rounded-xl border border-slate-800">
                    <h3 class="font-bold text-white text-sm mb-1">O produto tem garantia?</h3>
                    <p class="text-slate-400 text-xs">Sim! Todas as compras realizadas via Mercado Livre e Shopee contam com a proteção ao comprador e garantia de devolução sem custos caso haja qualquer imprevisto.</p>
                </div>
                <div class="bg-slate-900 p-4 rounded-xl border border-slate-800">
                    <h3 class="font-bold text-white text-sm mb-1">Como ganho Frete Grátis?</h3>
                    <p class="text-slate-400 text-xs">No Mercado Livre, compras acima do valor mínimo ou pelo programa Meli+ têm frete grátis. Na Shopee, utilize os cupões de frete grátis disponíveis na sua aplicação.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Barra Fixa de Ação Rápida (Mobile) -->
    <div class="fixed bottom-0 left-0 right-0 z-40 bg-slate-900/95 border-t border-slate-800 p-3 backdrop-blur-md block md:hidden">
        <a id="mobileAffiliateBtn" href="https://meli.la/2ajKx5K" target="_blank" rel="noopener noreferrer" class="w-full py-3 bg-mercadolivre-400 hover:bg-mercadolivre-500 text-slate-950 font-black rounded-xl text-xs flex items-center justify-center gap-2 shadow-lg uppercase tracking-wide">
            <i class="fa-solid fa-cart-shopping"></i>
            <span>Ver Oferta no Mercado Livre (R$ 74,90)</span>
        </a>
    </div>

    <!-- Modal: Adicionar / Editar Produto Afiliado -->
    <div id="productModal" class="fixed inset-0 bg-slate-950/80 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="bg-slate-900 border border-slate-800 rounded-2xl w-full max-w-lg p-6 shadow-2xl relative max-h-[90vh] overflow-y-auto">
            <div class="flex items-center justify-between pb-4 border-b border-slate-800 mb-5">
                <div class="flex items-center gap-2 text-amber-400 font-bold text-base">
                    <i class="fa-solid fa-link"></i>
                    <span id="modalTitle">Cadastrar Novo Produto de Afiliado</span>
                </div>
                <button onclick="closeModal()" class="text-slate-400 hover:text-white text-lg">
                    <i class="fa-solid fa-xmark"></i>
                </button>
            </div>

            <form id="productForm" onsubmit="handleProductSubmit(event)" class="space-y-4">
                <input type="hidden" id="editProductId">

                <div>
                    <label class="block text-xs font-semibold text-slate-300 uppercase mb-1">Nome do Produto Físico *</label>
                    <input type="text" id="pName" required placeholder="Ex: Fone Bluetooth Gamer Kapbom KA-999" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-3.5 py-2 text-xs text-slate-100 focus:border-amber-500 focus:outline-none">
                </div>

                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-semibold text-slate-300 uppercase mb-1">Preço Atual (R$) *</label>
                        <input type="number" step="0.01" id="pPrice" required placeholder="74.90" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-3.5 py-2 text-xs text-slate-100 focus:border-amber-500 focus:outline-none">
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-slate-300 uppercase mb-1">Preço Original (R$)</label>
                        <input type="number" step="0.01" id="pOldPrice" placeholder="129.90" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-3.5 py-2 text-xs text-slate-100 focus:border-amber-500 focus:outline-none">
                    </div>
                </div>

                <div>
                    <label class="block text-xs font-semibold text-slate-300 uppercase mb-1">Plataforma / Origem *</label>
                    <select id="pPlatform" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-3.5 py-2 text-xs text-slate-100 focus:border-amber-500 focus:outline-none">
                        <option value="mercadolivre">Mercado Livre (Selo Amarelo)</option>
                        <option value="shopee">Shopee (Selo Laranja)</option>
                    </select>
                </div>

                <div>
                    <label class="block text-xs font-semibold text-slate-300 uppercase mb-1">Seu Link de Afiliado (URL de Destino) *</label>
                    <input type="url" id="pAffiliateLink" required placeholder="https://meli.la/... ou https://shope.ee/..." class="w-full bg-slate-950 border border-slate-800 rounded-xl px-3.5 py-2 text-xs text-slate-100 focus:border-amber-500 focus:outline-none">
                </div>

                <div>
                    <label class="block text-xs font-semibold text-slate-300 uppercase mb-1">URL da Foto do Produto (HD) *</label>
                    <input type="url" id="pImg" required placeholder="https://..." class="w-full bg-slate-950 border border-slate-800 rounded-xl px-3.5 py-2 text-xs text-slate-100 focus:border-amber-500 focus:outline-none">
                </div>

                <div>
                    <label class="block text-xs font-semibold text-slate-300 uppercase mb-1">Onde Exibir na Página? *</label>
                    <select id="pLocation" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-3.5 py-2 text-xs text-slate-100 focus:border-amber-500 focus:outline-none">
                        <option value="grid">Na Grade "Outros Produtos Recomendados"</option>
                        <option value="hero">Como Produto Principal do Topo (Hero)</option>
                    </select>
                </div>

                <div class="pt-3 flex gap-3">
                    <button type="button" onclick="closeModal()" class="w-1/2 py-2.5 rounded-xl border border-slate-800 hover:bg-slate-800 text-slate-300 text-xs font-medium transition">Cancelar</button>
                    <button type="submit" class="w-1/2 py-2.5 rounded-xl bg-emerald-600 hover:bg-emerald-500 text-white text-xs font-bold transition shadow-lg shadow-emerald-900/40">Salvar Produto</button>
                </div>
            </form>
        </div>
    </div>

    <script>
        let affiliateProducts = [
            {
                id: 'prod-cowin',
                name: 'Fone Headset Bluetooth Over-Ear Cowin Regulável',
                price: 29.99,
                oldPrice: 39.90,
                platform: 'mercadolivre',
                affiliateLink: 'https://meli.la/2FLn4WD',
                img: 'https://images.unsplash.com/photo-1505740420928-5e560c06d30e?auto=format&fit=crop&w=800&q=95',
                badge: 'MAIS VENDIDO'
            },
            {
                id: 'prod-mouse',
                name: 'Mouse Gamer RGB 7200 DPI 7 Botões Programáveis',
                price: 49.90,
                oldPrice: 89.90,
                platform: 'shopee',
                affiliateLink: 'https://shopee.com.br',
                img: 'https://images.unsplash.com/photo-1615663245857-ac93bb7c39e7?auto=format&fit=crop&w=800&q=95',
                badge: 'FRETE GRÁTIS'
            },
            {
                id: 'prod-smartwatch',
                name: 'Smartwatch Esportivo IWO D20 Monitor Cardíaco',
                price: 34.90,
                oldPrice: 79.90,
                platform: 'mercadolivre',
                affiliateLink: 'https://meli.la/2FLn4WD',
                img: 'https://images.unsplash.com/photo-1579586337278-3befd40fd17a?auto=format&fit=crop&w=800&q=95',
                badge: 'OFERTA'
            }
        ];

        window.onload = function() {
            renderGridProducts();
            startCountdown();
        };

        function renderGridProducts() {
            const grid = document.getElementById('productsGrid');
            grid.innerHTML = '';

            affiliateProducts.forEach(p => {
                const card = document.createElement('div');
                card.className = 'bg-slate-900 border border-slate-800 rounded-2xl p-5 flex flex-col justify-between hover:border-slate-700 transition shadow-xl relative group';

                const isML = p.platform === 'mercadolivre';
                const platformBadgeClass = isML ? 'bg-mercadolivre-400 text-slate-950' : 'bg-shopee-500 text-white';
                const platformName = isML ? 'Mercado Livre' : 'Shopee';
                const btnBgClass = isML ? 'bg-mercadolivre-400 hover:bg-mercadolivre-500 text-slate-950 font-extrabold' : 'bg-shopee-500 hover:bg-shopee-600 text-white font-extrabold';

                const discountPercent = p.oldPrice ? Math.round(((p.oldPrice - p.price) / p.oldPrice) * 100) : 0;

                card.innerHTML = `
                    <div>
                        <div class="relative w-full h-48 bg-slate-950 rounded-xl overflow-hidden mb-4 border border-slate-800/80 p-2">
                            <span class="absolute top-2 left-2 z-10 text-[10px] font-black px-2 py-0.5 rounded ${platformBadgeClass} uppercase tracking-wider">
                                ${platformName}
                            </span>
                            ${discountPercent > 0 ? `<span class="absolute top-2 right-2 z-10 bg-red-600 text-white text-[10px] font-extrabold px-1.5 py-0.5 rounded">${discountPercent}% OFF</span>` : ''}
                            <img src="${p.img}" alt="${p.name}" class="w-full h-full object-contain crisp-img group-hover:scale-105 transition duration-300">
                        </div>

                        <h3 class="text-sm font-bold text-white mb-2 line-clamp-2 min-h-[40px]">${p.name}</h3>

                        <div class="mb-4">
                            ${p.oldPrice ? `<span class="text-xs text-slate-500 line-through block">R$ ${p.oldPrice.toFixed(2)}</span>` : ''}
                            <span class="text-2xl font-black text-emerald-400">R$ ${p.price.toFixed(2)}</span>
                        </div>
                    </div>

                    <div class="space-y-2">
                        <a href="${p.affiliateLink}" target="_blank" rel="noopener noreferrer" class="w-full py-2.5 ${btnBgClass} rounded-xl text-xs flex items-center justify-center gap-1.5 transition uppercase tracking-wide">
                            <i class="fa-solid fa-external-link text-xs"></i>
                            <span>Ver no ${platformName}</span>
                        </a>
                        <button onclick="deleteProduct('${p.id}')" class="w-full text-[11px] text-slate-500 hover:text-red-400 py-1 transition flex items-center justify-center gap-1">
                            <i class="fa-solid fa-trash"></i> Remover da Vitrine
                        </button>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        function openAddProductModal() {
            document.getElementById('modalTitle').innerText = 'Cadastrar Novo Produto de Afiliado';
            document.getElementById('editProductId').value = '';
            document.getElementById('productForm').reset();
            document.getElementById('productModal').classList.remove('hidden');
        }

        function closeModal() {
            document.getElementById('productModal').classList.add('hidden');
        }

        function handleProductSubmit(e) {
            e.preventDefault();
            const name = document.getElementById('pName').value;
            const price = parseFloat(document.getElementById('pPrice').value);
            const oldPrice = parseFloat(document.getElementById('pOldPrice').value) || price * 1.4;
            const platform = document.getElementById('pPlatform').value;
            const affiliateLink = document.getElementById('pAffiliateLink').value;
            const img = document.getElementById('pImg').value;
            const location = document.getElementById('pLocation').value;

            if (location === 'hero') {
                document.getElementById('heroTitle').innerText = name;
                document.getElementById('heroPrice').innerText = 'R$ ' + price.toFixed(2);
                document.getElementById('heroOldPrice').innerText = 'De R$ ' + oldPrice.toFixed(2);
                document.getElementById('heroProductImg').src = img;
                document.getElementById('heroAffiliateBtn').href = affiliateLink;
                document.getElementById('mobileAffiliateBtn').href = affiliateLink;
                showToast('Produto do Topo (Hero) atualizado com sucesso!');
            } else {
                const newProd = {
                    id: 'prod-' + Date.now(),
                    name,
                    price,
                    oldPrice,
                    platform,
                    affiliateLink,
                    img,
                    badge: 'NOVO'
                };
                affiliateProducts.push(newProd);
                renderGridProducts();
                showToast('Produto adicionado à vitrine!');
            }

            closeModal();
        }

        function deleteProduct(id) {
            affiliateProducts = affiliateProducts.filter(p => p.id !== id);
            renderGridProducts();
            showToast('Produto removido da vitrine!');
        }

        function showToast(msg) {
            const toast = document.createElement('div');
            toast.className = 'fixed bottom-5 right-5 z-50 bg-emerald-600 text-white font-bold text-xs py-3 px-5 rounded-xl shadow-2xl flex items-center gap-2 border border-emerald-400/30 animate-bounce';
            toast.innerHTML = `<i class="fa-solid fa-circle-check"></i> ${msg}`;
            document.body.appendChild(toast);
            setTimeout(() => toast.remove(), 3000);
        }

        function startCountdown() {
            let duration = 899;
            const display = document.getElementById('countdownTimer');
            setInterval(() => {
                let minutes = parseInt(duration / 60, 10);
                let seconds = parseInt(duration % 60, 10);

                minutes = minutes < 10 ? "0" + minutes : minutes;
                seconds = seconds < 10 ? "0" + seconds : seconds;

                if (display) display.textContent = minutes + ":" + seconds;

                if (--duration < 0) duration = 899;
            }, 1000);
        }
    </script>
</body>
</html>
