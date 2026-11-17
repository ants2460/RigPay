<html lang="en" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RigPay — Heavy Vehicle Hours &amp; Pay Tracker</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Inter -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', system-ui, -apple-system, sans-serif;
            background-color: #020617;
            color: #f8fafc;
        }
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #0f172a;
        }
        ::-webkit-scrollbar-thumb {
            background: #334155;
            border-radius: 9999px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #475569;
        }
        .bg-slate-850 {
            background-color: #131c31;
        }
        input[type="number"]::-webkit-inner-spin-button,
        input[type="number"]::-webkit-outer-spin-button {
            -webkit-appearance: none;
            margin: 0;
        }
        input[type="number"] {
            -moz-appearance: textfield;
        }
    </style>
</head>
<body class="min-h-screen bg-slate-950 text-slate-100 antialiased selection:bg-amber-500 selection:text-slate-950 overflow-x-hidden">

    <!-- Toast Notification Banner -->
    <div id="toastBanner" class="fixed bottom-4 right-4 left-4 sm:left-auto z-50 transform translate-y-24 opacity-0 transition-all duration-300 pointer-events-none">
        <div class="bg-slate-800 border border-slate-700 text-white px-4 py-3 rounded-xl shadow-2xl flex items-center justify-center sm:justify-start gap-2.5 text-sm font-semibold">
            <span class="w-2.5 h-2.5 rounded-full bg-emerald-400 shrink-0"></span>
            <span id="toastMessage">Saved</span>
        </div>
    </div>

    <!-- Top Sticky Header -->
    <header class="sticky top-0 z-30 bg-slate-950/90 backdrop-blur-md border-b border-slate-800/80">
        <div class="max-w-6xl mx-auto px-3.5 sm:px-6 h-16 flex items-center justify-between gap-3">
            <!-- Brand Logo & Title -->
            <div class="flex items-center gap-2.5 min-w-0">
                <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-amber-400 to-orange-500 text-slate-950 flex items-center justify-center shadow-lg shadow-amber-500/20 shrink-0">
                    <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
                        <path d="M14 18V6a2 2 0 0 0-2-2H4a2 2 0 0 0-2 2v11a1 1 0 0 0 1 1h2"/>
                        <path d="M15 18H9"/>
                        <path d="M19 18h2a1 1 0 0 0 1-1v-3.65a1 1 0 0 0-.22-.624l-3.48-4.35A1 1 0 0 0 17.52 8H14"/>
                        <circle cx="17" cy="18" r="2"/>
                        <circle cx="7" cy="18" r="2"/>
                    </svg>
                </div>
                <h1 class="text-xl sm:text-2xl font-extrabold tracking-tight text-white truncate">RigPay</h1>
            </div>

            <!-- Settings Gear Button -->
            <button type="button" id="btnOpenAccountSettings" class="inline-flex items-center gap-2 px-3.5 py-2.5 rounded-xl bg-slate-900 hover:bg-slate-800 active:scale-[0.98] text-slate-200 border border-slate-700/80 text-xs sm:text-sm font-semibold transition shrink-0">
                <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4 text-amber-400 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <circle cx="12" cy="12" r="3"/>
                    <path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"/>
                </svg>
                <span>Settings</span>
            </button>
        </div>
    </header>

    <!-- Main Content -->
    <main class="max-w-6xl mx-auto px-3.5 sm:px-6 py-5 sm:py-7 space-y-6">

        <!-- Period Filter Bar & Date Range Label -->
        <section class="bg-slate-900/90 border border-slate-800 rounded-2xl p-3 sm:p-4 flex flex-col md:flex-row md:items-center justify-between gap-3 shadow-lg">
            <div class="grid grid-cols-3 sm:grid-cols-5 gap-1.5 sm:gap-2 w-full md:w-auto">
                <button type="button" data-period="thisWeek" class="period-btn px-3 py-2 rounded-xl text-xs font-bold bg-amber-500 text-slate-950 shadow transition">This Week</button>
                <button type="button" data-period="lastWeek" class="period-btn px-3 py-2 rounded-xl text-xs font-semibold bg-slate-950 text-slate-300 hover:bg-slate-800 border border-slate-800 transition">Last Week</button>
                <button type="button" data-period="fortnight" class="period-btn px-3 py-2 rounded-xl text-xs font-semibold bg-slate-950 text-slate-300 hover:bg-slate-800 border border-slate-800 transition">Fortnight</button>
                <button type="button" data-period="thisMonth" class="period-btn px-3 py-2 rounded-xl text-xs font-semibold bg-slate-950 text-slate-300 hover:bg-slate-800 border border-slate-800 transition">This Month</button>
                <button type="button" data-period="allTime" class="period-btn col-span-2 sm:col-span-1 px-3 py-2 rounded-xl text-xs font-semibold bg-slate-950 text-slate-300 hover:bg-slate-800 border border-slate-800 transition">All Time</button>
            </div>
            <div class="flex items-center justify-between md:justify-end gap-2 text-xs text-slate-400 px-1">
                <span class="uppercase tracking-wider font-semibold text-slate-500">Range:</span>
                <span id="periodRangeText" class="font-bold text-slate-200 tabular-nums">Current Pay Week</span>
            </div>
        </section>

        <!-- Summary KPI Cards -->
        <section class="grid grid-cols-1 min-[420px]:grid-cols-2 lg:grid-cols-4 gap-3 sm:gap-4">
            <!-- Gross Earnings -->
            <div class="bg-slate-900 border border-slate-800 rounded-2xl p-4 sm:p-5 shadow-lg min-w-0">
                <div class="flex items-center justify-between gap-2 mb-1.5">
                    <span class="text-xs font-semibold uppercase tracking-wider text-slate-400">Gross Earnings</span>
                    <span class="w-7 h-7 rounded-lg bg-emerald-500/15 text-emerald-400 flex items-center justify-center text-xs font-bold shrink-0">$</span>
                </div>
                <div id="kpiGrossPay" class="text-2xl sm:text-3xl font-extrabold text-emerald-400 tabular-nums truncate">$0.00</div>
                <div id="kpiAvgHourly" class="text-xs text-slate-400 mt-1 tabular-nums">Avg $0.00/hr</div>
            </div>

            <!-- Total Hours -->
            <div class="bg-slate-900 border border-slate-800 rounded-2xl p-4 sm:p-5 shadow-lg min-w-0">
                <div class="flex items-center justify-between gap-2 mb-1.5">
                    <span class="text-xs font-semibold uppercase tracking-wider text-slate-400">Total Hours</span>
                    <span class="w-7 h-7 rounded-lg bg-sky-500/15 text-sky-400 flex items-center justify-center text-xs font-bold shrink-0">H</span>
                </div>
                <div id="kpiTotalHours" class="text-2xl sm:text-3xl font-extrabold text-white tabular-nums truncate">0.00 hrs</div>
                <div id="kpiShiftCount" class="text-xs text-slate-400 mt-1 tabular-nums">0 shifts logged</div>
            </div>

            <!-- B-Double Hours -->
            <div class="bg-slate-900 border border-slate-800 rounded-2xl p-4 sm:p-5 shadow-lg min-w-0">
                <div class="flex items-center justify-between gap-2 mb-1.5">
                    <span class="text-xs font-semibold uppercase tracking-wider text-amber-400/90">B-Double Hours</span>
                    <span class="w-7 h-7 rounded-lg bg-amber-500/15 text-amber-400 flex items-center justify-center text-[11px] font-extrabold shrink-0">BD</span>
                </div>
                <div id="kpiBDHours" class="text-2xl sm:text-3xl font-extrabold text-amber-400 tabular-nums truncate">0.00 hrs</div>
                <div id="kpiBDAllowance" class="text-xs text-slate-400 mt-1 tabular-nums">+$0.00 BD extra</div>
            </div>

            <!-- Weekend Hours -->
            <div class="bg-slate-900 border border-slate-800 rounded-2xl p-4 sm:p-5 shadow-lg min-w-0">
                <div class="flex items-center justify-between gap-2 mb-1.5">
                    <span class="text-xs font-semibold uppercase tracking-wider text-purple-400/90">Weekend Hours</span>
                    <span class="w-7 h-7 rounded-lg bg-purple-500/15 text-purple-400 flex items-center justify-center text-[11px] font-extrabold shrink-0">WK</span>
                </div>
                <div id="kpiWeekendHours" class="text-2xl sm:text-3xl font-extrabold text-purple-400 tabular-nums truncate">0.00 hrs</div>
                <div id="kpiWeekendAllowance" class="text-xs text-slate-400 mt-1 tabular-nums">+$0.00 wknd extra</div>
            </div>
        </section>

        <!-- Main 2-Column Workspace -->
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-5 sm:gap-6 items-start">

            <!-- Left Column (5 cols on lg): Shift Entry Form + Pay Rates -->
            <div class="lg:col-span-5 space-y-5 sm:space-y-6">

                <!-- 1. Log / Edit Shift Card -->
                <div class="bg-slate-900 border border-slate-800 rounded-2xl shadow-xl overflow-hidden">
                    <div class="px-4 sm:px-5 py-3.5 sm:py-4 bg-slate-850 border-b border-slate-800 flex items-center justify-between gap-2">
                        <div class="flex items-center gap-2 min-w-0">
                            <span class="w-2.5 h-2.5 rounded-full bg-amber-400 shrink-0"></span>
                            <h2 id="formTitle" class="text-base font-bold text-white truncate">Log New Shift</h2>
                        </div>
                        <button type="button" id="btnCancelEdit" class="hidden text-xs font-bold text-rose-400 hover:text-rose-300 bg-rose-500/10 px-2.5 py-1 rounded-lg border border-rose-500/20 transition shrink-0">
                            Cancel Edit
                        </button>
                    </div>

                    <form id="shiftForm" class="p-4 sm:p-5 space-y-4">
                        <input type="hidden" id="editShiftId" value="">

                        <!-- Date & Weekend Toggle -->
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                            <div class="space-y-1.5">
                                <div class="flex items-center justify-between gap-2">
                                    <label for="shiftDate" class="text-xs font-semibold uppercase tracking-wider text-slate-400">Shift Date</label>
                                    <span id="dayOfWeekBadge" class="text-[11px] font-bold text-amber-400">Today</span>
                                </div>
                                <input type="date" id="shiftDate" required class="w-full px-3.5 py-2.5 rounded-xl bg-slate-950 border border-slate-700 text-white font-semibold text-sm focus:outline-none focus:border-amber-500 transition">
                            </div>

                            <!-- Weekend Rate Toggle Box -->
                            <div class="space-y-1.5">
                                <div class="flex items-center justify-between gap-2">
                                    <span class="text-xs font-semibold uppercase tracking-wider text-slate-400">Day Rate</span>
                                    <span id="weekendAutoTag" class="hidden text-[10px] font-extrabold uppercase px-1.5 py-0.5 rounded bg-purple-500/20 text-purple-300 border border-purple-500/30">Weekend +$</span>
                                </div>
                                <label class="flex items-center justify-between px-3.5 py-2.5 rounded-xl bg-slate-950 border border-slate-700 cursor-pointer select-none">
                                    <span class="text-xs font-bold text-purple-300">Weekend Shift</span>
                                    <input type="checkbox" id="isWeekendToggle" class="w-4 h-4 rounded accent-purple-500 cursor-pointer">
                                </label>
                            </div>
                        </div>

                        <!-- Optional Start / Finish Time Calculator -->
                        <div class="rounded-xl bg-slate-950/80 border border-slate-800/90 p-3 space-y-2.5">
                            <div class="flex items-center justify-between">
                                <span class="text-[11px] font-bold uppercase tracking-wider text-slate-400">Quick Time Calculator (Optional)</span>
                                <span class="text-[11px] text-slate-500">Auto-fills hours</span>
                            </div>
                            <div class="grid grid-cols-1 min-[400px]:grid-cols-3 gap-2">
                                <div>
                                    <label for="startTime" class="block text-[11px] text-slate-400 mb-1">Start</label>
                                    <input type="time" id="startTime" class="time-calc-input w-full px-2.5 py-2 rounded-lg bg-slate-900 border border-slate-700 text-slate-200 text-xs font-semibold focus:border-amber-500 focus:outline-none">
                                </div>
                                <div>
                                    <label for="endTime" class="block text-[11px] text-slate-400 mb-1">Finish</label>
                                    <input type="time" id="endTime" class="time-calc-input w-full px-2.5 py-2 rounded-lg bg-slate-900 border border-slate-700 text-slate-200 text-xs font-semibold focus:border-amber-500 focus:outline-none">
                                </div>
                                <div>
                                    <label for="breakMinutes" class="block text-[11px] text-slate-400 mb-1">Unpaid Break (m)</label>
                                    <input type="number" id="breakMinutes" min="0" max="480" step="5" value="30" inputmode="numeric" class="time-calc-input w-full px-2.5 py-2 rounded-lg bg-slate-900 border border-slate-700 text-slate-200 text-xs font-semibold tabular-nums focus:border-amber-500 focus:outline-none">
                                </div>
                            </div>
                        </div>

                        <!-- Total Hours Worked -->
                        <div class="space-y-1.5">
                            <div class="flex items-center justify-between gap-2">
                                <label for="totalHours" class="text-xs font-semibold uppercase tracking-wider text-slate-400">Total Hours Worked</label>
                                <label class="inline-flex items-center gap-1.5 px-2.5 py-1 rounded-lg bg-slate-950 border border-slate-700/90 hover:border-amber-500/50 cursor-pointer select-none transition">
                                    <input type="checkbox" id="deductHalfHrLunch" class="w-3.5 h-3.5 rounded accent-amber-500 cursor-pointer">
                                    <span class="text-[11px] font-bold text-amber-300">-30m Lunch Break</span>
                                </label>
                            </div>
                            <div class="relative">
                                <input type="number" id="totalHours" step="0.01" min="0.01" max="24" required inputmode="decimal" placeholder="e.g. 11.5" class="w-full px-3.5 py-3 pr-16 rounded-xl bg-slate-950 border border-slate-700 text-white font-extrabold text-base tabular-nums focus:outline-none focus:border-amber-500 transition">
                                <span class="absolute right-4 top-1/2 -translate-y-1/2 text-xs font-bold text-slate-500">HOURS</span>
                            </div>
                        </div>

                        <!-- B-Double Toggle & B-Double Hours Box -->
                        <div id="bDoubleBox" class="rounded-xl bg-slate-950/90 border border-slate-800 p-3.5 space-y-3 transition-colors">
                            <div class="flex items-center justify-between gap-3">
                                <div>
                                    <div class="text-sm font-bold text-amber-300">Drove B-Double?</div>
                                    <div class="text-xs text-slate-400">Adds B-Double hourly allowance</div>
                                </div>
                                <label class="relative inline-flex items-center cursor-pointer shrink-0">
                                    <input type="checkbox" id="droveBDoubleToggle" class="sr-only peer">
                                    <div class="w-11 h-6 bg-slate-800 rounded-full peer peer-checked:after:translate-x-full after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-slate-300 after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-amber-500 peer-checked:after:bg-slate-950"></div>
                                </label>
                            </div>

                            <!-- Collapsible B-Double Hours Input -->
                            <div id="bDoubleHoursWrapper" class="hidden pt-2 border-t border-slate-800/90 space-y-2">
                                <div class="flex items-center justify-between gap-2">
                                    <label for="bDoubleHours" class="text-xs font-semibold text-amber-200">B-Double Hours Worked</label>
                                    <button type="button" id="btnAllHoursBD" class="text-[11px] font-bold text-amber-400 hover:text-amber-300 bg-amber-500/10 hover:bg-amber-500/20 px-2.5 py-1 rounded-lg border border-amber-500/30 transition">
                                        Same as Total Hours
                                    </button>
                                </div>
                                <div class="relative">
                                    <input type="number" id="bDoubleHours" step="0.01" min="0" max="24" inputmode="decimal" placeholder="e.g. 8.0" class="w-full px-3.5 py-2.5 pr-16 rounded-xl bg-slate-900 border border-amber-500/40 text-amber-300 font-extrabold text-sm tabular-nums focus:outline-none focus:border-amber-400 transition">
                                    <span class="absolute right-4 top-1/2 -translate-y-1/2 text-xs font-bold text-amber-500/70">BD HRS</span>
                                </div>
                                <p id="bdValidationMsg" class="hidden text-xs text-rose-400 font-medium">B-Double hours cannot exceed Total Hours Worked.</p>
                            </div>
                        </div>

                        <!-- Optional Notes / Route / Load -->
                        <div class="space-y-1.5">
                            <label for="shiftNotes" class="text-xs font-semibold uppercase tracking-wider text-slate-400">Route / Load / Notes <span class=
