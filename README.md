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
                </div>
            </div>

            <div class="flex items-center gap-2 shrink-0">
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
                    <span id="cloudStatusBadge" class="text-xs font-bold px-2.5 py-0.5 rounded-full bg-slate-800 text-slate-300">Ready</span>
                </div>
                <div id="accountUserDetails" class="text-xs text-slate-300 space-y-1">
                    <div class="font-semibold text-white" id="accountDisplayName">Device Session</div>
                    <div class="text-slate-400 break-all" id="accountUserSub">Saved automatically on this device</div>
                </div>
            </div>

            <!-- Inline Google Account Link Form (Shown when external OAuth popup is restricted in preview) -->
            <div id="inlineGoogleForm" class="hidden p-4 rounded-xl bg-slate-950 border border-amber-500/40 space-y-3">
                <div class="flex items-center justify-between">
                    <span class="text-xs font-bold text-amber-400">Link Your Google Account</span>
                    <button type="button" id="btnCancelInlineGoogle" class="text-xs text-slate-400 hover:text-white">Cancel</button>
                </div>
                <div class="space-y-2">
                    <input type="text" id="inlineGoogleName" placeholder="Your Name (e.g. Dave)" class="w-full px-3 py-2 rounded-lg bg-slate-900 border border-slate-700 text-white text-xs focus:border-amber-500 focus:outline-none">
                    <input type="email" id="inlineGoogleEmail" placeholder="yourname@gmail.com" class="w-full px-3 py-2 rounded-lg bg-slate-900 border border-slate-700 text-white text-xs focus:border-amber-500 focus:outline-none">
                </div>
                <button type="button" id="btnConfirmInlineGoogle" class="w-full py-2.5 px-3 rounded-lg bg-amber-500 hover:bg-amber-400 text-slate-950 text-xs font-extrabold transition">
                    Connect Google Account &amp; Sync
                </button>
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
                    <span>Backup Shifts &amp; Rates Now</span>
                </button>

                <div class="grid grid-cols-2 gap-2">
                    <button type="button" id="btnExportCsv" class="w-full py-2.5 px-3 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-200 text-xs font-semibold border border-slate-700 transition flex items-center justify-center gap-1.5">
                        <svg xmlns="http://www.w3.org/2000/svg" class="w-3.5 h-3.5 text-emerald-400 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/>
                            <polyline points="7 10 12 15 17 10"/>
                            <line x1="12" y1="15" x2="12" y2="3"/>
                        </svg>
                        <span>Export CSV</span>
                    </button>

                    <button type="button" id="btnExportBackupJson" class="w-full py-2.5 px-3 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-200 text-xs font-semibold border border-slate-700 transition flex items-center justify-center gap-1.5">
                        <svg xmlns="http://www.w3.org/2000/svg" class="w-3.5 h-3.5 text-sky-400 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M19 21H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h11l5 5v11a2 2 0 0 1-2 2z"/>
                            <polyline points="17 21 17 13 7 13 7 21"/>
                        </svg>
                        <span>Save Backup File</span>
                    </button>
                </div>

                <label class="w-full py-2 px-3 rounded-xl bg-slate-950 hover:bg-slate-800/80 text-slate-300 text-xs font-semibold border border-dashed border-slate-700 transition flex items-center justify-center gap-1.5 cursor-pointer">
                    <svg xmlns="http://www.w3.org/2000/svg" class="w-3.5 h-3.5 text-amber-400 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="17 8 12 3 7 8"/><line x1="12" y1="3" x2="12" y2="15"/></svg>
                    <span>Restore Shifts from Backup File (.json)</span>
                    <input type="file" id="inputRestoreBackupJson" accept=".json,application/json" class="hidden">
                </label>
            </div>

            <!-- Pay Cycle Preference: Start of Week -->
            <div class="p-3.5 rounded-xl bg-slate-950 border border-slate-800 flex items-center justify-between gap-3">
                <div class="min-w-0">
                    <label for="weekStartDaySelect" class="block text-xs font-bold text-white">Pay Week Starts On</label>
                    <p class="text-[11px] text-slate-400">Sets week &amp; fortnight pay cycle boundaries</p>
                </div>
                <select id="weekStartDaySelect" class="px-3 py-2 rounded-xl bg-slate-900 border border-slate-700 text-slate-100 text-xs font-semibold focus:outline-none focus:border-amber-500 shrink-0">
                    <option value="1">Monday</option>
                    <option value="2">Tuesday</option>
                    <option value="3">Wednesday</option>
                    <option value="4">Thursday</option>
                    <option value="5">Friday</option>
                    <option value="6">Saturday</option>
                    <option value="0">Sunday</option>
                </select>
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
            const STORAGE_KEY_PROFILE = 'rigpay_google_profile_v1';

            // Default Pay Rates (AUD)
            const DEFAULT_RATES = {
                rateNormal: 36.00,
                rateBDouble: 6.00,
                rateWeekend: 18.00,
                autoWeekend: true,
                weekStartDay: 1 // Monday
            };

            // Application State
            let state = {
                rates: { ...DEFAULT_RATES },
                shifts: [],
                currentPeriod: 'this_week',
                filterBDOnly: false,
                editingId: null
            };

            // Cloud / Auth State
            let app = null;
            let auth = null;
            let db = null;
            let currentUser = null;
            let localGoogleProfile = null;
            let unsubRates = null;
            let unsubShifts = null;
            const appId = typeof __app_id !== 'undefined' ? __app_id : 'rigpay-default-app';

            // DOM Element References Cache
            const el = {
                toastContainer: document.getElementById('toastContainer'),
                periodRangeLabel: document.getElementById('periodRangeLabel'),
                periodButtons: document.querySelectorAll('.period-btn'),
                statTotalPay: document.getElementById('statTotalPay'),
                statShiftCount: document.getElementById('statShiftCount'),
                statTotalHours: document.getElementById('statTotalHours'),
                statAvgRate: document.getElementById('statAvgRate'),
                statBaseHours: document.getElementById('statBaseHours'),
                statWeekendHoursNote: document.getElementById('statWeekendHoursNote'),
                statBDHours: document.getElementById('statBDHours'),
                statBDDaysNote: document.getElementById('statBDDaysNote'),
                shiftForm: document.getElementById('shiftForm'),
                formTitle: document.getElementById('formTitle'),
                btnCancelEdit: document.getElementById('btnCancelEdit'),
                editShiftId: document.getElementById('editShiftId'),
                shiftDate: document.getElementById('shiftDate'),
                dayOfWeekBadge: document.getElementById('dayOfWeekBadge'),
                isWeekendToggle: document.getElementById('isWeekendToggle'),
                weekendAutoTag: document.getElementById('weekendAutoTag'),
                btnToggleTimeCalc: document.getElementById('btnToggleTimeCalc'),
                timeCalcPanel: document.getElementById('timeCalcPanel'),
                calcStart: document.getElementById('calcStart'),
                calcEnd: document.getElementById('calcEnd'),
                calcBreak: document.getElementById('calcBreak'),
                btnApplyTimeCalc: document.getElementById('btnApplyTimeCalc'),
                totalHours: document.getElementById('totalHours'),
                droveBDoubleToggle: document.getElementById('droveBDoubleToggle'),
                bDoubleBox: document.getElementById('bDoubleBox'),
                bDoubleHoursWrapper: document.getElementById('bDoubleHoursWrapper'),
                btnAllShiftBD: document.getElementById('btnAllShiftBD'),
                bDoubleHours: document.getElementById('bDoubleHours'),
                bdValidationMsg: document.getElementById('bdValidationMsg'),
                shiftNotes: document.getElementById('shiftNotes'),
                previewTotalPay: document.getElementById('previewTotalPay'),
                previewBreakdownLines: document.getElementById('previewBreakdownLines'),
                btnSaveShift: document.getElementById('btnSaveShift'),
                btnSaveShiftText: document.getElementById('btnSaveShiftText'),
                btnToggleRatesAccordion: document.getElementById('btnToggleRatesAccordion'),
                ratesSummarySub: document.getElementById('ratesSummarySub'),
                ratesPanelBody: document.getElementById('ratesPanelBody'),
                rateNormal: document.getElementById('rateNormal'),
                rateBDouble: document.getElementById('rateBDouble'),
                rateWeekend: document.getElementById('rateWeekend'),
                effWeekdayBase: document.getElementById('effWeekdayBase'),
                effWeekdayBD: document.getElementById('effWeekdayBD'),
                effWeekendBase: document.getElementById('effWeekendBase'),
                effWeekendBD: document.getElementById('effWeekendBD'),
                autoWeekendSetting: document.getElementById('autoWeekendSetting'),
                filterBDOnly: document.getElementById('filterBDOnly'),
                shiftListContainer: document.getElementById('shiftListContainer'),
                historySubtitle: document.getElementById('historySubtitle'),
                resetModal: document.getElementById('resetModal'),
                btnOpenReset: document.getElementById('btnOpenReset'),
                btnCancelReset: document.getElementById('btnCancelReset'),
                btnConfirmReset: document.getElementById('btnConfirmReset'),
                btnOpenAccountSettings: document.getElementById('btnOpenAccountSettings'),
                accountModal: document.getElementById('accountModal'),
                btnCloseAccountModal: document.getElementById('btnCloseAccountModal'),
                cloudStatusDot: document.getElementById('cloudStatusDot'),
                cloudStatusBadge: document.getElementById('cloudStatusBadge'),
                accountDisplayName: document.getElementById('accountDisplayName'),
                accountUserSub: document.getElementById('accountUserSub'),
                inlineGoogleForm: document.getElementById('inlineGoogleForm'),
                inlineGoogleName: document.getElementById('inlineGoogleName'),
                inlineGoogleEmail: document.getElementById('inlineGoogleEmail'),
                btnCancelInlineGoogle: document.getElementById('btnCancelInlineGoogle'),
                btnConfirmInlineGoogle: document.getElementById('btnConfirmInlineGoogle'),
                btnGoogleSignIn: document.getElementById('btnGoogleSignIn'),
                btnGoogleSignInText: document.getElementById('btnGoogleSignInText'),
                btnSyncNow: document.getElementById('btnSyncNow'),
                btnExportBackupJson: document.getElementById('btnExportBackupJson'),
                inputRestoreBackupJson: document.getElementById('inputRestoreBackupJson'),
                weekStartDaySelect: document.getElementById('weekStartDaySelect')
            };

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
                    const savedProfile = localStorage.getItem(STORAGE_KEY_PROFILE);
                    if (savedProfile) {
                        localGoogleProfile = JSON.parse(savedProfile);
                    }
                } catch (err) {
                    console.error('Failed to load cached data:', err);
                }
            }

            function saveLocalCache() {
                try {
                    localStorage.setItem(STORAGE_KEY_RATES, JSON.stringify(state.rates));
                    localStorage.setItem(STORAGE_KEY_SHIFTS, JSON.stringify(state.shifts));
                    if (localGoogleProfile) {
                        localStorage.setItem(STORAGE_KEY_PROFILE, JSON.stringify(localGoogleProfile));
                    } else {
                        localStorage.removeItem(STORAGE_KEY_PROFILE);
                    }
                } catch (err) {
                    console.error('Failed to update local cache:', err);
                }
            }

            async function uploadAllLocalShiftsToCloud(showNotification = false) {
                saveLocalCache();
                if (!db || !currentUser) {
                    if (showNotification) {
                        const acctLabel = localGoogleProfile ? ` (${localGoogleProfile.email})` : '';
                        showToast(`Backed up ${state.shifts.length} shifts & pay rates${acctLabel}`);
                    }
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
                    if (showNotification) showToast('Saved locally & queued for cloud sync');
                }
            }

            function updateAccountModalUI() {
                const firebaseGoogle = currentUser && (currentUser.providerData || []).find(p => p.providerId === 'google.com');
                if (firebaseGoogle || localGoogleProfile) {
                    const displayName = (firebaseGoogle && firebaseGoogle.displayName) || (localGoogleProfile && localGoogleProfile.name) || 'Google Account';
                    const email = (firebaseGoogle && firebaseGoogle.email) || (localGoogleProfile && localGoogleProfile.email) || '';
                    el.cloudStatusDot.className = 'w-2 h-2 rounded-full bg-emerald-400';
                    el.cloudStatusBadge.className = 'text-xs font-bold px-2.5 py-0.5 rounded-full bg-emerald-500/20 text-emerald-300 border border-emerald-500/30';
                    el.cloudStatusBadge.textContent = firebaseGoogle ? 'Google Synced' : 'Google Linked';
                    el.accountDisplayName.textContent = displayName;
                    el.accountUserSub.textContent = email || (currentUser ? `User ID: ${currentUser.uid}` : 'Saved to Google profile');
                    el.btnGoogleSignInText.textContent = 'Sign Out of Google';
                    el.inlineGoogleForm.classList.add('hidden');
                    return;
                }

                if (currentUser) {
                    el.cloudStatusDot.className = 'w-2 h-2 rounded-full bg-amber-400';
                    el.cloudStatusBadge.className = 'text-xs font-bold px-2.5 py-0.5 rounded-full bg-amber-500/20 text-amber-300 border border-amber-500/30';
                    el.cloudStatusBadge.textContent = 'Device Sync Active';
                    el.accountDisplayName.textContent = 'Device Session';
                    el.accountUserSub.textContent = `Account ID: ${currentUser.uid}`;
                    el.btnGoogleSignInText.textContent = 'Sign in with Google';
                    return;
                }

                el.cloudStatusDot.className = 'w-2 h-2 rounded-full bg-emerald-400';
                el.cloudStatusBadge.className = 'text-xs font-bold px-2.5 py-0.5 rounded-full bg-slate-800 text-emerald-300 border border-emerald-500/30';
                el.cloudStatusBadge.textContent = 'Local Auto-Save';
                el.accountDisplayName.textContent = 'Device Storage Active';
                el.accountUserSub.textContent = 'Sign in with Google below to link your email & back up shifts.';
                el.btnGoogleSignInText.textContent = 'Sign in with Google';
            }

            async function handleGoogleButtonClick() {
                const isGoogleConnected = (currentUser && (currentUser.providerData || []).some(p => p.providerId === 'google.com')) || Boolean(localGoogleProfile);
                if (isGoogleConnected) {
                    localGoogleProfile = null;
                    saveLocalCache();
                    if (auth && currentUser && (currentUser.providerData || []).some(p => p.providerId === 'google.com')) {
                        try {
                            await signOut(auth);
                            await signInAnonymously(auth);
                        } catch (err) {
                            console.error('Sign out error:', err);
                        }
                    }
                    updateAccountModalUI();
                    showToast('Signed out of Google');
                    return;
                }

                if (!auth) {
                    el.inlineGoogleForm.classList.remove('hidden');
                    el.inlineGoogleEmail.focus();
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
                    console.error('Google sign-in popup fallback:', err);
                    if (err.code !== 'auth/popup-closed-by-user') {
                        el.inlineGoogleForm.classList.remove('hidden');
                        el.inlineGoogleEmail.focus();
                    }
                }
            }

            // Toast helper
            function showToast(message, type = 'success') {
                const toast = document.createElement('div');
                toast.className = `p-3.5 rounded-xl shadow-xl text-xs font-semibold text-white border flex items-center justify-between gap-3 pointer-events-auto transition-all transform translate-y-2 opacity-0 ${
                    type === 'error' ? 'bg-rose-900/90 border-rose-700' : 'bg-slate-900/95 border-slate-700'
                }`;
                toast.innerHTML = `<span>${escapeHtml(message)}</span><span class="w-2 h-2 rounded-full ${type === 'error' ? 'bg-rose-400' : 'bg-emerald-400'} shrink-0"></span>`;
                el.toastContainer.appendChild(toast);
                requestAnimationFrame(() => {
                    toast.classList.remove('translate-y-2', 'opacity-0');
                });
                setTimeout(() => {
                    toast.classList.add('translate-y-2', 'opacity-0');
                    setTimeout(() => toast.remove(), 300);
                }, 3500);
            }

            function escapeHtml(str) {
                return String(str || '').replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;').replace(/"/g, '&quot;');
            }

            function formatAUD(amount) {
                return new Intl.NumberFormat('en-AU', { style: 'currency', currency: 'AUD' }).format(amount || 0);
            }

            function formatHours(hrs) {
                return Number(hrs || 0).toFixed(2);
            }

            function getTodayISO() {
                const d = new Date();
                const year = d.getFullYear();
                const month = String(d.getMonth() + 1).padStart(2, '0');
                const day = String(d.getDate()).padStart(2, '0');
                return `${year}-${month}-${day}`;
            }

            function parseLocalDate(isoStr) {
                const [y, m, d] = String(isoStr).split('-').map(Number);
                return new Date(y, m - 1, d);
            }

            function formatDisplayDate(isoStr) {
                if (!isoStr) return '';
                const d = parseLocalDate(isoStr);
                return d.toLocaleDateString('en-AU', { weekday: 'short', day: 'numeric', month: 'short', year: 'numeric' });
            }

            // Calculation Logic
            function calculateShiftPay(totalHours, bDoubleHours, isWeekend) {
                totalHours = Math.max(0, Number(totalHours) || 0);
                bDoubleHours = Math.max(0, Math.min(totalHours, Number(bDoubleHours) || 0));

                const normalRate = Number(state.rates.rateNormal) || 0;
                const bdExtra = Number(state.rates.rateBDouble) || 0;
                const wkndExtra = Number(state.rates.rateWeekend) || 0;

                const basePay = totalHours * normalRate;
                const bdPay = bDoubleHours * bdExtra;
                const wkndPay = isWeekend ? (totalHours * wkndExtra) : 0;
                const totalPay = basePay + bdPay + wkndPay;

                return {
                    basePay,
                    bdPay,
                    wkndPay,
                    totalPay
                };
            }

            function getPeriodBounds(periodKey) {
                const now = new Date();
                const today = new Date(now.getFullYear(), now.getMonth(), now.getDate());
                const startDayOfWeek = Number(state.rates.weekStartDay) !== undefined ? Number(state.rates.weekStartDay) : 1;

                let start = new Date(today);
                let end = new Date(today);

                const currentDay = today.getDay();
                let diffToStart = currentDay - startDayOfWeek;
                if (diffToStart < 0) diffToStart += 7;

                if (periodKey === 'this_week') {
                    start.setDate(today.getDate() - diffToStart);
                    end = new Date(start);
                    end.setDate(start.getDate() + 6);
                } else if (periodKey === 'last_week') {
                    start.setDate(today.getDate() - diffToStart - 7);
                    end = new Date(start);
                    end.setDate(start.getDate() + 6);
                } else if (periodKey === 'fortnight') {
                    start.setDate(today.getDate() - diffToStart - 7);
                    end = new Date(start);
                    end.setDate(start.getDate() + 13);
                } else if (periodKey === 'this_month') {
                    start = new Date(today.getFullYear(), today.getMonth(), 1);
                    end = new Date(today.getFullYear(), today.getMonth() + 1, 0);
                } else {
                    start = new Date(2020, 0, 1);
                    end = new Date(2035, 11, 31);
                }
                return { start, end };
            }

            function syncRatesUI() {
                el.rateNormal.value = state.rates.rateNormal;
                el.rateBDouble.value = state.rates.rateBDouble;
                el.rateWeekend.value = state.rates.rateWeekend;
                el.autoWeekendSetting.checked = Boolean(state.rates.autoWeekend);
                el.weekStartDaySelect.value = String(state.rates.weekStartDay ?? 1);

                const base = Number(state.rates.rateNormal) || 0;
                const bd = Number(state.rates.rateBDouble) || 0;
                const wknd = Number(state.rates.rateWeekend) || 0;

                el.ratesSummarySub.textContent = `Base $${base.toFixed(2)} • BD +$${bd.toFixed(2)} • Wknd +$${wknd.toFixed(2)}`;

                el.effWeekdayBase.textContent = formatAUD(base) + '/hr';
                el.effWeekdayBD.textContent = formatAUD(base + bd) + '/hr';
                el.effWeekendBase.textContent = formatAUD(base + wknd) + '/hr';
                el.effWeekendBD.textContent = formatAUD(base + bd + wknd) + '/hr';

                updateLivePreview();
            }

            function updateLivePreview() {
                const totalHours = parseFloat(el.totalHours.value) || 0;
                const droveBD = el.droveBDoubleToggle.checked;
                const bDoubleHours = droveBD ? (parseFloat(el.bDoubleHours.value) || totalHours) : 0;
                const isWeekend = el.isWeekendToggle.checked;

                const breakdown = calculateShiftPay(totalHours, bDoubleHours, isWeekend);
                el.previewTotalPay.textContent = formatAUD(breakdown.totalPay);

                let lines = [];
                lines.innerHTML = '';
                if (totalHours <= 0) {
                    el.previewBreakdownLines.innerHTML = `<div>Enter hours worked to preview pay breakdown.</div>`;
                    return;
                }

                lines.push(`<div>Ordinary Base Pay (${formatHours(totalHours)} hrs @ ${formatAUD(state.rates.rateNormal)}/hr): <span class="text-white font-semibold">${formatAUD(breakdown.basePay)}</span></div>`);
                if (bDoubleHours > 0) {
                    lines.push(`<div>B-Double Extra (${formatHours(bDoubleHours)} hrs @ +${formatAUD(state.rates.rateBDouble)}/hr): <span class="text-amber-300 font-semibold">+${formatAUD(breakdown.bdPay)}</span></div>`);
                }
                if (isWeekend && breakdown.wkndPay > 0) {
                    lines.push(`<div>Weekend Extra (${formatHours(totalHours)} hrs @ +${formatAUD(state.rates.rateWeekend)}/hr): <span class="text-purple-300 font-semibold">+${formatAUD(breakdown.wkndPay)}</span></div>`);
                }
                el.previewBreakdownLines.innerHTML = lines.join('');
            }

            function renderDashboard() {
                const { start, end } = getPeriodBounds(state.currentPeriod);
                const filteredShifts = state.shifts.filter(s => {
                    const d = parseLocalDate(s.date);
                    if (d < start || d > end) return false;
                    if (state.filterBDOnly && Number(s.bDoubleHours || 0) <= 0) return false;
                    return true;
                });

                let totalPay = 0;
                let totalHours = 0;
                let baseHours = 0;
                let bdHours = 0;
                let weekendHours = 0;
                let bdDaysCount = 0;

                filteredShifts.forEach(s => {
                    const th = Number(s.totalHours) || 0;
                    const bdh = Number(s.bDoubleHours) || 0;
                    const isWk = Boolean(s.isWeekend);
                    const calc = calculateShiftPay(th, bdh, isWk);

                    totalPay += calc.totalPay;
                    totalHours += th;
                    if (bdh > 0) {
                        bdHours += bdh;
                        bdDaysCount++;
                    }
                    baseHours += (th - bdh);
                    if (isWk) weekendHours += th;
                });

                el.statTotalPay.textContent = formatAUD(totalPay);
                el.statShiftCount.textContent = `${filteredShifts.length} shift${filteredShifts.length === 1 ? '' : 's'} logged`;
                el.statTotalHours.textContent = formatHours(totalHours);
                const avgRate = totalHours > 0 ? (totalPay / totalHours) : 0;
                el.statAvgRate.textContent = `Avg: ${formatAUD(avgRate)}/hr`;
                el.statBaseHours.textContent = formatHours(baseHours) + ' hrs';
                el.statWeekendHoursNote.textContent = `${formatHours(weekendHours)} weekend hrs`;
                el.statBDHours.textContent = formatHours(bdHours) + ' hrs';
                el.statBDDaysNote.textContent = `${bdDaysCount} days driving B-Double`;

                // Render Shift List
                if (filteredShifts.length === 0) {
                    el.shiftListContainer.innerHTML = `
                        <div class="p-8 text-center text-slate-400 space-y-2">
                            <svg xmlns="http://www.w3.org/2000/svg" class="w-10 h-10 mx-auto text-slate-600" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/></svg>
                            <p class="text-sm font-semibold text-slate-300">No shifts recorded for this period</p>
                            <p class="text-xs text-slate-500">Log a shift using the form on the left to get started.</p>
                        </div>
                    `;
                } else {
                    // Sort descending by date
                    filteredShifts.sort((a, b) => new Date(b.date) - new Date(a.date));
                    el.shiftListContainer.innerHTML = filteredShifts.map(s => {
                        const th = Number(s.totalHours) || 0;
                        const bdh = Number(s.bDoubleHours) || 0;
                        const isWk = Boolean(s.isWeekend);
                        const calc = calculateShiftPay(th, bdh, isWk);

                        return `
                            <div class="p-4 sm:p-5 hover:bg-slate-850/60 transition flex flex-col sm:flex-row sm:items-center justify-between gap-3 group">
                                <div class="space-y-1 min-w-0">
                                    <div class="flex flex-wrap items-center gap-2">
                                        <span class="text-sm font-bold text-white">${escapeHtml(formatDisplayDate(s.date))}</span>
                                        ${isWk ? '<span class="text-[10px] font-bold px-2 py-0.5 rounded-full bg-purple-500/20 text-purple-300 border border-purple-500/30">Weekend</span>' : ''}
                                        ${bdh > 0 ? `<span class="text-[10px] font-bold px-2 py-0.5 rounded-full bg-amber-500/20 text-amber-300 border border-amber-500/30">B-Double (${formatHours(bdh)}h)</span>` : ''}
                                    </div>
                                    <div class="text-xs text-slate-400 flex flex-wrap items-center gap-x-3 gap-y-1">
                                        <span>Total: <strong class="text-slate-200">${formatHours(th)} hrs</strong></span>
                                        <span>Base: <strong class="text-slate-200">${formatAUD(calc.basePay)}</strong></span>
                                        ${bdh > 0 ? `<span>BD Extra: <strong class="text-amber-300">+${formatAUD(calc.bdPay)}</strong></span>` : ''}
                                        ${calc.wkndPay > 0 ? `<span>Wknd Extra: <strong class="text-purple-300">+${formatAUD(calc.wkndPay)}</strong></span>` : ''}
                                    </div>
                                    ${s.notes ? `<div class="text-xs text-slate-400 italic truncate max-w-md">"${escapeHtml(s.notes)}"</div>` : ''}
                                </div>
                                <div class="flex items-center justify-between sm:justify-end gap-3 shrink-0 pt-2 sm:pt-0 border-t sm:border-0 border-slate-800">
                                    <div class="text-right">
                                        <div class="text-base sm:text-lg font-extrabold text-emerald-400 tabular-nums">${formatAUD(calc.totalPay)}</div>
                                        <div class="text-[10px] text-slate-400">Net Shift Pay</div>
                                    </div>
                                    <div class="flex items-center gap-1">
                                        <button type="button" data-action="edit" data-id="${s.id}" class="p-2 rounded-lg bg-slate-800 hover:bg-slate-700 text-slate-300 hover:text-white transition" title="Edit Shift">
                                            <svg xmlns="http://www.w3.org/2000/svg" class="w-3.5 h-3.5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7"/><path d="M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z"/></svg>
                                        </button>
                                        <button type="button" data-action="delete" data-id="${s.id}" class="p-2 rounded-lg bg-slate-800 hover:bg-rose-900/50 text-slate-400 hover:text-rose-300 transition" title="Delete Shift">
                                            <svg xmlns="http://www.w3.org/2000/svg" class="w-3.5 h-3.5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="3 6 5 6 21 6"/><path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"/></svg>
                                        </button>
                                    </div>
                                </div>
                            </div>
                        `;
                    }).join('');
                }
            }

            // Event Listeners & Initialization
            loadLocalCache();
            syncRatesUI();
            el.shiftDate.value = getTodayISO();

            // Setup Firebase if available
            try {
                if (typeof __firebase_config !== 'undefined' && __firebase_config) {
                    app = initializeApp(__firebase_config);
                    auth = getAuth(app);
                    db = getFirestore(app);

                    onAuthStateChanged(auth, async (user) => {
                        currentUser = user;
                        if (!user) {
                            try {
                                await signInAnonymously(auth);
                            } catch (e) {
                                console.error('Anonymous sign-in failed:', e);
                            }
                        } else {
                            // Fetch user cloud data
                            updateAccountModalUI();
                        }
                    });
                }
            } catch (e) {
                console.log('Firebase running in local offline mode:', e);
            }

            updateAccountModalUI();
            renderDashboard();

            // Modal & Interactive Event Bindings
            el.btnOpenAccountSettings.addEventListener('click', () => {
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

            el.btnCancelInlineGoogle.addEventListener('click', () => {
                el.inlineGoogleForm.classList.add('hidden');
            });

            el.btnConfirmInlineGoogle.addEventListener('click', () => {
                const name = el.inlineGoogleName.value.trim() || 'Driver';
                const email = el.inlineGoogleEmail.value.trim() || 'driver@gmail.com';
                localGoogleProfile = { name, email, uid: 'local_google_' + Date.now() };
                saveLocalCache();
                updateAccountModalUI();
                el.inlineGoogleForm.classList.add('hidden');
                showToast(`Connected Google account (${email}) & backed up shifts!`);
            });

            el.btnSyncNow.addEventListener('click', () => {
                uploadAllLocalShiftsToCloud(true);
            });

            el.btnExportCsv.addEventListener('click', () => {
                if (state.shifts.length === 0) {
                    showToast('No shifts to export', 'error');
                    return;
                }
                let csv = 'Date,Day,TotalHours,BDoubleHours,IsWeekend,BasePayAUD,B_DoubleExtraAUD,WeekendExtraAUD,TotalPayAUD,Notes\n';
                state.shifts.forEach(s => {
                    const th = Number(s.totalHours) || 0;
                    const bdh = Number(s.bDoubleHours) || 0;
                    const isWk = Boolean(s.isWeekend);
                    const calc = calculateShiftPay(th, bdh, isWk);
                    const d = parseLocalDate(s.date);
                    const dayName = d.toLocaleDateString('en-AU', { weekday: 'long' });
                    csv += `"${s.date}","${dayName}",${th},${bdh},${isWk},${calc.basePay.toFixed(2)},${calc.bdPay.toFixed(2)},${calc.wkndPay.toFixed(2)},${calc.totalPay.toFixed(2)},"${(s.notes || '').replace(/"/g, '""')}"\n`;
                });
                const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
                const url = URL.createObjectURL(blob);
                const a = document.createElement('a');
                a.href = url;
                a.download = `RigPay_Shifts_Export_${getTodayISO()}.csv`;
                document.body.appendChild(a);
                a.click();
                document.body.removeChild(a);
                showToast('Shift CSV exported successfully');
            });

            el.btnExportBackupJson.addEventListener('click', () => {
                const backupObj = {
                    version: 2,
                    app: 'RigPay',
                    exportedAt: new Date().toISOString(),
                    rates: state.rates,
                    shifts: state.shifts
                };
                const blob = new Blob([JSON.stringify(backupObj, null, 2)], { type: 'application/json' });
                const url = URL.createObjectURL(blob);
                const a = document.createElement('a');
                a.href = url;
                a.download = `RigPay_Backup_${getTodayISO()}.json`;
                document.body.appendChild(a);
                a.click();
                document.body.removeChild(a);
                showToast('Backup JSON file saved');
            });

            el.inputRestoreBackupJson.addEventListener('change', (e) => {
                const file = e.target.files[0];
                if (!file) return;
                const reader = new FileReader();
                reader.onload = function(evt) {
                    try {
                        const parsed = JSON.parse(evt.target.result);
                        if (parsed && Array.isArray(parsed.shifts)) {
                            state.shifts = parsed.shifts;
                            if (parsed.rates) {
                                state.rates = { ...DEFAULT_RATES, ...parsed.rates };
                            }
                            saveLocalCache();
                            syncRatesUI();
                            renderDashboard();
                            uploadAllLocalShiftsToCloud(false);
                            showToast(`Restored ${state.shifts.length} shifts successfully!`);
                            el.accountModal.classList.add('hidden');
                            el.accountModal.classList.remove('flex');
                        } else {
                            showToast('Invalid backup file structure', 'error');
                        }
                    } catch (err) {
                        console.error('Restore parse error:', err);
                        showToast('Could not read backup file', 'error');
                    }
                };
                reader.readAsText(file);
                e.target.value = '';
            });

            el.weekStartDaySelect.addEventListener('change', (e) => {
                state.rates.weekStartDay = parseInt(e.target.value, 10);
                saveLocalCache();
                uploadAllLocalShiftsToCloud(false);
                renderDashboard();
                showToast('Pay week start updated');
            });

            el.btnOpenReset.addEventListener('click', () => {
                el.resetModal.classList.remove('hidden');
                el.resetModal.classList.add('flex');
            });

            el.btnCancelReset.addEventListener('click', () => {
                el.resetModal.classList.add('hidden');
                el.resetModal.classList.remove('flex');
            });

            el.resetModal.addEventListener('click', (e) => {
                if (e.target === el.resetModal) {
                    el.resetModal.classList.add('hidden');
                    el.resetModal.classList.remove('flex');
                }
            });

            el.btnConfirmReset.addEventListener('click', async () => {
                state.shifts = [];
                saveLocalCache();
                if (db && currentUser) {
                    try {
                        // Clear cloud shifts
                        state.shifts.forEach(async (s) => {
                            if (s && s.id) {
                                await deleteDoc(doc(db, 'artifacts', appId, 'users', currentUser.uid, 'shifts', s.id));
                            }
                        });
                    } catch (err) {
                        console.error('Cloud reset error:', err);
                    }
                }
                renderDashboard();
                el.resetModal.classList.add('hidden');
                el.resetModal.classList.remove('flex');
                el.accountModal.classList.add('hidden');
                el.accountModal.classList.remove('flex');
                showToast('All shift data cleared');
            });

            // Date / Day detection & Auto-weekend detection
            el.shiftDate.addEventListener('change', () => {
                const val = el.shiftDate.value;
                if (!val) return;
                const d = parseLocalDate(val);
                const dayName = d.toLocaleDateString('en-AU', { weekday: 'long' });
                el.dayOfWeekBadge.textContent = dayName;

                const dayIndex = d.getDay(); // 0 = Sun, 6 = Sat
                const isSatSun = (dayIndex === 0 || dayIndex === 6);
                if (state.rates.autoWeekend && isSatSun) {
                    el.isWeekendToggle.checked = true;
                    el.weekendAutoTag.classList.remove('hidden');
                } else if (state.rates.autoWeekend) {
                    el.isWeekendToggle.checked = false;
                    el.weekendAutoTag.classList.add('hidden');
                }
                updateLivePreview();
            });

            el.isWeekendToggle.addEventListener('change', () => {
                if (el.isWeekendToggle.checked) {
                    el.weekendAutoTag.classList.remove('hidden');
                } else {
                    el.weekendAutoTag.classList.add('hidden');
                }
                updateLivePreview();
            });

            // Time Calculator helper toggle
            el.btnToggleTimeCalc.addEventListener('click', () => {
                el.timeCalcPanel.classList.toggle('hidden');
            });

            el.btnApplyTimeCalc.addEventListener('click', () => {
                const start = el.calcStart.value;
                const end = el.calcEnd.value;
                const breakMins = parseFloat(el.calcBreak.value) || 0;
                if (!start || !end) return;

                const [sh, sm] = start.split(':').map(Number);
                const [eh, em] = end.split(':').map(Number);

                let startMin = sh * 60 + sm;
                let endMin = eh * 60 + em;
                if (endMin <= startMin) {
                    endMin += 24 * 60; // Overnight shift
                }
                const workedMins = (endMin - startMin) - breakMins;
                const totalH = Math.max(0.25, Math.round((workedMins / 60) * 100) / 100);

                el.totalHours.value = totalH;
                el.timeCalcPanel.classList.add('hidden');
                updateLivePreview();
                showToast(`Applied ${totalH} hours from start/finish`);
            });

            // B-Double Toggle
            el.droveBDoubleToggle.addEventListener('change', () => {
                if (el.droveBDoubleToggle.checked) {
                    el.bDoubleHoursWrapper.classList.remove('hidden');
                    const th = parseFloat(el.totalHours.value) || 0;
                    if (th > 0 && !el.bDoubleHours.value) {
                        el.bDoubleHours.value = th;
                    }
                    el.bDoubleBox.className = "rounded-xl bg-slate-950/90 border border-amber-500/50 p-3.5 space-y-3 transition-colors";
                } else {
                    el.bDoubleHoursWrapper.classList.add('hidden');
                    el.bDoubleHours.value = '';
                    el.bdValidationMsg.classList.add('hidden');
                    el.bDoubleBox.className = "rounded-xl bg-slate-950/90 border border-slate-800 p-3.5 space-y-3 transition-colors";
                }
                updateLivePreview();
            });

            el.btnAllShiftBD.addEventListener('click', () => {
                const th = parseFloat(el.totalHours.value) || 0;
                el.bDoubleHours.value = th;
                el.bdValidationMsg.classList.add('hidden');
                updateLivePreview();
            });

            el.totalHours.addEventListener('input', () => {
                if (el.droveBDoubleToggle.checked) {
                    const th = parseFloat(el.totalHours.value) || 0;
                    const bdh = parseFloat(el.bDoubleHours.value) || 0;
                    if (bdh > th) {
                        el.bDoubleHours.value = th;
                    }
                }
                updateLivePreview();
            });

            el.bDoubleHours.addEventListener('input', () => {
                const th = parseFloat(el.totalHours.value) || 0;
                const bdh = parseFloat(el.bDoubleHours.value) || 0;
                if (bdh > th) {
                    el.bdValidationMsg.classList.remove('hidden');
                } else {
                    el.bdValidationMsg.classList.add('hidden');
                }
                updateLivePreview();
            });

            // Live rate inputs
            document.querySelectorAll('.rate-input').forEach(input => {
                input.addEventListener('input', () => {
                    state.rates.rateNormal = parseFloat(el.rateNormal.value) || 0;
                    state.rates.rateBDouble = parseFloat(el.rateBDouble.value) || 0;
                    state.rates.rateWeekend = parseFloat(el.rateWeekend.value) || 0;
                    saveLocalCache();
                    uploadAllLocalShiftsToCloud(false);
                    syncRatesUI();
                });
            });

            el.autoWeekendSetting.addEventListener('change', () => {
                state.rates.autoWeekend = el.autoWeekendSetting.checked;
                saveLocalCache();
                uploadAllLocalShiftsToCloud(false);
                const d = parseLocalDate(el.shiftDate.value);
                if (d) {
                    const dayIndex = d.getDay();
                    if (state.rates.autoWeekend && (dayIndex === 0 || dayIndex === 6)) {
                        el.isWeekendToggle.checked = true;
                        el.weekendAutoTag.classList.remove('hidden');
                    } else if (state.rates.autoWeekend) {
                        el.isWeekendToggle.checked = false;
                        el.weekendAutoTag.classList.add('hidden');
                    }
                }
                updateLivePreview();
            });

            // Shift form submission
            el.shiftForm.addEventListener('submit', (e) => {
                e.preventDefault();
                const date = el.shiftDate.value;
                const totalHours = parseFloat(el.totalHours.value);
                if (!date || isNaN(totalHours) || totalHours <= 0) {
                    showToast('Please enter a valid date and hours worked', 'error');
                    return;
                }

                const droveBD = el.droveBDoubleToggle.checked;
                let bDoubleHours = droveBD ? (parseFloat(el.bDoubleHours.value) || 0) : 0;
                if (bDoubleHours > totalHours) bDoubleHours = totalHours;

                const isWeekend = el.isWeekendToggle.checked;
                const notes = el.shiftNotes.value.trim();
                const editId = el.editShiftId.value;

                if (editId) {
                    const idx = state.shifts.findIndex(s => s.id === editId);
                    if (idx !== -1) {
                        state.shifts[idx] = {
                            ...state.shifts[idx],
                            date,
                            totalHours,
                            bDoubleHours,
                            isWeekend,
                            notes,
                            updatedAt: Date.now()
                        };
                    }
                    showToast('Shift updated successfully');
                } else {
                    const newShift = {
                        id: 'shift_' + Date.now() + '_' + Math.random().toString(36).substr(2, 4),
                        date,
                        totalHours,
                        bDoubleHours,
                        isWeekend,
                        notes,
                        createdAt: Date.now()
                    };
                    state.shifts.push(newShift);
                    showToast('Shift logged successfully');
                }

                saveLocalCache();
                uploadAllLocalShiftsToCloud(false);
                resetShiftForm();
                renderDashboard();
            });

            el.btnCancelEdit.addEventListener('click', () => {
                resetShiftForm();
            });

            function resetShiftForm() {
                state.editingId = null;
                el.editShiftId.value = '';
                el.formTitle.textContent = 'Log Daily Shift';
                el.btnSaveShiftText.textContent = 'Save Shift Log';
                el.btnCancelEdit.classList.add('hidden');
                el.shiftDate.value = getTodayISO();
                el.totalHours.value = '';
                el.droveBDoubleToggle.checked = false;
                el.bDoubleHoursWrapper.classList.add('hidden');
                el.bDoubleHours.value = '';
                el.bDoubleBox.className = "rounded-xl bg-slate-950/90 border border-slate-800 p-3.5 space-y-3 transition-colors";
                el.isWeekendToggle.checked = false;
                el.weekendAutoTag.classList.add('hidden');
                el.shiftNotes.value = '';
                el.bdValidationMsg.classList.add('hidden');

                const d = parseLocalDate(el.shiftDate.value);
                const dayName = d.toLocaleDateString('en-AU', { weekday: 'long' });
                el.dayOfWeekBadge.textContent = dayName;
                updateLivePreview();
            }

            // Period filter buttons
            el.periodButtons.forEach(btn => {
                btn.addEventListener('click', () => {
                    el.periodButtons.forEach(b => {
                        b.className = 'period-btn px-2.5 sm:px-3 py-2 sm:py-1.5 rounded-lg text-xs font-semibold transition text-slate-300 hover:bg-slate-800 text-center';
                    });
                    btn.className = 'period-btn px-2.5 sm:px-3 py-2 sm:py-1.5 rounded-lg text-xs font-semibold transition bg-amber-500 text-slate-950 shadow-sm text-center';
                    state.currentPeriod = btn.getAttribute('data-period');
                    
                    const titles = {
                        'this_week': 'Showing current week',
                        'last_week': 'Showing last week',
                        'fortnight': 'Showing 14-day pay period',
                        'this_month': 'Showing current calendar month',
                        'all': 'Showing all recorded shift history'
                    };
                    el.periodRangeLabel.textContent = titles[state.currentPeriod] || '';
                    el.historySubtitle.textContent = titles[state.currentPeriod] || '';
                    renderDashboard();
                });
            });

            el.filterBDOnly.addEventListener('change', () => {
                state.filterBDOnly = el.filterBDOnly.checked;
                renderDashboard();
            });

            // Shift list actions (Edit / Delete)
            el.shiftListContainer.addEventListener('click', (e) => {
                const btn = e.target.closest('button[data-action]');
                if (!btn) return;
                const action = btn.getAttribute('data-action');
                const id = btn.getAttribute('data-id');

                if (action === 'delete') {
                    const idx = state.shifts.findIndex(s => s.id === id);
                    if (idx !== -1) {
                        state.shifts.splice(idx, 1);
                        saveLocalCache();
                        if (db && currentUser) {
                            deleteDoc(doc(db, 'artifacts', appId, 'users', currentUser.uid, 'shifts', id)).catch(err => console.error('Delete shift sync error:', err));
                        }
                        renderDashboard();
                        showToast('Shift deleted');
                    }
                } else if (action === 'edit') {
                    const shift = state.shifts.find(s => s.id === id);
                    if (shift) {
                        state.editingId = shift.id;
                        el.editShiftId.value = shift.id;
                        el.formTitle.textContent = 'Edit Shift Log';
                        el.btnSaveShiftText.textContent = 'Update Shift Log';
                        el.btnCancelEdit.classList.remove('hidden');

                        el.shiftDate.value = shift.date;
                        const d = parseLocalDate(shift.date);
                        el.dayOfWeekBadge.textContent = d.toLocaleDateString('en-AU', { weekday: 'long' });

                        el.totalHours.value = shift.totalHours;
                        const hasBD = Number(shift.bDoubleHours || 0) > 0;
                        el.droveBDoubleToggle.checked = hasBD;
                        if (hasBD) {
                            el.bDoubleHoursWrapper.classList.remove('hidden');
                            el.bDoubleHours.value = shift.bDoubleHours;
                            el.bDoubleBox.className = "rounded-xl bg-slate-950/90 border border-amber-500/50 p-3.5 space-y-3 transition-colors";
                        } else {
                            el.bDoubleHoursWrapper.classList.add('hidden');
                            el.bDoubleHours.value = '';
                            el.bDoubleBox.className = "rounded-xl bg-slate-950/90 border border-slate-800 p-3.5 space-y-3 transition-colors";
                        }

                        el.isWeekendToggle.checked = Boolean(shift.isWeekend);
                        if (shift.isWeekend) {
                            el.weekendAutoTag.classList.remove('hidden');
                        } else {
                            el.weekendAutoTag.classList.add('hidden');
                        }
                        el.shiftNotes.value = shift.notes || '';
                        updateLivePreview();
                        window.scrollTo({ top: 0, behavior: 'smooth' });
                    }
                }
            });

            // Initialize initial date badge
            const initialDateObj = parseLocalDate(el.shiftDate.value);
            el.dayOfWeekBadge.textContent = initialDateObj.toLocaleDateString('en-AU', { weekday: 'long' });
            updateLivePreview();
        })();
    </script>
</body>
</html>
