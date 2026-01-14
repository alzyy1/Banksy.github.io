<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Armored Dove: Anatomy of a Paradox</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700;900&display=swap" rel="stylesheet">
    
    <!-- Palette: "Bold Contrast" 
         Primary Dark: #1D3557 (Navy)
         Primary Red: #E63946 (Vibrant Red)
         Secondary Blue: #457B9D (Steel Blue)
         Light/Background: #F1FAEE (Off White)
         Accent: #A8DADC (Light Blue)
    -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        navy: '#1D3557',
                        danger: '#E63946',
                        steel: '#457B9D',
                        bone: '#F1FAEE',
                        sky: '#A8DADC',
                    },
                    fontFamily: {
                        sans: ['Roboto', 'sans-serif'],
                    },
                }
            }
        }
    </script>
    <style>
        body {
            background-color: #F1FAEE;
            color: #1D3557;
        }
        /* Chart Container Styling Rules */
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px; /* Constraint for large screens */
            margin-left: auto;
            margin-right: auto;
            height: 300px; /* Base height */
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 350px;
            }
        }
        .section-card {
            background-color: white;
            border-radius: 0.5rem; /* rounded-lg */
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06); /* shadow-md */
            padding: 1.5rem; /* p-6 */
            margin-bottom: 2rem;
            border-left: 6px solid #E63946;
        }
        .timeline-line {
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            width: 4px;
            height: 100%;
            background-color: #457B9D;
            z-index: 0;
        }
        .crosshair-overlay {
            position: relative;
        }
        .crosshair-overlay::after {
            content: "+";
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 10rem;
            color: rgba(230, 57, 70, 0.2);
            pointer-events: none;
            font-weight: 100;
        }
    </style>
</head>
<body class="font-sans antialiased">

    <!-- Narrative Plan Summary -->
    <!-- 
    1. Introduction: Hook with the artwork title and basic data (Bethlehem, 2005).
    2. Analysis: Visual breakdown using charts for the "Oxymoron" and Color Theory.
    3. Technique: Explaining the Stencil method via cards.
    4. Transfer (The Core): Comparison of 2026 Rhetoric vs Reality using Radar chart.
    5. Timeline: The hypothetical Jan 3, 2026 event flow.
    6. Conclusion: Final synthesis.
    
    NO SVG USED. NO MERMAID USED.
    -->

    <!-- Header / Hero -->
    <header class="bg-navy text-bone py-12 px-4 shadow-lg">
        <div class="max-w-6xl mx-auto text-center">
            <h1 class="text-5xl md:text-7xl font-black mb-4 tracking-tight">ARMORED DOVE</h1>
            <p class="text-xl md:text-2xl font-light text-sky mb-2">Anatomy of a Paradox</p>
            <div class="w-24 h-1 bg-danger mx-auto mt-6"></div>
            <p class="mt-4 text-sm uppercase tracking-widest text-steel">Banksy | Bethlehem | West Bank</p>
        </div>
    </header>

    <main class="max-w-6xl mx-auto px-4 py-8 grid grid-cols-1 gap-8">

        <!-- Section 1: Context & Basisdaten -->
        <section class="grid grid-cols-1 md:grid-cols-2 gap-8">
            <div class="section-card flex flex-col justify-center">
                <h2 class="text-3xl font-bold text-navy mb-4">The Context</h2>
                <p class="text-gray-700 leading-relaxed mb-4">
                    Created around 2005/2007, Banksy's "Armored Dove" is not just graffiti; it is a geopolitical marker. Located on a concrete wall in Bethlehem, directly facing the conflict zone and Israeli separation barriers, the artwork serves as a permanent protest against the concept of "Peace Enforcement."
                </p>
                <div class="grid grid-cols-2 gap-4 mt-4">
                    <div class="bg-bone p-4 rounded text-center">
                        <span class="block text-4xl font-black text-danger">2005</span>
                        <span class="text-xs uppercase font-bold text-navy">Approx. Creation</span>
                    </div>
                    <div class="bg-bone p-4 rounded text-center">
                        <span class="block text-4xl font-black text-danger">BTL</span>
                        <span class="text-xs uppercase font-bold text-navy">Bethlehem, West Bank</span>
                    </div>
                </div>
            </div>
            
            <!-- Visualization: Color Impact -->
            <div class="section-card">
                <h3 class="text-xl font-bold text-navy mb-2">Visual Hierarchy & Color</h3>
                <p class="text-sm text-gray-600 mb-4">
                    The artwork uses extreme color parsimony. While white represents purity, the aggressive red crosshair dominates the viewer's attention, symbolizing an immediate lethal threat.
                </p>
                <!-- Chart Container -->
                <div class="chart-container">
                    <canvas id="colorChart"></canvas>
                </div>
            </div>
        </section>

        <!-- Section 2: The Visual Oxymoron -->
        <section class="section-card">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
                <div>
                    <h2 class="text-3xl font-bold text-navy mb-4">The Oxymoron</h2>
                    <p class="text-gray-700 leading-relaxed mb-6">
                        The core rhetorical device is the <strong>Oxymoron</strong>—a sharp contradiction. Banksy forces two incompatible symbol worlds to collide: the ancient, soft symbols of hope and the modern, hard symbols of war. This clash reveals the absurdity of "militarized peace."
                    </p>
                    <ul class="space-y-3">
                        <li class="flex items-center">
                            <span class="w-3 h-3 bg-sky rounded-full mr-3"></span>
                            <span class="font-bold text-navy w-32">The Thesis:</span>
                            <span class="text-gray-600">Dove, Olive Branch (Innocence)</span>
                        </li>
                        <li class="flex items-center">
                            <span class="w-3 h-3 bg-navy rounded-full mr-3"></span>
                            <span class="font-bold text-navy w-32">The Antithesis:</span>
                            <span class="text-gray-600">Kevlar Vest, Crosshair (Coercion)</span>
                        </li>
                    </ul>
                </div>
                <!-- Chart Container -->
                <div class="chart-container">
                    <canvas id="compositionChart"></canvas>
                </div>
            </div>
        </section>

        <!-- Section 3: Technique (The Stencil) -->
        <section class="w-full mb-8">
            <h2 class="text-3xl font-bold text-navy mb-6 text-center">Technique: The Stencil</h2>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <!-- Card 1 -->
                <div class="bg-white p-6 rounded-lg shadow-md border-t-4 border-steel">
                    <div class="text-5xl text-steel mb-4 font-black">01</div>
                    <h3 class="text-xl font-bold mb-2">Necessity</h3>
                    <p class="text-gray-600 text-sm">Illegal environments require speed. Stencils allow complex images to be applied in seconds, minimizing risk of arrest.</p>
                </div>
                <!-- Card 2 -->
                <div class="bg-white p-6 rounded-lg shadow-md border-t-4 border-steel">
                    <div class="text-5xl text-steel mb-4 font-black">02</div>
                    <h3 class="text-xl font-bold mb-2">Aesthetic</h3>
                    <p class="text-gray-600 text-sm">Hard edges, no gradients, high contrast. The visual "hardness" mirrors the harsh political reality of the location.</p>
                </div>
                <!-- Card 3 -->
                <div class="bg-white p-6 rounded-lg shadow-md border-t-4 border-steel">
                    <div class="text-5xl text-steel mb-4 font-black">03</div>
                    <h3 class="text-xl font-bold mb-2">Integration</h3>
                    <p class="text-gray-600 text-sm">The rough, weathered concrete is not covered but integrated, becoming the texture of the dove itself.</p>
                </div>
            </div>
        </section>

        <!-- Section 4: The Transfer (Venezuela 2026) -->
        <section class="bg-navy text-bone p-8 rounded-lg shadow-xl crosshair-overlay">
            <div class="text-center mb-8">
                <span class="bg-danger text-white px-3 py-1 text-xs font-bold uppercase rounded-full">Scenario Analysis</span>
                <h2 class="text-4xl font-black mt-4">THE TRANSFER: VENEZUELA 2026</h2>
                <p class="text-sky mt-2 text-lg">Banksy's metaphor applied to the hypothetical US Intervention</p>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
                <div>
                    <p class="leading-relaxed mb-6 opacity-90">
                        In the context of the hypothetical January 2026 intervention, the image acts as a decoder. The official narrative uses "Olive Branch" terms—Humanitarian Aid, Democracy, Restoration. However, the operational reality is pure "Kevlar"—a Decapitation Strike targeting national sovereignty.
                    </p>
                    <div class="bg-white/10 p-6 rounded backdrop-blur-sm">
                        <h4 class="text-danger font-bold uppercase tracking-wider mb-4 border-b border-danger/30 pb-2">The Crosshair Meaning</h4>
                        <p class="text-sm">
                            On January 3rd, the red crosshair isn't abstract. It represents the specific, tactical targeting of the legitimate President. The "Peace Mission" is actually a manhunt.
                        </p>
                    </div>
                </div>

                <!-- Chart Container for Radar -->
                <div class="chart-container bg-white/5 rounded-lg p-2">
                    <canvas id="radarChart"></canvas>
                </div>
            </div>
        </section>

        <!-- Section 5: Timeline of Events -->
        <section class="max-w-4xl mx-auto py-8">
            <h2 class="text-3xl font-bold text-navy mb-8 text-center">Anatomy of the 3rd January</h2>
            
            <div class="relative py-8">
                <!-- Vertical Line -->
                <div class="timeline-line hidden md:block"></div>

                <!-- Event 1 -->
                <div class="flex flex-col md:flex-row items-center justify-between mb-8 relative z-10">
                    <div class="w-full md:w-5/12 bg-white p-6 rounded shadow-md border-l-4 border-sky text-right md:text-right">
                        <h4 class="font-bold text-navy text-lg">The "Olive Branch"</h4>
                        <p class="text-xs text-gray-500 mb-2">06:00 AM - Official Statement</p>
                        <p class="text-sm text-gray-700">US announces "Humanitarian Support Mission" to restore order and aid the population.</p>
                    </div>
                    <div class="hidden md:flex w-10 h-10 bg-sky rounded-full items-center justify-center font-bold text-white shadow">1</div>
                    <div class="w-full md:w-5/12 md:invisible"></div> <!-- Spacer -->
                </div>

                <!-- Event 2 -->
                <div class="flex flex-col md:flex-row items-center justify-between mb-8 relative z-10">
                    <div class="w-full md:w-5/12 md:invisible"></div> <!-- Spacer -->
                    <div class="hidden md:flex w-10 h-10 bg-navy rounded-full items-center justify-center font-bold text-white shadow">2</div>
                    <div class="w-full md:w-5/12 bg-white p-6 rounded shadow-md border-l-4 border-navy">
                        <h4 class="font-bold text-navy text-lg">The "Kevlar" Reality</h4>
                        <p class="text-xs text-gray-500 mb-2">07:30 AM - Boots on Ground</p>
                        <p class="text-sm text-gray-700">Heavily armored units secure key infrastructure. No diplomats, only soldiers.</p>
                    </div>
                </div>

                <!-- Event 3 -->
                <div class="flex flex-col md:flex-row items-center justify-between mb-8 relative z-10">
                    <div class="w-full md:w-5/12 bg-white p-6 rounded shadow-md border-l-4 border-danger">
                        <h4 class="font-bold text-danger text-lg">The "Sniper Shot"</h4>
                        <p class="text-xs text-gray-500 mb-2">12:00 PM - Decapitation Strike</p>
                        <p class="text-sm text-gray-700">The President is targeted and detained. The crosshair on the dove's chest becomes reality.</p>
                    </div>
                    <div class="hidden md:flex w-10 h-10 bg-danger rounded-full items-center justify-center font-bold text-white shadow">3</div>
                    <div class="w-full md:w-5/12 md:invisible"></div> <!-- Spacer -->
                </div>
            </div>
        </section>

    </main>

    <footer class="bg-navy text-bone text-center py-8 mt-12">
        <p class="opacity-75 text-sm">&copy; 2026 Canvas Infographics. Analysis based on Banksy's "Armored Dove".</p>
    </footer>

    <!-- Scripts -->
    <script>
        // Label Wrapping Utility (Max 16 chars)
        function wrapLabel(str, maxLen = 16) {
            if (str.length <= maxLen) return str;
            const words = str.split(' ');
            const lines = [];
            let currentLine = words[0];

            for (let i = 1; i < words.length; i++) {
                if (currentLine.length + 1 + words[i].length <= maxLen) {
                    currentLine += ' ' + words[i];
                } else {
                    lines.push(currentLine);
                    currentLine = words[i];
                }
            }
            lines.push(currentLine);
            return lines;
        }

        // Shared Tooltip Configuration
        const sharedTooltipConfig = {
            callbacks: {
                title: function(tooltipItems) {
                    const item = tooltipItems[0];
                    let label = item.chart.data.labels[item.dataIndex];
                    if (Array.isArray(label)) {
                        return label.join(' ');
                    } else {
                        return label;
                    }
                }
            }
        };

        // --- Chart 1: Composition (Doughnut) ---
        const ctxComposition = document.getElementById('compositionChart').getContext('2d');
        const labelsComp = ["Innocence & Hope (Soft Symbols)", "Threat & War (Hard Symbols)"];
        const processedLabelsComp = labelsComp.map(l => wrapLabel(l));

        new Chart(ctxComposition, {
            type: 'doughnut',
            data: {
                labels: processedLabelsComp,
                datasets: [{
                    data: [40, 60], // Conceptual weight: War overwhelms Peace
                    backgroundColor: ['#A8DADC', '#1D3557'],
                    borderColor: '#ffffff',
                    borderWidth: 2,
                    hoverOffset: 10
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { position: 'bottom' },
                    tooltip: sharedTooltipConfig,
                    title: {
                        display: true,
                        text: 'Symbolic Weight Composition'
                    }
                }
            }
        });

        // --- Chart 2: Color Impact (Bar) ---
        const ctxColor = document.getElementById('colorChart').getContext('2d');
        const labelsColor = ["White (Innocence)", "Grey (Concrete/Depression)", "Red (Lethal Threat)"];
        const processedLabelsColor = labelsColor.map(l => wrapLabel(l));

        new Chart(ctxColor, {
            type: 'bar',
            data: {
                labels: processedLabelsColor,
                datasets: [{
                    label: 'Visual Impact Intensity',
                    data: [3, 5, 9], // Red has the highest visual impact despite small area
                    backgroundColor: ['#F1FAEE', '#B0B0B0', '#E63946'],
                    borderColor: '#1D3557',
                    borderWidth: 1
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                scales: {
                    y: { beginAtZero: true, display: false },
                    x: { grid: { display: false } }
                },
                plugins: {
                    legend: { display: false },
                    tooltip: sharedTooltipConfig,
                    title: {
                        display: true,
                        text: 'Visual Impact vs. Surface Area'
                    }
                }
            }
        });

        // --- Chart 3: Rhetoric vs Reality (Radar) ---
        // Comparison of the Venezuela 2026 Scenario
        const ctxRadar = document.getElementById('radarChart').getContext('2d');
        const labelsRadar = ["Humanitarian Rhetoric", "Military Force", "Diplomatic Channels", "Aggression", "Sovereignty Respect"];
        const processedLabelsRadar = labelsRadar.map(l => wrapLabel(l));

        new Chart(ctxRadar, {
            type: 'radar',
            data: {
                labels: processedLabelsRadar,
                datasets: [{
                    label: 'Official US Narrative (The Olive Branch)',
                    data: [9, 3, 8, 1, 9],
                    fill: true,
                    backgroundColor: 'rgba(168, 218, 220, 0.4)', // Sky Blue transparency
                    borderColor: '#A8DADC',
                    pointBackgroundColor: '#A8DADC',
                    pointBorderColor: '#fff',
                    pointHoverBackgroundColor: '#fff',
                    pointHoverBorderColor: '#A8DADC'
                }, {
                    label: 'Ground Reality (The Kevlar Vest)',
                    data: [2, 9, 1, 9, 1],
                    fill: true,
                    backgroundColor: 'rgba(230, 57, 70, 0.4)', // Red transparency
                    borderColor: '#E63946',
                    pointBackgroundColor: '#E63946',
                    pointBorderColor: '#fff',
                    pointHoverBackgroundColor: '#fff',
                    pointHoverBorderColor: '#E63946'
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                scales: {
                    r: {
                        angleLines: { color: 'rgba(255, 255, 255, 0.2)' },
                        grid: { color: 'rgba(255, 255, 255, 0.2)' },
                        pointLabels: {
                            color: 'white',
                            font: { size: 11 }
                        },
                        ticks: { display: false }
                    }
                },
                plugins: {
                    legend: { 
                        position: 'top',
                        labels: { color: 'white' }
                    },
                    tooltip: sharedTooltipConfig
                }
            }
        });
    </script>
</body>
</html>
