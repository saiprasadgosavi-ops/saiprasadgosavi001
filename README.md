<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Guide to Financial Literacy</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Calm Neutrals (Beige, Soft Slate, Muted Teal, Charcoal) -->
    <!-- Application Structure Plan: The application is structured as a single-page, scrollable journey, moving from foundational concepts to practical application. It uses a top navigation bar for quick access to thematic sections: 'Introduction', 'The Four Pillars', 'Key Principles', 'The Goal', and 'Your First Steps'. This structure was chosen over a linear slide format to allow users to explore topics non-linearly and engage with interactive tools at their own pace. The flow is designed to first build understanding (what and why), then provide hands-on tools (how), and finally offer clear, actionable takeaways, enhancing both learning and user retention. -->
    <!-- Visualization & Content Choices: 
        1. Four Pillars Section: Report Info -> Defining Financial Literacy. Goal -> Organize/Inform. Viz -> Interactive Cards. Interaction -> On click, reveal detailed text. Justification -> More engaging than a static list, encourages user exploration. Method -> HTML/CSS/JS.
        2. Budgeting Tool: Report Info -> The Power of a Budget. Goal -> Inform/Organize. Viz -> Dynamic Doughnut Chart. Interaction -> Sliders update chart and values in real-time. Justification -> Turns a theoretical concept into a practical planning tool. Library -> Chart.js.
        3. Compound Growth Calculator: Report Info -> Saving & Investing. Goal -> Show Change. Viz -> Dynamic Line Chart. Interaction -> User inputs values to generate a personalized growth projection. Justification -> Visually demonstrates the long-term impact of investing, which is more powerful than text alone. Library -> Chart.js.
        4. Actionable Checklist: Report Info -> Actionable Steps. Goal -> Inform/Organize. Viz -> Interactive Checklist. Interaction -> Users can check items off the list. Justification -> Provides a sense of accomplishment and a clear, memorable takeaway. Method -> HTML/CSS/JS.
    -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #F5F5F3; /* Warm Beige */
            color: #333333;
        }
        .nav-link {
            transition: color 0.3s ease, border-bottom-color 0.3s ease;
            border-bottom: 2px solid transparent;
        }
        .nav-link:hover, .nav-link.active {
            color: #14B8A6; /* Muted Teal */
            border-bottom-color: #14B8A6;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 400px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 350px;
            }
        }
        .pillar-card {
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .pillar-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
    </style>
</head>
<body class="antialiased">

    <header class="bg-white/80 backdrop-blur-lg shadow-sm sticky top-0 z-50">
        <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
            <h1 class="text-xl md:text-2xl font-bold text-slate-700">Financial Freedom</h1>
            <div class="hidden md:flex space-x-8">
                <a href="#introduction" class="nav-link font-medium text-slate-600">Introduction</a>
                <a href="#pillars" class="nav-link font-medium text-slate-600">The Four Pillars</a>
                <a href="#principles" class="nav-link font-medium text-slate-600">Key Principles</a>
                <a href="#goal" class="nav-link font-medium text-slate-600">The Goal</a>
                <a href="#steps" class="nav-link font-medium text-slate-600">Your First Steps</a>
            </div>
            <button id="mobile-menu-button" class="md:hidden text-slate-700 focus:outline-none">
                <span class="text-2xl">&#9776;</span>
            </button>
        </nav>
        <div id="mobile-menu" class="hidden md:hidden px-6 pb-4">
            <a href="#introduction" class="block py-2 nav-link font-medium text-slate-600">Introduction</a>
            <a href="#pillars" class="block py-2 nav-link font-medium text-slate-600">The Four Pillars</a>
            <a href="#principles" class="block py-2 nav-link font-medium text-slate-600">Key Principles</a>
            <a href="#goal" class="block py-2 nav-link font-medium text-slate-600">The Goal</a>
            <a href="#steps" class="block py-2 nav-link font-medium text-slate-600">Your First Steps</a>
        </div>
    </header>

    <main class="container mx-auto px-6 py-8 md:py-16">

        <section id="introduction" class="text-center mb-16 md:mb-24">
            <h2 class="text-3xl md:text-5xl font-bold text-slate-800 mb-4">Unlock Your Financial Security</h2>
            <p class="text-lg md:text-xl text-slate-600 max-w-3xl mx-auto">
                Financial literacy is the key to taking control of your future. It's not about complex math; it's about understanding your money to make informed decisions, reduce stress, and build a life of freedom and choice. This guide will walk you through the essential concepts and provide interactive tools to help you on your journey.
            </p>
        </section>

        <section id="pillars" class="mb-16 md:mb-24">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold text-slate-800">The Four Pillars of Financial Literacy</h2>
                <p class="mt-4 text-lg text-slate-600 max-w-2xl mx-auto">These four areas form the foundation of a healthy financial life. Click on each pillar to learn more about its role in your journey to financial freedom.</p>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
                <div class="pillar-card bg-white p-6 rounded-lg shadow-md cursor-pointer" data-pillar="earning">
                    <div class="flex items-center mb-4">
                        <span class="text-3xl mr-4">&#128176;</span>
                        <h3 class="text-2xl font-bold text-slate-700">Earning</h3>
                    </div>
                    <p id="earning-text" class="text-slate-600">Generating income through employment, business, or other ventures. This is the starting point of your financial journey.</p>
                </div>
                <div class="pillar-card bg-white p-6 rounded-lg shadow-md cursor-pointer" data-pillar="managing">
                    <div class="flex items-center mb-4">
                        <span class="text-3xl mr-4">&#128203;</span>
                        <h3 class="text-2xl font-bold text-slate-700">Managing</h3>
                    </div>
                    <p id="managing-text" class="text-slate-600">The strategic allocation of your resources through budgeting, planning, and tracking your spending.</p>
                </div>
                <div class="pillar-card bg-white p-6 rounded-lg shadow-md cursor-pointer" data-pillar="growing">
                    <div class="flex items-center mb-4">
                        <span class="text-3xl mr-4">&#127793;</span>
                        <h3 class="text-2xl font-bold text-slate-700">Growing</h3>
                    </div>
                    <p id="growing-text" class="text-slate-600">Accumulating wealth through prudent saving and investing to make your money work for you over the long term.</p>
                </div>
                <div class="pillar-card bg-white p-6 rounded-lg shadow-md cursor-pointer" data-pillar="protecting">
                    <div class="flex items-center mb-4">
                        <span class="text-3xl mr-4">&#128737;</span>
                        <h3 class="text-2xl font-bold text-slate-700">Protecting</h3>
                    </div>
                    <p id="protecting-text" class="text-slate-600">Safeguarding your assets and financial well-being through insurance and effective risk management.</p>
                </div>
            </div>
        </section>

        <section id="principles" class="mb-16 md:mb-24">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold text-slate-800">Key Principles in Action</h2>
                <p class="mt-4 text-lg text-slate-600 max-w-2xl mx-auto">Understanding concepts is one thing; applying them is another. Use these interactive tools to see how key financial principles can work for you.</p>
            </div>

            <div class="bg-white p-8 rounded-lg shadow-lg mb-12">
                <h3 class="text-2xl font-bold text-slate-700 mb-4">1. The Power of a Budget</h3>
                <p class="text-slate-600 mb-6">A budget is a plan for your money. A common guideline is the 50/30/20 rule: 50% for needs, 30% for wants, and 20% for savings. Use the sliders below to see how adjusting your allocations can impact your financial picture.</p>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
                    <div>
                        <div class="mb-4">
                            <label for="needs-slider" class="font-medium text-slate-700">Needs: <span id="needs-value">50</span>%</label>
                            <input id="needs-slider" type="range" min="0" max="100" value="50" class="w-full h-2 bg-slate-200 rounded-lg appearance-none cursor-pointer">
                        </div>
                        <div class="mb-4">
                            <label for="wants-slider" class="font-medium text-slate-700">Wants: <span id="wants-value">30</span>%</label>
                            <input id="wants-slider" type="range" min="0" max="100" value="30" class="w-full h-2 bg-slate-200 rounded-lg appearance-none cursor-pointer">
                        </div>
                        <div>
                            <label for="savings-slider" class="font-medium text-slate-700">Savings: <span id="savings-value">20</span>%</label>
                            <input id="savings-slider" type="range" min="0" max="100" value="20" class="w-full h-2 bg-slate-200 rounded-lg appearance-none cursor-pointer">
                        </div>
                    </div>
                    <div class="chart-container">
                        <canvas id="budgetChart"></canvas>
                    </div>
                </div>
            </div>

            <div class="bg-white p-8 rounded-lg shadow-lg">
                <h3 class="text-2xl font-bold text-slate-700 mb-4">2. The Magic of Compound Growth</h3>
                <p class="text-slate-600 mb-6">Compound interest is your money earning its own money. The earlier you start investing, the more powerful it becomes. Enter some numbers below to project your potential growth over time.</p>
                <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                    <div class="lg:col-span-1 space-y-4">
                        <div>
                            <label for="initial-investment" class="block font-medium text-slate-700">Initial Investment ($)</label>
                            <input type="number" id="initial-investment" value="1000" class="w-full mt-1 p-2 border border-slate-300 rounded-md">
                        </div>
                        <div>
                            <label for="monthly-contribution" class="block font-medium text-slate-700">Monthly Contribution ($)</label>
                            <input type="number" id="monthly-contribution" value="100" class="w-full mt-1 p-2 border border-slate-300 rounded-md">
                        </div>
                        <div>
                            <label for="interest-rate" class="block font-medium text-slate-700">Annual Interest Rate (%)</label>
                            <input type="number" id="interest-rate" value="7" class="w-full mt-1 p-2 border border-slate-300 rounded-md">
                        </div>
                        <div>
                            <label for="years" class="block font-medium text-slate-700">Years to Grow</label>
                            <input type="number" id="years" value="20" class="w-full mt-1 p-2 border border-slate-300 rounded-md">
                        </div>
                        <button id="calculate-growth" class="w-full bg-teal-500 text-white font-bold py-2 px-4 rounded-md hover:bg-teal-600 transition-colors">Calculate</button>
                    </div>
                    <div class="lg:col-span-2 chart-container h-96 max-h-[500px] w-full max-w-full">
                        <canvas id="growthChart"></canvas>
                    </div>
                </div>
            </div>
        </section>

        <section id="goal" class="mb-16 md:mb-24 bg-slate-700 text-white p-8 md:p-12 rounded-lg">
            <div class="text-center mb-8">
                <h2 class="text-3xl md:text-4xl font-bold">The Ultimate Goal: Financial Freedom</h2>
                <p class="mt-4 text-lg text-slate-300 max-w-3xl mx-auto">Financial freedom isn't about being a millionaire. It's a state where your assets generate enough income to cover your expenses, giving you the power to choose how you live and work.</p>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8 text-center">
                <div class="bg-slate-600 p-6 rounded-lg">
                    <h3 class="text-xl font-bold mb-2">Lifestyle by Design</h3>
                    <p class="text-slate-300">Fund a lifestyle you truly want, not one dictated by the need for a paycheck.</p>
                </div>
                <div class="bg-slate-600 p-6 rounded-lg">
                    <h3 class="text-xl font-bold mb-2">Autonomy & Choice</h3>
                    <p class="text-slate-300">Make decisions about your career, location, and time without financial constraints.</p>
                </div>
                <div class="bg-slate-600 p-6 rounded-lg">
                    <h3 class="text-xl font-bold mb-2">Work Becomes an Option</h3>
                    <p class="text-slate-300">Transition from working because you have to, to working because you want to.</p>
                </div>
                <div class="bg-slate-600 p-6 rounded-lg">
                    <h3 class="text-xl font-bold mb-2">Peace of Mind</h3>
                    <p class="text-slate-300">Eliminate the anxiety that comes from worrying about paying bills and meeting obligations.</p>
                </div>
            </div>
        </section>

        <section id="steps" class="text-center">
            <h2 class="text-3xl md:text-4xl font-bold text-slate-800">Your First Steps to Freedom</h2>
            <p class="mt-4 text-lg text-slate-600 max-w-2xl mx-auto mb-12">Developing financial expertise is a gradual process. The most critical step is the commitment to begin. Start with these simple, actionable steps today. Check them off as you go!</p>
            <div class="max-w-md mx-auto bg-white p-8 rounded-lg shadow-lg text-left">
                <div class="flex items-center mb-4">
                    <input type="checkbox" id="step1" class="h-6 w-6 rounded border-gray-300 text-teal-500 focus:ring-teal-500">
                    <label for="step1" class="ml-3 text-lg text-slate-700">Analyze your expenditures for one week.</label>
                </div>
                <div class="flex items-center mb-4">
                    <input type="checkbox" id="step2" class="h-6 w-6 rounded border-gray-300 text-teal-500 focus:ring-teal-500">
                    <label for="step2" class="ml-3 text-lg text-slate-700">Establish a small, achievable savings goal.</label>
                </div>
                <div class="flex items-center mb-4">
                    <input type="checkbox" id="step3" class="h-6 w-6 rounded border-gray-300 text-teal-500 focus:ring-teal-500">
                    <label for="step3" class="ml-3 text-lg text-slate-700">Read one foundational article on budgeting.</label>
                </div>
                <div class="flex items-center">
                    <input type="checkbox" id="step4" class="h-6 w-6 rounded border-gray-300 text-teal-500 focus:ring-teal-500">
                    <label for="step4" class="ml-3 text-lg text-slate-700">Automate your first contribution to savings.</label>
                </div>
            </div>
        </section>

    </main>

    <footer class="bg-slate-800 text-white mt-16 md:mt-24">
        <div class="container mx-auto px-6 py-8 text-center">
            <p class="text-lg">Created by: Saiprasad Uttam Gosavi</p>
            <p class="text-slate-300">B.Tech Electrical Engineering, Sanjivani College of Engineering, Kopargaon</p>
            <p class="text-sm text-slate-400 mt-4">This application is for educational purposes only.</p>
        </div>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const pillarData = {
                earning: "<strong>Earning:</strong> Generating income is the crucial first step. This can come from a primary job, a side business, or investments. The key is to maximize your earning potential while ensuring your income streams are stable and reliable.",
                managing: "<strong>Managing:</strong> This is about knowing where your money goes. Effective management involves creating a budget, tracking expenses, and making conscious decisions about spending to ensure you live within your means and have funds available for your goals.",
                growing: "<strong>Growing:</strong> This pillar focuses on building long-term wealth. Saving provides a safety net for emergencies and short-term goals, while investing allows your money to grow significantly over time through the power of compounding.",
                protecting: "<strong>Protecting:</strong> Protecting your assets is vital. This includes having adequate insurance (health, life, property), creating an emergency fund, and being aware of financial scams to safeguard what you've worked hard to build."
            };

            document.querySelectorAll('.pillar-card').forEach(card => {
                const pillar = card.dataset.pillar;
                const textElement = document.getElementById(`${pillar}-text`);
                const originalText = textElement.innerHTML;

                card.addEventListener('click', () => {
                    if (textElement.innerHTML === originalText) {
                        textElement.innerHTML = pillarData[pillar];
                    } else {
                        textElement.innerHTML = originalText;
                    }
                });
            });
            
            const mobileMenuButton = document.getElementById('mobile-menu-button');
            const mobileMenu = document.getElementById('mobile-menu');
            mobileMenuButton.addEventListener('click', () => {
                mobileMenu.classList.toggle('hidden');
            });

            const navLinks = document.querySelectorAll('.nav-link');
            const sections = document.querySelectorAll('section');

            window.addEventListener('scroll', () => {
                let current = '';
                sections.forEach(section => {
                    const sectionTop = section.offsetTop;
                    if (pageYOffset >= sectionTop - 60) {
                        current = section.getAttribute('id');
                    }
                });

                navLinks.forEach(link => {
                    link.classList.remove('active');
                    if (link.getAttribute('href').includes(current)) {
                        link.classList.add('active');
                    }
                });
            });

            const budgetCtx = document.getElementById('budgetChart').getContext('2d');
            let budgetChart = new Chart(budgetCtx, {
                type: 'doughnut',
                data: {
                    labels: ['Needs', 'Wants', 'Savings'],
                    datasets: [{
                        data: [50, 30, 20],
                        backgroundColor: ['#64748B', '#94A3B8', '#14B8A6'],
                        borderColor: '#F5F5F3',
                        borderWidth: 4
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom',
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return `${context.label}: ${context.raw}%`;
                                }
                            }
                        }
                    }
                }
            });

            const needsSlider = document.getElementById('needs-slider');
            const wantsSlider = document.getElementById('wants-slider');
            const savingsSlider = document.getElementById('savings-slider');
            const needsValue = document.getElementById('needs-value');
            const wantsValue = document.getElementById('wants-value');
            const savingsValue = document.getElementById('savings-value');

            function updateBudgetChart() {
                const needs = parseInt(needsSlider.value);
                const wants = parseInt(wantsSlider.value);
                const savings = parseInt(savingsSlider.value);
                const total = needs + wants + savings;

                if (total > 0) {
                    const needsPercent = Math.round((needs / total) * 100);
                    const wantsPercent = Math.round((wants / total) * 100);
                    const savingsPercent = 100 - needsPercent - wantsPercent;
                    
                    needsValue.textContent = needsPercent;
                    wantsValue.textContent = wantsPercent;
                    savingsValue.textContent = savingsPercent;

                    budgetChart.data.datasets[0].data = [needsPercent, wantsPercent, savingsPercent];
                    budgetChart.update();
                }
            }

            [needsSlider, wantsSlider, savingsSlider].forEach(slider => {
                slider.addEventListener('input', updateBudgetChart);
            });
            
            let growthChart;
            const growthCtx = document.getElementById('growthChart').getContext('2d');
            
            function calculateAndDrawGrowth() {
                const initial = parseFloat(document.getElementById('initial-investment').value) || 0;
                const monthly = parseFloat(document.getElementById('monthly-contribution').value) || 0;
                const rate = parseFloat(document.getElementById('interest-rate').value) / 100 || 0;
                const years = parseInt(document.getElementById('years').value) || 0;

                const labels = [];
                const data = [];
                let futureValue = initial;

                for (let i = 0; i <= years; i++) {
                    labels.push(`Year ${i}`);
                    data.push(futureValue.toFixed(2));
                    futureValue = (futureValue + monthly * 12) * (1 + rate);
                }
                
                if (growthChart) {
                    growthChart.destroy();
                }

                growthChart = new Chart(growthCtx, {
                    type: 'line',
                    data: {
                        labels: labels,
                        datasets: [{
                            label: 'Investment Growth',
                            data: data,
                            borderColor: '#14B8A6',
                            backgroundColor: 'rgba(20, 184, 166, 0.1)',
                            fill: true,
                            tension: 0.1
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        scales: {
                            y: {
                                ticks: {
                                    callback: function(value) {
                                        return '$' + value.toLocaleString();
                                    }
                                }
                            }
                        },
                        plugins: {
                            tooltip: {
                                callbacks: {
                                    label: function(context) {
                                        return `Value: $${parseFloat(context.raw).toLocaleString()}`;
                                    }
                                }
                            }
                        }
                    }
                });
            }

            document.getElementById('calculate-growth').addEventListener('click', calculateAndDrawGrowth);
            calculateAndDrawGrowth();
        });
    </script>
</body>
</html>
