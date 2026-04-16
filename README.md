<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WildConnect | Global Conservation Network</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;800&display=swap');
        body { font-family: 'Plus Jakarta Sans', sans-serif; }
        .hero-gradient { 
            background: linear-gradient(rgba(10, 30, 10, 0.75), rgba(10, 30, 10, 0.75)), 
                        url('https://images.unsplash.com/photo-1437622368342-7a3d73a34c8f?auto=format&fit=crop&w=1500&q=80'); 
            background-size: cover; background-position: center;
        }
        .glass { background: rgba(255, 255, 255, 0.95); backdrop-filter: blur(10px); }
        .project-card:hover { transform: translateY(-10px); transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275); }
    </style>
</head>
<body class="bg-gray-50 text-slate-900 scroll-smooth">

    <nav class="bg-white/90 backdrop-blur-md sticky top-0 z-50 border-b border-gray-100">
        <div class="container mx-auto px-6 py-4 flex justify-between items-center">
            <div class="flex items-center space-x-2">
                <div class="bg-emerald-600 p-2 rounded-lg">
                    <i class="fas fa-paw text-white"></i>
                </div>
                <span class="text-xl font-extrabold tracking-tight text-emerald-900">WildConnect</span>
            </div>
            <div class="hidden lg:flex space-x-8 font-bold text-sm uppercase tracking-widest text-gray-500">
                <a href="#projects" class="hover:text-emerald-600">Expeditions</a>
                <a href="#map" class="hover:text-emerald-600">Global Map</a>
                <a href="#dashboard" class="hover:text-emerald-600">My Portal</a>
            </div>
            <div class="flex items-center space-x-4">
                <button onclick="openModal('Researcher Login')" class="text-sm font-bold text-emerald-700">Login</button>
                <button onclick="openModal('Join Network')" class="bg-emerald-600 hover:bg-emerald-700 text-white px-6 py-2.5 rounded-full font-bold shadow-lg shadow-emerald-200 transition">Get Involved</button>
            </div>
        </div>
    </nav>

    <header class="hero-gradient text-white py-32 px-6">
        <div class="container mx-auto text-center">
            <div class="inline-flex items-center space-x-2 bg-white/10 px-4 py-2 rounded-full mb-8 backdrop-blur-md border border-white/20">
                <span class="relative flex h-3 w-3"><span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-emerald-400 opacity-75"></span><span class="relative inline-flex rounded-full h-3 w-3 bg-emerald-500"></span></span>
                <span class="text-xs font-bold uppercase tracking-widest">Live: 42 New Missions Posted Today</span>
            </div>
            <h1 class="text-5xl md:text-7xl font-black mb-6 leading-tight">Data for the Planet.<br>Hands for the <span class="text-emerald-400 italic">Wild.</span></h1>
            <p class="text-xl text-emerald-50/80 mb-12 max-w-2xl mx-auto">The world's largest open-source bridge connecting 5,000+ wildlife biologists with volunteers like you.</p>
            
            <div class="bg-white p-2 rounded-2xl shadow-2xl max-w-3xl mx-auto flex flex-col md:flex-row gap-2">
                <input type="text" id="searchInput" onkeyup="filterProjects()" placeholder="Try 'India', 'Marine', or 'Endangered'..." class="flex-grow p-4 rounded-xl text-gray-800 focus:outline-none">
                <button class="bg-emerald-600 text-white px-10 py-4 rounded-xl font-bold hover:bg-emerald-700 transition">Search Missions</button>
            </div>
        </div>
    </header>

    <section class="bg-white border-b sticky top-[73px] z-40">
        <div class="container mx-auto px-6 py-4 flex overflow-x-auto space-x-4 no-scrollbar">
            <button onclick="filterType('all')" class="whitespace-nowrap px-6 py-2 rounded-full bg-emerald-100 text-emerald-800 font-bold border border-emerald-200">All Missions</button>
            <button onclick="filterType('Mammals')" class="whitespace-nowrap px-6 py-2 rounded-full bg-gray-50 hover:bg-emerald-50 font-bold border transition">🦁 Mammals</button>
            <button onclick="filterType('Marine')" class="whitespace-nowrap px-6 py-2 rounded-full bg-gray-50 hover:bg-emerald-50 font-bold border transition">🐋 Marine</button>
            <button onclick="filterType('Birds')" class="whitespace-nowrap px-6 py-2 rounded-full bg-gray-50 hover:bg-emerald-50 font-bold border transition">🦅 Birds</button>
            <button onclick="filterType('Reptiles')" class="whitespace-nowrap px-6 py-2 rounded-full bg-gray-50 hover:bg-emerald-50 font-bold border transition">🦎 Reptiles</button>
            <button onclick="filterType('Insects')" class="whitespace-nowrap px-6 py-2 rounded-full bg-gray-50 hover:bg-emerald-50 font-bold border transition">🐝 Insects</button>
            <button onclick="filterType('Plants')" class="whitespace-nowrap px-6 py-2 rounded-full bg-gray-50 hover:bg-emerald-50 font-bold border transition">🌱 Botany</button>
        </div>
    </section>

    <main class="container mx-auto py-16 px-6" id="projects">
        <div id="projectGrid" class="grid md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-8">
            
            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Mammals">
                <img src="https://images.unsplash.com/photo-1546182990-dffeafbe841d?w=400" class="h-48 w-full object-cover">
                <div class="p-6">
                    <div class="flex justify-between mb-2"><span class="text-[10px] font-bold text-emerald-600 uppercase">Himalayas</span><span class="text-[10px] bg-red-100 text-red-700 px-2 py-0.5 rounded">Critical</span></div>
                    <h4 class="font-extrabold text-lg mb-2">Snow Leopard Scat DNA</h4>
                    <p class="text-gray-500 text-xs mb-4">Collecting samples at 4000m altitude to map genetic diversity of the 'Ghost of the Mountain'.</p>
                    <button onclick="openModal('Snow Leopard')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold hover:bg-emerald-600 transition">APPLY</button>
                </div>
            </div>

            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Marine">
                <img src="https://images.unsplash.com/photo-1518467166778-b88f373ffec7?w=400" class="h-48 w-full object-cover">
                <div class="p-6">
                    <div class="flex justify-between mb-2"><span class="text-[10px] font-bold text-blue-600 uppercase">Costa Rica</span><span class="text-[10px] bg-yellow-100 text-yellow-700 px-2 py-0.5 rounded">Vulnerable</span></div>
                    <h4 class="font-extrabold text-lg mb-2">Hatchling Night Guard</h4>
                    <p class="text-gray-500 text-xs mb-4">Protecting leatherback hatchlings as they make their first run to the Pacific Ocean.</p>
                    <button onclick="openModal('Sea Turtles')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold hover:bg-emerald-600 transition">APPLY</button>
                </div>
            </div>

            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Mammals">
                <img src="https://images.unsplash.com/photo-1544070282-591d487ca53e?w=400" class="h-48 w-full object-cover">
                <div class="p-6">
                    <div class="flex justify-between mb-2"><span class="text-[10px] font-bold text-emerald-600 uppercase">Nepal</span><span class="text-[10px] bg-red-100 text-red-700 px-2 py-0.5 rounded">Endangered</span></div>
                    <h4 class="font-extrabold text-lg mb-2">Panda Habitat Mapping</h4>
                    <p class="text-gray-500 text-xs mb-4">Surveying bamboo forest density to predict red panda migration shifts.</p>
                    <button onclick="openModal('Red Panda')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold hover:bg-emerald-600 transition">APPLY</button>
                </div>
            </div>

            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Marine">
                <img src="https://images.unsplash.com/photo-1560275619-4662e36fa65c?w=400" class="h-48 w-full object-cover">
                <div class="p-6">
                    <div class="flex justify-between mb-2"><span class="text-[10px] font-bold text-blue-600 uppercase">South Africa</span><span class="text-[10px] bg-gray-100 text-gray-700 px-2 py-0.5 rounded">Stable</span></div>
                    <h4 class="font-extrabold text-lg mb-2">Acoustic Fin Tagging</h4>
                    <p class="text-gray-500 text-xs mb-4">Joining Dr. Meyer on research vessels to tag sharks for migratory data tracking.</p>
                    <button onclick="openModal('Great White')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold hover:bg-emerald-600 transition">APPLY</button>
                </div>
            </div>

            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Insects">
                <img src="https://images.unsplash.com/photo-1533512900331-564537b06880?w=400" class="h-48 w-full object-cover">
                <div class="p-6">
                    <div class="flex justify-between mb-2"><span class="text-[10px] font-bold text-orange-600 uppercase">Mexico</span><span class="text-[10px] bg-orange-100 text-orange-700 px-2 py-0.5 rounded">Migration</span></div>
                    <h4 class="font-extrabold text-lg mb-2">Monarch Count 2026</h4>
                    <p class="text-gray-500 text-xs mb-4">Annual census of overwintering butterfly colonies in Michoacán forests.</p>
                    <button onclick="openModal('Monarch')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold hover:bg-emerald-600 transition">APPLY</button>
                </div>
            </div>

            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Reptiles">
                <img src="https://images.unsplash.com/photo-1548332159-f831349f2571?w=400" class="h-48 w-full object-cover">
                <div class="p-6">
                    <div class="flex justify-between mb-2"><span class="text-[10px] font-bold text-orange-600 uppercase">Galapagos</span><span class="text-[10px] bg-green-100 text-green-700 px-2 py-0.5 rounded">Stable</span></div>
                    <h4 class="font-extrabold text-lg mb-2">Giant Tortoise Health</h4>
                    <p class="text-gray-500 text-xs mb-4">Assisting vet teams with annual checkups and weight measurements.</p>
                    <button onclick="openModal('Tortoise')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold hover:bg-emerald-600 transition">APPLY</button>
                </div>
            </div>

            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Mammals">
                <img src="https://images.unsplash.com/photo-1614027126733-75778cca09be?w=400" class="h-48 w-full object-cover">
                <div class="p-6">
                    <div class="flex justify-between mb-2"><span class="text-[10px] font-bold text-emerald-600 uppercase">Tanzania</span><span class="text-[10px] bg-red-100 text-red-700 px-2 py-0.5 rounded">Vulnerable</span></div>
                    <h4 class="font-extrabold text-lg mb-2">Serengeti Pride Census</h4>
                    <p class="text-gray-500 text-xs mb-4">Identifying individual lions by whisker patterns to track pride dynamics.</p>
                    <button onclick="openModal('Lion')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold hover:bg-emerald-600 transition">APPLY</button>
                </div>
            </div>

            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Plants">
                <img src="https://images.unsplash.com/photo-1547471080-7cc2caa01a7e?w=400" class="h-48 w-full object-cover">
                <div class="p-6">
                    <div class="flex justify-between mb-2"><span class="text-[10px] font-bold text-emerald-600 uppercase">California</span><span class="text-[10px] bg-green-100 text-green-700 px-2 py-0.5 rounded">Iconic</span></div>
                    <h4 class="font-extrabold text-lg mb-2">Post-Fire Seedling Audit</h4>
                    <p class="text-gray-500 text-xs mb-4">Counting new growth in fire-affected areas to assess forest recovery.</p>
                    <button onclick="openModal('Sequoia')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold hover:bg-emerald-600 transition">APPLY</button>
                </div>
            </div>

            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Birds">
                <img src="https://images.unsplash.com/photo-1517783999520-f068d7431a60?w=400" class="h-48 w-full object-cover">
                <div class="p-6">
                    <div class="flex justify-between mb-2"><span class="text-[10px] font-bold text-indigo-600 uppercase">Antarctica</span><span class="text-[10px] bg-red-100 text-red-700 px-2 py-0.5 rounded">Near Threat</span></div>
                    <h4 class="font-extrabold text-lg mb-2">Ice Shelf Colony Count</h4>
                    <p class="text-gray-500 text-xs mb-4">Using satellite imagery and ground counts to monitor colony size.</p>
                    <button onclick="openModal('Penguin')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold hover:bg-emerald-600 transition">APPLY</button>
                </div>
            </div>

            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Insects">
                <img src="https://images.unsplash.com/photo-1508933256082-936657e2a969?w=400" class="h-48 w-full object-cover">
                <div class="p-6">
                    <div class="flex justify-between mb-2"><span class="text-[10px] font-bold text-orange-600 uppercase">UK / Remote</span><span class="text-[10px] bg-yellow-100 text-yellow-700 px-2 py-0.5 rounded">Critical</span></div>
                    <h4 class="font-extrabold text-lg mb-2">Pollinator Route Mapping</h4>
                    <p class="text-gray-500 text-xs mb-4">A citizen science project tracking urban garden pollinator visits.</p>
                    <button onclick="openModal('Honey Bees')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold hover:bg-emerald-600 transition">APPLY</button>
                </div>
            </div>

            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Mammals">
                <img src="https://images.unsplash.com/photo-1590420485404-f86d22b8abf8?w=400" class="h-48 w-full object-cover">
                <div class="p-6">
                    <div class="flex justify-between mb-2"><span class="text-[10px] font-bold text-emerald-600 uppercase">Yellowstone</span><span class="text-[10px] bg-green-100 text-green-700 px-2 py-0.5 rounded">Stable</span></div>
                    <h4 class="font-extrabold text-lg mb-2">Wolf Howl Audio Recording</h4>
                    <p class="text-gray-500 text-xs mb-4">Deploying acoustic sensors to identify pack communication zones.</p>
                    <button onclick="openModal('Wolf')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold hover:bg-emerald-600 transition">APPLY</button>
                </div>
            </div>

            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Marine">
                <img src="https://images.unsplash.com/photo-1544551763-46a013bb70d5?w=400" class="h-48 w-full object-cover">
                <div class="p-6">
                    <div class="flex justify-between mb-2"><span class="text-[10px] font-bold text-blue-600 uppercase">Fiji</span><span class="text-[10px] bg-blue-100 text-blue-700 px-2 py-0.5 rounded">Resilient</span></div>
                    <h4 class="font-extrabold text-lg mb-2">Anemone Health Survey</h4>
                    <p class="text-gray-500 text-xs mb-4">Scuba-based data collection on symbiotic reef relationships.</p>
                    <button onclick="openModal('Clownfish')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold hover:bg-emerald-600 transition">APPLY</button>
                </div>
            </div>

            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Mammals">
                <img src="https://images.unsplash.com/photo-1503919005314-30d93d07d823?w=400" class="h-48 w-full object-cover">
                <div class="p-6"><h4 class="font-extrabold text-lg mb-2">Giraffe Neck Pattern ID</h4><p class="text-gray-500 text-xs mb-4">Kenya: Individual identification through photo matching software.</p><button onclick="openModal('Giraffe')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold">APPLY</button></div>
            </div>
            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Birds">
                <img src="https://images.unsplash.com/photo-1444464666168-49d633b867ad?w=400" class="h-48 w-full object-cover">
                <div class="p-6"><h4 class="font-extrabold text-lg mb-2">Songbird Migration Netting</h4><p class="text-gray-500 text-xs mb-4">Canada: Safe banding of boreal birds to track summer breeding.</p><button onclick="openModal('Songbird')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold">APPLY</button></div>
            </div>
            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Reptiles">
                <img src="https://images.unsplash.com/photo-1528156438606-7ac3b1f129c1?w=400" class="h-48 w-full object-cover">
                <div class="p-6"><h4 class="font-extrabold text-lg mb-2">King Cobra Nest Guard</h4><p class="text-gray-500 text-xs mb-4">Western Ghats: Assisting in relocating nests from human zones.</p><button onclick="openModal('Cobra')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold">APPLY</button></div>
            </div>
            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Mammals">
                <img src="https://images.unsplash.com/photo-1534188753412-3e26d0d618d6?w=400" class="h-48 w-full object-cover">
                <div class="p-6"><h4 class="font-extrabold text-lg mb-2">Brown Bear Hibernation</h4><p class="text-gray-500 text-xs mb-4">Alaska: Monitoring den emergence via remote trail cams.</p><button onclick="openModal('Bear')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold">APPLY</button></div>
            </div>
            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Marine">
                <img src="https://images.unsplash.com/photo-1551244072-5d12893278ab?w=400" class="h-48 w-full object-cover">
                <div class="p-6"><h4 class="font-extrabold text-lg mb-2">Manta Ray Belly ID</h4><p class="text-gray-500 text-xs mb-4">Maldives: Diving to photograph unique ventral spot patterns.</p><button onclick="openModal('Manta')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold">APPLY</button></div>
            </div>
            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Mammals">
                <img src="https://images.unsplash.com/photo-1543158266-0066955047b1?w=400" class="h-48 w-full object-cover">
                <div class="p-6"><h4 class="font-extrabold text-lg mb-2">Koala Scat Analysis</h4><p class="text-gray-500 text-xs mb-4">Australia: Assessing stress levels in post-fire koala populations.</p><button onclick="openModal('Koala')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold">APPLY</button></div>
            </div>
            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Birds">
                <img src="https://images.unsplash.com/photo-1504121456602-0442308b3c2c?w=400" class="h-48 w-full object-cover">
                <div class="p-6"><h4 class="font-extrabold text-lg mb-2">Bald Eagle Nest Watch</h4><p class="text-gray-500 text-xs mb-4">Florida: Observing and reporting fledgling success rates.</p><button onclick="openModal('Eagle')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold">APPLY</button></div>
            </div>
            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Mammals">
                <img src="https://images.unsplash.com/photo-1574068468668-a05a11f871da?w=400" class="h-48 w-full object-cover">
                <div class="p-6"><h4 class="font-extrabold text-lg mb-2">Arctic Fox Fur Change</h4><p class="text-gray-500 text-xs mb-4">Sweden: Tracking timing of seasonal coat color shifts.</p><button onclick="openModal('Arctic Fox')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold">APPLY</button></div>
            </div>
            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Insects">
                <img src="https://images.unsplash.com/photo-1464349153735-7db519247a32?w=400" class="h-48 w-full object-cover">
                <div class="p-6"><h4 class="font-extrabold text-lg mb-2">Beetle Diversity Audit</h4><p class="text-gray-500 text-xs mb-4">Borneo: Ground-level insect collection in rainforest floor.</p><button onclick="openModal('Beetle')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold">APPLY</button></div>
            </div>
            <div class="bg-white rounded-3xl border border-gray-100 shadow-sm overflow-hidden project-card" data-type="Reptiles">
                <img src="https://images.unsplash.com/photo-1511225070737-5af5ac9a690d?w=400" class="h-48 w-full object-cover">
                <div class="p-6"><h4 class="font-extrabold text-lg mb-2">Green Iguana Growth</h4><p class="text-gray-500 text-xs mb-4">Florida: Tracking the expansion of invasive iguana colonies.</p><button onclick="openModal('Iguana')" class="w-full py-3 bg-slate-900 text-white rounded-xl text-xs font-bold">APPLY</button></div>
            </div>

        </div>
    </main>

    <section id="dashboard" class="bg-slate-900 py-20 text-white">
        <div class="container mx-auto px-6">
            <h3 class="text-3xl font-black mb-12 flex items-center"><i class="fas fa-chart-line mr-4 text-emerald-400"></i> My Impact Dashboard</h3>
            <div class="grid md:grid-cols-3 gap-8">
                <div class="bg-slate-800 p-8 rounded-3xl border border-slate-700">
                    <p class="text-gray-400 text-xs font-bold uppercase tracking-widest mb-2">Total Contributions</p>
                    <p class="text-4xl font-black text-emerald-400">0 Data Points</p>
                    <p class="text-sm text-gray-500 mt-4 italic">Start a mission to see your stats grow.</p>
                </div>
                <div class="bg-slate-800 p-8 rounded-3xl border border-slate-700">
                    <p class="text-gray-400 text-xs font-bold uppercase tracking-widest mb-2">Leaderboard Rank</p>
                    <p class="text-4xl font-black text-blue-400">Unranked</p>
                    <p class="text-sm text-gray-500 mt-4">Join the community of 15,000+ members.</p>
                </div>
                <div class="bg-slate-800 p-8 rounded-3xl border border-slate-700">
                    <p class="text-gray-400 text-xs font-bold uppercase tracking-widest mb-2">Badges Earned</p>
                    <div class="flex space-x-2 mt-4 opacity-20">
                        <i class="fas fa-seedling text-3xl"></i>
                        <i class="fas fa-water text-3xl"></i>
                        <i class="fas fa-mountain text-3xl"></i>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="bg-emerald-50 py-12 border-t border-emerald-100 overflow-hidden">
        <div class="flex animate-pulse items-center justify-center space-x-12 whitespace-nowrap text-emerald-800 font-bold text-sm tracking-widest uppercase">
            <span>● Live: New sighting of Blue Whale in Baja</span>
            <span>● Alert: 3 spots left for Kenya Expedition</span>
            <span>● Update: GPS Tag 82-X Active (Snow Leopard)</span>
            <span>● News: Coral recovery up 12% in Moorea</span>
            <span>● Live: New sighting of Blue Whale in Baja</span>
        </div>
    </section>

    <div id="modal" class="fixed inset-0 bg-black/60 backdrop-blur-md hidden z-[100] flex items-center justify-center p-4">
        <div class="bg-white rounded-[40px] max-w-lg w-full p-10 shadow-2xl relative">
            <button onclick="closeModal()" class="absolute top-8 right-8 text-gray-400 hover:text-black transition"><i class="fas fa-times text-xl"></i></button>
            <h3 id="modalTitle" class="text-4xl font-black mb-2 text-emerald-950 leading-tight">Apply</h3>
            <p class="text-gray-400 mb-8 font-medium">This application goes directly to the Lead Researcher.</p>
            <form onsubmit="submitForm(event)" class="space-y-4">
                <input type="text" placeholder="Your Name" required class="w-full p-4 bg-gray-50 rounded-2xl border-none outline-none focus:ring-2 focus:ring-emerald-500">
                <input type="email" placeholder="Email Address" required class="w-full p-4 bg-gray-50 rounded-2xl border-none outline-none focus:ring-2 focus:ring-emerald-500">
                <textarea placeholder="Why are you a good fit for this project?" class="w-full p-4 bg-gray-50 rounded-2xl border-none h-32 outline-none focus:ring-2 focus:ring-emerald-500"></textarea>
                <button type="submit" class="w-full bg-emerald-600 text-white py-5 rounded-2xl font-black text-lg hover:bg-emerald-700 shadow-xl shadow-emerald-200 transition transform active:scale-95">SEND APPLICATION</button>
            </form>
        </div>
    </div>

    <script>
        function filterProjects() {
            let input = document.getElementById('searchInput').value.toLowerCase();
            let cards = document.getElementsByClassName('project-card');
            for (let card of cards) {
                let text = card.innerText.toLowerCase();
                card.style.display = text.includes(input) ? "block" : "none";
            }
        }

        function filterType(type) {
            let cards = document.getElementsByClassName('project-card');
            for (let card of cards) {
                if (type === 'all' || card.getAttribute('data-type') === type) {
                    card.style.display = "block";
                } else {
                    card.style.display = "none";
                }
            }
        }

        function openModal(title) {
            document.getElementById('modalTitle').innerText = title;
            document.getElementById('modal').classList.remove('hidden');
        }

        function closeModal() {
            document.getElementById('modal').classList.add('hidden');
        }

        function submitForm(event) {
            event.preventDefault();
            alert("Application Encrypted & Sent! \n\nThe researcher will review your profile. You'll receive a confirmation email shortly.");
            closeModal();
        }
    </script>
</body>
</html>
