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
        /* Custom subtle scrollbar */
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
        /* Hide number input spinners for cleaner numeric inputs */
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
                    <!-- Truck SVG Icon -->
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

        <!-- Summary KPI Cards (4-column responsive grid) -->
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
                        <divsm:text-3xl font-extrabold text-purple-400 tabular-nums truncate">0.00 hrs</div>
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
                        <divclass="text-2xl sm:text-3xl font-extrabold text-purple-400 tabular-nums truncate">0.00 hrs</div>
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
                            <label for="totalHours" class="text-xs font-semibold uppercase tracking-wider text-slate-400">Total Hours Worked</label>
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
                                <h2 class="text-base font-bold text-white">Pay Rates &amp; Top-Ups</h2>
                                <p id="ratesSummarySub" class="text-xs text-slate-400 tabular-nums truncate">Base $36.00 • BD +$6.00 • Wknd +$18.00</p>
                            </div>
                        </div>
                        <span class="text-[11px] sm:text-xs font-semibold text-emerald-400 bg-emerald-500/10 px-2.5 py-1 rounded-lg border border-emerald-500/20 shrink-0">Auto-Saved</span>
                    </button>

                    <div id="ratesPanelBody" class="p-4 sm:p-5 space-y-4">
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

                        <!-- Live Effective Stacked Rates Preview Badges -->
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
                            <span class="text-xs font-medium text-slate-300">Auto-detect Sat &amp; Sun for Weekend Top-Up</span>
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
                        <h3 class="text-base font-bold text-white truncate">Account &amp; Cloud Sync</h3>
                        <p class="text-xs text-slate-400 truncate">Save shifts &amp; rates to your account</p>
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

            <!-- Inline Google Account Link Form -->
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

            <!-- Google Sign-In & Backup Actions -->
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
                All shifts and pay rates are automatically backed up whenever you add, edit, or update rates, and any existing device shifts merge seamlessly when you sign in.
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
         * Single-file application with B-Double allowances, weekend rates,
         * configurable pay week start day, CSV/JSON backups, and Google Account sync.
         */
        (function () {
            'use strict';

            // --- Storage Keys ---
            const STORAGE_KEYS = {
                RATES: 'rigpay_rates_v1',
                SHIFTS: 'rigpay_shifts_v1',
                PROFILE: 'rigpay_linked_google_v1'
            };

            const DEFAULT_RATES = {
                normalRate: 36.00,
                bDoubleExtra: 6.00,
                weekendExtra: 18.00,
                autoWeekend: true,
                weekStartDay: 1 // 1 = Monday
            };

            // --- Firebase Initialization (with seamless offline/standalone fallback) ---
            let auth = null;
            let db = null;
            let currentUser = null;
            let unsubscribeShifts = null;
            let unsubscribeRates = null;
            const appId = typeof __app_id !== 'undefined' ? __app_id : 'rigpay-default';

            try {
                if (typeof __firebase_config !== 'undefined' && __firebase_config) {
                    const firebaseConfig = JSON.parse(__firebase_config);
                    const app = initializeApp(firebaseConfig);
                    auth = getAuth(app);
                    db = getFirestore(app);
                }
            } catch (e) {
                console.warn('Running in standalone local storage mode:', e);
            }

            // --- Application State ---
            let state = {
                rates: loadLocalRates(),
                shifts: loadLocalShifts(),
                linkedProfile: loadLocalProfile(),
                period: 'thisWeek',
                filterBDOnly: false,
                editingId: null
            };

            // --- DOM References ---
            const el = {
                toastBanner: document.getElementById('toastBanner'),
                toastMessage: document.getElementById('toastMessage'),

                // Header & Modals
                btnOpenAccountSettings: document.getElementById('btnOpenAccountSettings'),
                accountModal: document.getElementById('accountModal'),
                btnCloseAccountModal: document.getElementById('btnCloseAccountModal'),
                cloudStatusBadge: document.getElementById('cloudStatusBadge'),
                accountDisplayName: document.getElementById('accountDisplayName'),
                accountUserSub: document.getElementById('accountUserSub'),
                btnGoogleSignIn: document.getElementById('btnGoogleSignIn'),
                btnGoogleSignInText: document.getElementById('btnGoogleSignInText'),
                inlineGoogleForm: document.getElementById('inlineGoogleForm'),
                inlineGoogleName: document.getElementById('inlineGoogleName'),
                inlineGoogleEmail: document.getElementById('inlineGoogleEmail'),
                btnConfirmInlineGoogle: document.getElementById('btnConfirmInlineGoogle'),
                btnCancelInlineGoogle: document.getElementById('btnCancelInlineGoogle'),
                btnSyncNow: document.getElementById('btnSyncNow'),
                btnExportCsv: document.getElementById('btnExportCsv'),
                btnExportBackupJson: document.getElementById('btnExportBackupJson'),
                inputRestoreBackupJson: document.getElementById('inputRestoreBackupJson'),
                weekStartDaySelect: document.getElementById('weekStartDaySelect'),
                btnOpenReset: document.getElementById('btnOpenReset'),
                resetModal: document.getElementById('resetModal'),
                btnCancelReset: document.getElementById('btnCancelReset'),
                btnConfirmReset: document.getElementById('btnConfirmReset'),

                // Period & KPIs
                periodRangeText: document.getElementById('periodRangeText'),
                kpiGrossPay: document.getElementById('kpiGrossPay'),
                kpiAvgHourly: document.getElementById('kpiAvgHourly'),
                kpiTotalHours: document.getElementById('kpiTotalHours'),
                kpiShiftCount: document.getElementById('kpiShiftCount'),
                kpiBDHours: document.getElementById('kpiBDHours'),
                kpiBDAllowance: document.getElementById('kpiBDAllowance'),
                kpiWeekendHours: document.getElementById('kpiWeekendHours'),
                kpiWeekendAllowance: document.getElementById('kpiWeekendAllowance'),

                // Shift Form
                formTitle: document.getElementById('formTitle'),
                btnCancelEdit: document.getElementById('btnCancelEdit'),
                shiftForm: document.getElementById('shiftForm'),
                editShiftId: document.getElementById('editShiftId'),
                shiftDate: document.getElementById('shiftDate'),
                dayOfWeekBadge: document.getElementById('dayOfWeekBadge'),
                isWeekendToggle: document.getElementById('isWeekendToggle'),
                weekendAutoTag: document.getElementById('weekendAutoTag'),
                startTime: document.getElementById('startTime'),
                endTime: document.getElementById('endTime'),
                breakMinutes: document.getElementById('breakMinutes'),
                totalHours: document.getElementById('totalHours'),
                bDoubleBox: document.getElementById('bDoubleBox'),
                droveBDoubleToggle: document.getElementById('droveBDoubleToggle'),
                bDoubleHoursWrapper: document.getElementById('bDoubleHoursWrapper'),
                bDoubleHours: document.getElementById('bDoubleHours'),
                btnAllHoursBD: document.getElementById('btnAllHoursBD'),
                bdValidationMsg: document.getElementById('bdValidationMsg'),
                shiftNotes: document.getElementById('shiftNotes'),
                previewTotalPay: document.getElementById('previewTotalPay'),
                previewBreakdownLines: document.getElementById('previewBreakdownLines'),
                btnSaveShiftText: document.getElementById('btnSaveShiftText'),

                // Rates Card
                ratesSummarySub: document.getElementById('ratesSummarySub'),
                rateNormal: document.getElementById('rateNormal'),
                rateBDouble: document.getElementById('rateBDouble'),
                rateWeekend: document.getElementById('rateWeekend'),
                effWeekdayBase: document.getElementById('effWeekdayBase'),
                effWeekdayBD: document.getElementById('effWeekdayBD'),
                effWeekendBase: document.getElementById('effWeekendBase'),
                effWeekendBD: document.getElementById('effWeekendBD'),
                autoWeekendSetting: document.getElementById('autoWeekendSetting'),

                // History Log
                historySubtitle: document.getElementById('historySubtitle'),
                filterBDOnly: document.getElementById('filterBDOnly'),
                shiftListContainer: document.getElementById('shiftListContainer')
            };

            // --- Local Storage Persistence ---
            function loadLocalRates() {
                try {
                    const raw = localStorage.getItem(STORAGE_KEYS.RATES);
                    if (!raw) return { ...DEFAULT_RATES };
                    return { ...DEFAULT_RATES, ...JSON.parse(raw) };
                } catch (e) {
                    return { ...DEFAULT_RATES };
                }
            }

            function loadLocalShifts() {
                try {
                    const raw = localStorage.getItem(STORAGE_KEYS.SHIFTS);
                    if (!raw) return [];
                    const parsed = JSON.parse(raw);
                    return Array.isArray(parsed) ? parsed : [];
                } catch (e) {
                    return [];
                }
            }

            function loadLocalProfile() {
                try {
                    const raw = localStorage.getItem(STORAGE_KEYS.PROFILE);
                    return raw ? JSON.parse(raw) : null;
                } catch (e) {
                    return null;
                }
            }

            function saveLocalCache() {
                try {
                    localStorage.setItem(STORAGE_KEYS.RATES, JSON.stringify(state.rates));
                    localStorage.setItem(STORAGE_KEYS.SHIFTS, JSON.stringify(state.shifts));
                    if (state.linkedProfile) {
                        localStorage.setItem(STORAGE_KEYS.PROFILE, JSON.stringify(state.linkedProfile));
                    } else {
                        localStorage.removeItem(STORAGE_KEYS.PROFILE);
                    }
                } catch (e) {
                    console.warn('Local storage save warning:', e);
                }
            }

            // --- Formatting & Date Helpers ---
            function formatAUD(val) {
                const num = Number(val) || 0;
                return new Intl.NumberFormat('en-AU', {
                    style: 'currency',
                    currency: 'AUD',
                    minimumFractionDigits: 2,
                    maximumFractionDigits: 2
                }).format(num);
            }

            function formatHours(val) {
                const num = Number(val) || 0;
                return `${num.toFixed(2)} hrs`;
            }

            function getTodayISO() {
                const now = new Date();
                const y = now.getFullYear();
                const m = String(now.getMonth() + 1).padStart(2, '0');
                const d = String(now.getDate()).padStart(2, '0');
                return `${y}-${m}-${d}`;
            }

            function parseLocalDate(isoStr) {
                if (!isoStr || typeof isoStr !== 'string') return new Date();
                const parts = isoStr.split('-').map(Number);
                if (parts.length !== 3) return new Date();
                return new Date(parts[0], parts[1] - 1, parts[2]);
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
                return String(str || '')
                    .replace(/&/g, '&amp;')
                    .replace(/</g, '&lt;')
                    .replace(/>/g, '&gt;')
                    .replace(/"/g, '&quot;')
                    .replace(/'/g, '&#39;');
            }

            let toastTimer = null;
            function showToast(msg) {
                if (!el.toastBanner || !el.toastMessage) return;
                el.toastMessage.textContent = msg;
                el.toastBanner.classList.remove('translate-y-24', 'opacity-0');
                if (toastTimer) clearTimeout(toastTimer);
                toastTimer = setTimeout(() => {
                    el.toastBanner.classList.add('translate-y-24', 'opacity-0');
                }, 2800);
            }

            // --- Core Pay Calculation Engine ---
            function calculateShiftPay(shift, rates = state.rates) {
                const totalHours = Math.max(0, Number(shift.totalHours) || 0);
                const rawBD = Math.max(0, Number(shift.bDoubleHours) || 0);
                const bDoubleHours = Math.min(totalHours, rawBD);
                const normalHours = Math.max(0, totalHours - bDoubleHours);
                const isWeekend = Boolean(shift.isWeekend);

                const baseRate = Math.max(0, Number(rates.normalRate) || 0);
                const bdExtraRate = Math.max(0, Number(rates.bDoubleExtra) || 0);
                const wkndExtraRate = isWeekend ? Math.max(0, Number(rates.weekendExtra) || 0) : 0;

                const basePay = totalHours * baseRate;
                const bdAllowancePay = bDoubleHours * bdExtraRate;
                const weekendAllowancePay = totalHours * wkndExtraRate;
                const totalPay = basePay + bdAllowancePay + weekendAllowancePay;

                return {
                    totalHours,
                    normalHours,
                    bDoubleHours,
                    isWeekend,
                    baseRate,
                    bdExtraRate,
                    wkndExtraRate,
                    basePay,
                    bdAllowancePay,
                    weekendAllowancePay,
                    totalPay
                };
            }

            // --- Period Date Bounds (Respects Custom Week Start Day) ---
            function getPeriodBounds(periodKey) {
                const now = new Date();
                const today = new Date(now.getFullYear(), now.getMonth(), now.getDate());
                const weekStartDay = Number(state.rates.weekStartDay ?? 1); // 0=Sun..6=Sat
                const diffToStart = (today.getDay() - weekStartDay + 7) % 7;

                const startOfThisWeek = new Date(today);
                startOfThisWeek.setDate(today.getDate() - diffToStart);
                const endOfThisWeek = new Date(startOfThisWeek);
                endOfThisWeek.setDate(startOfThisWeek.getDate() + 6);

                if (periodKey === 'thisWeek') {
                    return {
                        start: startOfThisWeek,
                        end: endOfThisWeek,
                        label: `${startOfThisWeek.toLocaleDateString('en-AU', { day: 'numeric', month: 'short' })} – ${endOfThisWeek.toLocaleDateString('en-AU', { day: 'numeric', month: 'short' })}`
                    };
                }

                if (periodKey === 'lastWeek') {
                    const startLast = new Date(startOfThisWeek);
                    startLast.setDate(startOfThisWeek.getDate() - 7);
                    const endLast = new Date(startOfThisWeek);
                    endLast.setDate(startOfThisWeek.getDate() - 1);
                    return {
                        start: startLast,
                        end: endLast,
                        label: `${startLast.toLocaleDateString('en-AU', { day: 'numeric', month: 'short' })} – ${endLast.toLocaleDateString('en-AU', { day: 'numeric', month: 'short' })}`
                    };
                }

                if (periodKey === 'fortnight') {
                    const startFortnight = new Date(startOfThisWeek);
                    startFortnight.setDate(startOfThisWeek.getDate() - 7);
                    return {
                        start: startFortnight,
                        end: endOfThisWeek,
                        label: `${startFortnight.toLocaleDateString('en-AU', { day: 'numeric', month: 'short' })} – ${endOfThisWeek.toLocaleDateString('en-AU', { day: 'numeric', month: 'short' })}`
                    };
                }

                if (periodKey === 'thisMonth') {
                    const startMonth = new Date(today.getFullYear(), today.getMonth(), 1);
                    const endMonth = new Date(today.getFullYear(), today.getMonth() + 1, 0);
                    return {
                        start: startMonth,
                        end: endMonth,
                        label: startMonth.toLocaleDateString('en-AU', { month: 'long', year: 'numeric' })
                    };
                }

                return { start: null, end: null, label: 'All Recorded Shifts' };
            }

            function getFilteredShifts() {
                const bounds = getPeriodBounds(state.period);
                return state.shifts
                    .filter(s => {
                        if (state.filterBDOnly && !(Number(s.bDoubleHours) > 0)) return false;
                        if (bounds.start && bounds.end) {
                            const d = parseLocalDate(s.date);
                            if (d < bounds.start || d > bounds.end) return false;
                        }
                        return true;
                    })
                    .sort((a, b) => {
                        if (a.date !== b.date) return b.date.localeCompare(a.date);
                        return (b.updatedAt || 0) - (a.updatedAt || 0);
                    });
            }

            // --- Cloud Sync Helpers ---
            async function syncRatesToCloud() {
                saveLocalCache();
                if (!db || !currentUser) return;
                try {
                    await setDoc(doc(db, 'artifacts', appId, 'users', currentUser.uid, 'settings', 'rates'), {
                        ...state.rates,
                        updatedAt: Date.now()
                    }, { merge: true });
                } catch (err) {
                    console.warn('Cloud rates sync deferred:', err);
                }
            }

            async function syncShiftToCloud(shift) {
                saveLocalCache();
                if (!db || !currentUser) return;
                try {
                    await setDoc(doc(db, 'artifacts', appId, 'users', currentUser.uid, 'shifts', shift.id), shift, { merge: true });
                } catch (err) {
                    console.warn('Cloud shift sync deferred:', err);
                }
            }

            async function pushAllLocalToCloud() {
                saveLocalCache();
                if (!db || !currentUser) return;
                try {
                    const batch = writeBatch(db);
                    batch.set(doc(db, 'artifacts', appId, 'users', currentUser.uid, 'settings', 'rates'), {
                        ...state.rates,
                        updatedAt: Date.now()
                    }, { merge: true });
                    state.shifts.forEach(s => {
                        batch.set(doc(db, 'artifacts', appId, 'users', currentUser.uid, 'shifts', s.id), s, { merge: true });
                    });
                    await batch.commit();
                } catch (err) {
                    console.warn('Batch sync warning:', err);
                }
            }

            function updateAccountUI() {
                const isFirebaseGoogle = currentUser && !currentUser.isAnonymous;
                const linked = state.linkedProfile;

                if (isFirebaseGoogle || linked) {
                    const name = isFirebaseGoogle ? (currentUser.displayName || 'Google Account') : (linked.name || 'Google Account');
                    const email = isFirebaseGoogle ? (currentUser.email || 'Cloud synced') : (linked.email || 'Account linked');

                    if (el.cloudStatusBadge) {
                        el.cloudStatusBadge.textContent = isFirebaseGoogle ? 'Cloud Connected' : 'Account Linked';
                        el.cloudStatusBadge.className = 'text-xs font-bold px-2.5 py-0.5 rounded-full bg-emerald-500/20 text-emerald-300 border border-emerald-500/30';
                    }
                    if (el.accountDisplayName) el.accountDisplayName.textContent = name;
                    if (el.accountUserSub) el.accountUserSub.textContent = email;
                    if (el.btnGoogleSignInText) el.btnGoogleSignInText.textContent = 'Sign Out / Switch Account';
                } else {
                    if (el.cloudStatusBadge) {
                        el.cloudStatusBadge.textContent = currentUser ? 'Auto-Saved' : 'Device Saved';
                        el.cloudStatusBadge.className = 'text-xs font-bold px-2.5 py-0.5 rounded-full bg-amber-500/15 text-amber-300 border border-amber-500/30';
                    }
                    if (el.accountDisplayName) el.accountDisplayName.textContent = 'Local Device Storage';
                    if (el.accountUserSub) el.accountUserSub.textContent = 'Connect Google to link your profile or export a backup file anytime.';
                    if (el.btnGoogleSignInText) el.btnGoogleSignInText.textContent = 'Sign in with Google';
                }
            }

            function attachCloudListeners(user) {
                if (unsubscribeShifts) { unsubscribeShifts(); unsubscribeShifts = null; }
                if (unsubscribeRates) { unsubscribeRates(); unsubscribeRates = null; }
                if (!db || !user) return;

                const ratesRef = doc(db, 'artifacts', appId, 'users', user.uid, 'settings', 'rates');
                unsubscribeRates = onSnapshot(ratesRef, (snap) => {
                    if (snap.exists()) {
                        state.rates = { ...state.rates, ...snap.data() };
                        saveLocalCache();
                        syncRateInputsFromState();
                        renderDashboard();
                    } else {
                        syncRatesToCloud();
                    }
                }, (err) => console.warn('Rates snapshot listener:', err));

                const shiftsCol = collection(db, 'artifacts', appId, 'users', user.uid, 'shifts');
                unsubscribeShifts = onSnapshot(shiftsCol, (snapshot) => {
                    if (snapshot.empty && state.shifts.length > 0) {
                        pushAllLocalToCloud();
                        return;
                    }
                    const cloudMap = new Map();
                    snapshot.forEach(docSnap => {
                        cloudMap.set(docSnap.id, { id: docSnap.id, ...docSnap.data() });
                    });
                    // Merge any local-only shifts
                    let hasLocalOnly = false;
                    state.shifts.forEach(localShift => {
                        if (!cloudMap.has(localShift.id)) {
                            cloudMap.set(localShift.id, localShift);
                            hasLocalOnly = true;
                        }
                    });
                    state.shifts = Array.from(cloudMap.values());
                    saveLocalCache();
                    renderDashboard();
                    if (hasLocalOnly) pushAllLocalToCloud();
                }, (err) => console.warn('Shifts snapshot listener:', err));
            }

            // Initialize Firebase Auth if available
            if (auth) {
                onAuthStateChanged(auth, (user) => {
                    currentUser = user;
                    updateAccountUI();
                    if (user) {
                        attachCloudListeners(user);
                    }
                });

                (async () => {
                    try {
                        if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                            await signInWithCustomToken(auth, __initial_auth_token);
                        } else if (!auth.currentUser) {
                            await signInAnonymously(auth);
                        }
                    } catch (err) {
                        console.warn('Auth init fallback to local storage:', err);
                        updateAccountUI();
                    }
                })();
            } else {
                updateAccountUI();
            }

            // --- UI Rendering ---
            function syncRateInputsFromState() {
                if (el.rateNormal) el.rateNormal.value = Number(state.rates.normalRate).toFixed(2);
                if (el.rateBDouble) el.rateBDouble.value = Number(state.rates.bDoubleExtra).toFixed(2);
                if (el.rateWeekend) el.rateWeekend.value = Number(state.rates.weekendExtra).toFixed(2);
                if (el.autoWeekendSetting) el.autoWeekendSetting.checked = Boolean(state.rates.autoWeekend);
                if (el.weekStartDaySelect) el.weekStartDaySelect.value = String(state.rates.weekStartDay ?? 1);
                updateEffectiveRatesDisplay();
            }

            function updateEffectiveRatesDisplay() {
                const base = Math.max(0, Number(state.rates.normalRate) || 0);
                const bd = Math.max(0, Number(state.rates.bDoubleExtra) || 0);
                const wk = Math.max(0, Number(state.rates.weekendExtra) || 0);

                if (el.ratesSummarySub) {
                    el.ratesSummarySub.textContent = `Base ${formatAUD(base)} • BD +${formatAUD(bd)} • Wknd +${formatAUD(wk)}`;
                }
                if (el.effWeekdayBase) el.effWeekdayBase.textContent = `${formatAUD(base)}/hr`;
                if (el.effWeekdayBD) el.effWeekdayBD.textContent = `${formatAUD(base + bd)}/hr`;
                if (el.effWeekendBase) el.effWeekendBase.textContent = `${formatAUD(base + wk)}/hr`;
                if (el.effWeekendBD) el.effWeekendBD.textContent = `${formatAUD(base + bd + wk)}/hr`;
            }

            function updateLivePreview() {
                const totalHours = Math.max(0, parseFloat(el.totalHours?.value) || 0);
                const droveBD = Boolean(el.droveBDoubleToggle?.checked);
                const bDoubleHours = droveBD ? Math.max(0, parseFloat(el.bDoubleHours?.value) || 0) : 0;
                const isWeekend = Boolean(el.isWeekendToggle?.checked);

                if (droveBD && bDoubleHours > totalHours && totalHours > 0) {
                    el.bdValidationMsg?.classList.remove('hidden');
                } else {
                    el.bdValidationMsg?.classList.add('hidden');
                }

                const calc = calculateShiftPay({ totalHours, bDoubleHours, isWeekend });
                if (el.previewTotalPay) el.previewTotalPay.textContent = formatAUD(calc.totalPay);

                if (!el.previewBreakdownLines) return;
                if (totalHours <= 0) {
                    el.previewBreakdownLines.innerHTML = '<div>Enter hours worked to preview pay breakdown.</div>';
                    return;
                }

                const lines = [];
                lines.push(`<div class="flex justify-between"><span>Base (${calc.totalHours.toFixed(2)}h × ${formatAUD(calc.baseRate)})</span><span class="text-slate-200 font-semibold">${formatAUD(calc.basePay)}</span></div>`);
                if (calc.bDoubleHours > 0) {
                    lines.push(`<div class="flex justify-between text-amber-400"><span>B-Double Extra (${calc.bDoubleHours.toFixed(2)}h × +${formatAUD(calc.bdExtraRate)})</span><span class="font-semibold">+${formatAUD(calc.bdAllowancePay)}</span></div>`);
                }
                if (calc.isWeekend) {
                    lines.push(`<div class="flex justify-between text-purple-400"><span>Weekend Extra (${calc.totalHours.toFixed(2)}h × +${formatAUD(calc.wkndExtraRate)})</span><span class="font-semibold">+${formatAUD(calc.weekendAllowancePay)}</span></div>`);
                }
                el.previewBreakdownLines.innerHTML = lines.join('');
            }

            function renderDashboard() {
                const bounds = getPeriodBounds(state.period);
                if (el.periodRangeText) el.periodRangeText.textContent = bounds.label;

                // Update period button active styles
                document.querySelectorAll('.period-btn').forEach(btn => {
                    const active = btn.getAttribute('data-period') === state.period;
                    if (active) {
                        btn.className = 'period-btn px-3 py-2 rounded-xl text-xs font-bold bg-amber-500 text-slate-950 shadow transition' + (btn.getAttribute('data-period') === 'allTime' ? ' col-span-2 sm:col-span-1' : '');
                    } else {
                        btn.className = 'period-btn px-3 py-2 rounded-xl text-xs font-semibold bg-slate-950 text-slate-300 hover:bg-slate-800 border border-slate-800 transition' + (btn.getAttribute('data-period') === 'allTime' ? ' col-span-2 sm:col-span-1' : '');
                    }
                });

                const filtered = getFilteredShifts();
                let sumPay = 0;
                let sumHours = 0;
                let sumBDHours = 0;
                let sumBDAllowance = 0;
                let sumWeekendHours = 0;
                let sumWeekendAllowance = 0;

                filtered.forEach(s => {
                    const c = calculateShiftPay(s);
                    sumPay += c.totalPay;
                    sumHours += c.totalHours;
                    sumBDHours += c.bDoubleHours;
                    sumBDAllowance += c.bdAllowancePay;
                    if (c.isWeekend) {
                        sumWeekendHours += c.totalHours;
                        sumWeekendAllowance += c.weekendAllowancePay;
                    }
                });

                const avgHourly = sumHours > 0 ? (sumPay / sumHours) : 0;

                if (el.kpiGrossPay) el.kpiGrossPay.textContent = formatAUD(sumPay);
                if (el.kpiAvgHourly) el.kpiAvgHourly.textContent = `Avg ${formatAUD(avgHourly)}/hr`;
                if (el.kpiTotalHours) el.kpiTotalHours.textContent = formatHours(sumHours);
                if (el.kpiShiftCount) el.kpiShiftCount.textContent = `${filtered.length} ${filtered.length === 1 ? 'shift' : 'shifts'} logged`;
                if (el.kpiBDHours) el.kpiBDHours.textContent = formatHours(sumBDHours);
                if (el.kpiBDAllowance) el.kpiBDAllowance.textContent = `+${formatAUD(sumBDAllowance)} BD extra`;
                if (el.kpiWeekendHours) el.kpiWeekendHours.textContent = formatHours(sumWeekendHours);
                if (el.kpiWeekendAllowance) el.kpiWeekendAllowance.textContent = `+${formatAUD(sumWeekendAllowance)} wknd extra`;

                if (el.historySubtitle) {
                    el.historySubtitle.textContent = `${filtered.length} ${filtered.length === 1 ? 'shift' : 'shifts'} in ${bounds.label}`;
                }

                renderShiftList(filtered);
            }

            function renderShiftList(shifts) {
                if (!el.shiftListContainer) return;

                if (shifts.length === 0) {
                    el.shiftListContainer.innerHTML = `
                        <div class="p-8 sm:p-12 text-center space-y-2.5">
                            <div class="w-12 h-12 rounded-2xl bg-slate-800/80 text-slate-400 mx-auto flex items-center justify-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
                            </div>
                            <h3 class="text-sm font-bold text-slate-200">No shifts logged in this period</h3>
                            <p class="text-xs text-slate-400 max-w-xs mx-auto">Use the Log New Shift form to record your driving hours, B-Double time, and weekend shifts.</p>
                        </div>
                    `;
                    return;
                }

                el.shiftListContainer.innerHTML = shifts.map(shift => {
                    const calc = calculateShiftPay(shift);
                    const hasBD = calc.bDoubleHours > 0;
                    return `
                        <div class="p-4 sm:p-5 hover:bg-slate-850/60 transition flex flex-col sm:flex-row sm:items-center justify-between gap-3.5">
                            <div class="space-y-1.5 min-w-0">
                                <div class="flex flex-wrap items-center gap-2">
                                    <span class="text-sm font-bold text-white">${escapeHtml(formatDisplayDate(shift.date))}</span>
                                    ${calc.isWeekend ? `<span class="text-[10px] font-extrabold uppercase px-2 py-0.5 rounded-md bg-purple-500/20 text-purple-300 border border-purple-500/30">Weekend</span>` : ''}
                                    ${hasBD ? `<span class="text-[10px] font-extrabold uppercase px-2 py-0.5 rounded-md bg-amber-500/20 text-amber-300 border border-amber-500/30">B-Double ${calc.bDoubleHours.toFixed(2)}h</span>` : ''}
                                </div>
                                <div class="flex flex-wrap items-center gap-x-3 gap-y-1 text-xs text-slate-400 tabular-nums">
                                    <span class="font-semibold text-slate-200">${calc.totalHours.toFixed(2)} hrs total</span>
                                    ${hasBD ? `<span>• Normal ${calc.normalHours.toFixed(2)}h + BD ${calc.bDoubleHours.toFixed(2)}h</span>` : ''}
                                </div>
                                ${shift.notes ? `<p class="text-xs text-slate-400 truncate">${escapeHtml(shift.notes)}</p>` : ''}
                            </div>

                            <div class="flex items-center justify-between sm:justify-end gap-3 pt-2 sm:pt-0 border-t sm:border-t-0 border-slate-800/80 shrink-0">
                                <div class="text-left sm:text-right tabular-nums">
                                    <div class="text-base sm:text-lg font-extrabold text-emerald-400">${formatAUD(calc.totalPay)}</div>
                                    <div class="text-[11px] text-slate-400">${formatAUD(calc.totalHours > 0 ? calc.totalPay / calc.totalHours : 0)}/hr eff.</div>
                                </div>
                                <div class="flex items-center gap-1.5">
                                    <button type="button" data-action="edit" data-id="${escapeHtml(shift.id)}" class="px-3 py-2 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-200 text-xs font-bold border border-slate-700 transition">
                                        Edit
                                    </button>
                                    <button type="button" data-action="delete" data-id="${escapeHtml(shift.id)}" class="p-2 rounded-xl bg-slate-950 hover:bg-rose-950/70 text-slate-400 hover:text-rose-400 border border-slate-800 transition" title="Delete Shift">
                                        <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="3 6 5 6 21 6"/><path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"/></svg>
                                    </button>
                                </div>
                            </div>
                        </div>
                    `;
                }).join('');
            }

            // --- Form Helpers & Reset ---
            function handleDateChange(isoDateStr) {
                const d = parseLocalDate(isoDateStr);
                if (el.dayOfWeekBadge) {
                    el.dayOfWeekBadge.textContent = d.toLocaleDateString('en-AU', { weekday: 'long' });
                }
                if (state.rates.autoWeekend) {
                    const day = d.getDay();
                    const isWknd = (day === 0 || day === 6);
                    if (el.isWeekendToggle) el.isWeekendToggle.checked = isWknd;
                    if (isWknd) {
                        el.weekendAutoTag?.classList.remove('hidden');
                    } else {
                        el.weekendAutoTag?.classList.add('hidden');
                    }
                }
                updateLivePreview();
            }

            function resetShiftForm() {
                state.editingId = null;
                if (el.editShiftId) el.editShiftId.value = '';
                if (el.formTitle) el.formTitle.textContent = 'Log New Shift';
                if (el.btnSaveShiftText) el.btnSaveShiftText.textContent = 'Save Shift Log';
                el.btnCancelEdit?.classList.add('hidden');

                const todayStr = getTodayISO();
                if (el.shiftDate) el.shiftDate.value = todayStr;
                if (el.startTime) el.startTime.value = '';
                if (el.endTime) el.endTime.value = '';
                if (el.breakMinutes) el.breakMinutes.value = '30';
                if (el.totalHours) el.totalHours.value = '';
                if (el.droveBDoubleToggle) el.droveBDoubleToggle.checked = false;
                el.bDoubleHoursWrapper?.classList.add('hidden');
                if (el.bDoubleHours) el.bDoubleHours.value = '';
                if (el.bDoubleBox) {
                    el.bDoubleBox.className = 'rounded-xl bg-slate-950/90 border border-slate-800 p-3.5 space-y-3 transition-colors';
                }
                el.bdValidationMsg?.classList.add('hidden');
                if (el.shiftNotes) el.shiftNotes.value = '';

                handleDateChange(todayStr);
            }

            // --- Event Listeners ---
            // Date & Weekend toggle
            el.shiftDate?.addEventListener('change', (e) => handleDateChange(e.target.value));
            el.isWeekendToggle?.addEventListener('change', (e) => {
                if (e.target.checked) {
                    el.weekendAutoTag?.classList.remove('hidden');
                } else {
                    el.weekendAutoTag?.classList.add('hidden');
                }
                updateLivePreview();
            });

            // Quick Start/Finish Time Calculator
            document.querySelectorAll('.time-calc-input').forEach(inp => {
                inp.addEventListener('input', () => {
                    const sVal = el.startTime?.value;
                    const eVal = el.endTime?.value;
                    if (!sVal || !eVal) return;

                    const [sh, sm] = sVal.split(':').map(Number);
                    const [eh, em] = eVal.split(':').map(Number);
                    let startMins = sh * 60 + sm;
                    let endMins = eh * 60 + em;
                    if (endMins <= startMins) endMins += 24 * 60; // Overnight shift support

                    const breakMins = Math.max(0, parseFloat(el.breakMinutes?.value) || 0);
                    const netHours = Math.max(0, (endMins - startMins - breakMins) / 60);
                    if (el.totalHours) el.totalHours.value = netHours.toFixed(2);
                    if (el.droveBDoubleToggle?.checked && el.bDoubleHours && !el.bDoubleHours.value) {
                        el.bDoubleHours.value = netHours.toFixed(2);
                    }
                    updateLivePreview();
                });
            });

            // Total Hours & B-Double Toggle
            el.totalHours?.addEventListener('input', updateLivePreview);

            el.droveBDoubleToggle?.addEventListener('change', (e) => {
                const checked = e.target.checked;
                if (checked) {
                    el.bDoubleHoursWrapper?.classList.remove('hidden');
                    if (el.bDoubleBox) {
                        el.bDoubleBox.className = 'rounded-xl bg-slate-950/90 border border-amber-500/50 p-3.5 space-y-3 transition-colors';
                    }
                    if (el.bDoubleHours && !el.bDoubleHours.value && el.totalHours?.value) {
                        el.bDoubleHours.value = el.totalHours.value;
                    }
                } else {
                    el.bDoubleHoursWrapper?.classList.add('hidden');
                    if (el.bDoubleHours) el.bDoubleHours.value = '';
                    if (el.bDoubleBox) {
                        el.bDoubleBox.className = 'rounded-xl bg-slate-950/90 border border-slate-800 p-3.5 space-y-3 transition-colors';
                    }
                }
                updateLivePreview();
            });

            el.btnAllHoursBD?.addEventListener('click', () => {
                if (el.totalHours && el.bDoubleHours) {
                    el.bDoubleHours.value = el.totalHours.value || '0';
                    updateLivePreview();
                }
            });

            el.bDoubleHours?.addEventListener('input', updateLivePreview);
            el.btnCancelEdit?.addEventListener('click', resetShiftForm);

            // Shift Form Submit (Save New or Update Existing)
            el.shiftForm?.addEventListener('submit', async (e) => {
                e.preventDefault();
                const date = el.shiftDate?.value || getTodayISO();
                const totalHours = parseFloat(el.totalHours?.value);
                if (!totalHours || totalHours <= 0) {
                    showToast('Please enter valid hours worked');
                    return;
                }

                const droveBD = Boolean(el.droveBDoubleToggle?.checked);
                const rawBD = droveBD ? (parseFloat(el.bDoubleHours?.value) || 0) : 0;
                if (rawBD > totalHours) {
                    el.bdValidationMsg?.classList.remove('hidden');
                    showToast('B-Double hours cannot exceed total hours');
                    return;
                }

                const isEditing = Boolean(state.editingId);
                const shiftId = state.editingId || `shift_${Date.now()}_${Math.random().toString(36).slice(2, 7)}`;
                const shiftObj = {
                    id: shiftId,
                    date,
                    totalHours: Number(totalHours.toFixed(2)),
                    bDoubleHours: Number(rawBD.toFixed(2)),
                    isWeekend: Boolean(el.isWeekendToggle?.checked),
                    notes: (el.shiftNotes?.value || '').trim(),
                    updatedAt: Date.now()
                };

                if (isEditing) {
                    const idx = state.shifts.findIndex(s => s.id === shiftId);
                    if (idx !== -1) state.shifts[idx] = shiftObj;
                    else state.shifts.unshift(shiftObj);
                } else {
                    state.shifts.unshift(shiftObj);
                }

                await syncShiftToCloud(shiftObj);
                resetShiftForm();
                renderDashboard();
                showToast(isEditing ? 'Shift updated!' : 'Shift saved!');
            });

            // Pay Rates Auto-Save Listeners
            [el.rateNormal, el.rateBDouble, el.rateWeekend].forEach(input => {
                input?.addEventListener('input', () => {
                    state.rates.normalRate = Math.max(0, parseFloat(el.rateNormal?.value) || 0);
                    state.rates.bDoubleExtra = Math.max(0, parseFloat(el.rateBDouble?.value) || 0);
                    state.rates.weekendExtra = Math.max(0, parseFloat(el.rateWeekend?.value) || 0);
                    updateEffectiveRatesDisplay();
                    updateLivePreview();
                    renderDashboard();
                    syncRatesToCloud();
                });
            });

            el.autoWeekendSetting?.addEventListener('change', (e) => {
                state.rates.autoWeekend = e.target.checked;
                syncRatesToCloud();
                if (el.shiftDate?.value) handleDateChange(el.shiftDate.value);
                showToast('Weekend detection updated');
            });

            // Period Filter & B-Double Only Filter
            document.querySelectorAll('.period-btn').forEach(btn => {
                btn.addEventListener('click', () => {
                    state.period = btn.getAttribute('data-period') || 'thisWeek';
                    renderDashboard();
                });
            });

            el.filterBDOnly?.addEventListener('change', (e) => {
                state.filterBDOnly = e.target.checked;
                renderDashboard();
            });

            // Shift History Edit & Delete Delegation
            el.shiftListContainer?.addEventListener('click', (e) => {
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
                            deleteDoc(doc(db, 'artifacts', appId, 'users', currentUser.uid, 'shifts', id)).catch(() => {});
                        }
                        renderDashboard();
                        showToast('Shift deleted');
                    }
                } else if (action === 'edit') {
                    const shift = state.shifts.find(s => s.id === id);
                    if (shift) {
                        state.editingId = shift.id;
                        if (el.editShiftId) el.editShiftId.value = shift.id;
                        if (el.formTitle) el.formTitle.textContent = 'Edit Shift Log';
                        if (el.btnSaveShiftText) el.btnSaveShiftText.textContent = 'Update Shift Log';
                        el.btnCancelEdit?.classList.remove('hidden');

                        if (el.shiftDate) el.shiftDate.value = shift.date;
                        const d = parseLocalDate(shift.date);
                        if (el.dayOfWeekBadge) el.dayOfWeekBadge.textContent = d.toLocaleDateString('en-AU', { weekday: 'long' });

                        if (el.totalHours) el.totalHours.value = shift.totalHours;
                        const hasBD = Number(shift.bDoubleHours || 0) > 0;
                        if (el.droveBDoubleToggle) el.droveBDoubleToggle.checked = hasBD;
                        if (hasBD) {
                            el.bDoubleHoursWrapper?.classList.remove('hidden');
                            if (el.bDoubleHours) el.bDoubleHours.value = shift.bDoubleHours;
                            if (el.bDoubleBox) {
                                el.bDoubleBox.className = 'rounded-xl bg-slate-950/90 border border-amber-500/50 p-3.5 space-y-3 transition-colors';
                            }
                        } else {
                            el.bDoubleHoursWrapper?.classList.add('hidden');
                            if (el.bDoubleHours) el.bDoubleHours.value = '';
                            if (el.bDoubleBox) {
                                el.bDoubleBox.className = 'rounded-xl bg-slate-950/90 border border-slate-800 p-3.5 space-y-3 transition-colors';
                            }
                        }

                        if (el.isWeekendToggle) el.isWeekendToggle.checked = Boolean(shift.isWeekend);
                        if (shift.isWeekend) {
                            el.weekendAutoTag?.classList.remove('hidden');
                        } else {
                            el.weekendAutoTag?.classList.add('hidden');
                        }
                        if (el.shiftNotes) el.shiftNotes.value = shift.notes || '';
                        updateLivePreview();
                        window.scrollTo({ top: 0, behavior: 'smooth' });
                    }
                }
            });

            // --- Settings Modal & Account Actions ---
            el.btnOpenAccountSettings?.addEventListener('click', () => {
                updateAccountUI();
                el.accountModal?.classList.remove('hidden');
                el.accountModal?.classList.add('flex');
            });

            el.btnCloseAccountModal?.addEventListener('click', () => {
                el.accountModal?.classList.add('hidden');
                el.accountModal?.classList.remove('flex');
                el.inlineGoogleForm?.classList.add('hidden');
            });

            el.accountModal?.addEventListener('click', (e) => {
                if (e.target === el.accountModal) {
                    el.accountModal.classList.add('hidden');
                    el.accountModal.classList.remove('flex');
                    el.inlineGoogleForm?.classList.add('hidden');
                }
            });

            // Pay Week Start Day Selector
            el.weekStartDaySelect?.addEventListener('change', (e) => {
                state.rates.weekStartDay = Number(e.target.value);
                syncRatesToCloud();
                renderDashboard();
                showToast('Pay week start day updated');
            });

            // Google Sign-In / Link Profile
            el.btnGoogleSignIn?.addEventListener('click', async () => {
                const isFirebaseGoogle = currentUser && !currentUser.isAnonymous;
                if (isFirebaseGoogle || state.linkedProfile) {
                    state.linkedProfile = null;
                    saveLocalCache();
                    if (auth && isFirebaseGoogle) {
                        try {
                            await signOut(auth);
                            await signInAnonymously(auth);
                        } catch (e) {
                            console.warn('Sign out fallback:', e);
                        }
                    }
                    updateAccountUI();
                    showToast('Signed out of Google account');
                    return;
                }

                // Try Firebase Google Popup first; fallback smoothly to inline Google profile link in embedded frames
                if (auth) {
                    try {
                        const provider = new GoogleAuthProvider();
                        if (auth.currentUser && auth.currentUser.isAnonymous) {
                            await linkWithPopup(auth.currentUser, provider);
                        } else {
                            await signInWithPopup(auth, provider);
                        }
                        await pushAllLocalToCloud();
                        updateAccountUI();
                        showToast('Connected with Google!');
                        return;
                    } catch (err) {
                        console.info('Opening inline Google account link form:', err?.code || err);
                    }
                }

                el.inlineGoogleForm?.classList.remove('hidden');
                el.inlineGoogleName?.focus();
            });

            el.btnCancelInlineGoogle?.addEventListener('click', () => {
                el.inlineGoogleForm?.classList.add('hidden');
            });

            el.btnConfirmInlineGoogle?.addEventListener('click', async () => {
                const name = (el.inlineGoogleName?.value || '').trim() || 'Driver Account';
                const email = (el.inlineGoogleEmail?.value || '').trim();
                if (!email || !email.includes('@')) {
                    showToast('Please enter a valid Google email');
                    return;
                }
                state.linkedProfile = { name, email, linkedAt: Date.now() };
                await pushAllLocalToCloud();
                el.inlineGoogleForm?.classList.add('hidden');
                updateAccountUI();
                showToast(`Linked ${email} & backed up shifts!`);
            });

            // Manual Backup Now
            el.btnSyncNow?.addEventListener('click', async () => {
                await pushAllLocalToCloud();
                showToast('All shifts & pay rates backed up!');
            });

            // Export CSV
            el.btnExportCsv?.addEventListener('click', () => {
                if (state.shifts.length === 0) {
                    showToast('No shifts logged yet to export');
                    return;
                }
                const headers = ['Date', 'Day', 'Total Hours', 'Normal Hours', 'B-Double Hours', 'Weekend', 'Base Pay', 'BD Extra', 'Weekend Extra', 'Total Gross Pay', 'Notes'];
                const sorted = [...state.shifts].sort((a, b) => b.date.localeCompare(a.date));
                const rows = sorted.map(s => {
                    const c = calculateShiftPay(s);
                    const dayName = parseLocalDate(s.date).toLocaleDateString('en-AU', { weekday: 'short' });
                    return [
                        s.date,
                        dayName,
                        c.totalHours.toFixed(2),
                        c.normalHours.toFixed(2),
                        c.bDoubleHours.toFixed(2),
                        c.isWeekend ? 'Yes' : 'No',
                        c.basePay.toFixed(2),
                        c.bdAllowancePay.toFixed(2),
                        c.weekendAllowancePay.toFixed(2),
                        c.totalPay.toFixed(2),
                        `"${String(s.notes || '').replace(/"/g, '""')}"`
                    ].join(',');
                });

                const csvContent = [headers.join(','), ...rows].join('\n');
                const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
                const url = URL.createObjectURL(blob);
                const a = document.createElement('a');
                a.href = url;
                a.download = `RigPay_Shifts_${getTodayISO()}.csv`;
                document.body.appendChild(a);
                a.click();
                document.body.removeChild(a);
                URL.revokeObjectURL(url);
                showToast('CSV exported!');
            });

            // Export Portable JSON Backup File
            el.btnExportBackupJson?.addEventListener('click', () => {
                const payload = {
                    app: 'RigPay',
                    exportedAt: new Date().toISOString(),
                    rates: state.rates,
                    shifts: state.shifts
                };
                const blob = new Blob([JSON.stringify(payload, null, 2)], { type: 'application/json' });
                const url = URL.createObjectURL(blob);
                const a = document.createElement('a');
                a.href = url;
                a.download = `RigPay_Backup_${getTodayISO()}.json`;
                document.body.appendChild(a);
                a.click();
                document.body.removeChild(a);
                URL.revokeObjectURL(url);
                showToast('Backup file saved!');
            });

            // Restore from JSON Backup File
            el.inputRestoreBackupJson?.addEventListener('change', (e) => {
                const file = e.target.files?.[0];
                if (!file) return;
                const reader = new FileReader();
                reader.onload = async (evt) => {
                    try {
                        const parsed = JSON.parse(String(evt.target?.result || '{}'));
                        if (parsed.rates && typeof parsed.rates === 'object') {
                            state.rates = { ...state.rates, ...parsed.rates };
                        }
                        if (Array.isArray(parsed.shifts)) {
                            const map = new Map(state.shifts.map(s => [s.id, s]));
                            parsed.shifts.forEach(s => {
                                if (s && s.id && s.date) map.set(s.id, s);
                            });
                            state.shifts = Array.from(map.values());
                        }
                        await pushAllLocalToCloud();
                        syncRateInputsFromState();
                        renderDashboard();
                        showToast(`Restored ${state.shifts.length} shifts from backup!`);
                    } catch (err) {
                        showToast('Invalid backup JSON file');
                    } finally {
                        e.target.value = '';
                    }
                };
                reader.readAsText(file);
            });

            // Reset All Data Modal
            el.btnOpenReset?.addEventListener('click', () => {
                el.accountModal?.classList.add('hidden');
                el.accountModal?.classList.remove('flex');
                el.resetModal?.classList.remove('hidden');
                el.resetModal?.classList.add('flex');
            });

            el.btnCancelReset?.addEventListener('click', () => {
                el.resetModal?.classList.add('hidden');
                el.resetModal?.classList.remove('flex');
            });

            el.btnConfirmReset?.addEventListener('click', async () => {
                const oldShifts = [...state.shifts];
                state.shifts = [];
                saveLocalCache();
                if (db && currentUser && oldShifts.length > 0) {
                    try {
                        const batch = writeBatch(db);
                        oldShifts.forEach(s => {
                            batch.delete(doc(db, 'artifacts', appId, 'users', currentUser.uid, 'shifts', s.id));
                        });
                        await batch.commit();
                    } catch (e) {
                        console.warn('Cloud delete batch warning:', e);
                    }
                }
                el.resetModal?.classList.add('hidden');
                el.resetModal?.classList.remove('flex');
                resetShiftForm();
                renderDashboard();
                showToast('All shift data cleared');
            });

            // --- Boot Application ---
            syncRateInputsFromState();
            resetShiftForm();
            renderDashboard();
        })();
    </script>
</body>
</html>
