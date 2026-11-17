<html lang="en" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RigPay</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'system-ui', 'sans-serif'],
                    },
                    colors: {
                        slate: {
                            850: '#151e2e',
                            950: '#0a0f1a',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        body {
            font-family: 'Inter', sans-serif;
            -webkit-tap-highlight-color: transparent;
            overflow-x: hidden;
        }
        .tabular-nums {
            font-variant-numeric: tabular-nums;
        }
        /* Custom scrollbar for clean look */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: rgba(15, 23, 42, 0.5);
        }
        ::-webkit-scrollbar-thumb {
            background: #334155;
            border-radius: 9999px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #475569;
        }
        /* Date input calendar icon color fix in dark mode */
        input[type="date"]::-webkit-calendar-picker-indicator,
        input[type="time"]::-webkit-calendar-picker-indicator {
            filter: invert(0.8);
            cursor: pointer;
        }
    </style>
</head>
<body class="bg-slate-950 text-slate-100 min-h-screen pb-16 overflow-x-hidden selection:bg-amber-500 selection:text-slate-950">

    <!-- Top Navigation Header -->
    <header class="sticky top-0 z-30 bg-slate-900/95 backdrop-blur-md border-b border-slate-800 shadow-lg">
        <div class="max-w-6xl mx-auto px-3.5 sm:px-6 py-3 sm:py-3.5 flex items-center justify-between gap-2 sm:gap-3">
            <div class="flex items-center gap-2.5 sm:gap-3 min-w-0">
                <div class="w-10 h-10 sm:w-11 sm:h-11 rounded-xl bg-gradient-to-br from-[#172136] to-[#0a0f1c] border border-slate-700/80 flex items-center justify-center shadow-lg shadow-slate-950/60 shrink-0 overflow-hidden">
                    <!-- Custom RigPay B-Double & Dollar/Clock Logo SVG -->
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 64 64" class="w-8 h-8 sm:w-9 sm:h-9">
                        <defs>
                            <linearGradient id="rigChrome" x1="0%" y1="0%" x2="0%" y2="100%">
                                <stop offset="0%" stop-color="#ffffff"/>
                                <stop offset="55%" stop-color="#cbd5e1"/>
                                <stop offset="100%" stop-color="#64748b"/>
                            </linearGradient>
                        </defs>
                        <!-- Circular Pay & Time Arc -->
                        <path d="M13 33 A20 20 0 0 1 26 14" fill="none" stroke="#64748b" stroke-width="1.6" stroke-linecap="round"/>
                        <path d="M37 14 A20 20 0 0 1 51 33" fill="none" stroke="#64748b" stroke-width="1.6" stroke-linecap="round"/>
                        <!-- Dollar Symbol -->
                        <text x="31.5" y="16.5" text-anchor="middle" fill="#e2e8f0" font-family="Inter, sans-serif" font-weight="800" font-size="11">$</text>
                        <!-- Clock Badge -->
                        <circle cx="47" cy="21" r="5.5" fill="#0f172a" stroke="#94a3b8" stroke-width="1.4"/>
                        <polyline points="47,18 47,21 49.2,22.2" fill="none" stroke="#e2e8f0" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
                        <!-- Rear Trailer (B-Double) -->
                        <rect x="44" y="29" width="13" height="12" rx="1.2" fill="url(#rigChrome)"/>
                        <!-- Lead Trailer (B-Double) -->
                        <rect x="27" y="27" width="15.5" height="14" rx="1.2" fill="url(#rigChrome)"/>
                        <!-- Prime Mover Cab & Hood -->
                        <path d="M16 41 L16 26 Q16 23 19.5 23 L25 23 L25 41 Z" fill="url(#rigChrome)"/>
                        <path d="M7 41 L7 33.5 Q7 31.5 9.5 31.5 L16 31.5 L16 41 Z" fill="url(#rigChrome)"/>
                        <!-- Cab Windshield & Grille Accents -->
                        <rect x="17.5" y="25.5" width="5.5" height="4.5" rx="0.8" fill="#0f172a"/>
                        <rect x="8.5" y="33.5" width="3.5" height="5.5" rx="0.6" fill="#0f172a"/>
                        <!-- Road Line -->
                        <line x1="6" y1="45.5" x2="58" y2="45.5" stroke="#94a3b8" stroke-width="1.6" stroke-linecap="round"/>
                        <!-- Wheels -->
                        <circle cx="12" cy="42.5" r="2.8" fill="#0f172a" stroke="#e2e8f0" stroke-width="1.5"/>
                        <circle cx="22.5" cy="42.5" r="2.6" fill="#0f172a" stroke="#e2e8f0" stroke-width="1.4"/>
                        <circle cx="38.5" cy="42.5" r="2.5" fill="#0f172a" stroke="#e2e8f0" stroke-width="1.4"/>
                        <circle cx="52" cy="42.5" r="2.5" fill="#0f172a" stroke="#e2e8f0" stroke-width="1.4"/>
                        <!-- RIGPAY Label -->
                        <text x="32" y="56.5" text-anchor="middle" fill="#ffffff" font-family="Inter, sans-serif" font-weight="800" font-size="9.5" letter-spacing="0.8">RIGPAY</text>
                    </svg>
                </div>
                <div class="min-w-0">
                    <h1 class="text-lg sm:text-xl font-extrabold tracking-tight text-white flex items-center gap-2 truncate">
                        RigPay
                        <span class="text-[11px] font-bold uppercase tracking-wider px-2 py-0.5 rounded-full bg-amber-500/15 text-amber-400 border border-amber-500/30 shrink-0">AUD</span>
                    </h1>
                    <p class="text-xs text-slate-400 hidden sm:block truncate">Heavy Vehicle Shift & B-Double Pay Tracker</p>
                </div>
            </div>

            <div class="flex items-center gap-1.5 sm:gap-2 shrink-0">
                <button id="btnExportCsv" type="button" class="inline-flex items-center gap-1.5 px-2.5 sm:px-3.5 py-2 sm:py-2.5 rounded-xl bg-slate-800 hover:bg-slate-700 active:scale-[0.98] text-slate-200 text-xs sm:text-sm font-semibold border border-slate-700 transition">
                    <h1 class="text-lg sm:text-xl font-extrabold tracking-tight text-white flex items-center gap-2">
                        RigPay
                        <span class="text-[11px] font-bold uppercase tracking-wider px-2 py-0.5 rounded-full bg-amber-500/15 text-amber-400 border border-amber-500/30">AUD</span>
                    </h1>
                </div>
            </div>

            <div class="flex items-center gap-2">
                <button id="btnOpenAccountSettings" type="button" title="Settings & Cloud Sync" class="inline-flex items-center gap-1.5 px-3 py-2.5 rounded-xl bg-slate-800 hover:bg-slate-700 active:scale-[0.98] text-slate-200 text-xs sm:text-sm font-semibold border border-slate-700 transition relative">
                    <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4 text-amber-400" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <circle cx="12" cy="12" r="3"/>
                        <path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"/>
                    </svg>
                    <span class="hidden sm:inline">Settings</span>
                    <span id="cloudStatusDot" class="w-2 h-2 rounded-full bg-slate-500"></span>
                </button>
            </div>
        </div>
    </header>

    <!-- Toast Notification Banner -->
    <div id="toastContainer" class="fixed bottom-4 right-3 sm:bottom-5 sm:right-5 z-50 flex flex-col gap-2 pointer-events-none max-w-sm w-[calc(100%-1.5rem)] sm:w-[calc(100%-2.5rem)]"></div>

    <!-- Main Content Container -->
    <main class="max-w-6xl mx-auto px-3.5 sm:px-6 pt-5 sm:pt-6 space-y-5 sm:space-y-6">

        <!-- Period Filter & Summary Cards Section -->
        <section aria-label="Earnings Summary" class="space-y-4">
            <div class="flex flex-col md:flex-row md:items-center justify-between gap-3">
                <div>
                    <h2 class="text-base font-bold text-slate-200">Pay Period Overview</h2>
                    <p id="periodRangeLabel" class="text-xs text-slate-400">Showing current week (Mon – Sun)</p>
                </div>
                <!-- Responsive Period Selector Grid on Mobile, Flex Row on Larger Screens -->
                <div class="grid grid-cols-3 sm:flex sm:flex-wrap gap-1.5 bg-slate-900 p-1.5 rounded-xl border border-slate-800 w-full md:w-auto" role="tablist">
                    <button type="button" data-period="this_week" class="period-btn px-2.5 sm:px-3 py-2 sm:py-1.5 rounded-lg text-xs font-semibold transition bg-amber-500 text-slate-950 shadow-sm text-center">This Week</button>
                    <button type="button" data-period="last_week" class="period-btn px-2.5 sm:px-3 py-2 sm:py-1.5 rounded-lg text-xs font-semibold transition text-slate-300 hover:bg-slate-800 text-center">Last Week</button>
                    <button type="button" data-period="fortnight" class="period-btn px-2.5 sm:px-3 py-2 sm:py-1.5 rounded-lg text-xs font-semibold transition text-slate-300 hover:bg-slate-800 text-center">Fortnight</button>
                    <button type="button" data-period="this_month" class="period-btn px-2.5 sm:px-3 py-2 sm:py-1.5 rounded-lg text-xs font-semibold transition text-slate-300 hover:bg-slate-800 text-center">This Month</button>
                    <button type="button" data-period="all" class="period-btn col-span-2 sm:col-span-1 px-2.5 sm:px-3 py-2 sm:py-1.5 rounded-lg text-xs font-semibold transition text-slate-300 hover:bg-slate-800 text-center">All Time</button>
                </div>
            </div>

            <!-- 4 KPI Cards: 1 col on ultra-small phones, 2 cols on phones/tablets, 4 cols on desktop -->
            <div class="grid grid-cols-1 min-[360px]:grid-cols-2 lg:grid-cols-4 gap-3 sm:gap-4">
                <!-- Total Earnings -->
                <div class="bg-gradient-to-br from-slate-900 to-slate-850 border border-slate-800 rounded-2xl p-3.5 sm:p-5 shadow-md relative overflow-hidden">
                    <div class="flex items-center justify-between mb-1.5 sm:mb-2 gap-2">
                        <span class="text-[11px] sm:text-xs font-semibold uppercase tracking-wider text-slate-400">Gross Earnings</span>
                        <span class="w-6 h-6 sm:w-7 sm:h-7 rounded-lg bg-emerald-500/15 text-emerald-400 flex items-center justify-center text-xs sm:text-sm font-bold shrink-0">$</span>
                    </div>
                    <div id="statTotalPay" class="text-xl sm:text-2xl xl:text-3xl font-extrabold text-emerald-400 tabular-nums tracking-tight truncate">$0.00</div>
                    <div id="statShiftCount" class="text-[11px] sm:text-xs text-slate-400 mt-1">0 shifts logged</div>
                </div>

                <!-- Total Hours -->
                <div class="bg-slate-900 border border-slate-800 rounded-2xl p-3.5 sm:p-5 shadow-md">
                    <div class="flex items-center justify-between mb-1.5 sm:mb-2 gap-2">
                        <span class="text-[11px] sm:text-xs font-semibold uppercase tracking-wider text-slate-400">Total Hours</span>
                        <span class="w-6 h-6 sm:w-7 sm:h-7 rounded-lg bg-sky-500/15 text-sky-400 flex items-center justify-center shrink-0">
                            <svg xmlns="http://www.w3.org/2000/svg" class="w-3.5 h-3.5 sm:w-4 sm:h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
                        </span>
                    </div>
                    <div id="statTotalHours" class="text-xl sm:text-2xl xl:text-3xl font-extrabold text-white tabular-nums tracking-tight">0.00 <span class="text-xs sm:text-sm font-semibold text-slate-400">hrs</span></div>
                    <div id="statAvgRate" class="text-[11px] sm:text-xs text-slate-400 mt-1 truncate">Avg: $0.00/hr</div>
                </div>

                <!-- Standard & Weekend Hours -->
                <div class="bg-slate-900 border border-slate-800 rounded-2xl p-3.5 sm:p-5 shadow-md">
                    <div class="flex items-center justify-between mb-1.5 sm:mb-2 gap-2">
                        <span class="text-[11px] sm:text-xs font-semibold uppercase tracking-wider text-slate-400">Single / Non-BD</span>
                        <span class="w-6 h-6 sm:w-7 sm:h-7 rounded-lg bg-indigo-500/15 text-indigo-400 flex items-center justify-center shrink-0">
                            <svg xmlns="http://www.w3.org/2000/svg" class="w-3.5 h-3.5 sm:w-4 sm:h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="1" y="3" width="15" height="13" rx="2"/><polygon points="16 8 20 8 23 11 23 16 16 16 16 8"/><circle cx="5.5" cy="18.5" r="2.5"/><circle cx="18.5" cy="18.5" r="2.5"/></svg>
                        </span>
                    </div>
                    <div id="statBaseHours" class="text-xl sm:text-2xl xl:text-3xl font-extrabold text-slate-100 tabular-nums tracking-tight">0.00 <span class="text-xs sm:text-sm font-semibold text-slate-400">hrs</span></div>
                    <div id="statWeekendHoursNote" class="text-[11px] sm:text-xs text-purple-400 mt-1 truncate">0.00 weekend hrs</div>
                </div>

                <!-- B-Double Hours -->
                <div class="bg-slate-900 border border-slate-800 rounded-2xl p-3.5 sm:p-5 shadow-md">
                    <div class="flex items-center justify-between mb-1.5 sm:mb-2 gap-2">
                        <span class="text-[11px] sm:text-xs font-semibold uppercase tracking-wider text-slate-400">B-Double Hours</span>
                        <span class="w-6 h-6 sm:w-7 sm:h-7 rounded-lg bg-amber-500/15 text-amber-400 flex items-center justify-center font-bold text-[11px] sm:text-xs shrink-0">BD</span>
                    </div>
                    <div id="statBDHours" class="text-xl sm:text-2xl xl:text-3xl font-extrabold text-amber-400 tabular-nums tracking-tight">0.00 <span class="text-xs sm:text-sm font-semibold text-amber-500/70">hrs</span></div>
                    <div id="statBDDaysNote" class="text-[11px] sm:text-xs text-slate-400 mt-1 truncate">0 days driving B-Double</div>
                </div>
            </div>
        </section>

        <!-- Main Workspace Grid: Left = Shift Logger & Rates, Right = Shift History -->
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-5 sm:gap-6 items-start">

            <!-- Left Column (5 cols on lg): Shift Logger + Pay Rate Settings -->
            <div class="lg:col-span-5 space-y-5 sm:space-y-6">

                <!-- 1. Daily Shift Logger Card -->
                <div class="bg-slate-900 border border-slate-800 rounded-2xl shadow-xl overflow-hidden">
                    <div class="px-4 sm:px-5 py-3.5 sm:py-4 bg-slate-850 border-b border-slate-800 flex items-center justify-between gap-2">
                        <div class="flex items-center gap-2.5">
                            <span class="w-2.5 h-2.5 rounded-full bg-amber-400 shrink-0"></span>
                            <h2 id="formTitle" class="text-base font-bold text-white">Log Daily Shift</h2>
                        </div>
                        <button id="btnCancelEdit" type="button" class="hidden text-xs font-semibold px-2.5 py-1 rounded-lg bg-slate-800 text-slate-300 hover:bg-slate-700 border border-slate-700">
                            Cancel Edit
                        </button>
                    </div>

                    <form id="shiftForm" class="p-4 sm:p-5 space-y-4">
                        <input type="hidden" id="editShiftId" value="">

                        <!-- Date & Day Detection -->
                        <div class="space-y-1.5">
                            <div class="flex items-center justify-between gap-2">
                                <label for="shiftDate" class="text-xs font-semibold uppercase tracking-wider text-slate-400">Shift Date</label>
                                <span id="dayOfWeekBadge" class="text-xs font-bold px-2.5 py-0.5 rounded-full bg-slate-800 text-slate-300">Tuesday</span>
                            </div>
                            <input type="date" id="shiftDate" required class="w-full px-3.5 py-3 rounded-xl bg-slate-950 border border-slate-700 text-white text-sm font-medium focus:outline-none focus:border-amber-500 focus:ring-1 focus:ring-amber-500 transition">
                        </div>

                        <!-- Weekend Toggle Switch -->
                        <div class="flex items-center justify-between gap-3 p-3.5 rounded-xl bg-slate-950/80 border border-slate-800">
                            <div class="min-w-0">
                                <div class="text-sm font-semibold text-slate-200 flex flex-wrap items-center gap-1.5">
                                    <span>Weekend Extra Allowance</span>
                                    <span id="weekendAutoTag" class="hidden text-[10px] uppercase font-bold px-1.5 py-0.5 rounded bg-purple-500/20 text-purple-300 border border-purple-500/30">Auto Sat/Sun</span>
                                </div>
                                <p class="text-xs text-slate-400">Adds +$/hr weekend top-up to all shift hours</p>
                            </div>
                            <label class="relative inline-flex items-center cursor-pointer shrink-0">
                                <input type="checkbox" id="isWeekendToggle" class="sr-only peer">
                                <div class="w-12 h-7 bg-slate-800 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[3px] after:left-[3px] after:bg-slate-300 after:rounded-full after:h-5.5 after:w-5.5 after:transition-all peer-checked:bg-purple-600 peer-checked:after:bg-white"></div>
                            </label>
                        </div>

                        <!-- Total Hours Worked + Time Calculator Helper -->
                        <div class="space-y-2">
                            <div class="flex items-center justify-between gap-2">
                                <label for="totalHours" class="text-xs font-semibold uppercase tracking-wider text-slate-400">Total Hours Worked</label>
                                <button type="button" id="btnToggleTimeCalc" class="text-xs font-semibold text-amber-400 hover:text-amber-300 flex items-center gap-1 shrink-0">
                                    <svg xmlns="http://www.w3.org/2000/svg" class="w-3.5 h-3.5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
                                    Start/Finish Helper
                                </button>
                            </div>

                            <!-- Collapsible Start / Finish / Break Calculator (Auto-stacks on narrow screens) -->
                            <div id="timeCalcPanel" class="hidden p-3.5 rounded-xl bg-slate-950 border border-slate-800 space-y-3">
                                <div class="grid grid-cols-1 sm:grid-cols-3 gap-2.5">
                                    <div>
                                        <label for="calcStart" class="block text-[11px] font-medium text-slate-400 mb-1">Start Time</label>
                                        <input type="time" id="calcStart" value="05:00" class="w-full px-2.5 py-2 rounded-lg bg-slate-900 border border-slate-700 text-white text-xs focus:border-amber-500 focus:outline-none">
                                    </div>
                                    <div>
                                        <label for="calcEnd" class="block text-[11px] font-medium text-slate-400 mb-1">Finish Time</label>
                                        <input type="time" id="calcEnd" value="16:30" class="w-full px-2.5 py-2 rounded-lg bg-slate-900 border border-slate-700 text-white text-xs focus:border-amber-500 focus:outline-none">
                                    </div>
                                    <div>
                                        <label for="calcBreak" class="block text-[11px] font-medium text-slate-400 mb-1">Unpaid Break (m)</label>
                                        <input type="number" id="calcBreak" value="30" min="0" step="15" inputmode="numeric" class="w-full px-2.5 py-2 rounded-lg bg-slate-900 border border-slate-700 text-white text-xs focus:border-amber-500 focus:outline-none">
                                    </div>
                                </div>
                                <button type="button" id="btnApplyTimeCalc" class="w-full py-2.5 rounded-lg bg-slate-800 hover:bg-slate-700 text-amber-400 text-xs font-bold border border-slate-700 transition">
                                    Apply Calculated Hours
                                </button>
                            </div>

                            <div class="relative">
                                <input type="number" id="totalHours" step="0.01" min="0.25" max="24" inputmode="decimal" placeholder="e.g. 11.5" required class="w-full px-3.5 py-3 pr-14 rounded-xl bg-slate-950 border border-slate-700 text-white text-base font-bold tabular-nums focus:outline-none focus:border-amber-500 focus:ring-1 focus:ring-amber-500 transition">
                                <span class="absolute right-4 top-1/2 -translate-y-1/2 text-xs font-bold text-slate-500">HRS</span>
                            </div>
                        </div>

                        <!-- B-Double Toggle & Hours Section -->
                        <div class="rounded-xl bg-slate-950/90 border border-slate-800 p-3.5 space-y-3 transition-colors" id="bDoubleBox">
                            <div class="flex items-center justify-between gap-3">
                                <div class="min-w-0">
                                    <div class="text-sm font-bold text-white flex items-center gap-2">
                                        Drove B-Double Today?
                                    </div>
                                    <p class="text-xs text-slate-400">Toggle ON to specify B-Double hours</p>
                                </div>
                                <label class="relative inline-flex items-center cursor-pointer shrink-0">
                                    <input type="checkbox" id="droveBDoubleToggle" class="sr-only peer">
                                    <div class="w-12 h-7 bg-slate-800 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[3px] after:left-[3px] after:bg-slate-300 after:rounded-full after:h-5.5 after:w-5.5 after:transition-all peer-checked:bg-amber-500 peer-checked:after:bg-slate-950"></div>
                                </label>
                            </div>

                            <!-- Conditional B-Double Hours Input -->
                            <div id="bDoubleHoursWrapper" class="hidden pt-2 border-t border-slate-800/80 space-y-2">
                                <div class="flex flex-wrap items-center justify-between gap-2">
                                    <label for="bDoubleHours" class="text-xs font-semibold uppercase tracking-wider text-amber-400">B-Double Hours Driven</label>
                                    <button type="button" id="btnAllShiftBD" class="text-xs font-bold px-2.5 py-1 rounded-lg bg-amber-500/15 hover:bg-amber-500/25 text-amber-400 border border-amber-500/30 transition">
                                        All Shift Hours
                                    </button>
                                </div>
                                <div class="relative">
                                    <input type="number" id="bDoubleHours" step="0.01" min="0" max="24" inputmode="decimal" placeholder="e.g. 8.0" class="w-full px-3.5 py-3 pr-16 rounded-xl bg-slate-900 border border-amber-500/50 text-amber-300 text-base font-bold tabular-nums focus:outline-none focus:border-amber-400 focus:ring-1 focus:ring-amber-400 transition">
                                    <span class="absolute right-4 top-1/2 -translate-y-1/2 text-xs font-bold text-amber-500/70">BD HRS</span>
                                </div>
                                <p id="bdValidationMsg" class="hidden text-xs text-rose-400 font-medium">B-Double hours cannot exceed Total Hours Worked.</p>
                            </div>
                        </div>

                        <!-- Optional Notes / Route / Load -->
                        <div class="space-y-1.5">
                            <label for="shiftNotes" class="text-xs font-semibold uppercase tracking-wider text-slate-400">Route / Load / Notes <span class="text-slate-500 font-normal">(Optional)</span></label>
                            <input type="text" id="shiftNotes" maxlength="100" placeholder="e.g. Brisbane – Toowoomba, Fridge Van, Rego XN42..." class="w-full px-3.5 py-2.5 rounded-xl bg-slate-950 border border-slate-700 text-slate-200 text-sm focus:outline-none focus:border-amber-500 transition">
                        </div>

                        <!-- Live Shift Pay Breakdown Preview -->
                        <div class="rounded-xl bg-gradient-to-r from-slate-950 to-slate-900 border border-slate-800 p-3.5 sm:p-4 space-y-2">
                            <div class="flex items-center justify-between gap-2">
                                <span class="text-xs font-bold uppercase tracking-wider text-slate-400">Live Shift Pay Estimate</span>
                                <span id="previewTotalPay" class="text-lg sm:text-xl font-extrabold text-emerald-400 tabular-nums">$0.00</span>
                            </div>
                            <div id="previewBreakdownLines" class="text-xs text-slate-400 space-y-1.5 pt-1.5 border-t border-slate-800/80 tabular-nums">
                                <div>Enter hours worked to preview pay breakdown.</div>
                            </div>
                        </div>

                        <!-- Submit Button -->
                        <button type="submit" id="btnSaveShift" class="w-full py-3.5 px-5 rounded-xl bg-gradient-to-r from-amber-500 to-orange-500 hover:from-amber-400 hover:to-orange-400 active:scale-[0.99] text-slate-950 font-extrabold text-sm sm:text-base shadow-lg shadow-amber-500/20 transition flex items-center justify-center gap-2">
                            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M19 21H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h11l5 5v11a2 2 0 0 1-2 2z"/><polyline points="17 21 17 13 7 13 7 21"/><polyline points="7 3 7 8 15 8"/></svg>
                            <span id="btnSaveShiftText">Save Shift Log</span>
                        </button>
                    </form>
                </div>

                <!-- 2. Pay Rates Configuration Card -->
                <div class="bg-slate-900 border border-slate-800 rounded-2xl shadow-xl overflow-hidden">
                    <button type="button" id="btnToggleRatesAccordion" class="w-full px-4 sm:px-5 py-3.5 sm:py-4 bg-slate-850 border-b border-slate-800 flex items-center justify-between gap-2 text-left">
                        <div class="flex items-center gap-2.5 min-w-0">
                            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-emerald-400 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="12" y1="1" x2="12" y2="23"/><path d="M17 5H9.5a3.5 3.5 0 0 0 0 7h5a3.5 3.5 0 0 1 0 7H6"/></svg>
                            <div class="min-w-0">
                                <h2 class="text-base font-bold text-white">Pay Rates & Top-Ups</h2>
                                <p id="ratesSummarySub" class="text-xs text-slate-400 tabular-nums truncate">Base $36.00 • BD +$6.00 • Wknd +$18.00</p>
                            </div>
                        </div>
                        <span class="text-[11px] sm:text-xs font-semibold text-emerald-400 bg-emerald-500/10 px-2.5 py-1 rounded-lg border border-emerald-500/20 shrink-0">Auto-Saved</span>
                    </button>

                    <div id="ratesPanelBody" class="p-4 sm:p-5 space-y-4">
                        <!-- 3 Rate Inputs: Stacks on small phones, 3-col on sm+ -->
                        <div class="grid grid-cols-1 sm:grid-cols-3 gap-3">
                            <div>
                                <label for="rateNormal" class="block text-xs font-semibold text-slate-300 mb-1">Ordinary Base ($/hr)</label>
                                <div class="relative">
                                    <span class="absolute left-3 top-1/2 -translate-y-1/2 text-slate-500 font-bold text-sm">$</span>
                                    <input type="number" id="rateNormal" step="0.01" min="0" inputmode="decimal" placeholder="0.00" class="rate-input w-full pl-7 pr-3 py-2.5 rounded-xl bg-slate-950 border border-slate-700 text-white font-bold text-sm tabular-nums focus:border-emerald-500 focus:outline-none">
                                </div>
                            </div>

                            <div>
                                <label for="rateBDouble" class="block text-xs font-semibold text-amber-400 mb-1">B-Double Extra (+$/hr)</label>
                                <div class="relative">
                                    <span class="absolute left-2.5 top-1/2 -translate-y-1/2 text-amber-500/80 font-bold text-xs">+$</span>
                                    <input type="number" id="rateBDouble" step="0.01" min="0" inputmode="decimal" placeholder="0.00" class="rate-input w-full pl-8 pr-3 py-2.5 rounded-xl bg-slate-950 border border-slate-700 text-amber-300 font-bold text-sm tabular-nums focus:border-amber-500 focus:outline-none">
                                </div>
                            </div>

                            <div>
                                <label for="rateWeekend" class="block text-xs font-semibold text-purple-400 mb-1">Weekend Extra (+$/hr)</label>
                                <div class="relative">
                                    <span class="absolute left-2.5 top-1/2 -translate-y-1/2 text-purple-500/80 font-bold text-xs">+$</span>
                                    <input type="number" id="rateWeekend" step="0.01" min="0" inputmode="decimal" placeholder="0.00" class="rate-input w-full pl-8 pr-3 py-2.5 rounded-xl bg-slate-950 border border-slate-700 text-purple-300 font-bold text-sm tabular-nums focus:border-purple-500 focus:outline-none">
                                </div>
                            </div>
                        </div>

                        <!-- Live Effective Stacked Rates Preview Badges: 1 col on tiny screens, 2 col on sm+ -->
                        <div class="rounded-xl bg-slate-950 border border-slate-800 p-3.5 space-y-2">
                            <div class="text-[11px] font-bold uppercase tracking-wider text-slate-400">Effective Stacked Hourly Rates</div>
                            <div class="grid grid-cols-1 min-[420px]:grid-cols-2 gap-2 text-xs tabular-nums">
                                <div class="p-2.5 rounded-lg bg-slate-900 border border-slate-800 flex items-center justify-between gap-2">
                                    <span class="text-slate-400">Weekday Base</span>
                                    <span id="effWeekdayBase" class="font-bold text-white">$36.00/hr</span>
                                </div>
                                <div class="p-2.5 rounded-lg bg-slate-900 border border-amber-500/25 flex items-center justify-between gap-2">
                                    <span class="text-amber-400/90">Weekday B-Double</span>
                                    <span id="effWeekdayBD" class="font-bold text-amber-300">$42.00/hr</span>
                                </div>
                                <div class="p-2.5 rounded-lg bg-slate-900 border border-purple-500/25 flex items-center justify-between gap-2">
                                    <span class="text-purple-400/90">Weekend Base</span>
                                    <span id="effWeekendBase" class="font-bold text-purple-300">$54.00/hr</span>
                                </div>
                                <div class="p-2.5 rounded-lg bg-slate-900 border border-emerald-500/25 flex items-center justify-between gap-2">
                                    <span class="text-emerald-400/90">Weekend B-Double</span>
                                    <span id="effWeekendBD" class="font-bold text-emerald-300">$60.00/hr</span>
                                </div>
                            </div>
                        </div>

                        <!-- Auto-Weekend Detection Setting -->
                        <div class="flex items-center justify-between gap-3 pt-1">
                            <span class="text-xs font-medium text-slate-300">Auto-detect Sat & Sun for Weekend Top-Up</span>
                            <label class="relative inline-flex items-center cursor-pointer shrink-0">
                                <input type="checkbox" id="autoWeekendSetting" checked class="sr-only peer">
                                <div class="w-10 h-6 bg-slate-800 rounded-full peer peer-checked:after:translate-x-full after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-slate-300 after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-purple-600 peer-checked:after:bg-white"></div>
                            </label>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Right Column (7 cols on lg): Shift History Log -->
            <div class="lg:col-span-7 bg-slate-900 border border-slate-800 rounded-2xl shadow-xl overflow-hidden">
                <div class="px-4 sm:px-5 py-3.5 sm:py-4 bg-slate-850 border-b border-slate-800 flex flex-wrap items-center justify-between gap-2.5">
                    <div>
                        <h2 class="text-base font-bold text-white">Shift History Log</h2>
                        <p id="historySubtitle" class="text-xs text-slate-400">Showing shifts for selected period</p>
                    </div>
                    <div class="flex items-center gap-2">
                        <label class="inline-flex items-center gap-2 text-xs text-slate-300 bg-slate-900 px-3 py-2 rounded-lg border border-slate-800 cursor-pointer select-none">
                            <input type="checkbox" id="filterBDOnly" class="rounded accent-amber-500">
                            <span>B-Double Only</span>
                        </label>
                    </div>
                </div>

                <!-- Shift List Container -->
                <div id="shiftListContainer" class="divide-y divide-slate-800/80 max-h-[820px] overflow-y-auto">
                    <!-- Populated dynamically via JS -->
                </div>
            </div>

        </div>
    </main>

    <!-- Custom Reset Confirmation Modal (No alert/confirm used) -->
    <div id="resetModal" class="fixed inset-0 z-50 hidden items-center justify-center p-4 bg-slate-950/80 backdrop-blur-sm overflow-y-auto">
        <div class="bg-slate-900 border border-slate-700 rounded-2xl max-w-md w-full p-5 sm:p-6 shadow-2xl space-y-4 my-auto">
            <div class="flex items-center gap-3 text-rose-400">
                <div class="w-10 h-10 rounded-full bg-rose-500/15 flex items-center justify-center shrink-0">
                    <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M10.29 3.86L1.82 18a2 2 0 0 0 1.71 3h16.94a2 2 0 0 0 1.71-3L13.71 3.86a2 2 0 0 0-3.42 0z"/><line x1="12" y1="9" x2="12" y2="13"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>
                </div>
                <h3 class="text-lg font-bold text-white">Reset Shift Data?</h3>
            </div>
            <p class="text-sm text-slate-300 leading-relaxed">
                This will permanently delete all recorded shifts from your account and device storage. Your saved pay rates will remain intact. Consider exporting a CSV backup first.
            </p>
            <div class="flex flex-col-reverse sm:flex-row sm:items-center justify-end gap-2 sm:gap-2.5 pt-2">
                <button type="button" id="btnCancelReset" class="w-full sm:w-auto px-4 py-2.5 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-200 text-sm font-semibold transition">
                    Cancel
                </button>
                <button type="button" id="btnConfirmReset" class="w-full sm:w-auto px-4 py-2.5 rounded-xl bg-rose-600 hover:bg-rose-500 text-white text-sm font-bold shadow-lg shadow-rose-600/20 transition">
                    Delete All Shifts
                </button>
            </div>
        </div>
    </div>

    <!-- Account & Cloud Backup Settings Modal -->
    <div id="accountModal" class="fixed inset-0 z-50 hidden items-center justify-center p-4 bg-slate-950/80 backdrop-blur-sm overflow-y-auto">
        <div class="bg-slate-900 border border-slate-700 rounded-2xl max-w-md w-full p-5 sm:p-6 shadow-2xl space-y-5 my-auto">
            <div class="flex items-center justify-between border-b border-slate-800 pb-3.5 gap-2">
                <div class="flex items-center gap-2.5 min-w-0">
                    <div class="w-9 h-9 rounded-xl bg-amber-500/15 text-amber-400 flex items-center justify-center shrink-0">
                        <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M17.5 19H9a7 7 0 1 1 6.71-9h1.79a4.5 4.5 0 1 1 0 9Z"/></svg>
                    </div>
                    <div class="min-w-0">
                        <h3 class="text-base font-bold text-white truncate">Account & Cloud Sync</h3>
                        <p class="text-xs text-slate-400 truncate">Save shifts & rates to your account</p>
                    </div>
                </div>
                <button type="button" id="btnCloseAccountModal" class="p-2 rounded-lg text-slate-400 hover:text-white hover:bg-slate-800 transition shrink-0">
                    <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
                </button>
            </div>

            <!-- Connection Status Card -->
            <div class="p-4 rounded-xl bg-slate-950 border border-slate-800 space-y-3">
                <div class="flex items-center justify-between gap-2">
                    <span class="text-xs font-semibold uppercase tracking-wider text-slate-400">Sync Status</span>
                    <span id="cloudStatusBadge" class="text-xs font-bold px-2.5 py-0.5 rounded-full bg-slate-800 text-slate-300">Connecting...</span>
                </div>
                <div id="accountUserDetails" class="text-xs text-slate-300 space-y-1">
                    <div class="font-semibold text-white" id="accountDisplayName">Device Session</div>
                    <div class="text-slate-400 break-all" id="accountUserSub">Checking cloud connection...</div>
                </div>
            </div>

            <!-- Google Sign-In / Sign-Out Action -->
            <div class="space-y-2.5">
                <button type="button" id="btnGoogleSignIn" class="w-full py-3 px-4 rounded-xl bg-white hover:bg-slate-100 active:scale-[0.99] text-slate-900 font-bold text-sm shadow-md transition flex items-center justify-center gap-2.5">
                    <svg class="w-4 h-4 shrink-0" viewBox="0 0 24 24">
                        <path fill="#4285F4" d="M23.745 12.27c0-.7-.06-1.4-.19-2.07H12v4.51h6.6c-.29 1.52-1.14 2.82-2.4 3.68v3.05h3.88c2.27-2.09 3.665-5.17 3.665-9.17Z"/>
                        <path fill="#34A853" d="M12 24c3.24 0 5.95-1.08 7.93-2.91l-3.88-3.05c-1.08.72-2.45 1.16-4.05 1.16-3.12 0-5.77-2.11-6.72-4.96H1.29v3.14C3.26 21.3 7.31 24 12 24Z"/>
                        <path fill="#FBBC05" d="M5.28 14.24c-.24-.72-.38-1.49-.38-2.24s.14-1.52.38-2.24V6.62H1.29C.47 8.24 0 10.06 0 12s.47 3.76 1.29 5.38l3.99-3.14Z"/>
                        <path fill="#EA4335" d="M12 4.75c1.77 0 3.35.61 4.6 1.8l3.42-3.42C17.95 1.19 15.24 0 12 0 7.31 0 3.26 2.7 1.29 6.62l3.99 3.14c.95-2.85 3.6-4.96 6.72-4.96Z"/>
                    </svg>
                    <span id="btnGoogleSignInText">Sign in with Google</span>
                </button>

                <button type="button" id="btnSyncNow" class="w-full py-2.5 px-4 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-200 text-xs font-semibold border border-slate-700 transition flex items-center justify-center gap-2">
                    <svg xmlns="http://www.w3.org/2000/svg" class="w-3.5 h-3.5 text-emerald-400" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="23 4 23 10 17 10"/><polyline points="1 20 1 14 7 14"/><path d="M3.51 9a9 9 0 0 1 14.85-3.36L23 10M1 14l4.64 4.36A9 9 0 0 0 20.49 15"/></svg>
                    <span>Backup Local Shifts to Cloud Now</span>
                </button>

                <button type="button" id="btnExportCsv" class="w-full py-2.5 px-4 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-200 text-xs font-semibold border border-slate-700 transition flex items-center justify-center gap-2">
                    <svg xmlns="http://www.w3.org/2000/svg" class="w-3.5 h-3.5 text-emerald-400" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/>
                        <polyline points="7 10 12 15 17 10"/>
                        <line x1="12" y1="15" x2="12" y2="3"/>
                    </svg>
                    <span>Export Shifts to CSV</span>
                </button>
            </div>

            <p class="text-[11px] text-slate-400 leading-relaxed">
                All shifts and pay rates are automatically backed up to your account whenever you add, edit, or update rates, and any existing device shifts merge seamlessly when you sign in.
            </p>

            <!-- Danger Zone: Reset All Shift Data -->
            <div class="pt-3 border-t border-slate-800 flex flex-col sm:flex-row sm:items-center justify-between gap-3">
                <div>
                    <div class="text-xs font-bold text-rose-400">Danger Zone</div>
                    <div class="text-[11px] text-slate-400">Permanently clear all logged shifts</div>
                </div>
                <button type="button" id="btnOpenReset" class="w-full sm:w-auto inline-flex items-center justify-center gap-1.5 px-3 py-2 rounded-xl bg-rose-950/60 hover:bg-rose-900/80 text-rose-300 hover:text-rose-200 text-xs font-bold border border-rose-800/70 transition shrink-0">
                    <svg xmlns="http://www.w3.org/2000/svg" class="w-3.5 h-3.5 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <polyline points="3 6 5 6 21 6"/>
                        <path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"/>
                    </svg>
                    <span>Reset All Data</span>
                </button>
            </div>
        </div>
    </div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import {
            getAuth,
            signInAnonymously,
            signInWithCustomToken,
            GoogleAuthProvider,
            signInWithPopup,
            linkWithPopup,
            signOut,
            onAuthStateChanged
        } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import {
            getFirestore,
            doc,
            setDoc,
            deleteDoc,
            onSnapshot,
            collection,
            writeBatch
        } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        /**
         * RigPay — Truck Driver Hours & Pay Tracker
         * Includes Account & Cloud Sync settings with Google Sign-In,
         * automatic cloud backup, and seamless local shift merging.
         */
        (function () {
            'use strict';

            // Storage Keys (used for initial migration/cache)
            const STORAGE_KEY_RATES = 'rigpay_rates_v2';
            const STORAGE_KEY_SHIFTS = 'rigpay_shifts_v1';

            // Default Configuration (B-Double and Weekend are +$/hr top-ups on top of Ordinary Base)
            const DEFAULT_RATES = {
                normalRate: 36.00,
                bDoubleRate: 6.00,
                weekendRate: 18.00,
                autoWeekend: true
            };

            // Application State
            let state = {
                rates: { ...DEFAULT_RATES },
                shifts: [],
                period: 'this_week', // 'this_week' | 'last_week' | 'fortnight' | 'this_month' | 'all'
                filterBDOnly: false
            };

            // Cloud / Auth State
            let app = null;
            let auth = null;
            let db = null;
            let currentUser = null;
            let unsubRates = null;
            let unsubShifts = null;
            const appId = typeof __app_id !== 'undefined' ? __app_id : 'rigpay-default-app';

            // DOM Element References
            const el = {
                // Header & Actions
                btnExportCsv: document.getElementById('btnExportCsv'),
                btnOpenAccountSettings: document.getElementById('btnOpenAccountSettings'),
                cloudStatusDot: document.getElementById('cloudStatusDot'),
                btnOpenReset: document.getElementById('btnOpenReset'),
                resetModal: document.getElementById('resetModal'),
                btnCancelReset: document.getElementById('btnCancelReset'),
                btnConfirmReset: document.getElementById('btnConfirmReset'),
                toastContainer: document.getElementById('toastContainer'),

                // Account Settings Modal
                accountModal: document.getElementById('accountModal'),
                btnCloseAccountModal: document.getElementById('btnCloseAccountModal'),
                cloudStatusBadge: document.getElementById('cloudStatusBadge'),
                accountDisplayName: document.getElementById('accountDisplayName'),
                accountUserSub: document.getElementById('accountUserSub'),
                btnGoogleSignIn: document.getElementById('btnGoogleSignIn'),
                btnGoogleSignInText: document.getElementById('btnGoogleSignInText'),
                btnSyncNow: document.getElementById('btnSyncNow'),

                // Summary & Filters
                periodRangeLabel: document.getElementById('periodRangeLabel'),
                periodBtns: document.querySelectorAll('.period-btn'),
                statTotalPay: document.getElementById('statTotalPay'),
                statShiftCount: document.getElementById('statShiftCount'),
                statTotalHours: document.getElementById('statTotalHours'),
                statAvgRate: document.getElementById('statAvgRate'),
                statBaseHours: document.getElementById('statBaseHours'),
                statWeekendHoursNote: document.getElementById('statWeekendHoursNote'),
                statBDHours: document.getElementById('statBDHours'),
                statBDDaysNote: document.getElementById('statBDDaysNote'),

                // Shift Form
                formTitle: document.getElementById('formTitle'),
                btnCancelEdit: document.getElementById('btnCancelEdit'),
                shiftForm: document.getElementById('shiftForm'),
                editShiftId: document.getElementById('editShiftId'),
                shiftDate: document.getElementById('shiftDate'),
                dayOfWeekBadge: document.getElementById('dayOfWeekBadge'),
                weekendAutoTag: document.getElementById('weekendAutoTag'),
                isWeekendToggle: document.getElementById('isWeekendToggle'),
                totalHours: document.getElementById('totalHours'),
                btnToggleTimeCalc: document.getElementById('btnToggleTimeCalc'),
                timeCalcPanel: document.getElementById('timeCalcPanel'),
                calcStart: document.getElementById('calcStart'),
                calcEnd: document.getElementById('calcEnd'),
                calcBreak: document.getElementById('calcBreak'),
                btnApplyTimeCalc: document.getElementById('btnApplyTimeCalc'),

                // B-Double Fields
                bDoubleBox: document.getElementById('bDoubleBox'),
                droveBDoubleToggle: document.getElementById('droveBDoubleToggle'),
                bDoubleHoursWrapper: document.getElementById('bDoubleHoursWrapper'),
                bDoubleHours: document.getElementById('bDoubleHours'),
                btnAllShiftBD: document.getElementById('btnAllShiftBD'),
                bdValidationMsg: document.getElementById('bdValidationMsg'),

                // Notes & Preview
                shiftNotes: document.getElementById('shiftNotes'),
                previewTotalPay: document.getElementById('previewTotalPay'),
                previewBreakdownLines: document.getElementById('previewBreakdownLines'),
                btnSaveShiftText: document.getElementById('btnSaveShiftText'),

                // Pay Rates Panel
                ratesSummarySub: document.getElementById('ratesSummarySub'),
                rateNormal: document.getElementById('rateNormal'),
                rateBDouble: document.getElementById('rateBDouble'),
                rateWeekend: document.getElementById('rateWeekend'),
                effWeekdayBase: document.getElementById('effWeekdayBase'),
                effWeekdayBD: document.getElementById('effWeekdayBD'),
                effWeekendBase: document.getElementById('effWeekendBase'),
                effWeekendBD: document.getElementById('effWeekendBD'),
                autoWeekendSetting: document.getElementById('autoWeekendSetting'),

                // History List
                historySubtitle: document.getElementById('historySubtitle'),
                filterBDOnly: document.getElementById('filterBDOnly'),
                shiftListContainer: document.getElementById('shiftListContainer')
            };

            // Utility Formatters
            function formatAUD(amount) {
                const num = Number.isFinite(amount) ? amount : 0;
                return num.toLocaleString('en-AU', {
                    style: 'currency',
                    currency: 'AUD',
                    minimumFractionDigits: 2,
                    maximumFractionDigits: 2
                });
            }

            function formatHours(hrs) {
                const num = Number.isFinite(hrs) ? hrs : 0;
                return Number.isInteger(num) ? num.toFixed(1) : parseFloat(num.toFixed(2)).toString();
            }

            function getTodayISO() {
                const now = new Date();
                const year = now.getFullYear();
                const month = String(now.getMonth() + 1).padStart(2, '0');
                const day = String(now.getDate()).padStart(2, '0');
                return `${year}-${month}-${day}`;
            }

            function parseLocalDate(isoStr) {
                const [y, m, d] = isoStr.split('-').map(Number);
                return new Date(y, m - 1, d);
            }

            function formatDisplayDate(isoStr) {
                const d = parseLocalDate(isoStr);
                return d.toLocaleDateString('en-AU', {
                    weekday: 'short',
                    day: 'numeric',
                    month: 'short',
                    year: 'numeric'
                });
            }

            function escapeHtml(str) {
                return String(str)
                    .replace(/&/g, '&amp;')
                    .replace(/</g, '&lt;')
                    .replace(/>/g, '&gt;')
                    .replace(/"/g, '&quot;');
            }

            function showToast(message, type = 'success') {
                const toast = document.createElement('div');
                const colors = type === 'error'
                    ? 'bg-rose-950/95 border-rose-700 text-rose-200'
                    : 'bg-slate-900/95 border-emerald-500/50 text-emerald-300';
                toast.className = `pointer-events-auto px-4 py-3 rounded-xl border shadow-xl text-xs sm:text-sm font-semibold flex items-center gap-2.5 transform transition-all duration-300 translate-y-2 opacity-0 ${colors}`;
                toast.innerHTML = `
                    <span class="w-2 h-2 rounded-full ${type === 'error' ? 'bg-rose-400' : 'bg-emerald-400'}"></span>
                    <span>${escapeHtml(message)}</span>
                `;
                el.toastContainer.appendChild(toast);
                requestAnimationFrame(() => {
                    toast.classList.remove('translate-y-2', 'opacity-0');
                });
                setTimeout(() => {
                    toast.classList.add('opacity-0', 'translate-y-2');
                    setTimeout(() => toast.remove(), 300);
                }, 2800);
            }

            // Persistence Layer (Cloud + Local Fallback)
            function loadLocalCache() {
                try {
                    const savedRates = localStorage.getItem(STORAGE_KEY_RATES);
                    if (savedRates) {
                        state.rates = { ...DEFAULT_RATES, ...JSON.parse(savedRates) };
                    }
                    const savedShifts = localStorage.getItem(STORAGE_KEY_SHIFTS);
                    if (savedShifts) {
                        const parsed = JSON.parse(savedShifts);
                        if (Array.isArray(parsed)) {
                            state.shifts = parsed;
                        }
                    }
                } catch (err) {
                    console.error('Failed to load cached data:', err);
                }
            }

            function saveLocalCache() {
                try {
                    localStorage.setItem(STORAGE_KEY_RATES, JSON.stringify(state.rates));
                    localStorage.setItem(STORAGE_KEY_SHIFTS, JSON.stringify(state.shifts));
                } catch (err) {
                    console.error('Failed to update local cache:', err);
                }
            }

            async function saveRates() {
                saveLocalCache();
                if (!db || !currentUser) return;
                try {
                    const ratesRef = doc(db, 'artifacts', appId, 'users', currentUser.uid, 'settings', 'rates');
                    await setDoc(ratesRef, {
                        ...state.rates,
                        updatedAt: Date.now()
                    }, { merge: true });
                } catch (err) {
                    console.error('Cloud rate save error:', err);
                }
            }

            async function saveSingleShiftToCloud(shift) {
                saveLocalCache();
                if (!db || !currentUser || !shift || !shift.id) return;
                try {
                    const shiftRef = doc(db, 'artifacts', appId, 'users', currentUser.uid, 'shifts', shift.id);
                    await setDoc(shiftRef, shift);
                } catch (err) {
                    console.error('Cloud shift save error:', err);
                }
            }

            async function deleteSingleShiftFromCloud(shiftId) {
                saveLocalCache();
                if (!db || !currentUser || !shiftId) return;
                try {
                    const shiftRef = doc(db, 'artifacts', appId, 'users', currentUser.uid, 'shifts', shiftId);
                    await deleteDoc(shiftRef);
                } catch (err) {
                    console.error('Cloud shift delete error:', err);
                }
            }

            async function uploadAllLocalShiftsToCloud(showNotification = false) {
                if (!db || !currentUser) {
                    if (showNotification) showToast('Cloud account not connected yet', 'error');
                    return;
                }
                try {
                    const batch = writeBatch(db);
                    const ratesRef = doc(db, 'artifacts', appId, 'users', currentUser.uid, 'settings', 'rates');
                    batch.set(ratesRef, { ...state.rates, updatedAt: Date.now() }, { merge: true });

                    state.shifts.forEach(shift => {
                        if (shift && shift.id) {
                            const shiftRef = doc(db, 'artifacts', appId, 'users', currentUser.uid, 'shifts', shift.id);
                            batch.set(shiftRef, shift, { merge: true });
                        }
                    });
                    await batch.commit();
                    if (showNotification) {
                        showToast(`Backed up ${state.shifts.length} shifts & pay rates to cloud`);
                    }
                } catch (err) {
                    console.error('Batch cloud upload failed:', err);
                    if (showNotification) showToast('Could not complete cloud backup', 'error');
                }
            }

            function updateAccountModalUI() {
                if (!currentUser) {
                    el.cloudStatusDot.className = 'w-2 h-2 rounded-full bg-slate-500';
                    el.cloudStatusBadge.className = 'text-xs font-bold px-2.5 py-0.5 rounded-full bg-slate-800 text-slate-300';
                    el.cloudStatusBadge.textContent = 'Offline / Local';
                    el.accountDisplayName.textContent = 'Not Signed In';
                    el.accountUserSub.textContent = 'Shifts are saved on this device.';
                    el.btnGoogleSignInText.textContent = 'Sign in with Google';
                    return;
                }

                const googleProvider = (currentUser.providerData || []).find(p => p.providerId === 'google.com');
                if (googleProvider) {
                    el.cloudStatusDot.className = 'w-2 h-2 rounded-full bg-emerald-400';
                    el.cloudStatusBadge.className = 'text-xs font-bold px-2.5 py-0.5 rounded-full bg-emerald-500/20 text-emerald-300 border border-emerald-500/30';
                    el.cloudStatusBadge.textContent = 'Google Synced';
                    el.accountDisplayName.textContent = googleProvider.displayName || 'Google Account';
                    el.accountUserSub.textContent = googleProvider.email || `User ID: ${currentUser.uid}`;
                    el.btnGoogleSignInText.textContent = 'Sign Out of Google';
                } else {
                    el.cloudStatusDot.className = 'w-2 h-2 rounded-full bg-amber-400';
                    el.cloudStatusBadge.className = 'text-xs font-bold px-2.5 py-0.5 rounded-full bg-amber-500/20 text-amber-300 border border-amber-500/30';
                    el.cloudStatusBadge.textContent = 'Device Cloud Active';
                    el.accountDisplayName.textContent = 'Guest Cloud Session';
                    el.accountUserSub.textContent = `Account ID: ${currentUser.uid}`;
                    el.btnGoogleSignInText.textContent = 'Sign in with Google';
                }
            }

            function attachCloudListeners(user) {
                if (unsubRates) { unsubRates(); unsubRates = null; }
                if (unsubShifts) { unsubShifts(); unsubShifts = null; }
                if (!db || !user) return;

                const ratesRef = doc(db, 'artifacts', appId, 'users', user.uid, 'settings', 'rates');
                unsubRates = onSnapshot(ratesRef, (snap) => {
                    if (snap.exists()) {
                        const data = snap.data();
                        state.rates = {
                            normalRate: Number.isFinite(data.normalRate) ? data.normalRate : state.rates.normalRate,
                            bDoubleRate: Number.isFinite(data.bDoubleRate) ? data.bDoubleRate : state.rates.bDoubleRate,
                            weekendRate: Number.isFinite(data.weekendRate) ? data.weekendRate : state.rates.weekendRate,
                            autoWeekend: typeof data.autoWeekend === 'boolean' ? data.autoWeekend : state.rates.autoWeekend
                        };
                        saveLocalCache();
                        const activeEl = document.activeElement;
                        const isEditingRate = activeEl && activeEl.classList.contains('rate-input');
                        syncRatesUI(!isEditingRate);
                        updateLivePreview();
                        renderDashboard();
                    } else {
                        saveRates();
                    }
                }, (err) => {
                    console.error('Rates listener error:', err);
                });

                const shiftsCol = collection(db, 'artifacts', appId, 'users', user.uid, 'shifts');
                unsubShifts = onSnapshot(shiftsCol, (snapshot) => {
                    const cloudShifts = [];
                    snapshot.forEach(docSnap => {
                        cloudShifts.push({ id: docSnap.id, ...docSnap.data() });
                    });

                    // Merge any local-only shifts into cloud on first connection
                    const cloudIds = new Set(cloudShifts.map(s => s.id));
                    const localOnly = state.shifts.filter(s => s && s.id && !cloudIds.has(s.id));

                    if (localOnly.length > 0) {
                        localOnly.forEach(s => saveSingleShiftToCloud(s));
                        state.shifts = [...cloudShifts, ...localOnly];
                    } else {
                        state.shifts = cloudShifts;
                    }

                    saveLocalCache();
                    renderDashboard();
                }, (err) => {
                    console.error('Shifts listener error:', err);
                });
            }

            async function initCloudAuth() {
                try {
                    if (typeof __firebase_config === 'undefined') {
                        updateAccountModalUI();
                        return;
                    }
                    const firebaseConfig = JSON.parse(__firebase_config);
                    app = initializeApp(firebaseConfig);
                    auth = getAuth(app);
                    db = getFirestore(app);

                    onAuthStateChanged(auth, (user) => {
                        currentUser = user;
                        updateAccountModalUI();
                        if (user) {
                            attachCloudListeners(user);
                        }
                    });

                    if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                        await signInWithCustomToken(auth, __initial_auth_token);
                    } else {
                        await signInAnonymously(auth);
                    }
                } catch (err) {
                    console.error('Cloud auth initialization error:', err);
                    updateAccountModalUI();
                }
            }

            async function handleGoogleButtonClick() {
                if (!auth) {
                    showToast('Cloud sign-in is unavailable in offline preview', 'error');
                    return;
                }

                const isGoogleConnected = currentUser && (currentUser.providerData || []).some(p => p.providerId === 'google.com');
                if (isGoogleConnected) {
                    try {
                        await signOut(auth);
                        await signInAnonymously(auth);
                        showToast('Signed out of Google');
                    } catch (err) {
                        console.error('Sign out error:', err);
                        showToast('Could not sign out', 'error');
                    }
                    return;
                }

                const provider = new GoogleAuthProvider();
                try {
                    if (currentUser && currentUser.isAnonymous) {
                        try {
                            await linkWithPopup(currentUser, provider);
                        } catch (linkErr) {
                            if (linkErr.code === 'auth/credential-already-in-use' || linkErr.code === 'auth/email-already-in-use') {
                                await signInWithPopup(auth, provider);
                            } else {
                                throw linkErr;
                            }
                        }
                    } else {
                        await signInWithPopup(auth, provider);
                    }
                    await uploadAllLocalShiftsToCloud(false);
                    updateAccountModalUI();
                    showToast('Signed in with Google & synced!');
                } catch (err) {
                    console.error('Google sign-in error:', err);
                    if (err.code !== 'auth/popup-closed-by-user') {
                        showToast('Google sign-in popup blocked or unavailable', 'error');
                    }
                }
            }

            /**
             * Core Pay Calculation Engine
             * Ordinary Base applies to all hours worked; B-Double Extra (+$/hr) adds on top
             * for B-Double hours; Weekend Extra (+$/hr) adds on top for all weekend hours.
             */
            function calculateShiftPay(shift, rates = state.rates) {
                const totalHrs = Math.max(0, parseFloat(shift.totalHours) || 0);
                const bdHrs = shift.droveBDouble ? Math.min(totalHrs, Math.max(0, parseFloat(shift.bDoubleHours) || 0)) : 0;
                const nonBdHrs = Math.max(0, +(totalHrs - bdHrs).toFixed(4));
                const isWeekend = Boolean(shift.isWeekend);

                const baseRate = Math.max(0, parseFloat(rates.normalRate) || 0);
                const bdExtraRate = Math.max(0, parseFloat(rates.bDoubleRate) || 0);
                const weekendExtraRate = isWeekend ? Math.max(0, parseFloat(rates.weekendRate) || 0) : 0;

                // Component pay totals
                const basePay = +(totalHrs * baseRate).toFixed(2);
                const bdExtraPay = +(bdHrs * bdExtraRate).toFixed(2);
                const weekendExtraPay = +(totalHrs * weekendExtraRate).toFixed(2);
                const totalPay = +(basePay + bdExtraPay + weekendExtraPay).toFixed(2);

                // Effective hourly rates for summary badges / CSV
                const effectiveSingleRate = +(baseRate + weekendExtraRate).toFixed(2);
                const effectiveBdRate = +(baseRate + weekendExtraRate + bdExtraRate).toFixed(2);

                return {
                    totalHrs,
                    nonBdHrs,
                    bdHrs,
                    isWeekend,
                    baseRate,
                    bdExtraRate,
                    weekendExtraRate,
                    effectiveSingleRate,
                    effectiveBdRate,
                    basePay,
                    bdExtraPay,
                    weekendExtraPay,
                    totalPay
                };
            }

            // Date Period Filtering Logic (Monday-Sunday weeks)
            function getPeriodBounds(periodKey) {
                const now = new Date();
                const today = new Date(now.getFullYear(), now.getMonth(), now.getDate());
                // Convert JS Sunday=0..Saturday=6 to Monday=0..Sunday=6
                const dayIdx = (today.getDay() + 6) % 7;

                const startOfThisWeek = new Date(today);
                startOfThisWeek.setDate(today.getDate() - dayIdx);

                const endOfThisWeek = new Date(startOfThisWeek);
                endOfThisWeek.setDate(startOfThisWeek.getDate() + 6);

                if (periodKey === 'this_week') {
                    return { start: startOfThisWeek, end: endOfThisWeek, label: 'Current Week (Mon – Sun)' };
                }
                if (periodKey === 'last_week') {
                    const start = new Date(startOfThisWeek);
                    start.setDate(start.getDate() - 7);
                    const end = new Date(endOfThisWeek);
                    end.setDate(end.getDate() - 7);
                    return { start, end, label: 'Last Week (Mon – Sun)' };
                }
                if (periodKey === 'fortnight') {
                    const start = new Date(startOfThisWeek);
                    start.setDate(start.getDate() - 7);
                    return { start, end: endOfThisWeek, label: 'Last 14 Days / Current Fortnight' };
                }
                if (periodKey === 'this_month') {
                    const start = new Date(today.getFullYear(), today.getMonth(), 1);
                    const end = new Date(today.getFullYear(), today.getMonth() + 1, 0);
                    const monthName = today.toLocaleDateString('en-AU', { month: 'long', year: 'numeric' });
                    return { start, end, label: monthName };
                }
                return { start: null, end: null, label: 'All Recorded Shifts' };
            }

            function getFilteredShifts() {
                const { start, end } = getPeriodBounds(state.period);
                return state.shifts
                    .filter(shift => {
                        if (state.filterBDOnly && (!shift.droveBDouble || (parseFloat(shift.bDoubleHours) || 0) <= 0)) {
                            return false;
                        }
                        if (!start || !end) return true;
                        const d = parseLocalDate(shift.date);
                        return d >= start && d <= end;
                    })
                    .sort((a, b) => {
                        if (a.date !== b.date) return b.date.localeCompare(a.date);
                        return (b.updatedAt || 0) - (a.updatedAt || 0);
                    });
            }

            // UI Sync Functions
            function syncRatesUI(updateInputs = true) {
                if (updateInputs) {
                    el.rateNormal.value = Number(state.rates.normalRate || 0).toFixed(2);
                    el.rateBDouble.value = Number(state.rates.bDoubleRate || 0).toFixed(2);
                    el.rateWeekend.value = Number(state.rates.weekendRate || 0).toFixed(2);
                }
                el.autoWeekendSetting.checked = state.rates.autoWeekend;

                const base = Math.max(0, parseFloat(state.rates.normalRate) || 0);
                const bd = Math.max(0, parseFloat(state.rates.bDoubleRate) || 0);
                const wknd = Math.max(0, parseFloat(state.rates.weekendRate) || 0);

                el.effWeekdayBase.textContent = `${formatAUD(base)}/hr`;
                el.effWeekdayBD.textContent = `${formatAUD(base + bd)}/hr`;
                el.effWeekendBase.textContent = `${formatAUD(base + wknd)}/hr`;
                el.effWeekendBD.textContent = `${formatAUD(base + wknd + bd)}/hr`;

                el.ratesSummarySub.textContent = `Base ${formatAUD(base)} • BD +${formatAUD(bd)} • Wknd +${formatAUD(wknd)}`;
            }

            function updateDateDayBadge(autoApplyWeekend = true) {
                const dateVal = el.shiftDate.value;
                if (!dateVal) return;

                const d = parseLocalDate(dateVal);
                const dayName = d.toLocaleDateString('en-AU', { weekday: 'long' });
                const isSatOrSun = (d.getDay() === 0 || d.getDay() === 6);

                el.dayOfWeekBadge.textContent = dayName;
                if (isSatOrSun) {
                    el.dayOfWeekBadge.className = 'text-xs font-bold px-2.5 py-0.5 rounded-full bg-purple-500/20 text-purple-300 border border-purple-500/30';
                    el.weekendAutoTag.classList.remove('hidden');
                } else {
                    el.dayOfWeekBadge.className = 'text-xs font-bold px-2.5 py-0.5 rounded-full bg-slate-800 text-slate-300';
                    el.weekendAutoTag.classList.add('hidden');
                }

                if (autoApplyWeekend && state.rates.autoWeekend) {
                    el.isWeekendToggle.checked = isSatOrSun;
                }
            }

            function syncBDoubleUI() {
                const checked = el.droveBDoubleToggle.checked;
                if (checked) {
                    el.bDoubleHoursWrapper.classList.remove('hidden');
                    el.bDoubleBox.classList.add('border-amber-500/40');
                } else {
                    el.bDoubleHoursWrapper.classList.add('hidden');
                    el.bDoubleBox.classList.remove('border-amber-500/40');
                    el.bdValidationMsg.classList.add('hidden');
                }
            }

            function validateBDoubleHours() {
                const total = parseFloat(el.totalHours.value) || 0;
                const bd = parseFloat(el.bDoubleHours.value) || 0;
                if (el.droveBDoubleToggle.checked && bd > total && total > 0) {
                    el.bdValidationMsg.classList.remove('hidden');
                    return false;
                }
                el.bdValidationMsg.classList.add('hidden');
                return true;
            }

            function updateLivePreview() {
                validateBDoubleHours();
                const draftShift = {
                    totalHours: parseFloat(el.totalHours.value) || 0,
                    droveBDouble: el.droveBDoubleToggle.checked,
                    bDoubleHours: parseFloat(el.bDoubleHours.value) || 0,
                    isWeekend: el.isWeekendToggle.checked
                };

                const calc = calculateShiftPay(draftShift);
                el.previewTotalPay.textContent = formatAUD(calc.totalPay);

                if (calc.totalHrs <= 0) {
                    el.previewBreakdownLines.innerHTML = '<div>Enter hours worked to preview pay breakdown.</div>';
                    return;
                }

                const lines = [];
                lines.push(
                    `<div class="flex justify-between">
                        <span>Ordinary Base: <strong class="text-slate-200">${formatHours(calc.totalHrs)} hrs</strong> × ${formatAUD(calc.baseRate)}/hr</span>
                        <span class="text-slate-200 font-semibold">${formatAUD(calc.basePay)}</span>
                    </div>`
                );
                if (calc.bdHrs > 0) {
                    lines.push(
                        `<div class="flex justify-between text-amber-300">
                            <span>B-Double Extra: <strong>${formatHours(calc.bdHrs)} hrs</strong> × +${formatAUD(calc.bdExtraRate)}/hr</span>
                            <span class="font-semibold">+${formatAUD(calc.bdExtraPay)}</span>
                        </div>`
                    );
                }
                if (calc.isWeekend) {
                    lines.push(
                        `<div class="flex justify-between text-purple-300">
                            <span>Weekend Extra: <strong>${formatHours(calc.totalHrs)} hrs</strong> × +${formatAUD(calc.weekendExtraRate)}/hr</span>
                            <span class="font-semibold">+${formatAUD(calc.weekendExtraPay)}</span>
                        </div>`
                    );
                }
                el.previewBreakdownLines.innerHTML = lines.join('');
            }

            // Render Dashboard KPIs & Shift History List
            function renderDashboard() {
                const { label } = getPeriodBounds(state.period);
                el.periodRangeLabel.textContent = `Period: ${label}`;

                const filtered = getFilteredShifts();

                let sumPay = 0;
                let sumTotalHrs = 0;
                let sumNonBdHrs = 0;
                let sumWeekendHrs = 0;
                let sumBdHrs = 0;
                let bdDaysCount = 0;

                filtered.forEach(shift => {
                    const c = calculateShiftPay(shift);
                    sumPay += c.totalPay;
                    sumTotalHrs += c.totalHrs;
                    sumNonBdHrs += c.nonBdHrs;
                    if (c.isWeekend) {
                        sumWeekendHrs += c.totalHrs;
                    }
                    sumBdHrs += c.bdHrs;
                    if (c.bdHrs > 0) {
                        bdDaysCount++;
                    }
                });

                const avgRate = sumTotalHrs > 0 ? (sumPay / sumTotalHrs) : 0;

                el.statTotalPay.textContent = formatAUD(sumPay);
                el.statShiftCount.textContent = `${filtered.length} ${filtered.length === 1 ? 'shift' : 'shifts'} logged`;
                el.statTotalHours.innerHTML = `${formatHours(sumTotalHrs)} <span class="text-sm font-semibold text-slate-400">hrs</span>`;
                el.statAvgRate.textContent = `Effective Avg: ${formatAUD(avgRate)}/hr`;
                el.statBaseHours.innerHTML = `${formatHours(sumNonBdHrs)} <span class="text-sm font-semibold text-slate-400">hrs</span>`;
                el.statWeekendHoursNote.textContent = `${formatHours(sumWeekendHrs)} total weekend hrs`;
                el.statBDHours.innerHTML = `${formatHours(sumBdHrs)} <span class="text-sm font-semibold text-amber-500/70">hrs</span>`;
                el.statBDDaysNote.textContent = `${bdDaysCount} ${bdDaysCount === 1 ? 'day' : 'days'} driving B-Double`;

                el.historySubtitle.textContent = `${filtered.length} ${filtered.length === 1 ? 'entry' : 'entries'} in ${label}`;

                renderShiftList(filtered);
            }

            function renderShiftList(shifts) {
                if (shifts.length === 0) {
                    el.shiftListContainer.innerHTML = `
                        <div class="p-10 text-center space-y-3">
                            <div class="w-12 h-12 rounded-2xl bg-slate-800/80 text-slate-500 mx-auto flex items-center justify-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
                            </div>
                            <div class="text-sm font-bold text-slate-300">No shifts recorded for this period</div>
                            <p class="text-xs text-slate-500 max-w-xs mx-auto">Use the shift logger to record your hours worked, weekend rates, and B-Double driving time.</p>
                        </div>
                    `;
                    return;
                }

                el.shiftListContainer.innerHTML = shifts.map(shift => {
                    const c = calculateShiftPay(shift);
                    const hasBD = c.bdHrs > 0;

                    const bdBadge = hasBD
                        ? `<span class="inline-flex items-center gap-1 px-2 py-0.5 rounded-md text-[11px] font-bold bg-amber-500/15 text-amber-400 border border-amber-500/30">B-Double • ${formatHours(c.bdHrs)}h</span>`
                        : '';

                    const wkndBadge = c.isWeekend
                        ? `<span class="inline-flex items-center px-2 py-0.5 rounded-md text-[11px] font-bold bg-purple-500/15 text-purple-300 border border-purple-500/30">Weekend</span>`
                        : '';

                    const notesHtml = shift.notes
                        ? `<p class="text-xs text-slate-400 mt-1.5 flex items-center gap-1.5">
                               <svg xmlns="http://www.w3.org/2000/svg" class="w-3.5 h-3.5 text-slate-500 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>
                               <span>${escapeHtml(shift.notes)}</span>
                           </p>`
                        : '';

                    const breakdownParts = [
                        `${formatHours(c.totalHrs)}h @ ${formatAUD(c.baseRate)}`
                    ];
                    if (c.bdHrs > 0) {
                        breakdownParts.push(`<span class="text-amber-400/90">+${formatHours(c.bdHrs)}h BD (+${formatAUD(c.bdExtraRate)})</span>`);
                    }
                    if (c.isWeekend) {
                        breakdownParts.push(`<span class="text-purple-300/90">+${formatHours(c.totalHrs)}h Wknd (+${formatAUD(c.weekendExtraRate)})</span>`);
                    }

                    return `
                        <article class="p-4 sm:p-5 hover:bg-slate-850/60 transition flex flex-col sm:flex-row sm:items-center justify-between gap-3">
                            <div class="space-y-1 min-w-0">
                                <div class="flex flex-wrap items-center gap-2">
                                    <h3 class="text-sm font-bold text-white">${formatDisplayDate(shift.date)}</h3>
                                    ${wkndBadge}
                                    ${bdBadge}
                                </div>
                                <div class="text-xs text-slate-300 tabular-nums flex flex-wrap items-center gap-x-2 gap-y-1">
                                    <span class="font-semibold text-slate-200">${formatHours(c.totalHrs)} hrs total</span>
                                    <span class="text-slate-600">•</span>
                                    <span>${breakdownParts.join(' + ')}</span>
                                </div>
                                ${notesHtml}
                            </div>

                            <div class="flex items-center justify-between sm:justify-end gap-4 pt-2 sm:pt-0 border-t sm:border-t-0 border-slate-800/70 shrink-0">
                                <div class="text-left sm:text-right">
                                    <div class="text-base sm:text-lg font-extrabold text-emerald-400 tabular-nums">${formatAUD(c.totalPay)}</div>
                                    <div class="text-[11px] text-slate-500 tabular-nums">Gross Shift Pay</div>
                                </div>
                                <div class="flex items-center gap-1.5">
                                    <button type="button" data-action="edit" data-id="${shift.id}" title="Edit Shift" class="p-2 rounded-lg bg-slate-800 hover:bg-slate-700 text-slate-300 hover:text-white border border-slate-700 transition">
                                        <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7"/><path d="M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z"/></svg>
                                    </button>
                                    <button type="button" data-action="delete" data-id="${shift.id}" title="Delete Shift" class="p-2 rounded-lg bg-slate-800 hover:bg-rose-950 text-slate-400 hover:text-rose-400 border border-slate-700 hover:border-rose-800/70 transition">
                                        <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="3 6 5 6 21 6"/><path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"/></svg>
                                    </button>
                                </div>
                            </div>
                        </article>
                    `;
                }).join('');
            }

            // Form Reset & Edit Mode Helpers
            function resetShiftForm() {
                el.editShiftId.value = '';
                el.formTitle.textContent = 'Log Daily Shift';
                el.btnSaveShiftText.textContent = 'Save Shift Log';
                el.btnCancelEdit.classList.add('hidden');

                el.shiftDate.value = getTodayISO();
                el.totalHours.value = '';
                el.droveBDoubleToggle.checked = false;
                el.bDoubleHours.value = '';
                el.shiftNotes.value = '';

                updateDateDayBadge(true);
                syncBDoubleUI();
                updateLivePreview();
            }

            function startEditShift(shiftId) {
                const shift = state.shifts.find(s => s.id === shiftId);
                if (!shift) return;

                el.editShiftId.value = shift.id;
                el.formTitle.textContent = 'Edit Logged Shift';
                el.btnSaveShiftText.textContent = 'Update Shift';
                el.btnCancelEdit.classList.remove('hidden');

                el.shiftDate.value = shift.date;
                updateDateDayBadge(false);
                el.isWeekendToggle.checked = Boolean(shift.isWeekend);
                el.totalHours.value = shift.totalHours;
                el.droveBDoubleToggle.checked = Boolean(shift.droveBDouble);
                el.bDoubleHours.value = shift.droveBDouble ? shift.bDoubleHours : '';
                el.shiftNotes.value = shift.notes || '';

                syncBDoubleUI();
                updateLivePreview();

                el.shiftForm.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
            }

            function deleteShift(shiftId) {
                state.shifts = state.shifts.filter(s => s.id !== shiftId);
                deleteSingleShiftFromCloud(shiftId);
                if (el.editShiftId.value === shiftId) {
                    resetShiftForm();
                }
                renderDashboard();
                showToast('Shift deleted');
            }

            // CSV Export Function
            function exportToCSV() {
                const shiftsToExport = getFilteredShifts();
                if (shiftsToExport.length === 0) {
                    showToast('No shifts in the current view to export', 'error');
                    return;
                }

                const headers = [
                    'Date',
                    'Day',
                    'Weekend Shift',
                    'Total Hours',
                    'Ordinary Base Rate (AUD)',
                    'Ordinary Base Pay (AUD)',
                    'B-Double Driven',
                    'B-Double Hours',
                    'B-Double Extra Rate (+AUD)',
                    'B-Double Extra Pay (AUD)',
                    'Weekend Extra Rate (+AUD)',
                    'Weekend Extra Pay (AUD)',
                    'Total Gross Pay (AUD)',
                    'Route / Notes'
                ];

                const rows = shiftsToExport.map(shift => {
                    const c = calculateShiftPay(shift);
                    const d = parseLocalDate(shift.date);
                    const dayName = d.toLocaleDateString('en-AU', { weekday: 'short' });
                    const cleanNotes = (shift.notes || '').replace(/"/g, '""');

                    return [
                        shift.date,
                        dayName,
                        c.isWeekend ? 'Yes' : 'No',
                        c.totalHrs.toFixed(2),
                        c.baseRate.toFixed(2),
                        c.basePay.toFixed(2),
                        c.bdHrs > 0 ? 'Yes' : 'No',
                        c.bdHrs.toFixed(2),
                        c.bdExtraRate.toFixed(2),
                        c.bdExtraPay.toFixed(2),
                        c.weekendExtraRate.toFixed(2),
                        c.weekendExtraPay.toFixed(2),
                        c.totalPay.toFixed(2),
                        `"${cleanNotes}"`
                    ].join(',');
                });

                const csvContent = [headers.join(','), ...rows].join('\n');
                const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
                const url = URL.createObjectURL(blob);

                const link = document.createElement('a');
                link.href = url;
                link.download = `RigPay_Shifts_${state.period}_${getTodayISO()}.csv`;
                document.body.appendChild(link);
                link.click();
                document.body.removeChild(link);
                URL.revokeObjectURL(url);

                showToast(`Exported ${shiftsToExport.length} shifts to CSV`);
            }

            // Event Listeners Setup
            function bindEvents() {
                // Shift Date change
                el.shiftDate.addEventListener('change', () => {
                    updateDateDayBadge(true);
                    updateLivePreview();
                });

                // Weekend manual toggle
                el.isWeekendToggle.addEventListener('change', updateLivePreview);

                // Total hours input
                el.totalHours.addEventListener('input', () => {
                    // If user already clicked "All Shift Hours" or BD hours exceeded, keep preview updated
                    updateLivePreview();
                });

                // Time Calculator Helper
                el.btnToggleTimeCalc.addEventListener('click', () => {
                    el.timeCalcPanel.classList.toggle('hidden');
                });

                el.btnApplyTimeCalc.addEventListener('click', () => {
                    const startStr = el.calcStart.value;
                    const endStr = el.calcEnd.value;
                    const breakMins = Math.max(0, parseInt(el.calcBreak.value, 10) || 0);

                    if (!startStr || !endStr) return;

                    const [sh, sm] = startStr.split(':').map(Number);
                    const [eh, em] = endStr.split(':').map(Number);

                    let startMins = sh * 60 + sm;
                    let endMins = eh * 60 + em;
                    // Handle overnight shifts crossing midnight
                    if (endMins <= startMins) {
                        endMins += 24 * 60;
                    }

                    const netMins = Math.max(0, endMins - startMins - breakMins);
                    const hoursDecimal = +(netMins / 60).toFixed(2);

                    el.totalHours.value = hoursDecimal;
                    el.timeCalcPanel.classList.add('hidden');
                    updateLivePreview();
                    showToast(`Calculated ${hoursDecimal} hrs`);
                });

                // Drove B-Double Toggle
                el.droveBDoubleToggle.addEventListener('change', () => {
                    syncBDoubleUI();
                    if (el.droveBDoubleToggle.checked && !el.bDoubleHours.value && el.totalHours.value) {
                        el.bDoubleHours.value = el.totalHours.value;
                    }
                    updateLivePreview();
                });

                // B-Double Hours Input
                el.bDoubleHours.addEventListener('input', updateLivePreview);

                // "All Shift Hours" quick button
                el.btnAllShiftBD.addEventListener('click', () => {
                    const total = parseFloat(el.totalHours.value);
                    if (total > 0) {
                        el.bDoubleHours.value = total;
                        updateLivePreview();
                    } else {
                        showToast('Enter Total Hours Worked first', 'error');
                        el.totalHours.focus();
                    }
                });

                // Cancel Edit
                el.btnCancelEdit.addEventListener('click', resetShiftForm);

                // Submit Shift Form
                el.shiftForm.addEventListener('submit', (e) => {
                    e.preventDefault();

                    const date = el.shiftDate.value;
                    const totalHours = parseFloat(el.totalHours.value);
                    const droveBDouble = el.droveBDoubleToggle.checked;
                    const bDoubleHours = droveBDouble ? (parseFloat(el.bDoubleHours.value) || 0) : 0;
                    const isWeekend = el.isWeekendToggle.checked;
                    const notes = el.shiftNotes.value.trim();

                    if (!date || !(totalHours > 0)) {
                        showToast('Please enter a valid date and hours worked', 'error');
                        return;
                    }

                    if (droveBDouble && bDoubleHours > totalHours) {
                        showToast('B-Double hours cannot exceed Total Hours Worked', 'error');
                        el.bDoubleHours.focus();
                        return;
                    }

                    const editId = el.editShiftId.value;
                    let savedShiftRecord = null;
                    if (editId) {
                        const idx = state.shifts.findIndex(s => s.id === editId);
                        if (idx !== -1) {
                            state.shifts[idx] = {
                                ...state.shifts[idx],
                                date,
                                totalHours,
                                droveBDouble: droveBDouble && bDoubleHours > 0,
                                bDoubleHours: droveBDouble ? bDoubleHours : 0,
                                isWeekend,
                                notes,
                                updatedAt: Date.now()
                            };
                            savedShiftRecord = state.shifts[idx];
                        }
                        showToast('Shift updated');
                    } else {
                        const newShift = {
                            id: 'sh_' + Date.now() + '_' + Math.random().toString(36).slice(2, 6),
                            date,
                            totalHours,
                            droveBDouble: droveBDouble && bDoubleHours > 0,
                            bDoubleHours: droveBDouble ? bDoubleHours : 0,
                            isWeekend,
                            notes,
                            updatedAt: Date.now()
                        };
                        state.shifts.push(newShift);
                        savedShiftRecord = newShift;
                        showToast('Shift saved');
                    }

                    saveSingleShiftToCloud(savedShiftRecord);
                    resetShiftForm();
                    renderDashboard();
                });

                // Pay Rate Inputs Auto-Save
                const handleRatesChange = (e) => {
                    const isTypingInRateBox = e && e.type === 'input' && e.target && e.target.classList.contains('rate-input');

                    const parseRateCents = (val) => {
                        const num = parseFloat(val);
                        if (!Number.isFinite(num) || num < 0) return 0;
                        return Math.round(num * 100) / 100;
                    };

                    state.rates.normalRate = parseRateCents(el.rateNormal.value);
                    state.rates.bDoubleRate = parseRateCents(el.rateBDouble.value);
                    state.rates.weekendRate = parseRateCents(el.rateWeekend.value);
                    state.rates.autoWeekend = el.autoWeekendSetting.checked;

                    saveRates();
                    syncRatesUI(!isTypingInRateBox);
                    updateLivePreview();
                    renderDashboard();
                };

                el.rateNormal.addEventListener('input', handleRatesChange);
                el.rateNormal.addEventListener('blur', handleRatesChange);
                el.rateBDouble.addEventListener('input', handleRatesChange);
                el.rateBDouble.addEventListener('blur', handleRatesChange);
                el.rateWeekend.addEventListener('input', handleRatesChange);
                el.rateWeekend.addEventListener('blur', handleRatesChange);
                el.autoWeekendSetting.addEventListener('change', () => {
                    handleRatesChange();
                    updateDateDayBadge(true);
                    updateLivePreview();
                });

                // Period Filter Buttons
                el.periodBtns.forEach(btn => {
                    btn.addEventListener('click', () => {
                        state.period = btn.dataset.period;
                        el.periodBtns.forEach(b => {
                            const spanClass = b.dataset.period === 'all' ? 'col-span-2 sm:col-span-1 ' : '';
                            if (b.dataset.period === state.period) {
                                b.className = `period-btn ${spanClass}px-2.5 sm:px-3 py-2 sm:py-1.5 rounded-lg text-xs font-semibold transition bg-amber-500 text-slate-950 shadow-sm text-center`;
                            } else {
                                b.className = `period-btn ${spanClass}px-2.5 sm:px-3 py-2 sm:py-1.5 rounded-lg text-xs font-semibold transition text-slate-300 hover:bg-slate-800 text-center`;
                            }
                        });
                        renderDashboard();
                    });
                });

                // B-Double Only Filter Checkbox
                el.filterBDOnly.addEventListener('change', () => {
                    state.filterBDOnly = el.filterBDOnly.checked;
                    renderDashboard();
                });

                // Shift List Edit / Delete Delegation
                el.shiftListContainer.addEventListener('click', (e) => {
                    const btn = e.target.closest('button[data-action]');
                    if (!btn) return;
                    const { action, id } = btn.dataset;
                    if (action === 'edit') {
                        startEditShift(id);
                    } else if (action === 'delete') {
                        deleteShift(id);
                    }
                });

                // Export CSV
                el.btnExportCsv.addEventListener('click', exportToCSV);

                // Account & Cloud Sync Modal Handlers
                el.btnOpenAccountSettings.addEventListener('click', () => {
                    updateAccountModalUI();
                    el.accountModal.classList.remove('hidden');
                    el.accountModal.classList.add('flex');
                });

                el.btnCloseAccountModal.addEventListener('click', () => {
                    el.accountModal.classList.add('hidden');
                    el.accountModal.classList.remove('flex');
                });

                el.accountModal.addEventListener('click', (e) => {
                    if (e.target === el.accountModal) {
                        el.accountModal.classList.add('hidden');
                        el.accountModal.classList.remove('flex');
                    }
                });

                el.btnGoogleSignIn.addEventListener('click', handleGoogleButtonClick);

                el.btnSyncNow.addEventListener('click', () => {
                    uploadAllLocalShiftsToCloud(true);
                });

                // Reset Modal Handlers
                el.btnOpenReset.addEventListener('click', () => {
                    el.accountModal.classList.add('hidden');
                    el.accountModal.classList.remove('flex');
                    el.resetModal.classList.remove('hidden');
                    el.resetModal.classList.add('flex');
                });

                el.btnCancelReset.addEventListener('click', () => {
                    el.resetModal.classList.add('hidden');
                    el.resetModal.classList.remove('flex');
                });

                el.btnConfirmReset.addEventListener('click', async () => {
                    const idsToDelete = state.shifts.map(s => s.id);
                    state.shifts = [];
                    saveLocalCache();
                    for (const id of idsToDelete) {
                        await deleteSingleShiftFromCloud(id);
                    }
                    resetShiftForm();
                    renderDashboard();
                    el.resetModal.classList.add('hidden');
                    el.resetModal.classList.remove('flex');
                    showToast('All shift logs cleared');
                });
            }

            // Initialize App
            function init() {
                loadLocalCache();
                syncRatesUI();
                resetShiftForm();
                bindEvents();
                renderDashboard();
                initCloudAuth();
            }

            window.addEventListener('DOMContentLoaded', init);
        })();
    </script>
</body>
</html>
