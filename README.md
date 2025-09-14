# Analisis-Keuangan-FamilyWallet
<!-- Chosen Palette: Brilliant Blues & Energetic Accents -->
<!-- Application Structure Plan: The infographic follows a clear narrative structure to guide the family through the financial analysis. It starts with a high-impact "Big Picture" section using large stat cards to immediately convey the key metrics (income, outcome, balance). This is followed by a side-by-side "Analysis" section that uses a Donut chart for income composition and a Bar chart for non-essential spending comparison, directly answering the core questions from the report. The page concludes with "Actionable Insights," presenting the report's conclusions as clear, digestible points for evaluation. This top-down structure—from overview to detailed comparison to conclusion—is the most logical way to tell the financial story and facilitate a productive family discussion. -->
<!-- Visualization & Content Choices: 1. Key Metrics (Income, Outcome, Balance) -> Goal: Inform -> Viz: Large Stat Cards (HTML/CSS) -> Justification: Provides an immediate, high-level financial snapshot. 2. Income Contribution -> Goal: Compare/Composition -> Viz: Donut Chart -> Justification: Best for showing part-to-whole proportions, making the primary breadwinner's contribution visually obvious (Chart.js/Canvas, NO SVG). 3. Non-Essential Spending -> Goal: Compare -> Viz: Bar Chart -> Justification: Ideal for directly comparing discrete spending amounts between individuals, clearly ranking them (Chart.js/Canvas, NO SVG). 4. Conclusions -> Goal: Organize -> Viz: Styled Numbered Cards (HTML/CSS) -> Justification: Breaks down the key takeaways into distinct, easy-to-remember points for discussion (NO SVG/Mermaid). -->
<!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
<!DOCTYPE html>
<html lang="id" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Infografis Analisis Keuangan Keluarga</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f0f4f8;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 400px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 320px;
            }
        }
    </style>
</head>
<body class="text-slate-700">

    <main class="container mx-auto p-6 md:p-10 max-w-5xl">

        <header class="text-center mb-12 md:mb-16">
            <h1 class="text-4xl md:text-5xl font-extrabold text-slate-800">Analisis Keuangan Keluarga</h1>
            <p class="mt-3 text-lg text-slate-500 max-w-3xl mx-auto">Sebuah ringkasan visual untuk membantu evaluasi keuangan bersama.</p>
        </header>

        <section id="big-picture" class="mb-12 md:mb-16">
            <h2 class="text-2xl font-bold text-center text-slate-700 mb-8">Gambaran Besar Arus Kas</h2>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 text-center">
                <div class="bg-white p-6 rounded-2xl shadow-lg border-t-4 border-teal-400">
                    <h3 class="text-md font-semibold text-slate-500">TOTAL UANG MASUK</h3>
                    <p class="text-4xl font-bold text-teal-600 mt-2">Rp 8.727.462</p>
                </div>
                <div class="bg-white p-6 rounded-2xl shadow-lg border-t-4 border-orange-500">
                    <h3 class="text-md font-semibold text-slate-500">TOTAL UANG KELUAR</h3>
                    <p class="text-4xl font-bold text-orange-600 mt-2">Rp 8.617.962</p>
                </div>
                <div class="bg-blue-800 text-white p-6 rounded-2xl shadow-xl">
                    <h3 class="text-md font-semibold text-blue-200">SISA SALDO AKHIR</h3>
                    <p class="text-4xl font-bold mt-2">Rp 109.500</p>
                </div>
            </div>
            <p class="text-center mt-8 text-slate-600 bg-slate-200 p-4 rounded-lg">Kondisi keuangan sangat ketat, dengan pengeluaran yang hampir menghabiskan seluruh pemasukan.</p>
        </section>

        <section id="analysis" class="mb-12 md:mb-16">
             <h2 class="text-2xl font-bold text-center text-slate-700 mb-8">Perbandingan Pemasukan & Pengeluaran</h2>
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                <div class="bg-white p-6 rounded-2xl shadow-lg">
                    <h3 class="text-xl font-bold text-center mb-1 text-slate-800">Siapa Pemasok Dana Terbesar?</h3>
                    <p class="text-center text-sm text-slate-500 mb-4">Distribusi total pemasukan per anggota keluarga.</p>
                    <div class="chart-container">
                        <canvas id="pemasukanChart"></canvas>
                    </div>
                     <p class="text-center mt-4 text-sm text-slate-600 px-4">Bapak menjadi sumber pemasukan utama, menyumbang porsi terbesar dari total pendapatan keluarga.</p>
                </div>
                <div class="bg-white p-6 rounded-2xl shadow-lg">
                    <h3 class="text-xl font-bold text-center mb-1 text-slate-800">Siapa dengan Pengeluaran Terbanyak?</h3>
                    <p class="text-center text-sm text-slate-500 mb-4">(Di luar biaya wajib seperti sekolah/kuliah)</p>
                    <div class="chart-container">
                        <canvas id="pengeluaranChart"></canvas>
                    </div>
                    <p class="text-center mt-4 text-sm text-slate-600 px-4">Bisma tercatat memiliki pengeluaran non-wajib tertinggi, menjadikannya area potensial untuk efisiensi.</p>
                </div>
            </div>
        </section>

        <section id="conclusion">
            <h2 class="text-2xl font-bold text-center text-slate-700 mb-8">Tiga Poin Kunci untuk Evaluasi</h2>
            <div class="space-y-6 max-w-3xl mx-auto">
                <div class="flex items-start bg-white p-6 rounded-2xl shadow-lg border-l-4 border-blue-600">
                    <span class="text-3xl font-extrabold text-blue-600 mr-5">1</span>
                    <div>
                        <h4 class="font-bold text-lg text-slate-800">Ketergantungan Pemasukan</h4>
                        <p class="text-slate-600 mt-1">Sumber dana keluarga sangat bergantung pada pemasukan dari Bapak. Penting untuk merencanakan mitigasi risiko jika terjadi sesuatu pada sumber pemasukan utama ini.</p>
                    </div>
                </div>
                 <div class="flex items-start bg-white p-6 rounded-2xl shadow-lg border-l-4 border-orange-600">
                    <span class="text-3xl font-extrabold text-orange-600 mr-5">2</span>
                    <div>
                        <h4 class="font-bold text-lg text-slate-800">Alokasi Pengeluaran Non-Wajib</h4>
                        <p class="text-slate-600 mt-1">Pengeluaran non-wajib yang tinggi, terutama oleh Bisma dan Renza, menunjukkan adanya ruang untuk penghematan. Diskusi tentang prioritas belanja bisa membantu mengendalikan arus kas keluar.</p>
                    </div>
                </div>
                 <div class="flex items-start bg-white p-6 rounded-2xl shadow-lg border-l-4 border-red-600">
                    <span class="text-3xl font-extrabold text-red-600 mr-5">3</span>
                    <div>
                        <h4 class="font-bold text-lg text-slate-800">Minimnya Dana Darurat</h4>
                        <p class="text-slate-600 mt-1">Sisa saldo yang sangat tipis mengindikasikan belum adanya jaring pengaman finansial. Membangun dana darurat harus menjadi prioritas utama untuk menghadapi kebutuhan tak terduga.</p>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const formatRupiah = (value) => new Intl.NumberFormat('id-ID', { style: 'currency', currency: 'IDR', minimumFractionDigits: 0 }).format(value);

            const pemasukanData = {
                labels: ['Bapak', 'Renza', 'Bisma'],
                datasets: [{
                    label: 'Total Pemasukan',
                    data: [7010000, 1190000, 519000],
                    backgroundColor: ['#00449E', '#3A86FF', '#83C5BE'],
                    borderColor: '#ffffff',
                    borderWidth: 4,
                    hoverOffset: 8
                }]
            };

            const pengeluaranData = {
                labels: ['Bisma', 'Renza', 'Bapak'],
                datasets: [{
                    label: 'Pengeluaran Non-Wajib',
                    data: [2779000, 2091270, 898000],
                    backgroundColor: ['#FB5607', '#FFBE0B', '#83C5BE'],
                    borderRadius: 4,
                    borderWidth: 0
                }]
            };

            const baseChartOptions = {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: {
                        position: 'bottom',
                        labels: {
                            padding: 20,
                            font: { size: 14 }
                        }
                    },
                    tooltip: {
                        enabled: true,
                        backgroundColor: '#1e293b',
                        titleFont: { size: 16, weight: 'bold' },
                        bodyFont: { size: 14 },
                        padding: 12,
                        cornerRadius: 8,
                        callbacks: {
                            title: function(tooltipItems) {
                                const item = tooltipItems[0];
                                let label = item.chart.data.labels[item.dataIndex];
                                if (Array.isArray(label)) {
                                  return label.join(' ');
                                }
                                return label;
                            },
                            label: function(context) {
                                let label = context.dataset.label || '';
                                if (label) {
                                    label += ': ';
                                }
                                if (context.parsed.y !== null) {
                                    label += formatRupiah(context.parsed.y);
                                } else if(context.parsed.x !== null) {
                                    label += formatRupiah(context.parsed.x);
                                } else if(context.parsed !== null) {
                                     label += formatRupiah(context.parsed);
                                }
                                return label;
                            }
                        }
                    }
                }
            };
            
            const pemasukanCtx = document.getElementById('pemasukanChart').getContext('2d');
            new Chart(pemasukanCtx, {
                type: 'doughnut',
                data: pemasukanData,
                options: {
                    ...baseChartOptions,
                    cutout: '65%'
                }
            });

            const pengeluaranCtx = document.getElementById('pengeluaranChart').getContext('2d');
            new Chart(pengeluaranCtx, {
                type: 'bar',
                data: pengeluaranData,
                options: {
                    ...baseChartOptions,
                    indexAxis: 'y',
                    plugins: { ...baseChartOptions.plugins, legend: { display: false } },
                    scales: {
                        x: {
                            ticks: {
                                callback: function(value, index, values) {
                                    return value / 1000000 + ' Jt';
                                }
                            }
                        }
                    }
                }
            });
        });
    </script>

</body>
</html>

