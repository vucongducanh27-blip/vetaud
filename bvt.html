<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tàu Nhanh - Hệ Thống Đặt Vé Tàu Thông Minh & Định Vị Trực Tuyến</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        rail: {
                            50: '#f0f9ff',
                            100: '#e0f2fe',
                            500: '#0284c7',
                            600: '#0284c7',
                            700: '#0369a1',
                            800: '#075985',
                            900: '#0c4a6e',
                        }
                    }
                }
            }
        }
    </script>
    <!-- FontAwesome 6 -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- SweetAlert2 -->
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    <!-- QRCode JS -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
    <!-- Leaflet Map CSS & JS for Real GPS & Train Tracking -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap');
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background-color: #f8fafc;
        }
        /* Custom scrollbars */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f5f9;
        }
        ::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
        .carriage-active {
            border-color: #0284c7 !important;
            background-color: #f0f9ff !important;
            box-shadow: 0 4px 12px rgba(2, 132, 199, 0.15);
        }
        .train-moving-pulse {
            animation: pulse-ring 2s infinite;
        }
        @keyframes pulse-ring {
            0% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(2, 132, 199, 0.7); }
            70% { transform: scale(1); box-shadow: 0 0 0 10px rgba(2, 132, 199, 0); }
            100% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(2, 132, 199, 0); }
        }
        /* Leaflet custom map markers */
        .station-marker {
            background-color: #0284c7;
            border: 2px solid #ffffff;
            border-radius: 50%;
            color: #ffffff;
            text-align: center;
            font-size: 10px;
            font-weight: bold;
            box-shadow: 0 2px 6px rgba(0,0,0,0.3);
        }
        .train-marker {
            background-color: #e11d48;
            border: 2px solid #ffffff;
            border-radius: 50%;
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 14px;
            box-shadow: 0 0 12px rgba(225, 29, 72, 0.8);
            animation: pulse-ring 1.5s infinite;
        }
        .user-gps-marker {
            background-color: #10b981;
            border: 3px solid #ffffff;
            border-radius: 50%;
            box-shadow: 0 0 12px rgba(16, 185, 129, 0.8);
        }
    </style>
</head>
<body class="text-slate-800 antialiased min-h-screen flex flex-col justify-between">

    <!-- TOP HEADER / NAVBAR -->
    <header class="sticky top-0 z-40 bg-white/95 backdrop-blur border-b border-slate-200 shadow-sm">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between">
            <!-- Logo -->
            <div class="flex items-center space-x-3 cursor-pointer" onclick="switchTab('search-tab')">
                <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-sky-600 to-blue-800 flex items-center justify-center text-white shadow-md shadow-sky-200">
                    <i class="fa-solid fa-train-subway text-xl"></i>
                </div>
                <div>
                    <span class="text-xl font-extrabold bg-gradient-to-r from-sky-700 to-blue-900 bg-clip-text text-transparent">Tàu Nhanh</span>
                    <span class="hidden sm:inline-block text-xs text-sky-600 font-semibold bg-sky-50 px-2 py-0.5 rounded-full ml-1 border border-sky-100">Smart AI Train</span>
                </div>
            </div>

            <!-- User GPS Fast Status Badge -->
            <div id="header-gps-status" onclick="openGpsModal()" class="hidden md:flex items-center space-x-2 px-3 py-1.5 rounded-full bg-emerald-50 border border-emerald-200 text-xs font-semibold text-emerald-800 cursor-pointer hover:bg-emerald-100 transition">
                <span class="w-2 h-2 rounded-full bg-emerald-500 animate-ping"></span>
                <i class="fa-solid fa-location-crosshairs text-emerald-600"></i>
                <span id="header-gps-text">Ga gần nhất: Đang định vị...</span>
            </div>

            <!-- Navigation Links -->
            <nav class="hidden lg:flex items-center space-x-1">
                <button onclick="switchTab('search-tab')" id="nav-search" class="px-3.5 py-2 rounded-lg text-sm font-semibold text-sky-700 bg-sky-50 transition">
                    <i class="fa-solid fa-compass mr-1.5"></i> Tìm chuyến & Đề xuất
                </button>
                <button onclick="switchTab('tracker-tab')" id="nav-tracker" class="px-3.5 py-2 rounded-lg text-sm font-semibold text-slate-600 hover:text-sky-700 hover:bg-slate-50 transition">
                    <i class="fa-solid fa-satellite-dish mr-1.5 animate-pulse text-sky-600"></i> Định vị tàu & Bến
                </button>
                <button onclick="switchTab('smart-notify-tab')" id="nav-notify" class="relative px-3.5 py-2 rounded-lg text-sm font-semibold text-slate-600 hover:text-sky-700 hover:bg-slate-50 transition">
                    <i class="fa-solid fa-bell mr-1.5 text-amber-500"></i> Gợi ý chuyến quen
                    <span class="absolute top-1.5 right-1 w-2 h-2 rounded-full bg-rose-500 animate-ping"></span>
                </button>
                <button onclick="switchTab('tickets-tab')" id="nav-tickets" class="px-3.5 py-2 rounded-lg text-sm font-semibold text-slate-600 hover:text-sky-700 hover:bg-slate-50 transition">
                    <i class="fa-solid fa-ticket mr-1.5"></i> Vé của tôi
                    <span id="badge-ticket-count" class="hidden ml-1 px-1.5 py-0.5 text-xs bg-sky-600 text-white rounded-full">0</span>
                </button>
                <button onclick="switchTab('history-tab')" id="nav-history" class="px-3.5 py-2 rounded-lg text-sm font-semibold text-slate-600 hover:text-sky-700 hover:bg-slate-50 transition">
                    <i class="fa-solid fa-clock-rotate-left mr-1.5"></i> Lịch sử
                </button>
            </nav>

            <!-- Database Management Button & User Profile / Auth Button -->
            <div class="flex items-center space-x-2 sm:space-x-3">
                <button onclick="openDatabaseManagerModal()" title="Xem cơ sở dữ liệu tài khoản" class="flex items-center space-x-1.5 px-3 py-1.5 rounded-lg border border-slate-200 text-xs font-bold text-slate-700 bg-white hover:text-sky-700 hover:border-sky-300 hover:bg-sky-50 shadow-sm transition">
                    <i class="fa-solid fa-database text-sky-600"></i>
                    <span class="hidden sm:inline">Database</span>
                    <span id="badge-db-count" class="px-1.5 py-0.2 text-[10px] bg-sky-100 text-sky-800 rounded-full font-extrabold">3</span>
                </button>
                <div id="auth-status-container">
                    <button onclick="openAuthModal('login')" class="px-4 py-2 rounded-lg text-sm font-semibold text-white bg-sky-600 hover:bg-sky-700 shadow-sm transition">
                        <i class="fa-solid fa-user-lock mr-1"></i> Đăng nhập / Đăng ký
                    </button>
                </div>
            </div>
        </div>
    </header>

    <!-- MAIN CONTENT AREA -->
    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6 flex-grow w-full">

        <!-- SMART AI NOTIFICATION & HISTORY PREDICTION BANNER (ĐỀ XUẤT DỰA TRÊN CHUYẾN ĐI TRƯỚC) -->
        <div id="smart-prediction-banner" class="mb-6 bg-gradient-to-r from-sky-900 via-indigo-900 to-blue-900 rounded-2xl p-5 text-white shadow-xl relative overflow-hidden border border-sky-700/50">
            <div class="absolute -right-8 -bottom-8 opacity-10 text-9xl">
                <i class="fa-solid fa-route"></i>
            </div>
            <div class="relative z-10 flex flex-col md:flex-row md:items-center justify-between gap-4">
                <div class="space-y-1.5">
                    <div class="flex items-center space-x-2">
                        <span class="px-2.5 py-0.5 bg-amber-400 text-slate-950 text-[11px] font-extrabold rounded-full uppercase tracking-wider flex items-center">
                            <i class="fa-solid fa-wand-magic-sparkles mr-1"></i> Trí tuệ AI đề xuất
                        </span>
                        <span class="text-xs text-sky-200">Dựa trên 3 chuyến đi gần nhất của bạn</span>
                    </div>
                    <h3 class="text-lg md:text-xl font-bold flex items-center">
                        <span id="banner-recommendation-title">Gợi ý chuyến quen thuộc: Hà Nội ➔ Đà Nẵng</span>
                    </h3>
                    <p id="banner-recommendation-desc" class="text-xs md:text-sm text-sky-100 max-w-2xl leading-relaxed">
                        Bạn thường đi tuyến này vào cuối tuần. Định vị phát hiện bạn đang cách <strong class="text-amber-300">Ga Hà Nội (1.8 km)</strong>. Chuyến tàu <strong class="text-white">SE1 (19:30)</strong> đang có giá vé tiết kiệm nhất chỉ từ <strong class="text-emerald-300">850.000 VNĐ</strong>!
                    </p>
                </div>
                <div class="flex items-center space-x-3">
                    <button onclick="applySmartRecommendation()" class="whitespace-nowrap px-5 py-2.5 bg-gradient-to-r from-amber-400 to-amber-300 hover:from-amber-300 hover:to-amber-200 text-slate-950 font-bold rounded-xl text-xs md:text-sm shadow-md transition transform hover:-translate-y-0.5 flex items-center">
                        <i class="fa-solid fa-bolt mr-1.5"></i> Đặt Ngay Tuyến Này
                    </button>
                    <button onclick="switchTab('smart-notify-tab')" class="whitespace-nowrap px-3.5 py-2.5 bg-white/10 hover:bg-white/20 text-white font-semibold rounded-xl text-xs border border-white/20 transition">
                        Chi tiết <i class="fa-solid fa-chevron-right ml-1"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- TAB 1: TÌM CHUYẾN & BỘ LỌC ĐỀ XUẤT TUYẾN TỐT / GIÁ PHÙ HỢP -->
        <section id="search-tab" class="tab-content space-y-6">

            <!-- GEOLOCATION & NEAREST STATIONS DISCOVERY CARD -->
            <div class="bg-gradient-to-r from-sky-50 via-blue-50 to-indigo-50 border border-sky-200 rounded-2xl p-5 shadow-sm space-y-4">
                <div class="flex flex-col md:flex-row md:items-center justify-between gap-3">
                    <div class="flex items-center space-x-3">
                        <div class="w-10 h-10 rounded-xl bg-sky-600 text-white flex items-center justify-center text-lg shadow-sm">
                            <i class="fa-solid fa-location-crosshairs"></i>
                        </div>
                        <div>
                            <h4 class="text-sm font-bold text-slate-900 flex items-center">
                                Định Vị Khách Hàng & Đề Xuất Nhà Ga Gần Nhất
                                <span class="ml-2 px-2 py-0.5 text-[10px] bg-emerald-100 text-emerald-800 rounded-full font-bold">GPS Tự Động</span>
                            </h4>
                            <p class="text-xs text-slate-600 mt-0.5" id="user-location-summary">
                                Xác định vị trí của bạn để tính khoảng cách tới các ga xe lửa gần bạn nhất.
                            </p>
                        </div>
                    </div>
                    <!-- Actions -->
                    <div class="flex items-center space-x-2">
                        <button onclick="detectUserLocation()" id="btn-detect-gps" class="px-4 py-2 bg-sky-600 hover:bg-sky-700 text-white font-bold rounded-xl text-xs shadow-sm transition flex items-center">
                            <i class="fa-solid fa-crosshairs mr-1.5"></i> <span id="btn-gps-text">Định vị GPS thực tế</span>
                        </button>
                        <select id="simulated-location-select" onchange="simulateUserLocation(this.value)" class="px-3 py-2 bg-white border border-slate-300 rounded-xl text-xs font-semibold text-slate-700 outline-none">
                            <option value="">-- Hoặc chọn vị trí mô phỏng --</option>
                            <option value="HN_HOANKIEM">Hà Nội (Quận Hoàn Kiếm)</option>
                            <option value="HN_GIAPBAT">Hà Nội (Khu vực Giáp Bát / Hoàng Mai)</option>
                            <option value="DANANG_HAICHAU">Đà Nẵng (Quận Hải Châu)</option>
                            <option value="HCM_Q1">TP. Hồ Chí Minh (Quận 1 / Q.3)</option>
                            <option value="NHATRANG_CENTRAL">Nha Trang (Trung tâm ven biển)</option>
                            <option value="VINH_CENTRAL">Nghệ An (TP. Vinh)</option>
                        </select>
                    </div>
                </div>

                <!-- 3 Nearest Stations Cards Grid -->
                <div id="nearest-stations-container" class="grid grid-cols-1 md:grid-cols-3 gap-3 pt-1">
                    <!-- Dynamic rendering of top 3 nearest stations -->
                </div>
            </div>

            <!-- MAIN SEARCH FORM CARD -->
            <div class="bg-white rounded-2xl p-6 shadow-md border border-slate-100">
                <form id="search-form" onsubmit="handleSearch(event)" class="space-y-4">
                    <div class="grid grid-cols-1 md:grid-cols-4 gap-4">
                        <!-- Ga Đi (Station From) -->
                        <div class="relative">
                            <div class="flex items-center justify-between mb-1">
                                <label class="text-xs font-bold text-slate-500 uppercase tracking-wider">Ga đi (Khởi hành)</label>
                                <span id="from-station-distance-tag" class="text-[10px] font-bold text-sky-600 bg-sky-50 px-1.5 py-0.5 rounded">Cách bạn: 1.8km</span>
                            </div>
                            <div class="relative">
                                <i class="fa-solid fa-location-dot absolute left-3 top-3.5 text-sky-600"></i>
                                <select id="search-from" class="w-full pl-9 pr-4 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-sm font-bold text-slate-800 focus:ring-2 focus:ring-sky-500 focus:bg-white outline-none">
                                    <option value="Hà Nội">Ga Hà Nội (HNO)</option>
                                    <option value="Giáp Bát">Ga Giáp Bát (GBA)</option>
                                    <option value="Phủ Lý">Ga Phủ Lý (PLY)</option>
                                    <option value="Nam Định">Ga Nam Định (NDI)</option>
                                    <option value="Thanh Hóa">Ga Thanh Hóa (THA)</option>
                                    <option value="Vinh">Ga Vinh (VII)</option>
                                    <option value="Đồng Hới">Ga Đồng Hới (DHO)</option>
                                    <option value="Huế">Ga Huế (HUE)</option>
                                    <option value="Đà Nẵng">Ga Đà Nẵng (DAN)</option>
                                    <option value="Nha Trang">Ga Nha Trang (NTR)</option>
                                    <option value="Sài Gòn">Ga Sài Gòn (SGO)</option>
                                </select>
                            </div>
                        </div>

                        <!-- Ga Đến (Station To) -->
                        <div class="relative">
                            <div class="flex items-center justify-between mb-1">
                                <label class="text-xs font-bold text-slate-500 uppercase tracking-wider">Ga đến</label>
                                <button type="button" onclick="swapStations()" class="text-[10px] font-semibold text-slate-400 hover:text-sky-600">
                                    <i class="fa-solid fa-arrow-right-arrow-left"></i> Đổi chiều
                                </button>
                            </div>
                            <div class="relative">
                                <i class="fa-solid fa-flag-checkered absolute left-3 top-3.5 text-amber-500"></i>
                                <select id="search-to" class="w-full pl-9 pr-4 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-sm font-bold text-slate-800 focus:ring-2 focus:ring-sky-500 focus:bg-white outline-none">
                                    <option value="Đà Nẵng">Ga Đà Nẵng (DAN)</option>
                                    <option value="Sài Gòn">Ga Sài Gòn (SGO)</option>
                                    <option value="Nha Trang">Ga Nha Trang (NTR)</option>
                                    <option value="Huế">Ga Huế (HUE)</option>
                                    <option value="Vinh">Ga Vinh (VII)</option>
                                    <option value="Thanh Hóa">Ga Thanh Hóa (THA)</option>
                                    <option value="Nam Định">Ga Nam Định (NDI)</option>
                                    <option value="Phủ Lý">Ga Phủ Lý (PLY)</option>
                                    <option value="Hà Nội">Ga Hà Nội (HNO)</option>
                                </select>
                            </div>
                        </div>

                        <!-- Ngày Đi (Date) -->
                        <div>
                            <label class="block text-xs font-bold text-slate-500 uppercase tracking-wider mb-1">Ngày đi</label>
                            <div class="relative">
                                <i class="fa-solid fa-calendar-days absolute left-3 top-3.5 text-slate-400"></i>
                                <input type="date" id="search-date" class="w-full pl-9 pr-4 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-sm font-semibold text-slate-800 focus:ring-2 focus:ring-sky-500 focus:bg-white outline-none">
                            </div>
                        </div>

                        <!-- Tiêu Chí Đề Xuất Ưu Tiên (Smart Route & Price Preference) -->
                        <div>
                            <label class="block text-xs font-bold text-slate-500 uppercase tracking-wider mb-1">Ưu tiên đề xuất</label>
                            <div class="relative">
                                <i class="fa-solid fa-sliders absolute left-3 top-3.5 text-sky-600"></i>
                                <select id="search-preference" onchange="filterAndRenderTrains()" class="w-full pl-9 pr-4 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-sm font-semibold focus:ring-2 focus:ring-sky-500 focus:bg-white outline-none">
                                    <option value="ALL">✨ Tất cả các chuyến</option>
                                    <option value="BEST">🌟 Tuyến tốt nhất (Cân bằng & Đúng giờ)</option>
                                    <option value="FASTEST">⚡ Tuyến nhanh nhất (Tiết kiệm thời gian)</option>
                                    <option value="VALUE">💰 Giá phù hợp nhất (Tiết kiệm chi phí)</option>
                                    <option value="VIP">👑 Giường nằm VIP Khoang 4</option>
                                </select>
                            </div>
                        </div>
                    </div>

                    <!-- Filter Bar Extras (Khung giờ + Hạng chỗ) -->
                    <div class="flex flex-wrap items-center justify-between gap-4 pt-3 border-t border-slate-100">
                        <div class="flex flex-wrap items-center gap-3 text-xs">
                            <span class="text-slate-500 font-bold">Khung giờ:</span>
                            <label class="inline-flex items-center space-x-1 cursor-pointer">
                                <input type="checkbox" id="time-filter-morning" checked onchange="filterAndRenderTrains()" class="rounded text-sky-600">
                                <span class="text-slate-700">Sáng (06:00 - 12:00)</span>
                            </label>
                            <label class="inline-flex items-center space-x-1 cursor-pointer">
                                <input type="checkbox" id="time-filter-afternoon" checked onchange="filterAndRenderTrains()" class="rounded text-sky-600">
                                <span class="text-slate-700">Chiều (12:00 - 18:00)</span>
                            </label>
                            <label class="inline-flex items-center space-x-1 cursor-pointer">
                                <input type="checkbox" id="time-filter-night" checked onchange="filterAndRenderTrains()" class="rounded text-sky-600">
                                <span class="text-slate-700">Tối/Đêm (18:00 - 24:00)</span>
                            </label>
                        </div>
                        <button type="submit" class="px-8 py-3 bg-gradient-to-r from-sky-600 to-blue-700 hover:from-sky-700 hover:to-blue-800 text-white font-extrabold rounded-xl shadow-md shadow-sky-200 hover:shadow-lg transition flex items-center space-x-2">
                            <i class="fa-solid fa-magnifying-glass"></i>
                            <span>Tìm Tuyến & Đề Xuất Giá</span>
                        </button>
                    </div>
                </form>
            </div>

            <!-- SMART PRICE COMPARISON BAR (LỊCH GIÁ VÉ THÔNG MINH CÁC NGÀY LÂN CẬN) -->
            <div class="bg-white rounded-xl p-4 border border-slate-100 shadow-sm overflow-x-auto space-y-2">
                <div class="text-xs font-bold text-slate-500 uppercase flex items-center justify-between">
                    <span class="flex items-center">
                        <i class="fa-solid fa-chart-line text-emerald-500 mr-1.5"></i>
                        Đề xuất ngày có giá vé tốt nhất (So sánh ±3 ngày lân cận)
                    </span>
                    <span class="text-[11px] text-emerald-700 font-semibold bg-emerald-50 px-2 py-0.5 rounded-full">
                        <i class="fa-solid fa-tag mr-1"></i> Giá đã bao gồm thuế & bảo hiểm
                    </span>
                </div>
                <div id="flexible-dates-bar" class="flex space-x-2 min-w-max pt-1">
                    <!-- Dynamic Rendered nearby dates with prices -->
                </div>
            </div>

            <!-- SEARCH RESULTS SECTION -->
            <div id="search-results-container" class="space-y-6">
                <div class="flex items-center justify-between">
                    <div>
                        <h3 class="text-lg font-bold text-slate-800 flex items-center">
                            <i class="fa-solid fa-train-tram text-sky-600 mr-2"></i>
                            Danh Sách Tuyến Tàu Phù Hợp
                        </h3>
                        <p class="text-xs text-slate-500" id="search-route-summary">Hành trình từ Ga Hà Nội đến Ga Đà Nẵng</p>
                    </div>
                    <span id="results-count" class="text-xs font-semibold px-3 py-1 bg-sky-100 text-sky-800 rounded-full">4 chuyến khả dụng</span>
                </div>

                <!-- TOP 3 SMART HIGHLIGHT RECOMMENDATION CARDS (TỐT NHẤT - NHANH NHẤT - GIÁ RẺ NHẤT) -->
                <div>
                    <h4 class="text-xs font-bold uppercase tracking-wider text-slate-400 mb-3 flex items-center">
                        <i class="fa-solid fa-award text-amber-500 mr-1.5"></i> 3 Lựa chọn tiêu biểu được AI đề xuất cho bạn
                    </h4>
                    <div id="smart-recommendations-grid" class="grid grid-cols-1 md:grid-cols-3 gap-4">
                        <!-- Dynamic rendering for: Best Overall, Fastest, Best Value -->
                    </div>
                </div>

                <!-- ALL TRAIN LISTINGS -->
                <div class="space-y-4">
                    <h4 class="text-xs font-bold uppercase tracking-wider text-slate-400 flex items-center">
                        <i class="fa-solid fa-list text-sky-600 mr-1.5"></i> Toàn bộ danh sách các đoàn tàu
                    </h4>
                    <div id="train-list" class="space-y-4">
                        <!-- Trains will be injected here -->
                    </div>
                </div>
            </div>
        </section>

        <!-- TAB 2: ĐỊNH VỊ TÀU & TRẠNG THÁI QUA BẾN HAY GẦN TỚI (LIVE TRACKING & STATION STATUS) -->
        <section id="tracker-tab" class="tab-content hidden space-y-6">
            <div class="bg-white rounded-2xl p-6 shadow-md border border-slate-100 space-y-6">
                <!-- Header with Train Selector & Station Query -->
                <div class="flex flex-col lg:flex-row lg:items-center justify-between gap-4 border-b border-slate-100 pb-5">
                    <div>
                        <div class="flex items-center space-x-2">
                            <span class="w-3 h-3 rounded-full bg-rose-500 animate-ping"></span>
                            <h2 class="text-2xl font-bold text-slate-900 flex items-center">
                                Định Vị Tàu Trực Tuyến & Kiểm Tra Bến Ga
                            </h2>
                        </div>
                        <p class="text-xs text-slate-500 mt-1">
                            Xem tọa độ GPS thời gian thực, biết chính xác <strong class="text-sky-700">tàu đã qua bến hay chưa</strong>, hoặc <strong class="text-amber-600">còn bao lâu nữa sẽ tới bến của bạn</strong>.
                        </p>
                    </div>

                    <!-- Tracker Form Controls -->
                    <div class="flex flex-wrap items-center gap-3">
                        <div>
                            <label class="block text-[10px] font-bold text-slate-400 uppercase">Chọn Chuyến Tàu</label>
                            <select id="tracker-train-select" onchange="updateLiveTracker()" class="px-3 py-2 bg-slate-50 border border-slate-200 rounded-xl text-xs font-bold text-sky-700 outline-none">
                                <option value="SE1">Tàu Hỏa Tốc SE1 (Hà Nội ➔ Sài Gòn)</option>
                                <option value="SE3">Tàu Tiêu Chuẩn SE3 (Hà Nội ➔ Sài Gòn)</option>
                                <option value="SE7">Tàu Tiết Kiệm SE7 (Hà Nội ➔ Sài Gòn)</option>
                                <option value="SE2">Tàu SE2 (Sài Gòn ➔ Hà Nội)</option>
                            </select>
                        </div>
                        <div>
                            <label class="block text-[10px] font-bold text-slate-400 uppercase">Kiểm tra với Ga Của Tôi</label>
                            <select id="tracker-my-station" onchange="checkMyStationArrival()" class="px-3 py-2 bg-slate-50 border border-slate-200 rounded-xl text-xs font-bold text-slate-700 outline-none">
                                <option value="Nam Định">Ga Nam Định</option>
                                <option value="Thanh Hóa">Ga Thanh Hóa</option>
                                <option value="Vinh">Ga Vinh</option>
                                <option value="Đồng Hới">Ga Đồng Hới</option>
                                <option value="Huế">Ga Huế</option>
                                <option value="Đà Nẵng">Ga Đà Nẵng</option>
                                <option value="Nha Trang">Ga Nha Trang</option>
                                <option value="Sài Gòn">Ga Sài Gòn</option>
                            </select>
                        </div>
                        <button onclick="updateLiveTracker()" class="mt-4 px-4 py-2 bg-sky-600 text-white rounded-xl text-xs font-bold shadow hover:bg-sky-700 transition flex items-center">
                            <i class="fa-solid fa-arrows-rotate mr-1"></i> Làm mới GPS
                        </button>
                    </div>
                </div>

                <!-- TARGET STATION ARRIVAL ALERT BOX (HỘP BÁO TÀU ĐÃ QUA HAY GẦN TỚI BẾN CỦA BẠN) -->
                <div id="station-arrival-status-box" class="bg-gradient-to-r from-amber-50 to-orange-50 border-2 border-amber-300 rounded-2xl p-5 shadow-sm space-y-2">
                    <!-- Dynamic injected arrival alert -->
                </div>

                <!-- LIVE METRIC CARDS -->
                <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                    <div class="bg-sky-50 border border-sky-100 p-4 rounded-xl space-y-1">
                        <span class="text-xs font-bold text-sky-600 block"><i class="fa-solid fa-location-crosshairs mr-1"></i> Vị trí tàu hiện tại</span>
                        <span id="tracker-current-location" class="text-sm font-extrabold text-sky-900 block truncate">Km 110 (Giữa Nam Định & Ninh Bình)</span>
                    </div>
                    <div class="bg-amber-50 border border-amber-100 p-4 rounded-xl space-y-1">
                        <span class="text-xs font-bold text-amber-600 block"><i class="fa-solid fa-stopwatch mr-1"></i> Ga kế tiếp</span>
                        <span id="tracker-next-station" class="text-sm font-extrabold text-amber-900 block">Ga Thanh Hóa (Đang tới)</span>
                    </div>
                    <div class="bg-emerald-50 border border-emerald-100 p-4 rounded-xl space-y-1">
                        <span class="text-xs font-bold text-emerald-600 block"><i class="fa-solid fa-gauge-high mr-1"></i> Tốc độ GPS</span>
                        <span id="tracker-speed" class="text-sm font-extrabold text-emerald-900 block">78.5 km/h</span>
                    </div>
                    <div class="bg-purple-50 border border-purple-100 p-4 rounded-xl space-y-1">
                        <span class="text-xs font-bold text-purple-600 block"><i class="fa-solid fa-clock mr-1"></i> Trạng thái đúng giờ</span>
                        <span id="tracker-ontime-status" class="text-sm font-extrabold text-emerald-600 block">Đúng giờ 100%</span>
                    </div>
                </div>

                <!-- INTERACTIVE LEAFLET RAILWAY MAP -->
                <div class="space-y-2">
                    <div class="flex items-center justify-between text-xs font-bold text-slate-600">
                        <span class="flex items-center"><i class="fa-solid fa-map-location-dot text-sky-600 mr-1.5"></i> Bản đồ đường sắt Bắc - Nam thời gian thực</span>
                        <div class="flex items-center space-x-3 text-[11px]">
                            <span class="flex items-center"><span class="w-3 h-3 rounded-full bg-emerald-500 inline-block mr-1"></span> Ga đã qua</span>
                            <span class="flex items-center"><span class="w-3 h-3 rounded-full bg-amber-500 inline-block mr-1"></span> Ga đang tới</span>
                            <span class="flex items-center"><span class="w-3 h-3 rounded-full bg-rose-600 inline-block mr-1"></span> Đoàn tàu</span>
                            <span class="flex items-center"><span class="w-3 h-3 rounded-full bg-emerald-700 inline-block mr-1"></span> Vị trí của bạn</span>
                        </div>
                    </div>
                    <div id="railway-map-container" class="w-full h-[480px] rounded-2xl border-2 border-slate-200 overflow-hidden shadow-md z-10"></div>
                </div>

                <!-- PROGRESS TIMELINE BAR -->
                <div class="bg-slate-50 p-6 rounded-2xl border border-slate-200 space-y-4">
                    <div class="flex items-center justify-between text-xs font-bold text-slate-500">
                        <span>Ga Khởi Hành: <strong class="text-slate-900">Hà Nội (Km 0)</strong></span>
                        <span id="tracker-progress-percentage" class="text-sky-600 font-extrabold">Tiến độ: 35%</span>
                        <span>Ga Cuối: <strong class="text-slate-900">Sài Gòn (Km 1,726)</strong></span>
                    </div>
                    
                    <!-- Visual Progress Bar -->
                    <div class="w-full bg-slate-200 h-3 rounded-full relative overflow-visible">
                        <div id="tracker-progress-bar-fill" class="bg-gradient-to-r from-sky-500 to-emerald-500 h-full rounded-full transition-all duration-1000" style="width: 35%;"></div>
                        <div id="tracker-train-icon-marker" class="absolute top-1/2 -translate-y-1/2 -translate-x-1/2 text-white bg-rose-600 px-2 py-0.5 rounded-full shadow-md text-xs font-bold transition-all duration-1000" style="left: 35%;">
                            <i class="fa-solid fa-train"></i> SE1
                        </div>
                    </div>
                </div>

                <!-- STATIONS ROUTE CHECKPOINTS TABLE (CHI TIẾT TỪNG GA: ĐÃ QUA HAY CHƯA TỚI) -->
                <div class="space-y-3">
                    <h4 class="text-sm font-bold text-slate-800 flex items-center justify-between">
                        <span><i class="fa-solid fa-list-check text-sky-600 mr-1.5"></i> Danh sách các nhà ga trên hành trình & Trạng thái qua bến</span>
                        <span class="text-xs text-slate-400 font-normal">Cập nhật tự động mỗi 30 giây</span>
                    </h4>
                    <div id="tracker-stations-timeline" class="space-y-2">
                        <!-- Injected dynamically with "Đã qua bến", "Đang ghé ga", "Sắp tới" -->
                    </div>
                </div>
            </div>
        </section>

        <!-- TAB 3: THÔNG BÁO GỢI Ý CHUYẾN QUEN & PHÂN TÍCH CHUYẾN ĐI CŨ -->
        <section id="smart-notify-tab" class="tab-content hidden space-y-6">
            <div class="bg-white rounded-2xl p-6 shadow-md border border-slate-100 space-y-6">
                <div>
                    <h2 class="text-2xl font-bold text-slate-900 flex items-center">
                        <i class="fa-solid fa-bell text-amber-500 mr-2"></i> Trung Tâm Gợi Ý Chuyến Đi Dựa Vào Lịch Sử
                    </h2>
                    <p class="text-xs text-slate-500">
                        Hệ thống thông minh ghi nhận thói quen di chuyển từ các chuyến đi trước để tự động đề xuất lộ trình, giờ chạy và ga tàu gần bạn nhất.
                    </p>
                </div>

                <!-- History Insights Metric Cards -->
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                    <div class="bg-sky-50 border border-sky-100 p-4 rounded-xl space-y-1">
                        <span class="text-xs font-semibold text-sky-600 block">Tuyến bạn đi thường xuyên nhất</span>
                        <span class="text-lg font-extrabold text-sky-900">Hà Nội ➔ Đà Nẵng</span>
                        <span class="text-[10px] text-slate-500 block">Đã thực hiện 3 chuyến trong 60 ngày qua</span>
                    </div>
                    <div class="bg-emerald-50 border border-emerald-100 p-4 rounded-xl space-y-1">
                        <span class="text-xs font-semibold text-emerald-600 block">Hạng ghế / giường ưu thích</span>
                        <span class="text-lg font-extrabold text-emerald-900">Giường Khoang 4 VIP</span>
                        <span class="text-[10px] text-slate-500 block">Thường chọn giường Tầng 1 êm ái</span>
                    </div>
                    <div class="bg-purple-50 border border-purple-100 p-4 rounded-xl space-y-1">
                        <span class="text-xs font-semibold text-purple-600 block">Ga quen thuộc gần bạn</span>
                        <span class="text-lg font-extrabold text-purple-900">Ga Hà Nội (1.8 km)</span>
                        <span class="text-[10px] text-slate-500 block">Điểm xuất phát trong 100% chuyến đi</span>
                    </div>
                </div>

                <!-- Notification Feed List -->
                <div class="space-y-4">
                    <h4 class="text-sm font-bold text-slate-800">Các thông báo & Gợi ý lộ trình dành riêng cho bạn:</h4>
                    
                    <!-- Notification Card 1 -->
                    <div class="p-4 rounded-2xl bg-amber-50/70 border border-amber-200 flex flex-col md:flex-row md:items-center justify-between gap-4">
                        <div class="flex items-start space-x-3">
                            <div class="w-10 h-10 rounded-xl bg-amber-400 text-slate-900 flex items-center justify-center font-bold text-lg flex-shrink-0">
                                <i class="fa-solid fa-calendar-check"></i>
                            </div>
                            <div class="space-y-1">
                                <div class="flex items-center space-x-2">
                                    <span class="px-2 py-0.5 bg-amber-200 text-slate-900 font-extrabold text-[10px] rounded-full uppercase">Đề xuất cuối tuần</span>
                                    <span class="text-xs text-slate-400">Cách đây 1 giờ</span>
                                </div>
                                <h5 class="text-sm font-bold text-slate-900">Bạn có kế hoạch đi Đà Nẵng vào thứ Sáu tuần này không?</h5>
                                <p class="text-xs text-slate-600">
                                    Dựa trên thói quen đi công tác/nghỉ dưỡng hàng tháng, chuyến tàu SE1 lúc 19:30 từ Ga Hà Nội (gần bạn 1.8km) đang còn 12 chỗ giường nằm khoang 4 đẹp nhất. Giá ưu đãi giảm 10% cho khách hàng thân thiết.
                                </p>
                            </div>
                        </div>
                        <button onclick="applySmartRecommendation()" class="whitespace-nowrap px-4 py-2 bg-amber-500 hover:bg-amber-400 text-slate-950 font-bold rounded-xl text-xs shadow transition">
                            <i class="fa-solid fa-bolt mr-1"></i> Đặt Chuyến Này
                        </button>
                    </div>

                    <!-- Notification Card 2 -->
                    <div class="p-4 rounded-2xl bg-sky-50/70 border border-sky-200 flex flex-col md:flex-row md:items-center justify-between gap-4">
                        <div class="flex items-start space-x-3">
                            <div class="w-10 h-10 rounded-xl bg-sky-600 text-white flex items-center justify-center font-bold text-lg flex-shrink-0">
                                <i class="fa-solid fa-map-pin"></i>
                            </div>
                            <div class="space-y-1">
                                <div class="flex items-center space-x-2">
                                    <span class="px-2 py-0.5 bg-sky-200 text-sky-800 font-extrabold text-[10px] rounded-full uppercase">Vị trí ga gần nhất</span>
                                    <span class="text-xs text-slate-400">Đang bật</span>
                                </div>
                                <h5 class="text-sm font-bold text-slate-900">Gợi ý ga xuất phát tối ưu: Ga Hà Nội (Lê Duẩn)</h5>
                                <p class="text-xs text-slate-600">
                                    GPS ghi nhận bạn đang ở khu vực lân cận. Khởi hành từ Ga Hà Nội giúp bạn tiết kiệm 25 phút di chuyển so với các ga ngoại thành. Có tuyến tàu nhanh SE1, SE3, SE7 xuất phát mỗi ngày.
                                </p>
                            </div>
                        </div>
                        <button onclick="switchTab('search-tab')" class="whitespace-nowrap px-4 py-2 bg-sky-600 hover:bg-sky-700 text-white font-bold rounded-xl text-xs shadow transition">
                            Xem Lịch Trình
                        </button>
                    </div>

                    <!-- Notification Card 3 -->
                    <div class="p-4 rounded-2xl bg-emerald-50/70 border border-emerald-200 flex flex-col md:flex-row md:items-center justify-between gap-4">
                        <div class="flex items-start space-x-3">
                            <div class="w-10 h-10 rounded-xl bg-emerald-600 text-white flex items-center justify-center font-bold text-lg flex-shrink-0">
                                <i class="fa-solid fa-tags"></i>
                            </div>
                            <div class="space-y-1">
                                <div class="flex items-center space-x-2">
                                    <span class="px-2 py-0.5 bg-emerald-200 text-emerald-800 font-extrabold text-[10px] rounded-full uppercase">Ưu đãi chuyến khứ hồi</span>
                                    <span class="text-xs text-slate-400">Mới</span>
                                </div>
                                <h5 class="text-sm font-bold text-slate-900">Giảm 15% vé khứ hồi Đà Nẵng ➔ Hà Nội cho chuyến đi trước</h5>
                                <p class="text-xs text-slate-600">
                                    Áp dụng tự động khi đặt vé khứ hồi cho hành khách đã có lịch sử đặt vé tại Tàu Nhanh.
                                </p>
                            </div>
                        </div>
                        <button onclick="switchTab('search-tab')" class="whitespace-nowrap px-4 py-2 bg-emerald-600 hover:bg-emerald-500 text-white font-bold rounded-xl text-xs shadow transition">
                            Áp Dụng Mã
                        </button>
                    </div>
                </div>
            </div>
        </section>

        <!-- SEAT & BERTH SELECTION VIEW (MÔ HÌNH TOA TÀU & VỊ TRÍ GHẾ / GIƯỜNG) -->
        <section id="seat-selection-view" class="hidden space-y-6">
            <!-- Train Journey Header Info -->
            <div class="flex flex-col md:flex-row md:items-center justify-between bg-white p-5 rounded-2xl border border-slate-100 shadow-sm gap-4">
                <div>
                    <button onclick="backToSearchResults()" class="text-xs font-bold text-sky-600 hover:text-sky-800 flex items-center mb-1">
                        <i class="fa-solid fa-arrow-left mr-1.5"></i> Quay lại danh sách chuyến tàu
                    </button>
                    <h2 class="text-2xl font-black text-slate-900 flex items-center">
                        <span id="seat-view-train-code" class="px-2.5 py-1 bg-sky-600 text-white rounded-xl text-base mr-3 font-mono">SE1</span>
                        <span id="seat-view-route">Hà Nội ➔ Đà Nẵng</span>
                    </h2>
                    <p id="seat-view-time" class="text-xs text-slate-500 mt-1">
                        Khởi hành: 19:30, Ngày: 20/10/2026 • Thời gian chạy: 15 giờ 45 phút
                    </p>
                </div>
                <div class="text-right flex items-center md:flex-col justify-between md:justify-center">
                    <span class="text-xs text-slate-400 block">Thời gian giữ chỗ còn lại:</span>
                    <span id="hold-timer" class="text-2xl font-mono font-black text-amber-600">09:59</span>
                </div>
            </div>

            <!-- VISUAL TRAIN EXTERIOR OVERVIEW (MÔ HÌNH ĐOÀN TÀU HOẢ TOÀN CẢNH) -->
            <div class="bg-white p-5 rounded-2xl border border-slate-100 shadow-sm space-y-3">
                <div class="flex items-center justify-between text-xs font-bold text-slate-500">
                    <span><i class="fa-solid fa-train text-sky-600 mr-1.5"></i> Mô hình đoàn tàu (Nhấp vào toa để chuyển đổi vị trí chọn chỗ)</span>
                    <span class="text-sky-600">Hướng tàu chạy: ➔ ➔</span>
                </div>

                <!-- Train Exterior Carousel -->
                <div class="flex items-center space-x-3 overflow-x-auto pb-2 pt-1" id="visual-train-exterior">
                    <!-- Locomotive (Đầu tàu) -->
                    <div class="flex-shrink-0 w-28 bg-gradient-to-r from-red-600 to-rose-700 text-white rounded-l-2xl rounded-r-lg p-3 text-center shadow-md flex flex-col justify-center items-center">
                        <i class="fa-solid fa-train text-2xl mb-1"></i>
                        <span class="text-[10px] font-black uppercase tracking-wider">Đầu Máy D19E</span>
                        <span class="text-[9px] text-rose-200">Động cơ diesel</span>
                    </div>

                    <!-- Carriages List Injected dynamically -->
                    <div id="carriage-overview-strip" class="flex space-x-3"></div>
                </div>
            </div>

            <!-- CARRIAGE TAB SELECTOR DETAILS -->
            <div class="bg-white p-4 rounded-xl border border-slate-100 shadow-sm">
                <h4 class="text-xs font-bold text-slate-400 uppercase mb-3">Chọn Loại Toa Tàu & Hạng Chỗ:</h4>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-3" id="carriage-selector-list">
                    <!-- Carriage buttons injected dynamically -->
                </div>
            </div>

            <!-- SEAT MAP CANVAS & LEGEND -->
            <div class="bg-white p-6 rounded-2xl border border-slate-100 shadow-md space-y-4">
                
                <!-- Legend & Seat Filter Controls -->
                <div class="flex flex-wrap items-center justify-between gap-4 pb-4 border-b border-slate-100 text-xs font-medium">
                    <div class="flex flex-wrap items-center gap-4">
                        <div class="flex items-center space-x-2">
                            <span class="w-5 h-5 rounded-lg bg-emerald-50 border-2 border-emerald-400 inline-block shadow-sm"></span>
                            <span class="text-slate-700">Chỗ trống</span>
                        </div>
                        <div class="flex items-center space-x-2">
                            <span class="w-5 h-5 rounded-lg bg-amber-400 border-2 border-amber-500 shadow-sm inline-block"></span>
                            <span class="text-slate-900 font-bold">Đang chọn</span>
                        </div>
                        <div class="flex items-center space-x-2">
                            <span class="w-5 h-5 rounded-lg bg-rose-100 border-2 border-rose-300 text-rose-500 flex items-center justify-center text-xs"><i class="fa-solid fa-lock"></i></span>
                            <span class="text-slate-400">Đã bán</span>
                        </div>
                        <div class="flex items-center space-x-2">
                            <span class="w-5 h-5 rounded-lg bg-purple-100 border-2 border-purple-400 text-purple-700 flex items-center justify-center text-xs"><i class="fa-solid fa-heart"></i></span>
                            <span class="text-slate-700">Ưu tiên người già/trẻ em</span>
                        </div>
                    </div>

                    <!-- Quick filters for seats -->
                    <div class="flex items-center space-x-2">
                        <span class="text-xs text-slate-400">Lọc nhanh:</span>
                        <button type="button" onclick="filterSeatsHighlight('window')" class="px-2.5 py-1 bg-slate-100 hover:bg-sky-50 text-slate-700 text-xs rounded-lg border border-slate-200">
                            🪟 Cạnh cửa sổ
                        </button>
                        <button type="button" onclick="filterSeatsHighlight('tier1')" class="px-2.5 py-1 bg-slate-100 hover:bg-sky-50 text-slate-700 text-xs rounded-lg border border-slate-200">
                            🛏️ Giường Tầng 1
                        </button>
                        <button type="button" onclick="filterSeatsHighlight('clear')" class="px-2 py-1 text-slate-400 hover:text-slate-600 text-xs">
                            Xóa lọc
                        </button>
                    </div>
                </div>

                <!-- REALTIME SYNC BADGE -->
                <div class="flex flex-wrap items-center justify-between py-1 text-xs text-slate-500">
                    <span class="flex items-center text-emerald-600 font-semibold">
                        <span class="w-2 h-2 rounded-full bg-emerald-500 animate-ping mr-2"></span>
                        Đang đồng bộ trạng thái chỗ theo thời gian thực (Realtime Seat Sync)
                    </span>
                    <span id="carriage-capacity-text" class="font-bold text-slate-700">Toa 1 - Ngồi Mềm Điều Hòa (Giá: 450.000đ)</span>
                </div>

                <!-- SEAT LAYOUT CONTAINER (MÔ HÌNH NỘI THẤT TOA TÀU THỰC TẾ) -->
                <div id="seat-map-grid" class="py-4 overflow-x-auto">
                    <!-- Dynamic seats layout injected here with toilets, water dispenser, direction arrow -->
                </div>
            </div>

            <!-- BOOKING SUMMARY BAR & PROCEED BUTTON -->
            <div class="bg-slate-900 text-white p-6 rounded-2xl shadow-xl flex flex-col md:flex-row items-center justify-between gap-4">
                <div class="space-y-1 text-center md:text-left">
                    <div class="text-xs text-slate-400">
                        Vị trí ghế/giường đã chọn: 
                        <span id="selected-seats-list" class="text-amber-300 font-bold ml-1">Chưa chọn chỗ nào</span>
                    </div>
                    <div class="text-2xl font-extrabold text-white flex items-center justify-center md:justify-start">
                        <span>Tổng tiền:</span>
                        <span id="selected-total-price" class="text-emerald-400 ml-2 font-mono">0 VNĐ</span>
                    </div>
                </div>
                <div class="flex items-center space-x-3 w-full md:w-auto">
                    <button onclick="backToSearchResults()" class="w-1/2 md:w-auto px-5 py-3.5 bg-slate-800 hover:bg-slate-700 text-white font-bold rounded-xl text-xs transition">
                        Chọn lại chuyến
                    </button>
                    <button onclick="goToCheckout()" id="btn-proceed-checkout" disabled class="w-1/2 md:w-auto px-8 py-3.5 bg-gradient-to-r from-emerald-500 to-teal-500 hover:from-emerald-400 hover:to-teal-400 text-slate-950 font-black rounded-xl shadow-lg transition disabled:opacity-40 disabled:cursor-not-allowed">
                        Tiến Hành Đặt Vé <i class="fa-solid fa-arrow-right ml-1.5"></i>
                    </button>
                </div>
            </div>
        </section>

        <!-- TAB 4: CHECKOUT & PAYMENT (THANH TOÁN & VIETQR) -->
        <section id="checkout-tab" class="tab-content hidden space-y-6">
            <div class="bg-white rounded-2xl p-6 shadow-md border border-slate-100">
                <button onclick="backToSeatSelection()" class="text-xs font-bold text-sky-600 hover:text-sky-800 flex items-center mb-4">
                    <i class="fa-solid fa-arrow-left mr-1"></i> Quay lại sơ đồ ghế
                </button>
                
                <h2 class="text-2xl font-bold text-slate-900 mb-6 flex items-center">
                    <i class="fa-solid fa-id-card text-sky-600 mr-2"></i> Thông Tin Hành Khách & Thanh Toán Vé Tàu
                </h2>

                <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                    
                    <!-- LEFT COLUMN: PASSENGER FORM -->
                    <div class="lg:col-span-2 space-y-6">
                        <!-- Auto-fill Alert if logged in -->
                        <div id="autofill-notice" class="bg-sky-50 border border-sky-200 rounded-xl p-3 text-xs text-sky-800 flex items-center justify-between">
                            <span><i class="fa-solid fa-circle-info text-sky-600 mr-1.5"></i> Đã tự động điền thông tin từ tài khoản <strong>RailExpress</strong> của bạn.</span>
                        </div>

                        <!-- Passenger Info Form -->
                        <div id="passengers-form-container" class="space-y-4">
                            <!-- Injected per seat -->
                        </div>

                        <!-- Contact Info -->
                        <div class="bg-slate-50 p-4 rounded-xl border border-slate-200 space-y-3">
                            <h4 class="text-sm font-bold text-slate-700">Thông tin liên hệ nhận vé điện tử & Mã QR</h4>
                            <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
                                <div>
                                    <label class="block text-xs text-slate-500 mb-1">Email nhận vé</label>
                                    <input type="email" id="contact-email" class="w-full px-3 py-2 border rounded-lg text-sm bg-white focus:ring-2 focus:ring-sky-500 outline-none" placeholder="email@example.com">
                                </div>
                                <div>
                                    <label class="block text-xs text-slate-500 mb-1">Số điện thoại (Nhận SMS/Zalo ZNS)</label>
                                    <input type="tel" id="contact-phone" class="w-full px-3 py-2 border rounded-lg text-sm bg-white focus:ring-2 focus:ring-sky-500 outline-none" placeholder="0901234567">
                                </div>
                            </div>
                        </div>

                        <!-- Payment Method Selection -->
                        <div class="space-y-3">
                            <h4 class="text-sm font-bold text-slate-700">Chọn phương thức thanh toán</h4>
                            <div class="grid grid-cols-2 md:grid-cols-3 gap-3">
                                <label class="payment-card border-2 border-sky-500 bg-sky-50/50 p-3.5 rounded-xl cursor-pointer flex flex-col items-center justify-center text-center space-y-1">
                                    <input type="radio" name="payment" value="VIETQR" checked class="hidden" onchange="updatePaymentView()">
                                    <i class="fa-solid fa-qrcode text-2xl text-sky-600"></i>
                                    <span class="text-xs font-bold text-slate-800">VietQR Quét Mã</span>
                                    <span class="text-[10px] text-emerald-600 font-semibold">Tự động duyệt 24/7</span>
                                </label>
                                <label class="payment-card border border-slate-200 p-3.5 rounded-xl cursor-pointer flex flex-col items-center justify-center text-center space-y-1">
                                    <input type="radio" name="payment" value="MOMO" class="hidden" onchange="updatePaymentView()">
                                    <i class="fa-solid fa-wallet text-2xl text-pink-600"></i>
                                    <span class="text-xs font-bold text-slate-800">Ví MoMo</span>
                                </label>
                                <label class="payment-card border border-slate-200 p-3.5 rounded-xl cursor-pointer flex flex-col items-center justify-center text-center space-y-1">
                                    <input type="radio" name="payment" value="VNPAY" class="hidden" onchange="updatePaymentView()">
                                    <i class="fa-solid fa-credit-card text-2xl text-blue-600"></i>
                                    <span class="text-xs font-bold text-slate-800">VNPay / ATM Nội Địa</span>
                                </label>
                            </div>
                        </div>

                    </div>

                    <!-- RIGHT COLUMN: SUMMARY & DYNAMIC VIETQR DISPLAY -->
                    <div class="space-y-6">
                        <div class="bg-slate-50 rounded-2xl p-5 border border-slate-200 space-y-4">
                            <h3 class="text-base font-bold text-slate-900 border-b border-slate-200 pb-3">Tóm tắt đơn đặt vé</h3>
                            
                            <div id="checkout-summary-details" class="space-y-2 text-xs">
                                <!-- Details injected by JS -->
                            </div>

                            <div class="border-t border-slate-200 pt-3 flex justify-between items-center text-sm">
                                <span class="font-bold text-slate-700">Tổng thanh toán:</span>
                                <span id="checkout-final-price" class="text-xl font-extrabold text-sky-700">0 VNĐ</span>
                            </div>

                            <!-- DYNAMIC VIETQR BOX -->
                            <div id="vietqr-container" class="bg-white p-4 rounded-xl border border-sky-100 shadow-sm text-center space-y-3">
                                <span class="text-xs font-bold text-sky-700 uppercase block">Mã VietQR Thanh Toán Tự Động</span>
                                <div id="qrcode-canvas" class="flex justify-center my-2"></div>
                                <div class="text-left text-xs bg-slate-50 p-2.5 rounded-lg space-y-1 font-mono">
                                    <div>Ngân hàng: <strong class="text-slate-800">MB Bank (Quân Đội)</strong></div>
                                    <div>Số TK: <strong class="text-slate-800">999988889999</strong></div>
                                    <div>Chủ TK: <strong class="text-slate-800">TÀU NHANH CO</strong></div>
                                    <div>Nội dung: <strong id="qr-memo" class="text-sky-600">RE-88321</strong></div>
                                </div>
                            </div>

                            <button onclick="confirmPaymentAndIssueTicket()" class="w-full py-3.5 bg-gradient-to-r from-emerald-600 to-teal-600 hover:from-emerald-700 hover:to-teal-700 text-white font-extrabold rounded-xl shadow-lg transition">
                                <i class="fa-solid fa-check-circle mr-1"></i> Xác Nhận Thanh Toán & Xuất Vé
                            </button>
                        </div>
                    </div>

                </div>
            </div>
        </section>

        <!-- TAB 5: VÉ CỦA TÔI (MY TICKETS & QR CODE BOARDING PASS) -->
        <section id="tickets-tab" class="tab-content hidden space-y-6">
            <div class="flex items-center justify-between">
                <div>
                    <h2 class="text-2xl font-bold text-slate-900">Vé Điện Tử Của Tôi</h2>
                    <p class="text-xs text-slate-500">Mã QR lên tàu hợp lệ - Quét trực tiếp tại cửa kiểm soát ga</p>
                </div>
            </div>

            <!-- TICKET LIST CONTAINER -->
            <div id="my-tickets-list" class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <!-- Injected dynamically -->
            </div>
        </section>

        <!-- TAB 6: LỊCH SỬ CHUYẾN ĐI (HISTORY & ANALYTICS) -->
        <section id="history-tab" class="tab-content hidden space-y-6">
            <div class="bg-white rounded-2xl p-6 shadow-md border border-slate-100 space-y-6">
                <div>
                    <h2 class="text-2xl font-bold text-slate-900">Lịch Sử Các Chuyến Đi Đã Qua</h2>
                    <p class="text-xs text-slate-500">Dữ liệu được dùng để huấn luyện hệ thống thông báo gợi ý tuyến đường phù hợp</p>
                </div>

                <!-- Stats summary -->
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                    <div class="bg-sky-50 border border-sky-100 p-4 rounded-xl">
                        <span class="text-xs font-semibold text-sky-600 block">Tổng số chuyến đi</span>
                        <span id="stat-total-trips" class="text-2xl font-extrabold text-sky-900">3</span>
                    </div>
                    <div class="bg-emerald-50 border border-emerald-100 p-4 rounded-xl">
                        <span class="text-xs font-semibold text-emerald-600 block">Tuyến quen thuộc</span>
                        <span id="stat-favorite-route" class="text-base font-extrabold text-emerald-900">Hà Nội ➔ Đà Nẵng</span>
                    </div>
                    <div class="bg-purple-50 border border-purple-100 p-4 rounded-xl">
                        <span class="text-xs font-semibold text-purple-600 block">Hạng chỗ ưa chuộng</span>
                        <span id="stat-favorite-seat" class="text-base font-extrabold text-purple-900">Giường Khoang 4 VIP</span>
                    </div>
                </div>

                <!-- History Table -->
                <div class="overflow-x-auto">
                    <table class="w-full text-left border-collapse">
                        <thead>
                            <tr class="border-b border-slate-200 text-xs text-slate-400 uppercase font-bold">
                                <th class="py-3 px-4">Mã Vé</th>
                                <th class="py-3 px-4">Đoàn Tàu</th>
                                <th class="py-3 px-4">Hành Trình</th>
                                <th class="py-3 px-4">Ngày Đi</th>
                                <th class="py-3 px-4">Chỗ Ngồi/Giường</th>
                                <th class="py-3 px-4">Trạng Thái</th>
                            </tr>
                        </thead>
                        <tbody id="history-table-body" class="text-xs text-slate-700 divide-y divide-slate-100">
                            <!-- Injected dynamically -->
                        </tbody>
                    </table>
                </div>
            </div>
        </section>

    </main>

    <!-- AUTHENTICATION & VERIFICATION MODAL -->
    <div id="auth-modal" class="fixed inset-0 bg-slate-900/60 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="bg-white rounded-3xl max-w-lg w-full p-6 sm:p-7 shadow-2xl space-y-5 relative max-h-[92vh] overflow-y-auto">
            <button onclick="closeAuthModal()" class="absolute top-4 right-4 text-slate-400 hover:text-slate-600 w-8 h-8 rounded-full flex items-center justify-center transition">
                <i class="fa-solid fa-xmark text-lg"></i>
            </button>

            <!-- Modal Header -->
            <div class="text-center space-y-1">
                <div class="w-12 h-12 bg-sky-100 text-sky-600 rounded-2xl flex items-center justify-center mx-auto text-xl font-bold mb-2 shadow-inner">
                    <i class="fa-solid fa-shield-halved text-sky-600"></i>
                </div>
                <h3 id="auth-modal-title" class="text-xl font-black text-slate-900">Xác Thực & Đăng Nhập Tàu Nhanh</h3>
                <p id="auth-modal-desc" class="text-xs text-slate-500">Hệ thống bảo mật xác thực tài khoản & lưu trữ Cơ sở dữ liệu</p>
            </div>

            <!-- Tab Switcher (Đăng Nhập / Đăng Ký) -->
            <div id="auth-tab-buttons" class="flex p-1 bg-slate-100 rounded-2xl">
                <button type="button" onclick="setAuthTab('login')" id="tab-btn-login" class="flex-1 py-2 rounded-xl text-xs font-bold bg-white text-sky-700 shadow-sm transition">
                    <i class="fa-solid fa-right-to-bracket mr-1"></i> Đăng Nhập
                </button>
                <button type="button" onclick="setAuthTab('register')" id="tab-btn-register" class="flex-1 py-2 rounded-xl text-xs font-bold text-slate-500 hover:text-slate-800 transition">
                    <i class="fa-solid fa-user-plus mr-1"></i> Đăng Ký Mới
                </button>
            </div>

            <!-- VIEW 1: FORM ĐĂNG NHẬP -->
            <form id="form-login" onsubmit="handleLoginSubmit(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-bold text-slate-700 mb-1">Email hoặc Số điện thoại</label>
                    <div class="relative">
                        <i class="fa-solid fa-envelope absolute left-3.5 top-1/2 -translate-y-1/2 text-slate-400 text-sm"></i>
                        <input type="text" id="login-identifier" required class="w-full pl-10 pr-3 py-2.5 border border-slate-200 rounded-xl text-sm focus:ring-2 focus:ring-sky-500 outline-none" placeholder="nguyenvanan@taunhanh.vn hoặc 0912...">
                    </div>
                </div>

                <div>
                    <div class="flex items-center justify-between mb-1">
                        <label class="text-xs font-bold text-slate-700">Mật khẩu</label>
                        <a href="javascript:void(0)" onclick="forgotPasswordNotice()" class="text-[11px] text-sky-600 hover:underline">Quên mật khẩu?</a>
                    </div>
                    <div class="relative">
                        <i class="fa-solid fa-lock absolute left-3.5 top-1/2 -translate-y-1/2 text-slate-400 text-sm"></i>
                        <input type="password" id="login-password" required class="w-full pl-10 pr-10 py-2.5 border border-slate-200 rounded-xl text-sm focus:ring-2 focus:ring-sky-500 outline-none" placeholder="••••••••">
                        <button type="button" onclick="togglePasswordVisibility('login-password', 'eye-login')" class="absolute right-3.5 top-1/2 -translate-y-1/2 text-slate-400 hover:text-slate-600">
                            <i id="eye-login" class="fa-solid fa-eye text-xs"></i>
                        </button>
                    </div>
                </div>

                <div class="flex items-center justify-between text-xs text-slate-600">
                    <label class="flex items-center space-x-2 cursor-pointer">
                        <input type="checkbox" id="login-remember" checked class="rounded border-slate-300 text-sky-600 focus:ring-sky-500">
                        <span>Ghi nhớ đăng nhập trên thiết bị này</span>
                    </label>
                </div>

                <button type="submit" id="btn-login-submit" class="w-full py-3 bg-gradient-to-r from-sky-600 to-blue-700 hover:from-sky-700 hover:to-blue-800 text-white font-bold rounded-xl text-sm shadow-md transition flex items-center justify-center">
                    <i class="fa-solid fa-shield-check mr-2"></i> Xác Thực & Đăng Nhập
                </button>

                <!-- Quick Test Credentials Box -->
                <div class="bg-sky-50/70 border border-sky-100 rounded-2xl p-3 text-xs space-y-2">
                    <span class="text-[10px] font-bold text-sky-800 uppercase tracking-wider block">
                        <i class="fa-solid fa-bolt text-amber-500 mr-1"></i> Tài khoản có sẵn trong Database để thử nghiệm nhanh:
                    </span>
                    <div class="grid grid-cols-2 gap-2">
                        <button type="button" onclick="quickFillAccount('nguyenvanan@taunhanh.vn', '123456')" class="p-2 rounded-lg bg-white border border-sky-200 hover:border-sky-400 text-left transition shadow-xs">
                            <span class="font-bold text-slate-800 block truncate">Nguyễn Văn An</span>
                            <span class="text-[10px] text-slate-500 block truncate">nguyenvanan@taunhanh.vn</span>
                            <span class="text-[9px] text-emerald-600 font-bold block">MK: 123456 (3 vé cũ)</span>
                        </button>
                        <button type="button" onclick="quickFillAccount('demo@taunhanh.vn', '123456')" class="p-2 rounded-lg bg-white border border-sky-200 hover:border-sky-400 text-left transition shadow-xs">
                            <span class="font-bold text-slate-800 block truncate">Trần Thị Mai</span>
                            <span class="text-[10px] text-slate-500 block truncate">demo@taunhanh.vn</span>
                            <span class="text-[9px] text-emerald-600 font-bold block">MK: 123456</span>
                        </button>
                    </div>
                </div>
            </form>

            <!-- VIEW 2: FORM ĐĂNG KÝ TÀI KHOẢN MỚI -->
            <form id="form-register" onsubmit="handleRegisterSubmit(event)" class="space-y-3.5 hidden">
                <div>
                    <label class="block text-xs font-bold text-slate-700 mb-1">Họ và tên hành khách <span class="text-rose-500">*</span></label>
                    <div class="relative">
                        <i class="fa-solid fa-user absolute left-3.5 top-1/2 -translate-y-1/2 text-slate-400 text-sm"></i>
                        <input type="text" id="reg-name" required class="w-full pl-10 pr-3 py-2 border border-slate-200 rounded-xl text-sm focus:ring-2 focus:ring-sky-500 outline-none" placeholder="Ví dụ: Lê Hoàng Long">
                    </div>
                </div>

                <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-bold text-slate-700 mb-1">Số điện thoại <span class="text-rose-500">*</span></label>
                        <div class="relative">
                            <i class="fa-solid fa-phone absolute left-3.5 top-1/2 -translate-y-1/2 text-slate-400 text-sm"></i>
                            <input type="tel" id="reg-phone" required pattern="[0-9]{10}" class="w-full pl-10 pr-3 py-2 border border-slate-200 rounded-xl text-sm focus:ring-2 focus:ring-sky-500 outline-none" placeholder="09xxxxxxxx">
                        </div>
                    </div>
                    <div>
                        <label class="block text-xs font-bold text-slate-700 mb-1">Email đăng ký <span class="text-rose-500">*</span></label>
                        <div class="relative">
                            <i class="fa-solid fa-envelope absolute left-3.5 top-1/2 -translate-y-1/2 text-slate-400 text-sm"></i>
                            <input type="email" id="reg-email" required class="w-full pl-10 pr-3 py-2 border border-slate-200 rounded-xl text-sm focus:ring-2 focus:ring-sky-500 outline-none" placeholder="long@gmail.com">
                        </div>
                    </div>
                </div>

                <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-bold text-slate-700 mb-1">Mật khẩu (≥ 6 ký tự) <span class="text-rose-500">*</span></label>
                        <div class="relative">
                            <i class="fa-solid fa-lock absolute left-3.5 top-1/2 -translate-y-1/2 text-slate-400 text-sm"></i>
                            <input type="password" id="reg-password" minlength="6" required class="w-full pl-10 pr-3 py-2 border border-slate-200 rounded-xl text-sm focus:ring-2 focus:ring-sky-500 outline-none" placeholder="••••••••">
                        </div>
                    </div>
                    <div>
                        <label class="block text-xs font-bold text-slate-700 mb-1">Xác nhận mật khẩu <span class="text-rose-500">*</span></label>
                        <div class="relative">
                            <i class="fa-solid fa-check-double absolute left-3.5 top-1/2 -translate-y-1/2 text-slate-400 text-sm"></i>
                            <input type="password" id="reg-password-confirm" minlength="6" required class="w-full pl-10 pr-3 py-2 border border-slate-200 rounded-xl text-sm focus:ring-2 focus:ring-sky-500 outline-none" placeholder="••••••••">
                        </div>
                    </div>
                </div>

                <div class="text-xs text-slate-600 flex items-start space-x-2 pt-1">
                    <input type="checkbox" id="reg-terms" required class="mt-0.5 rounded border-slate-300 text-sky-600 focus:ring-sky-500">
                    <label for="reg-terms">Tôi đồng ý đăng ký và lưu trữ dữ liệu an toàn trên Cơ Sở Dữ Liệu Tàu Nhanh</label>
                </div>

                <button type="submit" id="btn-reg-submit" class="w-full py-3 bg-gradient-to-r from-emerald-600 to-teal-600 hover:from-emerald-700 hover:to-teal-700 text-white font-bold rounded-xl text-sm shadow-md transition flex items-center justify-center">
                    <i class="fa-solid fa-database mr-2"></i> Tiếp Tục Xác Thực & Tạo Tài Khoản
                </button>
            </form>

            <!-- VIEW 3: BƯỚC NHẬP MÃ XÁC THỰC OTP -->
            <div id="view-otp-verification" class="space-y-4 hidden text-center">
                <div class="w-14 h-14 bg-amber-100 text-amber-600 rounded-2xl flex items-center justify-center mx-auto text-2xl font-bold">
                    <i class="fa-solid fa-key"></i>
                </div>
                <div class="space-y-1">
                    <h4 class="text-lg font-bold text-slate-900">Xác Thực Mã OTP 6 Số</h4>
                    <p class="text-xs text-slate-500">
                        Hệ thống bảo mật đã gửi mã xác thực tới <strong id="otp-target-destination" class="text-slate-800"></strong>
                    </p>
                    <div id="otp-demo-hint" class="bg-amber-50 text-amber-900 text-xs p-2.5 rounded-xl border border-amber-200 mt-2 font-mono">
                        Mã OTP xác thực của bạn: <strong id="otp-code-display" class="text-base text-amber-700">123456</strong>
                    </div>
                </div>

                <div class="py-2">
                    <input type="text" id="otp-input" maxlength="6" class="w-48 text-center text-2xl font-black tracking-widest py-2.5 border-2 border-sky-400 rounded-xl focus:ring-4 focus:ring-sky-200 outline-none font-mono" placeholder="------">
                    <span id="otp-error-msg" class="text-xs text-rose-500 block mt-1 hidden font-bold">Mã OTP không hợp lệ!</span>
                </div>

                <div class="flex space-x-3">
                    <button type="button" onclick="cancelOtpVerification()" class="flex-1 py-2.5 border border-slate-200 hover:bg-slate-50 text-slate-700 rounded-xl text-xs font-bold transition">
                        Quay lại
                    </button>
                    <button type="button" onclick="confirmOtpVerification()" class="flex-1 py-2.5 bg-emerald-600 hover:bg-emerald-700 text-white rounded-xl text-xs font-bold shadow-md transition">
                        <i class="fa-solid fa-circle-check mr-1"></i> Xác Nhận Lưu DB
                    </button>
                </div>
            </div>

            <!-- Footer Database Status Indicator -->
            <div class="pt-3 border-t border-slate-100 flex items-center justify-between text-[11px] text-slate-500">
                <span class="flex items-center">
                    <span class="w-2 h-2 rounded-full bg-emerald-500 mr-1.5 animate-pulse"></span>
                    <span>Database: <strong>IndexedDB + LocalStorage</strong></span>
                </span>
                <button type="button" onclick="openDatabaseManagerModal()" class="text-sky-600 font-bold hover:underline flex items-center">
                    <i class="fa-solid fa-server mr-1"></i> Xem Dữ Liệu DB (<span id="modal-db-count">3</span>)
                </button>
            </div>
        </div>
    </div>

    <!-- DATABASE MANAGER MODAL (XEM TOÀN BỘ TÀI KHOẢN ĐÃ LƯU TRONG DB) -->
    <div id="db-manager-modal" class="fixed inset-0 bg-slate-900/60 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="bg-white rounded-3xl max-w-4xl w-full p-6 sm:p-7 shadow-2xl space-y-4 relative max-h-[92vh] flex flex-col">
            <button onclick="closeDatabaseManagerModal()" class="absolute top-4 right-4 text-slate-400 hover:text-slate-600 w-8 h-8 rounded-full flex items-center justify-center transition">
                <i class="fa-solid fa-xmark text-lg"></i>
            </button>

            <!-- Header -->
            <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-3 border-b border-slate-100 pb-3">
                <div class="flex items-center space-x-3">
                    <div class="w-11 h-11 bg-sky-100 text-sky-700 rounded-2xl flex items-center justify-center text-xl font-bold shadow-inner">
                        <i class="fa-solid fa-database"></i>
                    </div>
                    <div>
                        <div class="flex items-center space-x-2">
                            <h3 class="text-lg font-extrabold text-slate-900">Cơ Sở Dữ Liệu Tài Khoản Tàu Nhanh</h3>
                            <span class="px-2 py-0.5 bg-emerald-100 text-emerald-800 text-[10px] font-extrabold rounded-full uppercase flex items-center">
                                <span class="w-1.5 h-1.5 rounded-full bg-emerald-500 mr-1"></span> Live DB
                            </span>
                        </div>
                        <p class="text-xs text-slate-500">Dữ liệu được lưu trữ trực tiếp trong IndexedDB & LocalStorage của trình duyệt</p>
                    </div>
                </div>

                <div class="flex items-center space-x-2">
                    <button onclick="exportDatabaseJSON()" class="px-3 py-1.5 bg-slate-100 hover:bg-slate-200 text-slate-700 font-bold rounded-xl text-xs transition">
                        <i class="fa-solid fa-download mr-1"></i> Xuất JSON
                    </button>
                    <button onclick="resetDatabaseToDefault()" class="px-3 py-1.5 bg-rose-50 hover:bg-rose-100 text-rose-700 border border-rose-200 font-bold rounded-xl text-xs transition">
                        <i class="fa-solid fa-rotate-left mr-1"></i> Reset Mặc Định
                    </button>
                </div>
            </div>

            <!-- Search and Stats Bar -->
            <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-3">
                <div class="relative flex-1">
                    <i class="fa-solid fa-magnifying-glass absolute left-3 top-1/2 -translate-y-1/2 text-slate-400 text-xs"></i>
                    <input type="text" id="db-search-input" oninput="filterDatabaseTable()" placeholder="Tìm kiếm theo tên, email, số điện thoại..." class="w-full pl-9 pr-3 py-2 border border-slate-200 rounded-xl text-xs outline-none focus:ring-2 focus:ring-sky-500">
                </div>
                <div class="text-xs font-semibold text-slate-600 bg-slate-50 px-3 py-2 rounded-xl border border-slate-200 flex items-center space-x-2">
                    <span>Tổng số tài khoản:</span>
                    <span id="db-total-count" class="px-2 py-0.5 bg-sky-600 text-white rounded-lg font-black text-xs">3</span>
                </div>
            </div>

            <!-- Database Accounts Table -->
            <div class="overflow-x-auto flex-grow max-h-72 border border-slate-200 rounded-2xl">
                <table class="w-full text-left border-collapse text-xs">
                    <thead class="bg-slate-50 sticky top-0 border-b border-slate-200 text-slate-600 font-bold uppercase text-[10px]">
                        <tr>
                            <th class="py-2.5 px-3">Mã User</th>
                            <th class="py-2.5 px-3">Họ và Tên</th>
                            <th class="py-2.5 px-3">Email & SĐT</th>
                            <th class="py-2.5 px-3">Mật khẩu</th>
                            <th class="py-2.5 px-3">Xác Thực</th>
                            <th class="py-2.5 px-3">Ngày Tạo</th>
                            <th class="py-2.5 px-3 text-right">Thao Tác</th>
                        </tr>
                    </thead>
                    <tbody id="db-users-table-body" class="divide-y divide-slate-100">
                        <!-- Populated by JS -->
                    </tbody>
                </table>
            </div>

            <!-- Footer -->
            <div class="flex items-center justify-between pt-2 border-t border-slate-100 text-xs">
                <span class="text-slate-400 text-[11px]"><i class="fa-solid fa-info-circle text-sky-500 mr-1"></i> Tài khoản sau khi đăng ký & xác thực OTP sẽ xuất hiện ngay tại đây.</span>
                <button onclick="closeDatabaseManagerModal()" class="px-5 py-2 bg-slate-800 hover:bg-slate-900 text-white rounded-xl font-bold transition">
                    Đóng
                </button>
            </div>
        </div>
    </div>

    <!-- GEOLOCATION POPUP MODAL -->
    <div id="gps-info-modal" class="fixed inset-0 bg-slate-900/60 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="bg-white rounded-3xl max-w-lg w-full p-6 shadow-2xl space-y-5 relative">
            <button onclick="closeGpsModal()" class="absolute top-4 right-4 text-slate-400 hover:text-slate-600 w-8 h-8 rounded-full flex items-center justify-center">
                <i class="fa-solid fa-xmark text-lg"></i>
            </button>

            <div class="space-y-1">
                <h3 class="text-xl font-bold text-slate-900 flex items-center">
                    <i class="fa-solid fa-location-crosshairs text-sky-600 mr-2"></i> Chi Tiết Định Vị & Nhà Ga Gần Nhất
                </h3>
                <p class="text-xs text-slate-500">Hệ thống đo khoảng cách chính xác theo đường chim bay và gợi ý thời gian di chuyển</p>
            </div>

            <div id="gps-modal-body" class="space-y-3">
                <!-- Dynamically populated -->
            </div>

            <div class="pt-2 text-right">
                <button onclick="closeGpsModal()" class="px-5 py-2.5 bg-slate-800 text-white rounded-xl text-xs font-bold">Đóng</button>
            </div>
        </div>
    </div>

    <!-- PUSH NOTIFICATION TOAST -->
    <div id="notification-toast" class="fixed bottom-5 right-5 z-50 transform translate-y-24 opacity-0 transition-all duration-300 max-w-sm w-full bg-slate-900 text-white p-4 rounded-2xl shadow-2xl flex items-start space-x-3 border border-slate-700">
        <div class="text-amber-400 text-xl pt-0.5"><i class="fa-solid fa-bell"></i></div>
        <div class="flex-grow space-y-0.5">
            <h5 id="toast-title" class="text-xs font-bold text-amber-400">Gợi ý từ Tàu Nhanh AI</h5>
            <p id="toast-body" class="text-xs text-slate-300">Đã phát hiện bạn ở gần Ga Hà Nội (1.8 km). Tuyến đi quen thuộc Đà Nẵng đang có giá tốt!</p>
        </div>
        <button onclick="dismissToast()" class="text-slate-500 hover:text-white text-xs"><i class="fa-solid fa-xmark"></i></button>
    </div>

    <!-- FOOTER -->
    <footer class="bg-white border-t border-slate-200 py-6 mt-12">
        <div class="max-w-7xl mx-auto px-4 text-center text-xs text-slate-500 space-y-2">
            <p>© 2026 Tàu Nhanh Smart AI Train Booking Engine. Tích hợp Định Vị GPS Khách Hàng, Giám Sát Tàu Thời Gian Thực & Sơ Đồ Toa 2D.</p>
            <p class="text-slate-400">Đồng bộ mạng lưới đường sắt Quốc Gia Việt Nam: Tuyến Bắc - Nam (Hà Nội ➔ Sài Gòn 1,726 km).</p>
        </div>
    </footer>

    <!-- CORE LOGIC & SCRIPTS -->
    <script>
        // =========================================================================
        // MASTER DATABASE: STATIONS, TRAINS & TRIPS
        // =========================================================================
        
        // Danh mục 11 Nhà ga chính Bắc - Nam kèm tọa độ GPS thực tế
        const STATIONS_MASTER = [
            { id: 'HNO', name: 'Hà Nội', fullName: 'Ga Hà Nội', lat: 21.0245, lng: 105.8412, km: 0, address: '120 Lê Duẩn, Hoàn Kiếm, Hà Nội' },
            { id: 'GBA', name: 'Giáp Bát', fullName: 'Ga Giáp Bát', lat: 20.9814, lng: 105.8415, km: 5, address: '366 Giải Phóng, Hoàng Mai, Hà Nội' },
            { id: 'PLY', name: 'Phủ Lý', fullName: 'Ga Phủ Lý', lat: 20.5367, lng: 105.9189, km: 56, address: 'Hai Bà Trưng, TP. Phủ Lý, Hà Nam' },
            { id: 'NDI', name: 'Nam Định', fullName: 'Ga Nam Định', lat: 20.4358, lng: 106.1669, km: 87, address: 'Trần Đăng Ninh, TP. Nam Định' },
            { id: 'THA', name: 'Thanh Hóa', fullName: 'Ga Thanh Hóa', lat: 19.8067, lng: 105.7767, km: 175, address: 'Dương Đình Nghệ, TP. Thanh Hóa' },
            { id: 'VII', name: 'Vinh', fullName: 'Ga Vinh', lat: 18.6796, lng: 105.6669, km: 319, address: 'Lê Ninh, Quán Bàu, TP. Vinh' },
            { id: 'DHO', name: 'Đồng Hới', fullName: 'Ga Đồng Hới', lat: 17.4764, lng: 106.6025, km: 522, address: 'Tiểu khu 4, Thuận Lý, TP. Đồng Hới' },
            { id: 'HUE', name: 'Huế', fullName: 'Ga Huế', lat: 16.4637, lng: 107.5794, km: 688, address: '02 Bùi Thị Xuân, TP. Huế' },
            { id: 'DAN', name: 'Đà Nẵng', fullName: 'Ga Đà Nẵng', lat: 16.0718, lng: 108.2068, km: 791, address: '791 Hải Phòng, Tam Thuận, Thanh Khê, Đà Nẵng' },
            { id: 'NTR', name: 'Nha Trang', fullName: 'Ga Nha Trang', lat: 12.2478, lng: 109.1867, km: 1315, address: '17 Thái Nguyên, Phước Tân, TP. Nha Trang' },
            { id: 'SGO', name: 'Sài Gòn', fullName: 'Ga Sài Gòn', lat: 10.7828, lng: 106.6775, km: 1726, address: '01 Nguyễn Thông, Phường 9, Quận 3, TP.HCM' }
        ];

        // Danh mục các đoàn tàu với đặc tính đề xuất (Tốt nhất, Nhanh nhất, Tiết kiệm nhất, VIP)
        const TRAINS_DATABASE = [
            {
                id: 'SE1',
                name: 'Tàu Hỏa Tốc SE1',
                typeDesc: 'Tàu Nhanh Thế Hệ Mới - Chất lượng cao 5 sao',
                departTime: '19:30',
                arriveTime: '11:15 (+1 ngày)',
                durationText: '15 giờ 45 phút',
                durationMinutes: 945,
                basePrice: 850000,
                rating: 4.9,
                badge: 'BEST', // 🌟 Lựa chọn tốt nhất
                badgeLabel: '🌟 Tuyến tốt nhất & Đúng giờ',
                badgeClass: 'bg-amber-400 text-slate-950',
                timeSlot: 'night',
                carriages: [
                    { id: 'c1', name: 'Toa 1 - Ngồi Mềm Điều Hòa', type: 'SEAT', totalSeats: 28, priceMultiplier: 1.0, icon: 'fa-couch' },
                    { id: 'c2', name: 'Toa 2 - Giường Nằm Khoang 6', type: 'BED6', totalSeats: 18, priceMultiplier: 1.35, icon: 'fa-bed' },
                    { id: 'c3', name: 'Toa 3 - Giường Nằm VIP Khoang 4', type: 'BED4', totalSeats: 12, priceMultiplier: 1.75, icon: 'fa-crown' }
                ]
            },
            {
                id: 'SE3',
                name: 'Tàu Hỏa Tốc SE3',
                typeDesc: 'Tàu Tốc Hành Bắc Nam - Tiết kiệm 2 giờ di chuyển',
                departTime: '06:00',
                arriveTime: '20:30 (Cùng ngày)',
                durationText: '14 giờ 30 phút',
                durationMinutes: 870,
                basePrice: 920000,
                rating: 4.8,
                badge: 'FASTEST', // ⚡ Nhanh nhất
                badgeLabel: '⚡ Tuyến nhanh nhất (Rút ngắn 2h)',
                badgeClass: 'bg-sky-600 text-white',
                timeSlot: 'morning',
                carriages: [
                    { id: 'c1', name: 'Toa 1 - Ngồi Mềm Điều Hòa', type: 'SEAT', totalSeats: 28, priceMultiplier: 1.0, icon: 'fa-couch' },
                    { id: 'c2', name: 'Toa 2 - Giường Nằm Khoang 6', type: 'BED6', totalSeats: 18, priceMultiplier: 1.35, icon: 'fa-bed' },
                    { id: 'c3', name: 'Toa 3 - Giường Nằm VIP Khoang 4', type: 'BED4', totalSeats: 12, priceMultiplier: 1.75, icon: 'fa-crown' }
                ]
            },
            {
                id: 'SE7',
                name: 'Tàu Tiêu Chuẩn SE7',
                typeDesc: 'Tàu Phổ Thông Tiết Kiệm - Giá rẻ sinh viên & gia đình',
                departTime: '12:15',
                arriveTime: '04:45 (+1 ngày)',
                durationText: '16 giờ 30 phút',
                durationMinutes: 990,
                basePrice: 590000,
                rating: 4.6,
                badge: 'VALUE', // 💰 Giá phù hợp nhất
                badgeLabel: '💰 Giá tiết kiệm nhất (-30%)',
                badgeClass: 'bg-emerald-600 text-white',
                timeSlot: 'afternoon',
                carriages: [
                    { id: 'c1', name: 'Toa 1 - Ngồi Mềm Điều Hòa', type: 'SEAT', totalSeats: 28, priceMultiplier: 1.0, icon: 'fa-couch' },
                    { id: 'c2', name: 'Toa 2 - Giường Nằm Khoang 6', type: 'BED6', totalSeats: 18, priceMultiplier: 1.35, icon: 'fa-bed' }
                ]
            },
            {
                id: 'SE5',
                name: 'Tàu Du Lịch Sang Trọng SE5',
                typeDesc: 'Khoang VIP Cao Cấp - Trải nghiệm ẩm thực & cảnh đẹp miền Trung',
                departTime: '08:50',
                arriveTime: '23:40 (Cùng ngày)',
                durationText: '14 giờ 50 phút',
                durationMinutes: 890,
                basePrice: 1150000,
                rating: 4.95,
                badge: 'VIP', // 👑 VIP
                badgeLabel: '👑 Sang trọng & Yên tĩnh VIP',
                badgeClass: 'bg-purple-600 text-white',
                timeSlot: 'morning',
                carriages: [
                    { id: 'c1', name: 'Toa 1 - Giường Nằm Khoang 6', type: 'BED6', totalSeats: 18, priceMultiplier: 1.2, icon: 'fa-bed' },
                    { id: 'c2', name: 'Toa 2 - Giường Nằm VIP Khoang 4', type: 'BED4', totalSeats: 12, priceMultiplier: 1.6, icon: 'fa-crown' }
                ]
            }
        ];

        // Lịch sử 3 chuyến đi trước của người dùng (Để máy học đề xuất chuyến quen)
        const DEFAULT_TRIP_HISTORY = [
            {
                ticketId: 'TK-849201',
                trainId: 'SE1',
                from: 'Hà Nội',
                to: 'Đà Nẵng',
                departDate: '2026-09-18',
                seats: [{ carriageName: 'Toa 3 - Giường Nằm VIP Khoang 4', number: 'G1', type: 'Giường Nằm VIP (Tầng 1)' }],
                price: 1487500,
                status: 'PAST'
            },
            {
                ticketId: 'TK-721903',
                trainId: 'SE1',
                from: 'Hà Nội',
                to: 'Đà Nẵng',
                departDate: '2026-08-14',
                seats: [{ carriageName: 'Toa 3 - Giường Nằm VIP Khoang 4', number: 'G2', type: 'Giường Nằm VIP (Tầng 1)' }],
                price: 1487500,
                status: 'PAST'
            },
            {
                ticketId: 'TK-610294',
                trainId: 'SE3',
                from: 'Hà Nội',
                to: 'Đà Nẵng',
                departDate: '2026-07-20',
                seats: [{ carriageName: 'Toa 3 - Giường Nằm VIP Khoang 4', number: 'G3', type: 'Giường Nằm VIP (Tầng 2)' }],
                price: 1420000,
                status: 'PAST'
            }
        ];

        // =========================================================================
        // APPLICATION STATE
        // =========================================================================
        let currentUserLocation = { lat: 21.0285, lng: 105.8542, name: 'Hà Nội (Khu vực Hoàn Kiếm)' }; // Default
        let nearestStations = [];
        let currentSearchData = { from: 'Hà Nội', to: 'Đà Nẵng', date: '', preference: 'ALL' };
        let selectedTrain = null;
        let selectedCarriageIndex = 0;
        let selectedSeats = []; // [{ id, number, price, carriageName, type }]
        let activeHoldTimer = null;
        let activeLeafletMap = null;
        let mapTrainMarker = null;
        let userBookings = JSON.parse(localStorage.getItem('rail_user_bookings') || 'null') || [...DEFAULT_TRIP_HISTORY];
        let currentUser = JSON.parse(localStorage.getItem('rail_auth_user') || 'null');

        // =========================================================================
        // GEOLOCATION ENGINE: CALCULATE DISTANCES & SUGGEST NEAREST STATIONS
        // =========================================================================

        // Công thức Haversine tính khoảng cách giữa 2 tọa độ GPS (km)
        function calculateDistanceKm(lat1, lon1, lat2, lon2) {
            const R = 6371; // Bán kính Trái Đất (km)
            const dLat = (lat2 - lat1) * Math.PI / 180;
            const dLon = (lon2 - lon1) * Math.PI / 180;
            const a = 
                Math.sin(dLat/2) * Math.sin(dLat/2) +
                Math.cos(lat1 * Math.PI / 180) * Math.cos(lat2 * Math.PI / 180) * 
                Math.sin(dLon/2) * Math.sin(dLon/2);
            const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1-a));
            return parseFloat((R * c).toFixed(1));
        }

        // Định vị GPS thực tế qua Browser Geolocation API
        function detectUserLocation() {
            const btn = document.getElementById('btn-detect-gps');
            const btnText = document.getElementById('btn-gps-text');
            btnText.textContent = 'Đang định vị...';
            btn.disabled = true;

            if ("geolocation" in navigator) {
                navigator.geolocation.getCurrentPosition(
                    (position) => {
                        currentUserLocation = {
                            lat: position.coords.latitude,
                            lng: position.coords.longitude,
                            name: `Tọa độ GPS (${position.coords.latitude.toFixed(3)}, ${position.coords.longitude.toFixed(3)})`
                        };
                        btnText.textContent = 'Định vị GPS thực tế';
                        btn.disabled = false;
                        updateNearestStations();
                        Swal.fire({
                            icon: 'success',
                            title: 'Đã xác định vị trí của bạn!',
                            html: `Hệ thống đã nhận diện vị trí hiện tại.<br>Ga gần bạn nhất: <strong>${nearestStations[0].station.fullName} (${nearestStations[0].distance} km)</strong>`,
                            timer: 3000,
                            timerProgressBar: true
                        });
                    },
                    (error) => {
                        console.warn("Geolocation denied/fallback:", error);
                        btnText.textContent = 'Định vị GPS thực tế';
                        btn.disabled = false;
                        // Fallback sang mặc định Hà Nội
                        simulateUserLocation('HN_HOANKIEM');
                        Swal.fire({
                            icon: 'info',
                            title: 'Sử dụng vị trí tiêu chuẩn',
                            text: 'Quyền định vị trình duyệt chưa được cấp hoặc đang chạy localhost. Hệ thống tự động thiết lập tại khu vực trung tâm Hà Nội để bạn trải nghiệm đầy đủ tính năng!',
                            confirmButtonColor: '#0284c7'
                        });
                    },
                    { enableHighAccuracy: true, timeout: 6000 }
                );
            } else {
                simulateUserLocation('HN_HOANKIEM');
            }
        }

        // Mô phỏng vị trí khách hàng tại các tỉnh thành để test tính năng
        function simulateUserLocation(presetKey) {
            if (!presetKey) return;

            const presets = {
                'HN_HOANKIEM': { lat: 21.0285, lng: 105.8542, name: 'Hà Nội (Quận Hoàn Kiếm)' },
                'HN_GIAPBAT': { lat: 20.9790, lng: 105.8420, name: 'Hà Nội (Khu vực Giáp Bát / Hoàng Mai)' },
                'DANANG_HAICHAU': { lat: 16.0680, lng: 108.2120, name: 'Đà Nẵng (Quận Hải Châu)' },
                'HCM_Q1': { lat: 10.7769, lng: 106.7009, name: 'TP. Hồ Chí Minh (Quận 1 / Q.3)' },
                'NHATRANG_CENTRAL': { lat: 12.2388, lng: 109.1967, name: 'Nha Trang (Trung tâm)' },
                'VINH_CENTRAL': { lat: 18.6733, lng: 105.6813, name: 'Nghệ An (TP. Vinh)' }
            };

            if (presets[presetKey]) {
                currentUserLocation = presets[presetKey];
                updateNearestStations();
            }
        }

        // Tính toán khoảng cách tới tất cả nhà ga & sắp xếp tăng dần
        function updateNearestStations() {
            nearestStations = STATIONS_MASTER.map(st => {
                const dist = calculateDistanceKm(currentUserLocation.lat, currentUserLocation.lng, st.lat, st.lng);
                return {
                    station: st,
                    distance: dist,
                    estimatedTaxiMinutes: Math.round(dist * 2.5 + 4) // Ước tính thời gian đi taxi
                };
            }).sort((a, b) => a.distance - b.distance);

            renderNearestStationsUI();
        }

        // Hiển thị 3 nhà ga gần nhất lên giao diện
        function renderNearestStationsUI() {
            const container = document.getElementById('nearest-stations-container');
            const summaryText = document.getElementById('user-location-summary');
            const headerGpsText = document.getElementById('header-gps-text');
            const fromDistanceTag = document.getElementById('from-station-distance-tag');

            const top1 = nearestStations[0];
            summaryText.innerHTML = `Vị trí của bạn: <strong class="text-slate-800">${currentUserLocation.name}</strong> • Ga gần nhất: <strong class="text-sky-700">${top1.station.fullName} (${top1.distance} km - ~${top1.estimatedTaxiMinutes} phút di chuyển)</strong>`;
            headerGpsText.textContent = `${top1.station.fullName} (${top1.distance}km)`;
            fromDistanceTag.textContent = `Cách bạn: ${top1.distance} km`;

            // Tự động gợi ý điền Ga Đi là ga gần nhất nếu form chưa chọn
            const searchFromSelect = document.getElementById('search-from');
            if (top1.distance < 50) {
                searchFromSelect.value = top1.station.name;
            }

            container.innerHTML = '';
            nearestStations.slice(0, 3).forEach((item, index) => {
                const isClosest = index === 0;
                const card = document.createElement('div');
                card.className = `p-3.5 rounded-xl border transition ${
                    isClosest ? 'bg-white border-sky-400 ring-2 ring-sky-400/20 shadow-sm' : 'bg-white/70 border-slate-200 hover:border-sky-300'
                }`;

                card.innerHTML = `
                    <div class="flex items-center justify-between mb-1">
                        <span class="text-xs font-bold text-slate-800 flex items-center">
                            <i class="fa-solid fa-train-subway text-sky-600 mr-1.5"></i> ${item.station.fullName}
                        </span>
                        <span class="text-[10px] font-extrabold ${isClosest ? 'bg-emerald-100 text-emerald-800' : 'bg-slate-100 text-slate-600'} px-2 py-0.5 rounded-full">
                            ${isClosest ? 'Gần bạn nhất' : `Top ${index + 1}`}
                        </span>
                    </div>
                    <div class="text-[11px] text-slate-500 space-y-0.5 mb-2.5">
                        <div><i class="fa-solid fa-road text-slate-400"></i> Khoảng cách: <strong class="text-slate-800">${item.distance} km</strong></div>
                        <div><i class="fa-solid fa-taxi text-slate-400"></i> Ước tính xe chạy: <strong>~${item.estimatedTaxiMinutes} phút</strong></div>
                        <div class="truncate text-[10px] text-slate-400">${item.station.address}</div>
                    </div>
                    <button type="button" onclick="setStationAsOrigin('${item.station.name}')" class="w-full py-1.5 px-3 ${isClosest ? 'bg-sky-600 hover:bg-sky-700 text-white' : 'bg-slate-100 hover:bg-sky-50 text-sky-700'} rounded-lg text-xs font-bold transition flex items-center justify-center">
                        <i class="fa-solid fa-thumbtack mr-1"></i> Chọn làm Ga Khởi Hành
                    </button>
                `;
                container.appendChild(card);
            });
        }

        // Chọn ga gần nhất làm Ga Khởi Hành
        window.setStationAsOrigin = (stationName) => {
            document.getElementById('search-from').value = stationName;
            // Nếu ga đến trùng ga đi, đổi ga đến
            if (document.getElementById('search-to').value === stationName) {
                document.getElementById('search-to').value = (stationName === 'Đà Nẵng') ? 'Hà Nội' : 'Đà Nẵng';
            }
            handleSearch();
            Swal.fire({
                icon: 'success',
                title: `Đã chọn ${stationName} làm ga đi`,
                text: 'Hệ thống đã cập nhật danh sách các tuyến tàu tốt nhất xuất phát từ ga này!',
                timer: 1500,
                showConfirmButton: false
            });
        };

        window.openGpsModal = () => {
            const modalBody = document.getElementById('gps-modal-body');
            modalBody.innerHTML = `
                <div class="bg-sky-50 p-4 rounded-xl border border-sky-200 text-xs text-sky-900 space-y-1">
                    <div><strong>Vị trí phát hiện:</strong> ${currentUserLocation.name}</div>
                    <div><strong>Tọa độ:</strong> ${currentUserLocation.lat.toFixed(4)} N, ${currentUserLocation.lng.toFixed(4)} E</div>
                </div>
                <div class="space-y-2">
                    <span class="text-xs font-bold text-slate-700 block">Khoảng cách đến các nhà ga xe lửa:</span>
                    <div class="max-h-60 overflow-y-auto space-y-2 pr-1">
                        ${nearestStations.map(st => `
                            <div class="p-2.5 rounded-lg border border-slate-200 flex items-center justify-between text-xs">
                                <div>
                                    <span class="font-bold text-slate-800">${st.station.fullName}</span>
                                    <span class="text-slate-400 block text-[10px]">${st.station.address}</span>
                                </div>
                                <div class="text-right">
                                    <span class="font-bold text-sky-600">${st.distance} km</span>
                                    <span class="text-[10px] text-slate-400 block">~${st.estimatedTaxiMinutes} phút</span>
                                </div>
                            </div>
                        `).join('')}
                    </div>
                </div>
            `;
            document.getElementById('gps-info-modal').classList.remove('hidden');
        };

        window.closeGpsModal = () => {
            document.getElementById('gps-info-modal').classList.add('hidden');
        };

        // =========================================================================
        // SMART NOTIFICATIONS DỰA TRÊN CÁC CHUYẾN ĐI TRƯỚC
        // =========================================================================
        function checkPastTripsAndRecommend() {
            // Phân tích lịch sử
            if (userBookings.length > 0) {
                // Đếm tuyến thường đi
                const routeCounts = {};
                userBookings.forEach(trip => {
                    const route = `${trip.from} ➔ ${trip.to}`;
                    routeCounts[route] = (routeCounts[route] || 0) + 1;
                });

                let mostFrequentRoute = 'Hà Nội ➔ Đà Nẵng';
                let maxCount = 0;
                for (const [r, count] of Object.entries(routeCounts)) {
                    if (count > maxCount) {
                        maxCount = count;
                        mostFrequentRoute = r;
                    }
                }

                const [orig, dest] = mostFrequentRoute.split(' ➔ ');
                const topNearest = nearestStations.length > 0 ? nearestStations[0] : null;
                const nearestName = topNearest ? topNearest.station.fullName : 'Ga Hà Nội';
                const distText = topNearest ? `${topNearest.distance} km` : '1.8 km';

                document.getElementById('banner-recommendation-title').textContent = `Gợi ý chuyến quen thuộc: ${orig} ➔ ${dest}`;
                document.getElementById('banner-recommendation-desc').innerHTML = 
                    `Hệ thống nhận thấy bạn đã đi tuyến <strong class="text-white">${mostFrequentRoute}</strong> ${maxCount} lần. Định vị phát hiện bạn đang cách <strong class="text-amber-300">${nearestName} (${distText})</strong>. Đoàn tàu <strong class="text-white">SE1 (19:30)</strong> đang có ưu đãi giá phù hợp nhất từ <strong class="text-emerald-300">850.000 VNĐ</strong>!`;

                // Update notification feed text
                document.getElementById('stat-favorite-route').textContent = mostFrequentRoute;
            }
        }

        window.applySmartRecommendation = () => {
            document.getElementById('search-from').value = 'Hà Nội';
            document.getElementById('search-to').value = 'Đà Nẵng';
            document.getElementById('search-preference').value = 'BEST';
            switchTab('search-tab');
            handleSearch();
            Swal.fire({
                icon: 'success',
                title: 'Đã tải chuyến đề xuất!',
                text: 'Tuyến Hà Nội ➔ Đà Nẵng với đoàn tàu SE1 tốt nhất đã sẵn sàng để bạn chọn chỗ.',
                timer: 2000,
                showConfirmButton: false
            });
        };

        // =========================================================================
        // SEARCH & SMART ROUTE RECOMMENDATIONS ENGINE
        // =========================================================================
        window.handleSearch = (e) => {
            if (e) e.preventDefault();
            const from = document.getElementById('search-from').value;
            const to = document.getElementById('search-to').value;
            const date = document.getElementById('search-date').value || getTodayISOString();
            const preference = document.getElementById('search-preference').value;

            if (from === to) {
                Swal.fire('Thông báo', 'Ga đi và Ga đến không được giống nhau!', 'warning');
                return;
            }

            currentSearchData = { from, to, date, preference };
            document.getElementById('search-route-summary').textContent = `Hành trình từ Ga ${from} đến Ga ${to} • Ngày: ${formatDateVN(date)}`;
            renderFlexibleDateBar(date);
            filterAndRenderTrains();
        };

        window.swapStations = () => {
            const fromEl = document.getElementById('search-from');
            const toEl = document.getElementById('search-to');
            const temp = fromEl.value;
            fromEl.value = toEl.value;
            toEl.value = temp;
            handleSearch();
        };

        function renderFlexibleDateBar(selectedDateStr) {
            const container = document.getElementById('flexible-dates-bar');
            container.innerHTML = '';
            
            const baseDate = new Date(selectedDateStr || getTodayISOString());
            for (let i = -3; i <= 3; i++) {
                const d = new Date(baseDate);
                d.setDate(d.getDate() + i);
                const dateISO = d.toISOString().split('T')[0];
                const dayName = d.toLocaleDateString('vi-VN', { weekday: 'short' });
                const isSelected = dateISO === selectedDateStr;
                
                // Giá vé thay đổi linh hoạt thông minh theo ngày trong tuần (Cuối tuần cao hơn chút)
                const isWeekend = (d.getDay() === 0 || d.getDay() === 6);
                const priceCoeff = isWeekend ? 1.15 : (Math.abs(i) % 2 === 0 ? 0.92 : 1.0);
                const samplePrice = Math.round(590000 * priceCoeff).toLocaleString('vi-VN');

                const btn = document.createElement('button');
                btn.type = 'button';
                btn.className = `flex-1 min-w-[110px] p-2.5 rounded-xl border text-center transition ${
                    isSelected 
                        ? 'border-sky-600 bg-sky-50 ring-2 ring-sky-500/30' 
                        : 'border-slate-200 bg-white hover:border-sky-300'
                }`;
                btn.onclick = () => {
                    document.getElementById('search-date').value = dateISO;
                    handleSearch();
                };

                btn.innerHTML = `
                    <span class="block text-[10px] uppercase font-bold text-slate-400">${dayName}</span>
                    <span class="block text-xs font-extrabold ${isSelected ? 'text-sky-700' : 'text-slate-800'}">${d.getDate()}/${d.getMonth()+1}</span>
                    <span class="block text-[11px] font-bold ${isWeekend ? 'text-amber-600' : 'text-emerald-600'} mt-0.5">${samplePrice}đ</span>
                    ${priceCoeff < 1.0 ? '<span class="text-[9px] bg-emerald-100 text-emerald-800 font-bold px-1 rounded block mt-0.5">Rẻ nhất</span>' : ''}
                `;
                container.appendChild(btn);
            }
        }

        function filterAndRenderTrains() {
            const pref = document.getElementById('search-preference').value;
            const morningChecked = document.getElementById('time-filter-morning').checked;
            const afternoonChecked = document.getElementById('time-filter-afternoon').checked;
            const nightChecked = document.getElementById('time-filter-night').checked;

            let filtered = TRAINS_DATABASE.filter(t => {
                // Lọc theo khung giờ
                if (t.timeSlot === 'morning' && !morningChecked) return false;
                if (t.timeSlot === 'afternoon' && !afternoonChecked) return false;
                if (t.timeSlot === 'night' && !nightChecked) return false;

                // Lọc theo ưu tiên
                if (pref === 'BEST' && t.badge !== 'BEST') return false;
                if (pref === 'FASTEST' && t.badge !== 'FASTEST') return false;
                if (pref === 'VALUE' && t.badge !== 'VALUE') return false;
                if (pref === 'VIP' && t.badge !== 'VIP') return false;

                return true;
            });

            document.getElementById('results-count').textContent = `${filtered.length} chuyến khả dụng`;
            renderSmartRecommendationCards(filtered);
            renderTrainListings(filtered);
        }

        // Render 3 Card đề xuất nổi bật (Tốt nhất - Nhanh nhất - Giá phù hợp)
        function renderSmartRecommendationCards(trains) {
            const container = document.getElementById('smart-recommendations-grid');
            container.innerHTML = '';

            const topPicks = TRAINS_DATABASE.slice(0, 3);
            topPicks.forEach(t => {
                const card = document.createElement('div');
                card.className = `bg-white rounded-2xl p-4 border ${t.badge === 'BEST' ? 'border-amber-400 ring-2 ring-amber-400/20 shadow-md' : 'border-slate-200'} shadow-sm space-y-3 flex flex-col justify-between`;
                
                card.innerHTML = `
                    <div class="space-y-2">
                        <div class="flex items-center justify-between">
                            <span class="px-2.5 py-1 ${t.badgeClass} font-extrabold text-[10px] rounded-full uppercase tracking-wider">
                                ${t.badgeLabel}
                            </span>
                            <span class="text-xs font-bold text-slate-500"><i class="fa-solid fa-star text-amber-400"></i> ${t.rating}</span>
                        </div>
                        <h4 class="text-base font-extrabold text-slate-900">${t.name} (${t.id})</h4>
                        <div class="text-xs text-slate-500 space-y-1">
                            <div><i class="fa-solid fa-clock text-sky-600 mr-1"></i> Khởi hành: <strong class="text-slate-800">${t.departTime}</strong></div>
                            <div><i class="fa-solid fa-hourglass-half text-sky-600 mr-1"></i> Thời gian chạy: <strong>${t.durationText}</strong></div>
                            <div class="text-[11px] text-slate-400 italic">${t.typeDesc}</div>
                        </div>
                    </div>
                    <div class="border-t border-slate-100 pt-3 flex items-center justify-between">
                        <div>
                            <span class="text-[10px] text-slate-400 block">Giá vé từ</span>
                            <span class="text-base font-black text-sky-700">${t.basePrice.toLocaleString('vi-VN')} đ</span>
                        </div>
                        <button onclick="selectTrainForSeats('${t.id}')" class="px-4 py-2 bg-sky-600 hover:bg-sky-700 text-white font-bold rounded-xl text-xs shadow transition">
                            Chọn Chỗ
                        </button>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        // Render toàn bộ danh sách chi tiết các chuyến tàu
        function renderTrainListings(trains) {
            const container = document.getElementById('train-list');
            container.innerHTML = '';

            if (trains.length === 0) {
                container.innerHTML = `
                    <div class="p-8 text-center bg-white rounded-2xl border border-dashed border-slate-300">
                        <i class="fa-solid fa-train text-3xl text-slate-300 mb-2"></i>
                        <h5 class="text-sm font-bold text-slate-700">Không tìm thấy chuyến tàu phù hợp với bộ lọc</h5>
                        <p class="text-xs text-slate-400 mt-1">Vui lòng điều chỉnh lại khung giờ hoặc tiêu chí đề xuất.</p>
                        <button onclick="resetFilters()" class="mt-3 px-4 py-1.5 bg-sky-600 text-white rounded-xl text-xs font-bold">Đặt lại bộ lọc</button>
                    </div>
                `;
                return;
            }

            trains.forEach(train => {
                const card = document.createElement('div');
                card.className = "bg-white rounded-2xl p-5 border border-slate-200 shadow-sm hover:shadow-md transition space-y-4";
                
                card.innerHTML = `
                    <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 pb-4 border-b border-slate-100">
                        <div class="flex items-center space-x-3">
                            <div class="w-12 h-12 bg-sky-50 border border-sky-100 rounded-xl flex items-center justify-center text-sky-700 font-extrabold text-lg">
                                ${train.id}
                            </div>
                            <div>
                                <div class="flex items-center space-x-2">
                                    <h4 class="text-base font-bold text-slate-900">${train.name}</h4>
                                    <span class="px-2 py-0.5 ${train.badgeClass} text-[10px] font-bold rounded-full">${train.badgeLabel}</span>
                                </div>
                                <span class="text-xs text-slate-400"><i class="fa-solid fa-shield text-emerald-500 mr-1"></i> Đúng giờ 99.4% • Wifi 5G tốc độ cao • Điều hòa 2 chiều</span>
                            </div>
                        </div>

                        <!-- Schedule timeline visualization -->
                        <div class="flex items-center space-x-6 text-center">
                            <div>
                                <span class="text-lg font-black text-slate-900 block">${train.departTime}</span>
                                <span class="text-xs font-semibold text-slate-500">${currentSearchData.from}</span>
                            </div>
                            <div class="text-center px-2">
                                <span class="text-[10px] text-sky-600 font-bold block">${train.durationText}</span>
                                <div class="w-24 h-0.5 bg-slate-200 relative my-1">
                                    <i class="fa-solid fa-train text-sky-600 text-xs absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 bg-white px-1"></i>
                                </div>
                                <span class="text-[10px] text-slate-400 block">Tàu chạy thẳng</span>
                            </div>
                            <div>
                                <span class="text-lg font-black text-slate-900 block">${train.arriveTime}</span>
                                <span class="text-xs font-semibold text-slate-500">${currentSearchData.to}</span>
                            </div>
                        </div>
                    </div>

                    <!-- Smart Upgrade Recommendation Box -->
                    <div class="bg-amber-50/80 border border-amber-200 rounded-xl p-2.5 text-xs text-amber-900 flex items-center justify-between">
                        <span><i class="fa-solid fa-lightbulb text-amber-600 mr-1.5"></i> Gợi ý chi phí phù hợp: Chỉ thêm <strong>45.000đ</strong> để nâng cấp từ Ghế ngồi lên Giường nằm Khoang 6 mát mẻ!</span>
                        <span class="text-[10px] bg-amber-200 font-bold px-2 py-0.5 rounded-full uppercase">Ưu đãi hôm nay</span>
                    </div>

                    <!-- Carriages breakdown & Select button -->
                    <div class="flex flex-col md:flex-row md:items-center justify-between gap-3 pt-1">
                        <div class="flex flex-wrap items-center gap-2 text-xs">
                            ${train.carriages.map(c => `
                                <span class="px-2.5 py-1 bg-slate-100 text-slate-700 font-semibold rounded-lg flex items-center">
                                    <i class="fa-solid ${c.icon} mr-1 text-slate-500"></i> ${c.name}
                                </span>
                            `).join('')}
                        </div>
                        <div class="flex items-center space-x-4">
                            <div class="text-right">
                                <span class="text-[10px] text-slate-400 block">Giá vé từ</span>
                                <span class="text-xl font-extrabold text-sky-700">${train.basePrice.toLocaleString('vi-VN')} VNĐ</span>
                            </div>
                            <button onclick="selectTrainForSeats('${train.id}')" class="px-6 py-2.5 bg-sky-600 hover:bg-sky-700 text-white font-extrabold rounded-xl shadow-md transition">
                                <i class="fa-solid fa-couch mr-1"></i> Chọn Toa & Chỗ Ngồi
                            </button>
                        </div>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        window.resetFilters = () => {
            document.getElementById('search-preference').value = 'ALL';
            document.getElementById('time-filter-morning').checked = true;
            document.getElementById('time-filter-afternoon').checked = true;
            document.getElementById('time-filter-night').checked = true;
            filterAndRenderTrains();
        };

        // =========================================================================
        // LIVE TRAIN GPS TRACKING & STATIONS ARRIVAL STATUS ENGINE
        // =========================================================================
        function initRailwayMap() {
            if (activeLeafletMap) return;

            const mapEl = document.getElementById('railway-map-container');
            if (!mapEl) return;

            // Khởi tạo bản đồ Leaflet - tab đã hiển thị trước khi hàm này chạy
            activeLeafletMap = L.map('railway-map-container', {
                zoomControl: true,
                scrollWheelZoom: true,
                attributionControl: true
            }).setView([17.0, 106.5], 6);

            // Tile layer OpenStreetMap
            L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
                attribution: '© <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> | Tàu Nhanh GPS Tracker',
                maxZoom: 18
            }).addTo(activeLeafletMap);

            // Vẽ tuyến đường ray Bắc-Nam bằng Polyline
            const latLngs = STATIONS_MASTER.map(s => [s.lat, s.lng]);
            const railwayLine = L.polyline(latLngs, {
                color: '#0284c7',
                weight: 4,
                opacity: 0.85,
                dashArray: '10, 6',
                lineJoin: 'round'
            }).addTo(activeLeafletMap);

            // Đánh dấu các nhà ga với màu sắc theo vị trí
            STATIONS_MASTER.forEach((s, idx) => {
                const isStart = idx === 0;
                const isEnd = idx === STATIONS_MASTER.length - 1;
                const color = isStart ? '#10b981' : (isEnd ? '#e11d48' : '#0284c7');

                const marker = L.circleMarker([s.lat, s.lng], {
                    radius: isStart || isEnd ? 9 : 7,
                    fillColor: color,
                    color: '#ffffff',
                    weight: 2.5,
                    opacity: 1,
                    fillOpacity: 0.95
                }).addTo(activeLeafletMap);

                marker.bindPopup(`
                    <div style="font-family:sans-serif;min-width:160px;line-height:1.6">
                        <strong style="font-size:13px">${s.fullName}</strong><br>
                        <span style="color:#64748b;font-size:11px">Mã ga: ${s.id} &nbsp;|&nbsp; Km ${s.km}</span><br>
                        <span style="color:#64748b;font-size:11px">${s.address}</span>
                    </div>
                `);

                // Label tên ga
                const label = L.divIcon({
                    className: '',
                    html: `<div style="background:white;border:1px solid #cbd5e1;border-radius:4px;padding:2px 6px;font-size:10px;font-weight:700;color:#1e293b;white-space:nowrap;box-shadow:0 1px 3px rgba(0,0,0,.15)">${s.name}</div>`,
                    iconAnchor: [-10, 8]
                });
                L.marker([s.lat, s.lng], { icon: label, interactive: false }).addTo(activeLeafletMap);
            });

            // Đánh dấu vị trí người dùng
            if (currentUserLocation) {
                const userIcon = L.divIcon({
                    className: '',
                    html: `<div style="width:16px;height:16px;border-radius:50%;background:#10b981;border:3px solid white;box-shadow:0 0 8px rgba(16,185,129,.8)"></div>`,
                    iconSize: [16, 16],
                    iconAnchor: [8, 8]
                });
                L.marker([currentUserLocation.lat, currentUserLocation.lng], { icon: userIcon })
                    .addTo(activeLeafletMap)
                    .bindPopup(`<strong>📍 Vị trí của bạn</strong><br>${currentUserLocation.name}`);
            }

            // Đánh dấu đoàn tàu SE1 (~Km 655, khu vực Huế)
            const trainIcon = L.divIcon({
                className: '',
                html: `<div style="background:#e11d48;border:2.5px solid white;border-radius:50%;width:28px;height:28px;display:flex;align-items:center;justify-content:center;box-shadow:0 0 12px rgba(225,29,72,.7);font-size:14px">🚂</div>`,
                iconSize: [28, 28],
                iconAnchor: [14, 14]
            });
            mapTrainMarker = L.marker([16.4637, 107.5794], { icon: trainIcon }).addTo(activeLeafletMap);
            mapTrainMarker.bindPopup(`
                <div style="font-family:sans-serif;min-width:180px;line-height:1.6">
                    <strong style="font-size:13px">🚄 Đoàn Tàu SE1 — LIVE</strong><br>
                    <span style="color:#0284c7;font-size:11px;font-weight:700">Tốc độ: 78.5 km/h</span><br>
                    <span style="color:#64748b;font-size:11px">Đã qua Ga Đồng Hới • Đang tới Ga Huế</span><br>
                    <span style="color:#e11d48;font-size:11px;font-weight:700">Km 655 / 1726</span>
                </div>
            `);

            // Auto-zoom theo toàn bộ tuyến đường
            activeLeafletMap.fitBounds(railwayLine.getBounds(), { padding: [40, 40] });
        }



        // Cập nhật trạng thái tàu đã qua bến hay chưa theo thời gian thực
        function updateLiveTracker() {
            const trainId = document.getElementById('tracker-train-select').value;
            
            // Giả lập tiến độ hành trình (Mô phỏng chân thực)
            const progressRatio = 0.38; // Đang ở 38% hành trình (~Km 655 gần Huế)
            const currentKm = Math.round(progressRatio * 1726);
            const speed = 78 + Math.floor(Math.random() * 6);
            
            document.getElementById('tracker-current-location').textContent = `Km ${currentKm} (Khu vực Quảng Trị - Huế)`;
            document.getElementById('tracker-speed').textContent = `${speed} km/h`;
            document.getElementById('tracker-next-station').textContent = `Ga Huế (Sắp tới)`;
            document.getElementById('tracker-progress-percentage').textContent = `Tiến độ: ${Math.round(progressRatio * 100)}%`;
            document.getElementById('tracker-progress-bar-fill').style.width = `${Math.round(progressRatio * 100)}%`;
            document.getElementById('tracker-train-icon-marker').style.left = `${Math.round(progressRatio * 100)}%`;
            document.getElementById('tracker-train-icon-marker').innerHTML = `<i class="fa-solid fa-train"></i> ${trainId}`;

            // Render bảng kiểm tra các ga: Đã qua bến / Đang tới / Chưa tới
            const timelineContainer = document.getElementById('tracker-stations-timeline');
            timelineContainer.innerHTML = '';

            STATIONS_MASTER.forEach(st => {
                const stationRatio = st.km / 1726;
                let statusBadge = '';
                let rowBg = 'bg-white border-slate-200';
                let timeInfo = '';

                if (stationRatio < progressRatio - 0.03) {
                    // Đã qua bến
                    statusBadge = '<span class="px-3 py-1 bg-emerald-100 text-emerald-800 font-extrabold text-xs rounded-full flex items-center"><i class="fa-solid fa-circle-check mr-1.5"></i> ĐÃ QUA BẾN</span>';
                    rowBg = 'bg-slate-50 border-slate-200 text-slate-500';
                    timeInfo = `<span class="text-emerald-700 font-semibold">Đã rời bến an toàn</span>`;
                } else if (Math.abs(stationRatio - progressRatio) <= 0.05) {
                    // Đang tới bến hoặc sắp cập ga
                    statusBadge = '<span class="px-3 py-1 bg-amber-400 text-slate-950 font-black text-xs rounded-full animate-pulse flex items-center shadow-sm"><i class="fa-solid fa-train mr-1.5"></i> ĐANG TỚI BẾN (Dự kiến sau 18 phút)</span>';
                    rowBg = 'bg-amber-50/80 border-amber-300 ring-2 ring-amber-400/30 text-amber-950 font-bold';
                    timeInfo = `<span class="text-amber-800 font-bold">Khoảng cách: 15 km • Dự kiến: 10:45</span>`;
                } else {
                    // Chưa tới bến
                    statusBadge = '<span class="px-3 py-1 bg-slate-100 text-slate-600 font-bold text-xs rounded-full">CHƯA TỚI BẾN</span>';
                    timeInfo = `<span class="text-slate-500">Dự kiến theo lịch trình</span>`;
                }

                const row = document.createElement('div');
                row.className = `p-4 rounded-xl border flex flex-col md:flex-row md:items-center justify-between gap-2 transition ${rowBg}`;
                row.innerHTML = `
                    <div class="flex items-center space-x-3">
                        <div class="w-9 h-9 rounded-xl bg-sky-100 text-sky-700 flex items-center justify-center font-bold text-sm">
                            <i class="fa-solid fa-building-flag"></i>
                        </div>
                        <div>
                            <span class="block text-sm font-bold text-slate-900">${st.fullName} (${st.id})</span>
                            <span class="text-xs text-slate-500">Cột mốc Km ${st.km} • ${timeInfo}</span>
                        </div>
                    </div>
                    <div>${statusBadge}</div>
                `;
                timelineContainer.appendChild(row);
            });

            checkMyStationArrival();
        }

        // Kiểm tra cụ thể xem tàu đã qua bến của khách hay chưa
        function checkMyStationArrival() {
            const myStationName = document.getElementById('tracker-my-station').value;
            const trainId = document.getElementById('tracker-train-select').value;
            const alertBox = document.getElementById('station-arrival-status-box');

            const st = STATIONS_MASTER.find(s => s.name === myStationName);
            if (!st) return;

            const progressRatio = 0.38;
            const currentKm = Math.round(progressRatio * 1726); // ~655 km
            const diffKm = st.km - currentKm;

            if (diffKm < -15) {
                // Tàu đã qua ga của bạn
                alertBox.className = "bg-rose-50 border-2 border-rose-300 rounded-2xl p-5 shadow-sm space-y-1.5";
                alertBox.innerHTML = `
                    <div class="flex items-center justify-between">
                        <span class="text-xs font-bold text-rose-700 uppercase tracking-wider flex items-center">
                            <i class="fa-solid fa-triangle-exclamation mr-1.5 text-rose-600"></i> Trạng thái đoàn tàu với ${st.fullName}
                        </span>
                        <span class="px-2.5 py-0.5 bg-rose-200 text-rose-900 font-extrabold text-[11px] rounded-full">ĐÃ QUA GA</span>
                    </div>
                    <h4 class="text-base font-extrabold text-slate-900">Tàu ${trainId} ĐÃ QUA ${st.fullName}!</h4>
                    <p class="text-xs text-slate-600">
                        Đoàn tàu đã hoàn tất việc đón trả khách tại ga này và đang tiếp tục hành trình hướng về các ga tiếp theo. Vui lòng theo dõi các chuyến tàu kế tiếp trong ngày.
                    </p>
                `;
            } else if (Math.abs(diffKm) <= 30) {
                // Tàu đang rất gần ga của bạn
                alertBox.className = "bg-amber-100/90 border-2 border-amber-400 rounded-2xl p-5 shadow-sm space-y-1.5 animate-pulse";
                alertBox.innerHTML = `
                    <div class="flex items-center justify-between">
                        <span class="text-xs font-bold text-amber-800 uppercase tracking-wider flex items-center">
                            <i class="fa-solid fa-bell mr-1.5 text-amber-600"></i> Cảnh báo khách chuẩn bị lên tàu
                        </span>
                        <span class="px-2.5 py-0.5 bg-amber-400 text-slate-950 font-black text-[11px] rounded-full">GẦN TỚI BẾN (ETA: 18 phút)</span>
                    </div>
                    <h4 class="text-base font-black text-slate-900">Tàu ${trainId} ĐANG CÁCH ${st.fullName} KHOẢNG ${Math.abs(diffKm)} KM!</h4>
                    <p class="text-xs text-slate-700">
                        Đoàn tàu dự kiến sẽ cập ga sau <strong>18 phút</strong> nữa. Hành khách vui lòng di chuyển vào sảnh ga và chuẩn bị sẵn Vé điện tử / Thẻ căn cước công dân để soát vé.
                    </p>
                `;
            } else {
                // Tàu chưa tới ga
                const hoursLeft = (diffKm / 78).toFixed(1);
                alertBox.className = "bg-emerald-50 border-2 border-emerald-300 rounded-2xl p-5 shadow-sm space-y-1.5";
                alertBox.innerHTML = `
                    <div class="flex items-center justify-between">
                        <span class="text-xs font-bold text-emerald-700 uppercase tracking-wider flex items-center">
                            <i class="fa-solid fa-route mr-1.5 text-emerald-600"></i> Thông tin hành trình tới ${st.fullName}
                        </span>
                        <span class="px-2.5 py-0.5 bg-emerald-200 text-emerald-900 font-extrabold text-[11px] rounded-full">CHƯA QUA BẾN</span>
                    </div>
                    <h4 class="text-base font-extrabold text-slate-900">Tàu ${trainId} Đang Cách ${st.fullName} ${diffKm} km</h4>
                    <p class="text-xs text-slate-600">
                        Đoàn tàu đang duy trì tốc độ ổn định 78.5 km/h và chạy đúng giờ. Dự kiến sẽ tới ${st.fullName} sau khoảng <strong>${hoursLeft} giờ</strong>.
                    </p>
                `;
            }
        }

        // =========================================================================
        // VISUAL SEAT & BERTH SELECTION ENGINE (MÔ HÌNH TOA & VỊ TRÍ GHẾ / GIƯỜNG)
        // =========================================================================
        window.selectTrainForSeats = (trainId) => {
            selectedTrain = TRAINS_DATABASE.find(t => t.id === trainId);
            selectedCarriageIndex = 0;
            selectedSeats = [];

            document.getElementById('seat-view-train-code').textContent = selectedTrain.id;
            document.getElementById('seat-view-route').textContent = `${currentSearchData.from} ➔ ${currentSearchData.to}`;
            document.getElementById('seat-view-time').textContent = `Khởi hành: ${selectedTrain.departTime}, Ngày: ${currentSearchData.date || getTodayISOString()}`;

            // Chuyển view sang sơ đồ ghế
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            document.getElementById('seat-selection-view').classList.remove('hidden');

            startHoldTimer();
            renderVisualTrainExterior();
            renderCarriageTabs();
            renderSeatMap();
            updateBookingSummaryUI();
        };

        window.backToSearchResults = () => {
            document.getElementById('seat-selection-view').classList.add('hidden');
            document.getElementById('search-tab').classList.remove('hidden');
            clearInterval(activeHoldTimer);
        };

        // Render mô hình ngoại thất đoàn tàu toàn cảnh
        function renderVisualTrainExterior() {
            const container = document.getElementById('carriage-overview-strip');
            container.innerHTML = '';

            selectedTrain.carriages.forEach((c, idx) => {
                const isActive = idx === selectedCarriageIndex;
                const carBox = document.createElement('div');
                carBox.className = `flex-shrink-0 w-36 rounded-xl border-2 p-2.5 text-center cursor-pointer transition ${
                    isActive ? 'border-sky-600 bg-sky-50 shadow-md transform -translate-y-1' : 'border-slate-200 bg-slate-50 hover:border-sky-300'
                }`;
                carBox.onclick = () => {
                    selectedCarriageIndex = idx;
                    renderVisualTrainExterior();
                    renderCarriageTabs();
                    renderSeatMap();
                };

                carBox.innerHTML = `
                    <div class="flex items-center justify-between text-[10px] text-slate-400 font-bold mb-1">
                        <span>TOA ${idx + 1}</span>
                        <i class="fa-solid ${c.icon} text-sky-600"></i>
                    </div>
                    <span class="block text-xs font-bold text-slate-800 truncate">${c.name.split(' - ')[1] || c.name}</span>
                    <span class="block text-[10px] ${isActive ? 'text-sky-700 font-extrabold' : 'text-slate-500'} mt-0.5">
                        ${c.totalSeats} chỗ • ${isActive ? 'ĐANG CHỌN' : 'Xem sơ đồ'}
                    </span>
                `;
                container.appendChild(carBox);
            });
        }

        function renderCarriageTabs() {
            const container = document.getElementById('carriage-selector-list');
            container.innerHTML = '';

            selectedTrain.carriages.forEach((c, idx) => {
                const isActive = idx === selectedCarriageIndex;
                const unitPrice = Math.round(selectedTrain.basePrice * c.priceMultiplier);

                const btn = document.createElement('button');
                btn.type = 'button';
                btn.onclick = () => {
                    selectedCarriageIndex = idx;
                    renderVisualTrainExterior();
                    renderCarriageTabs();
                    renderSeatMap();
                };

                btn.className = `p-3 rounded-xl border text-left transition flex items-center justify-between ${
                    isActive ? 'carriage-active border-sky-600 ring-2 ring-sky-500/20' : 'border-slate-200 hover:border-sky-300 bg-white'
                }`;

                btn.innerHTML = `
                    <div>
                        <span class="block text-xs font-extrabold text-slate-800">${c.name}</span>
                        <span class="block text-[11px] text-emerald-600 font-bold mt-0.5">${unitPrice.toLocaleString('vi-VN')} đ/vé</span>
                    </div>
                    <i class="fa-solid fa-chevron-right text-xs ${isActive ? 'text-sky-600' : 'text-slate-300'}"></i>
                `;
                container.appendChild(btn);
            });
        }

        // Render mặt cắt nội thất toa tàu (Sơ đồ ghế ngồi mềm hoặc Giường nằm K4 / K6)
        function renderSeatMap() {
            const container = document.getElementById('seat-map-grid');
            container.innerHTML = '';

            const carriage = selectedTrain.carriages[selectedCarriageIndex];
            const unitPrice = Math.round(selectedTrain.basePrice * carriage.priceMultiplier);

            document.getElementById('carriage-capacity-text').textContent = 
                `${carriage.name} • Đơn giá: ${unitPrice.toLocaleString('vi-VN')} đ`;

            // Khung thân tàu bao bọc bên ngoài (Realistic Train Car Shell)
            const shell = document.createElement('div');
            shell.className = "min-w-[650px] max-w-3xl mx-auto bg-slate-100 p-4 rounded-3xl border-4 border-slate-300 shadow-inner relative";

            // Header Toa: Cửa ra vào + Nhà vệ sinh (WC) + Hướng tàu chạy
            const topBar = document.createElement('div');
            topBar.className = "flex items-center justify-between pb-3 border-b border-slate-300 text-xs font-bold text-slate-600 px-2";
            topBar.innerHTML = `
                <div class="flex items-center space-x-3">
                    <span class="px-2 py-0.5 bg-slate-200 text-slate-700 rounded text-[10px]"><i class="fa-solid fa-door-open mr-1"></i> Cửa lên xuống</span>
                    <span class="px-2 py-0.5 bg-rose-100 text-rose-700 rounded text-[10px]"><i class="fa-solid fa-restroom mr-1"></i> Khu WC tự hoại</span>
                    <span class="px-2 py-0.5 bg-sky-100 text-sky-700 rounded text-[10px]"><i class="fa-solid fa-mug-hot mr-1"></i> Nước nóng/lạnh</span>
                </div>
                <div class="text-sky-700 flex items-center">
                    <span>Hướng đầu tàu</span>
                    <i class="fa-solid fa-arrow-right-long ml-1.5 animate-pulse"></i>
                </div>
            `;
            shell.appendChild(topBar);

            // Nội dung theo loại toa
            if (carriage.type === 'SEAT') {
                // SƠ ĐỒ TOA GHẾ NGỒI MỀM 2+2 (Cửa sổ - Ghế - Lối đi - Ghế - Cửa sổ)
                const seatsContainer = document.createElement('div');
                seatsContainer.className = "py-4 space-y-3";

                // Header mô tả các hàng
                const seatColsHeader = document.createElement('div');
                seatColsHeader.className = "grid grid-cols-5 gap-3 text-center text-[10px] font-bold text-slate-400 uppercase select-none px-4";
                seatColsHeader.innerHTML = `
                    <span>🪟 Cửa sổ A</span>
                    <span>Ghế B</span>
                    <span class="text-sky-600">Lối Đi</span>
                    <span>Ghế C</span>
                    <span>🪟 Cửa sổ D</span>
                `;
                seatsContainer.appendChild(seatColsHeader);

                const grid = document.createElement('div');
                grid.className = "grid grid-cols-5 gap-3 px-4";

                const soldMock = { 3: true, 7: true, 12: true, 18: true, 23: true };

                for (let i = 1; i <= carriage.totalSeats; i++) {
                    // Chèn khoảng trống lối đi ở giữa (sau mỗi 2 ghế)
                    if ((i - 1) % 4 === 2 && (i - 1) !== 0) {
                        const aisle = document.createElement('div');
                        aisle.className = "flex items-center justify-center text-[9px] text-slate-400 font-mono tracking-widest uppercase select-none";
                        aisle.textContent = "•••••";
                        grid.appendChild(aisle);
                    }

                    const seatId = `${selectedTrain.id}-${carriage.id}-S${i}`;
                    const isSold = soldMock[i] === true;
                    const isSelected = selectedSeats.some(s => s.id === seatId);
                    const isPriority = i <= 4;
                    const isWindow = (i % 4 === 1 || i % 4 === 0);

                    const seatBtn = document.createElement('button');
                    seatBtn.type = 'button';
                    seatBtn.disabled = isSold;
                    
                    let bgClasses = 'bg-white border-slate-300 text-slate-800 hover:border-sky-400 hover:bg-sky-50/50';
                    if (isSold) {
                        bgClasses = 'bg-rose-100 border-rose-300 text-rose-500 cursor-not-allowed';
                    } else if (isSelected) {
                        bgClasses = 'bg-amber-400 border-amber-500 text-slate-950 font-black shadow-md transform scale-105';
                    } else if (isPriority) {
                        bgClasses = 'bg-purple-50 border-purple-300 text-purple-700 hover:bg-purple-100';
                    }

                    seatBtn.className = `h-14 rounded-xl border-2 flex flex-col items-center justify-center transition relative group ${bgClasses}`;
                    seatBtn.onclick = () => toggleSeatSelection(seatId, i, unitPrice, carriage.name, 'Ghế Ngồi Mềm Điều Hòa');

                    const tooltipText = isSold 
                        ? 'Chỗ này đã có hành khách đặt mua' 
                        : `${isWindow ? '🪟 Cạnh cửa sổ ngắm cảnh' : '🚶 Cạnh lối đi ra vào dễ dàng'} • 🔌 Ổ sạc USB & Đèn đọc sách`;

                    seatBtn.innerHTML = `
                        <i class="fa-solid ${isSold ? 'fa-lock' : isPriority ? 'fa-heart text-purple-500' : 'fa-couch'} text-xs"></i>
                        <span class="text-xs font-bold mt-0.5">${i}</span>
                        <div class="absolute bottom-full mb-2 hidden group-hover:block w-40 bg-slate-900 text-white text-[10px] p-2 rounded-lg shadow-xl z-20 pointer-events-none text-center">
                            ${tooltipText}
                        </div>
                    `;
                    grid.appendChild(seatBtn);
                }
                seatsContainer.appendChild(grid);
                shell.appendChild(seatsContainer);

            } else {
                // SƠ ĐỒ TOA GIƯỜNG NẰM KHOANG 4 HOẶC KHOANG 6
                const isBed4 = carriage.type === 'BED4';
                const compCount = 3;
                const bedsPerComp = isBed4 ? 4 : 6;

                const compGrid = document.createElement('div');
                compGrid.className = "grid grid-cols-1 md:grid-cols-3 gap-4 py-4 px-2";

                let currentBedNumber = 1;
                const soldMockBeds = { 2: true, 5: true, 9: true };

                for (let c = 1; c <= compCount; c++) {
                    const compBox = document.createElement('div');
                    compBox.className = "bg-white p-3.5 rounded-2xl border border-slate-200 shadow-sm space-y-3";
                    compBox.innerHTML = `
                        <div class="flex items-center justify-between border-b pb-1.5 text-xs font-bold text-slate-700">
                            <span><i class="fa-solid fa-door-closed text-sky-600 mr-1"></i> Khoang ${c} ${isBed4 ? '(VIP 4 Giường)' : '(6 Giường)'}</span>
                            <span class="text-[10px] text-slate-400 font-normal">Cửa lùa riêng tư</span>
                        </div>
                    `;

                    const bedsContainer = document.createElement('div');
                    bedsContainer.className = "grid grid-cols-2 gap-2.5";

                    for (let b = 1; b <= bedsPerComp; b++) {
                        const bedNum = currentBedNumber++;
                        const seatId = `${selectedTrain.id}-${carriage.id}-B${bedNum}`;
                        const isSold = soldMockBeds[bedNum] === true;
                        const isSelected = selectedSeats.some(s => s.id === seatId);

                        let tierLabel = '';
                        if (isBed4) {
                            tierLabel = (b % 2 === 1) ? 'Tầng 1 (VIP)' : 'Tầng 2';
                        } else {
                            tierLabel = (b <= 2) ? 'Tầng 1' : (b <= 4 ? 'Tầng 2' : 'Tầng 3');
                        }

                        let bgClasses = 'bg-slate-50 border-slate-200 text-slate-800 hover:border-sky-400 hover:bg-sky-50';
                        if (isSold) bgClasses = 'bg-rose-100 border-rose-300 text-rose-500 cursor-not-allowed';
                        if (isSelected) bgClasses = 'bg-amber-400 border-amber-500 text-slate-950 font-black scale-105';

                        const bedBtn = document.createElement('button');
                        bedBtn.type = 'button';
                        bedBtn.disabled = isSold;
                        bedBtn.className = `p-2.5 rounded-xl border-2 flex flex-col items-center justify-center transition relative group ${bgClasses}`;
                        bedBtn.onclick = () => toggleSeatSelection(seatId, bedNum, unitPrice, carriage.name, `Giường Nằm (${tierLabel})`);

                        bedBtn.innerHTML = `
                            <i class="fa-solid ${isSold ? 'fa-lock' : isBed4 ? 'fa-crown text-amber-500' : 'fa-bed'} text-xs"></i>
                            <span class="text-xs font-bold">G${bedNum}</span>
                            <span class="text-[9px] font-semibold text-slate-500">${tierLabel}</span>
                            <div class="absolute bottom-full mb-2 hidden group-hover:block w-36 bg-slate-900 text-white text-[10px] p-2 rounded-lg shadow-xl z-20 pointer-events-none text-center">
                                ${isSold ? 'Đã bán' : `Đệm êm ái • Rèm riêng tư • Ổ điện 220V`}
                            </div>
                        `;
                        bedsContainer.appendChild(bedBtn);
                    }
                    compBox.appendChild(bedsContainer);
                    compGrid.appendChild(compBox);
                }
                shell.appendChild(compGrid);
            }

            container.appendChild(shell);
        }

        function toggleSeatSelection(id, number, price, carriageName, type) {
            const index = selectedSeats.findIndex(s => s.id === id);
            if (index > -1) {
                selectedSeats.splice(index, 1);
            } else {
                if (selectedSeats.length >= 6) {
                    Swal.fire('Giới hạn', 'Bạn chỉ được đặt tối đa 6 chỗ trong 1 lần giao dịch.', 'warning');
                    return;
                }
                selectedSeats.push({ id, number, price, carriageName, type });
            }
            updateBookingSummaryUI();
            renderSeatMap();
        }

        function filterSeatsHighlight(filterType) {
            // Hỗ trợ người dùng lọc nhanh ghế cạnh cửa sổ hoặc giường tầng 1
            if (filterType === 'window') {
                Swal.fire({
                    title: 'Đã làm nổi bật ghế cạnh cửa sổ',
                    text: 'Các vị trí ghế A và D sát cửa sổ để ngắm cảnh đẹp nhất suốt hành trình!',
                    icon: 'info',
                    timer: 1500,
                    showConfirmButton: false
                });
            } else if (filterType === 'tier1') {
                Swal.fire({
                    title: 'Đã lọc giường Tầng 1',
                    text: 'Giường tầng 1 thuận tiện lên xuống, phù hợp nhất cho người lớn tuổi và gia đình có trẻ em.',
                    icon: 'info',
                    timer: 1500,
                    showConfirmButton: false
                });
            }
        }

        function updateBookingSummaryUI() {
            const seatsText = document.getElementById('selected-seats-list');
            const totalPriceText = document.getElementById('selected-total-price');
            const checkoutBtn = document.getElementById('btn-proceed-checkout');

            if (selectedSeats.length === 0) {
                seatsText.textContent = "Chưa chọn chỗ nào";
                totalPriceText.textContent = "0 VNĐ";
                checkoutBtn.disabled = true;
            } else {
                const names = selectedSeats.map(s => `Chỗ ${s.number}`).join(', ');
                const total = selectedSeats.reduce((acc, curr) => acc + curr.price, 0);
                seatsText.textContent = `${names} (${selectedSeats.length} chỗ)`;
                totalPriceText.textContent = `${total.toLocaleString('vi-VN')} VNĐ`;
                checkoutBtn.disabled = false;
            }
        }

        function startHoldTimer() {
            clearInterval(activeHoldTimer);
            let duration = 600; // 10 phút giữ chỗ
            const timerEl = document.getElementById('hold-timer');

            activeHoldTimer = setInterval(() => {
                const minutes = Math.floor(duration / 60);
                const seconds = duration % 60;
                timerEl.textContent = `${String(minutes).padStart(2, '0')}:${String(seconds).padStart(2, '0')}`;

                if (--duration < 0) {
                    clearInterval(activeHoldTimer);
                    Swal.fire('Hết thời gian giữ chỗ', 'Phiên chọn chỗ của bạn đã hết hạn, vui lòng chọn lại chuyến.', 'warning');
                    backToSearchResults();
                }
            }, 1000);
        }

        // =========================================================================
        // CHECKOUT & DYNAMIC VIETQR PAYMENT
        // =========================================================================
        window.goToCheckout = () => {
            if (selectedSeats.length === 0) return;

            document.getElementById('seat-selection-view').classList.add('hidden');
            document.getElementById('checkout-tab').classList.remove('hidden');

            renderPassengerForms();
            renderCheckoutSummary();
            generateDynamicVietQR();
        };

        window.backToSeatSelection = () => {
            document.getElementById('checkout-tab').classList.add('hidden');
            document.getElementById('seat-selection-view').classList.remove('hidden');
        };

        function renderPassengerForms() {
            const container = document.getElementById('passengers-form-container');
            container.innerHTML = '';

            const defaultName = currentUser ? currentUser.displayName : '';
            const defaultEmail = currentUser ? currentUser.email : '';
            document.getElementById('contact-email').value = defaultEmail;

            selectedSeats.forEach((seat, idx) => {
                const card = document.createElement('div');
                card.className = "bg-slate-50 p-4 rounded-xl border border-slate-200 space-y-3";
                card.innerHTML = `
                    <div class="flex items-center justify-between text-xs font-bold text-sky-700">
                        <span>Hành khách ${idx + 1} (${seat.carriageName} - Chỗ ${seat.number})</span>
                        <span class="text-slate-500 font-normal">${seat.type}</span>
                    </div>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
                        <div>
                            <label class="block text-xs text-slate-500 mb-1">Họ và tên hành khách</label>
                            <input type="text" id="passenger-name-${idx}" value="${idx === 0 ? defaultName : ''}" required class="w-full px-3 py-2 border rounded-lg text-sm bg-white focus:ring-2 focus:ring-sky-500 outline-none" placeholder="Nguyễn Văn A">
                        </div>
                        <div>
                            <label class="block text-xs text-slate-500 mb-1">Số Căn Cước Công Dân / Hộ Chiếu</label>
                            <input type="text" id="passenger-id-${idx}" value="${idx === 0 ? '001201008899' : ''}" required class="w-full px-3 py-2 border rounded-lg text-sm bg-white focus:ring-2 focus:ring-sky-500 outline-none" placeholder="001200000000">
                        </div>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        function renderCheckoutSummary() {
            const container = document.getElementById('checkout-summary-details');
            const totalPriceEl = document.getElementById('checkout-final-price');

            const total = selectedSeats.reduce((acc, curr) => acc + curr.price, 0);

            container.innerHTML = `
                <div class="flex justify-between"><span>Đoàn tàu:</span><strong class="text-slate-800">${selectedTrain.name} (${selectedTrain.id})</strong></div>
                <div class="flex justify-between"><span>Lộ trình:</span><strong class="text-slate-800">Ga ${currentSearchData.from} ➔ Ga ${currentSearchData.to}</strong></div>
                <div class="flex justify-between"><span>Khởi hành:</span><strong class="text-slate-800">${currentSearchData.date || getTodayISOString()} (${selectedTrain.departTime})</strong></div>
                <div class="flex justify-between"><span>Số lượng vé:</span><strong class="text-slate-800">${selectedSeats.length} chỗ</strong></div>
                <div class="flex justify-between"><span>Bảo hiểm hành khách:</span><strong class="text-emerald-600">Đã bao gồm</strong></div>
            `;

            totalPriceEl.textContent = `${total.toLocaleString('vi-VN')} VNĐ`;
        }

        function generateDynamicVietQR() {
            const memo = `RE${Math.floor(100000 + Math.random() * 900000)}`;
            document.getElementById('qr-memo').textContent = memo;

            const total = selectedSeats.reduce((acc, curr) => acc + curr.price, 0);
            const qrContainer = document.getElementById('qrcode-canvas');
            qrContainer.innerHTML = '';

            const vietQRPayload = `https://img.vietqr.io/image/MB-999988889999-compact2.png?amount=${total}&addInfo=${memo}&accountName=TAUNHANH`;

            const img = document.createElement('img');
            img.src = vietQRPayload;
            img.alt = "Mã QR Thanh Toán";
            img.className = "w-44 h-44 rounded-xl shadow-sm border border-slate-100";
            qrContainer.appendChild(img);
        }

        window.updatePaymentView = () => {
            const method = document.querySelector('input[name="payment"]:checked').value;
            const qrBox = document.getElementById('vietqr-container');
            if (method === 'VIETQR') {
                qrBox.classList.remove('hidden');
            } else {
                qrBox.classList.add('hidden');
            }
        };

        window.confirmPaymentAndIssueTicket = () => {
            Swal.fire({
                title: 'Đang xác thực giao dịch...',
                text: 'Hệ thống đang xuất vé điện tử kèm mã QR lên tàu',
                allowOutsideClick: false,
                didOpen: () => { Swal.showLoading(); }
            });

            setTimeout(() => {
                const total = selectedSeats.reduce((acc, curr) => acc + curr.price, 0);
                const ticketId = `TK-${Math.floor(100000 + Math.random() * 900000)}`;

                const newBooking = {
                    ticketId,
                    trainId: selectedTrain.id,
                    from: currentSearchData.from,
                    to: currentSearchData.to,
                    departDate: currentSearchData.date || getTodayISOString(),
                    departTime: selectedTrain.departTime,
                    seats: [...selectedSeats],
                    price: total,
                    status: 'LIVE'
                };

                userBookings.unshift(newBooking);
                localStorage.setItem('rail_user_bookings', JSON.stringify(userBookings));

                clearInterval(activeHoldTimer);
                renderMyTicketsUI();
                renderHistoryUI();
                checkPastTripsAndRecommend();

                Swal.fire({
                    icon: 'success',
                    title: 'Đặt Vé Tàu Thành Công!',
                    html: `Mã vé: <strong>${ticketId}</strong> đã được lưu vào ví Vé điện tử của bạn.<br>Hệ thống đã chuẩn bị mã QR để bạn lên tàu!`,
                    confirmButtonText: 'Xem vé điện tử ngay',
                    confirmButtonColor: '#0284c7'
                }).then(() => {
                    switchTab('tickets-tab');
                });
            }, 1200);
        };

        // =========================================================================
        // MY TICKETS & HISTORY MANAGEMENT
        // =========================================================================
        function renderMyTicketsUI() {
            const container = document.getElementById('my-tickets-list');
            const badgeCount = document.getElementById('badge-ticket-count');
            container.innerHTML = '';

            const liveTickets = userBookings.filter(b => b.status === 'LIVE');

            if (liveTickets.length > 0) {
                badgeCount.textContent = liveTickets.length;
                badgeCount.classList.remove('hidden');
            } else {
                badgeCount.classList.add('hidden');
            }

            if (liveTickets.length === 0) {
                container.innerHTML = `
                    <div class="col-span-2 text-center py-12 bg-white rounded-2xl border border-dashed border-slate-300">
                        <i class="fa-solid fa-ticket text-4xl text-slate-300 mb-3 block"></i>
                        <h4 class="text-base font-bold text-slate-700">Chưa có vé điện tử nào đang hoạt động</h4>
                        <p class="text-xs text-slate-400 mt-1">Hãy thực hiện tìm chuyến và chọn chỗ ngay hôm nay.</p>
                        <button onclick="switchTab('search-tab')" class="mt-4 px-4 py-2 bg-sky-600 text-white rounded-xl text-xs font-bold shadow">
                            Tìm vé mới
                        </button>
                    </div>
                `;
                return;
            }

            liveTickets.forEach(t => {
                const seatsStr = t.seats.map(s => `${s.carriageName} - Chỗ ${s.number}`).join(', ');

                const card = document.createElement('div');
                card.className = "bg-white rounded-2xl border border-slate-200 shadow-md p-6 space-y-4 relative overflow-hidden";
                card.innerHTML = `
                    <div class="flex items-center justify-between border-b border-slate-100 pb-3">
                        <div class="flex items-center space-x-2">
                            <span class="px-2.5 py-1 bg-sky-100 text-sky-800 font-extrabold text-xs rounded-lg">${t.trainId}</span>
                            <span class="text-xs font-mono font-bold text-slate-800">${t.ticketId}</span>
                        </div>
                        <span class="px-2 py-0.5 bg-emerald-100 text-emerald-800 text-[10px] font-bold rounded-full uppercase"><i class="fa-solid fa-circle-check"></i> Hợp lệ lên tàu</span>
                    </div>

                    <div class="flex items-center justify-between text-center">
                        <div class="text-left">
                            <span class="text-xl font-black text-slate-900">${t.from}</span>
                            <span class="text-xs text-slate-400 block">${t.departTime}</span>
                        </div>
                        <i class="fa-solid fa-arrow-right text-sky-600 text-sm"></i>
                        <div class="text-right">
                            <span class="text-xl font-black text-slate-900">${t.to}</span>
                            <span class="text-xs text-slate-400 block">${t.departDate}</span>
                        </div>
                    </div>

                    <div class="bg-slate-50 p-3 rounded-xl text-xs text-slate-600 space-y-1">
                        <div>Vị trí chỗ: <strong class="text-slate-900">${seatsStr}</strong></div>
                        <div>Hành khách: <strong class="text-slate-900">${currentUser.displayName}</strong></div>
                    </div>

                    <!-- BOARDING QR CODE CONTAINER -->
                    <div class="flex items-center justify-between pt-2 border-t border-slate-100">
                        <div id="ticket-qr-${t.ticketId}" class="w-16 h-16 bg-slate-50 border border-slate-200 rounded-lg p-1 flex items-center justify-center"></div>
                        <div class="text-right space-y-1">
                            <button onclick="cancelTicket('${t.ticketId}')" class="px-3 py-1.5 bg-rose-50 hover:bg-rose-100 text-rose-600 border border-rose-200 text-xs font-bold rounded-lg transition">
                                <i class="fa-solid fa-ban"></i> Hủy vé trực tuyến
                            </button>
                        </div>
                    </div>
                `;
                container.appendChild(card);

                setTimeout(() => {
                    const qrel = document.getElementById(`ticket-qr-${t.ticketId}`);
                    if (qrel) {
                        qrel.innerHTML = '';
                        new QRCode(qrel, {
                            text: `TAUNHANH-BOARDING:${t.ticketId}`,
                            width: 56,
                            height: 56
                        });
                    }
                }, 100);
            });
        }

        function renderHistoryUI() {
            const tableBody = document.getElementById('history-table-body');
            tableBody.innerHTML = '';

            document.getElementById('stat-total-trips').textContent = userBookings.length;

            userBookings.forEach(b => {
                const tr = document.createElement('tr');
                tr.innerHTML = `
                    <td class="py-3 px-4 font-mono font-bold text-sky-700">${b.ticketId}</td>
                    <td class="py-3 px-4 font-bold">${b.trainId}</td>
                    <td class="py-3 px-4">${b.from} ➔ ${b.to}</td>
                    <td class="py-3 px-4">${b.departDate}</td>
                    <td class="py-3 px-4">${b.seats ? b.seats.length : 1} chỗ</td>
                    <td class="py-3 px-4">
                        <span class="px-2 py-0.5 text-[10px] font-bold rounded-full ${
                            b.status === 'LIVE' ? 'bg-emerald-100 text-emerald-800' : 'bg-slate-100 text-slate-600'
                        }">
                            ${b.status === 'LIVE' ? 'Sắp đi' : 'Đã hoàn thành'}
                        </span>
                    </td>
                `;
                tableBody.appendChild(tr);
            });
        }

        window.cancelTicket = (ticketId) => {
            Swal.fire({
                title: 'Xác nhận hủy vé?',
                text: "Vé đã hủy sẽ được hoàn tiền 90% về tài khoản theo quy định của Tàu Nhanh.",
                icon: 'warning',
                showCancelButton: true,
                confirmButtonColor: '#e11d48',
                confirmButtonText: 'Đồng ý Hủy',
                cancelButtonText: 'Bỏ qua'
            }).then((res) => {
                if (res.isConfirmed) {
                    const idx = userBookings.findIndex(b => b.ticketId === ticketId);
                    if (idx > -1) {
                        userBookings[idx].status = 'CANCELLED';
                        localStorage.setItem('rail_user_bookings', JSON.stringify(userBookings));
                        renderMyTicketsUI();
                        renderHistoryUI();
                        Swal.fire('Đã hủy vé', 'Vé của bạn đã được hủy thành công.', 'success');
                    }
                }
            });
        };

        // =========================================================================
        // 7. DATABASE ENGINE: TAU NHANH DB (INDEXEDDB + LOCALSTORAGE SYNCHRONIZED)
        // =========================================================================
        const TauNhanhDB = {
            dbName: 'TauNhanh_Database',
            dbVersion: 1,
            storeName: 'users',
            storageKey: 'taunhanh_users_db',
            sessionKey: 'rail_auth_user',

            // Dữ liệu tài khoản mẫu được cấp sẵn trong Database
            initialUsers: [
                {
                    id: 'USR-1001',
                    fullName: 'Nguyễn Văn An',
                    email: 'nguyenvanan@taunhanh.vn',
                    phone: '0912345678',
                    password: 'password123',
                    role: 'Hành khách thân thiết',
                    isVerified: true,
                    createdAt: '15/06/2026, 08:30:00',
                    lastLogin: '15/10/2026, 10:45:00',
                    bookingsCount: 3
                },
                {
                    id: 'USR-1002',
                    fullName: 'Trần Thị Mai',
                    email: 'demo@taunhanh.vn',
                    phone: '0987654321',
                    password: 'password123',
                    role: 'Hành khách tiêu chuẩn',
                    isVerified: true,
                    createdAt: '20/08/2026, 14:15:00',
                    lastLogin: '12/10/2026, 16:20:00',
                    bookingsCount: 0
                },
                {
                    id: 'USR-1003',
                    fullName: 'Quản Trị Viên Tàu Nhanh',
                    email: 'admin@taunhanh.vn',
                    phone: '0909090909',
                    password: 'admin123',
                    role: 'Quản trị viên hệ thống',
                    isVerified: true,
                    createdAt: '01/01/2026, 00:00:00',
                    lastLogin: '15/10/2026, 10:50:00',
                    bookingsCount: 0
                }
            ],

            init() {
                // Kiểm tra và khởi tạo dữ liệu trong LocalStorage
                let users = this.getAllUsers();
                if (!users || users.length === 0) {
                    localStorage.setItem(this.storageKey, JSON.stringify(this.initialUsers));
                }

                // Khởi tạo IndexedDB chuẩn browser
                if ('indexedDB' in window) {
                    const req = indexedDB.open(this.dbName, this.dbVersion);
                    req.onupgradeneeded = (e) => {
                        const db = e.target.result;
                        if (!db.objectStoreNames.contains(this.storeName)) {
                            const store = db.createObjectStore(this.storeName, { keyPath: 'id' });
                            store.createIndex('email', 'email', { unique: true });
                            store.createIndex('phone', 'phone', { unique: false });
                        }
                    };
                    req.onsuccess = (e) => {
                        const db = e.target.result;
                        const tx = db.transaction(this.storeName, 'readwrite');
                        const store = tx.objectStore(this.storeName);
                        const currentList = this.getAllUsers();
                        currentList.forEach(u => store.put(u));
                    };
                }

                this.updateDbBadges();
            },

            getAllUsers() {
                try {
                    const data = localStorage.getItem(this.storageKey);
                    return data ? JSON.parse(data) : [...this.initialUsers];
                } catch(e) {
                    return [...this.initialUsers];
                }
            },

            saveAllUsers(users) {
                localStorage.setItem(this.storageKey, JSON.stringify(users));
                if ('indexedDB' in window) {
                    const req = indexedDB.open(this.dbName, this.dbVersion);
                    req.onsuccess = (e) => {
                        const db = e.target.result;
                        const tx = db.transaction(this.storeName, 'readwrite');
                        const store = tx.objectStore(this.storeName);
                        users.forEach(u => store.put(u));
                    };
                }
                this.updateDbBadges();
            },

            getUserByEmailOrPhone(identifier) {
                if (!identifier) return null;
                const term = identifier.trim().toLowerCase();
                const users = this.getAllUsers();
                return users.find(u => (u.email && u.email.toLowerCase() === term) || (u.phone && u.phone === term));
            },

            registerUser(userData) {
                const users = this.getAllUsers();
                const emailExists = users.some(u => u.email.toLowerCase() === userData.email.trim().toLowerCase());
                if (emailExists) {
                    return { success: false, message: 'Email này đã tồn tại trong Cơ sở dữ liệu!' };
                }

                const newUser = {
                    id: `USR-${Math.floor(1000 + Math.random() * 9000)}`,
                    fullName: userData.fullName.trim(),
                    email: userData.email.trim().toLowerCase(),
                    phone: userData.phone.trim(),
                    password: userData.password,
                    role: 'Hành khách',
                    isVerified: true,
                    createdAt: new Date().toLocaleString('vi-VN'),
                    lastLogin: new Date().toLocaleString('vi-VN'),
                    bookingsCount: 0
                };

                users.unshift(newUser);
                this.saveAllUsers(users);
                return { success: true, user: newUser };
            },

            loginUser(identifier, password) {
                const user = this.getUserByEmailOrPhone(identifier);
                if (!user) {
                    return { success: false, message: 'Tài khoản không tồn tại trong Cơ sở dữ liệu! Vui lòng chọn tab Đăng Ký Mới.' };
                }
                if (user.password !== password) {
                    return { success: false, message: 'Mật khẩu xác thực không chính xác! Vui lòng kiểm tra lại.' };
                }

                user.lastLogin = new Date().toLocaleString('vi-VN');
                const users = this.getAllUsers();
                const idx = users.findIndex(u => u.id === user.id);
                if (idx > -1) {
                    users[idx] = user;
                    this.saveAllUsers(users);
                }

                return { success: true, user };
            },

            deleteUser(userId) {
                let users = this.getAllUsers();
                users = users.filter(u => u.id !== userId);
                this.saveAllUsers(users);
            },

            resetToDefault() {
                this.saveAllUsers([...this.initialUsers]);
            },

            updateDbBadges() {
                const count = this.getAllUsers().length;
                const b1 = document.getElementById('badge-db-count');
                const b2 = document.getElementById('modal-db-count');
                const b3 = document.getElementById('db-total-count');
                if (b1) b1.textContent = count;
                if (b2) b2.textContent = count;
                if (b3) b3.textContent = count;
            }
        };

        // =========================================================================
        // 8. AUTHENTICATION & OTP VERIFICATION WORKFLOW
        // =========================================================================
        let currentAuthTab = 'login';
        let pendingRegistration = null;

        window.openAuthModal = (tab = 'login') => {
            setAuthTab(tab);
            document.getElementById('auth-modal').classList.remove('hidden');
        };

        window.closeAuthModal = () => {
            document.getElementById('auth-modal').classList.add('hidden');
            cancelOtpVerification();
        };

        window.setAuthTab = (tab) => {
            currentAuthTab = tab;
            const btnLogin = document.getElementById('tab-btn-login');
            const btnRegister = document.getElementById('tab-btn-register');
            const formLogin = document.getElementById('form-login');
            const formRegister = document.getElementById('form-register');
            const viewOtp = document.getElementById('view-otp-verification');
            const tabButtons = document.getElementById('auth-tab-buttons');
            const modalTitle = document.getElementById('auth-modal-title');
            const modalDesc = document.getElementById('auth-modal-desc');

            tabButtons.classList.remove('hidden');
            viewOtp.classList.add('hidden');

            if (tab === 'login') {
                btnLogin.className = "flex-1 py-2 rounded-xl text-xs font-bold bg-white text-sky-700 shadow-sm transition";
                btnRegister.className = "flex-1 py-2 rounded-xl text-xs font-bold text-slate-500 hover:text-slate-800 transition";
                formLogin.classList.remove('hidden');
                formRegister.classList.add('hidden');
                modalTitle.textContent = "Xác Thực & Đăng Nhập Tàu Nhanh";
                modalDesc.textContent = "Đồng bộ lịch sử chuyến đi & gợi ý cá nhân hóa từ Database";
            } else {
                btnRegister.className = "flex-1 py-2 rounded-xl text-xs font-bold bg-white text-emerald-700 shadow-sm transition";
                btnLogin.className = "flex-1 py-2 rounded-xl text-xs font-bold text-slate-500 hover:text-slate-800 transition";
                formRegister.classList.remove('hidden');
                formLogin.classList.add('hidden');
                modalTitle.textContent = "Đăng Ký Tài Khoản & Lưu Database";
                modalDesc.textContent = "Thông tin tài khoản được xác thực và lưu trữ an toàn trong Cơ Sở Dữ Liệu";
            }
        };

        window.togglePasswordVisibility = (inputId, iconId) => {
            const input = document.getElementById(inputId);
            const icon = document.getElementById(iconId);
            if (input.type === 'password') {
                input.type = 'text';
                icon.className = 'fa-solid fa-eye-slash text-xs text-sky-600';
            } else {
                input.type = 'password';
                icon.className = 'fa-solid fa-eye text-xs text-slate-400';
            }
        };

        window.quickFillAccount = (email, pass) => {
            document.getElementById('login-identifier').value = email;
            document.getElementById('login-password').value = pass;
            Swal.fire({
                toast: true,
                position: 'top-end',
                icon: 'info',
                title: `Đã điền tài khoản: ${email}`,
                showConfirmButton: false,
                timer: 1500
            });
        };

        window.forgotPasswordNotice = () => {
            Swal.fire({
                icon: 'info',
                title: 'Khôi Phục Mật Khẩu',
                html: `Vui lòng liên hệ quản trị viên hoặc mở bảng <strong>Quản Lý Database</strong> trên thanh tiêu đề để tra cứu mật khẩu tài khoản trong Cơ sở dữ liệu!`,
                confirmButtonColor: '#0284c7'
            });
        };

        // Xử lý gửi Form Đăng Nhập kèm xác thực DB
        window.handleLoginSubmit = (e) => {
            e.preventDefault();
            const identifier = document.getElementById('login-identifier').value.trim();
            const password = document.getElementById('login-password').value;

            const res = TauNhanhDB.loginUser(identifier, password);
            if (!res.success) {
                Swal.fire({
                    icon: 'error',
                    title: 'Xác Thực Thất Bại',
                    text: res.message,
                    confirmButtonColor: '#0284c7'
                });
                return;
            }

            currentUser = res.user;
            localStorage.setItem(TauNhanhDB.sessionKey, JSON.stringify(currentUser));
            renderAuthUI();
            closeAuthModal();

            // Cập nhật các đề xuất và danh sách vé theo user
            checkPastTripsAndRecommend();
            renderMyTicketsUI();

            Swal.fire({
                icon: 'success',
                title: 'Đăng Nhập Thành Công!',
                html: `Chào mừng <strong>${currentUser.fullName}</strong> trở lại!<br>Dữ liệu cá nhân & lịch sử đặt vé đã được kết nối từ Database.`,
                timer: 2200,
                showConfirmButton: false
            });
        };

        // Xử lý gửi Form Đăng Ký -> Chuyển sang bước Xác Thực OTP
        window.handleRegisterSubmit = (e) => {
            e.preventDefault();
            const fullName = document.getElementById('reg-name').value.trim();
            const phone = document.getElementById('reg-phone').value.trim();
            const email = document.getElementById('reg-email').value.trim();
            const password = document.getElementById('reg-password').value;
            const passwordConfirm = document.getElementById('reg-password-confirm').value;

            // Kiểm tra mật khẩu khớp
            if (password !== passwordConfirm) {
                Swal.fire('Lỗi mật khẩu', 'Mật khẩu xác nhận không khớp! Vui lòng nhập lại chính xác.', 'warning');
                return;
            }

            // Kiểm tra email đã có trong DB chưa
            const existing = TauNhanhDB.getUserByEmailOrPhone(email);
            if (existing) {
                Swal.fire({
                    icon: 'warning',
                    title: 'Tài khoản đã tồn tại',
                    html: `Email <strong>${email}</strong> đã được đăng ký trong Database!<br>Bạn có thể chuyển sang tab Đăng Nhập.`,
                    confirmButtonColor: '#0284c7'
                });
                return;
            }

            // Sinh mã xác thực OTP 6 số
            const randomOtp = String(Math.floor(100000 + Math.random() * 900000));
            pendingRegistration = { fullName, phone, email, password, otp: randomOtp };

            // Hiển thị bước nhập OTP
            document.getElementById('form-register').classList.add('hidden');
            document.getElementById('auth-tab-buttons').classList.add('hidden');
            document.getElementById('view-otp-verification').classList.remove('hidden');
            document.getElementById('otp-target-destination').textContent = `${email} / ${phone}`;
            document.getElementById('otp-code-display').textContent = randomOtp;
            document.getElementById('otp-input').value = '';
            document.getElementById('otp-error-msg').classList.add('hidden');

            document.getElementById('auth-modal-title').textContent = "Bảo Mật: Xác Thực Mã OTP";
            document.getElementById('auth-modal-desc').textContent = "Nhập mã xác thực để kích hoạt tài khoản và lưu vào Cơ sở dữ liệu";

            Swal.fire({
                toast: true,
                position: 'top-end',
                icon: 'success',
                title: `Mã OTP xác thực của bạn: ${randomOtp}`,
                text: 'Hệ thống mô phỏng tin nhắn SMS & Email bảo mật',
                timer: 5000,
                showConfirmButton: false
            });
        };

        // Xác nhận mã OTP để hoàn tất đăng ký vào Database
        window.confirmOtpVerification = () => {
            const inputOtp = document.getElementById('otp-input').value.trim();
            if (!pendingRegistration) return;

            if (inputOtp !== pendingRegistration.otp) {
                document.getElementById('otp-error-msg').classList.remove('hidden');
                return;
            }

            // Lưu tài khoản mới vào Database
            const result = TauNhanhDB.registerUser(pendingRegistration);
            if (!result.success) {
                Swal.fire('Lỗi', result.message, 'error');
                return;
            }

            currentUser = result.user;
            localStorage.setItem(TauNhanhDB.sessionKey, JSON.stringify(currentUser));
            renderAuthUI();
            closeAuthModal();

            Swal.fire({
                icon: 'success',
                title: 'Đăng Ký & Xác Thực Thành Công!',
                html: `Tài khoản <strong>${currentUser.fullName}</strong> (${currentUser.email}) đã được kích hoạt và lưu vào <strong>Cơ Sở Dữ Liệu Tàu Nhanh</strong>!<br>Mã người dùng: <strong class="text-sky-600">${currentUser.id}</strong>`,
                confirmButtonColor: '#0284c7'
            });

            pendingRegistration = null;
        };

        window.cancelOtpVerification = () => {
            pendingRegistration = null;
            document.getElementById('view-otp-verification').classList.add('hidden');
            document.getElementById('auth-tab-buttons').classList.remove('hidden');
            setAuthTab('register');
        };

        // Cập nhật giao diện Trạng Thái Đăng Nhập / Profile trên Navbar
        function renderAuthUI() {
            const container = document.getElementById('auth-status-container');
            if (currentUser) {
                const initialChar = currentUser.fullName ? currentUser.fullName.charAt(0).toUpperCase() : 'U';
                container.innerHTML = `
                    <div class="relative group">
                        <button class="flex items-center space-x-2 py-1 px-2 rounded-xl bg-slate-50 hover:bg-sky-50 border border-slate-200 hover:border-sky-300 transition">
                            <div class="w-8 h-8 rounded-full bg-gradient-to-tr from-sky-600 to-blue-800 text-white font-extrabold flex items-center justify-center text-xs shadow-sm">
                                ${initialChar}
                            </div>
                            <div class="text-left hidden sm:block">
                                <span class="block text-xs font-bold text-slate-900 leading-tight">${currentUser.fullName}</span>
                                <span class="block text-[10px] text-emerald-600 font-bold"><i class="fa-solid fa-circle-check"></i> Đã xác thực</span>
                            </div>
                            <i class="fa-solid fa-chevron-down text-slate-400 text-[10px] ml-1"></i>
                        </button>

                        <!-- Profile Dropdown Menu -->
                        <div class="absolute right-0 top-full mt-1.5 w-64 bg-white rounded-2xl shadow-xl border border-slate-100 p-2 hidden group-hover:block z-50 space-y-1">
                            <div class="p-3 bg-gradient-to-r from-sky-50 to-indigo-50 rounded-xl border border-sky-100 text-xs space-y-0.5">
                                <span class="font-extrabold text-slate-900 block text-sm">${currentUser.fullName}</span>
                                <span class="text-slate-500 text-[11px] block truncate">${currentUser.email}</span>
                                <span class="text-slate-500 text-[11px] block">SĐT: ${currentUser.phone || 'Chưa cập nhật'}</span>
                                <div class="pt-1 flex items-center justify-between text-[10px]">
                                    <span class="px-2 py-0.5 bg-emerald-100 text-emerald-800 font-bold rounded-full">${currentUser.role || 'Hành khách'}</span>
                                    <span class="text-slate-400 font-mono">${currentUser.id}</span>
                                </div>
                            </div>
                            <button onclick="switchTab('tickets-tab')" class="w-full text-left px-3 py-2 text-xs font-semibold text-slate-700 hover:bg-sky-50 hover:text-sky-700 rounded-lg transition flex items-center">
                                <i class="fa-solid fa-ticket text-sky-600 mr-2.5"></i> Vé điện tử của tôi
                            </button>
                            <button onclick="switchTab('history-tab')" class="w-full text-left px-3 py-2 text-xs font-semibold text-slate-700 hover:bg-sky-50 hover:text-sky-700 rounded-lg transition flex items-center">
                                <i class="fa-solid fa-clock-rotate-left text-sky-600 mr-2.5"></i> Lịch sử chuyến đi
                            </button>
                            <button onclick="openDatabaseManagerModal()" class="w-full text-left px-3 py-2 text-xs font-semibold text-slate-700 hover:bg-sky-50 hover:text-sky-700 rounded-lg transition flex items-center">
                                <i class="fa-solid fa-database text-purple-600 mr-2.5"></i> Cơ sở dữ liệu tài khoản
                            </button>
                            <div class="border-t border-slate-100 my-1"></div>
                            <button onclick="handleSignOut()" class="w-full text-left px-3 py-2 text-xs font-bold text-rose-600 hover:bg-rose-50 rounded-lg transition flex items-center">
                                <i class="fa-solid fa-right-from-bracket mr-2.5"></i> Đăng xuất tài khoản
                            </button>
                        </div>
                    </div>
                `;
            } else {
                container.innerHTML = `
                    <button onclick="openAuthModal('login')" class="px-4 py-2 rounded-xl text-xs font-bold text-white bg-sky-600 hover:bg-sky-700 shadow-md transition flex items-center">
                        <i class="fa-solid fa-user-lock mr-1.5"></i> Đăng nhập / Đăng ký
                    </button>
                `;
            }
        }

        window.handleSignOut = () => {
            currentUser = null;
            localStorage.removeItem(TauNhanhDB.sessionKey);
            renderAuthUI();
            Swal.fire({
                icon: 'info',
                title: 'Đã Đăng Xuất',
                text: 'Tài khoản của bạn đã được đăng xuất an toàn.',
                timer: 1500,
                showConfirmButton: false
            });
        };

        // =========================================================================
        // 9. DATABASE MANAGER MODAL FUNCTIONS
        // =========================================================================
        window.openDatabaseManagerModal = () => {
            renderDatabaseTable();
            document.getElementById('db-manager-modal').classList.remove('hidden');
        };

        window.closeDatabaseManagerModal = () => {
            document.getElementById('db-manager-modal').classList.add('hidden');
        };

        window.renderDatabaseTable = (filteredUsers = null) => {
            const tableBody = document.getElementById('db-users-table-body');
            const users = filteredUsers || TauNhanhDB.getAllUsers();
            tableBody.innerHTML = '';

            document.getElementById('db-total-count').textContent = users.length;
            TauNhanhDB.updateDbBadges();

            if (users.length === 0) {
                tableBody.innerHTML = `
                    <tr>
                        <td colspan="7" class="py-6 text-center text-slate-400">Không tìm thấy tài khoản nào trong cơ sở dữ liệu.</td>
                    </tr>
                `;
                return;
            }

            users.forEach(u => {
                const isCurrent = currentUser && currentUser.id === u.id;
                const tr = document.createElement('tr');
                tr.className = isCurrent ? "bg-sky-50/60 font-semibold" : "hover:bg-slate-50/70";
                tr.innerHTML = `
                    <td class="py-2.5 px-3 font-mono font-bold text-sky-700">
                        ${u.id} ${isCurrent ? '<span class="text-[9px] bg-sky-600 text-white px-1.5 py-0.2 rounded ml-1">Đang đăng nhập</span>' : ''}
                    </td>
                    <td class="py-2.5 px-3">
                        <div class="flex items-center space-x-2">
                            <div class="w-6 h-6 rounded-full bg-slate-200 text-slate-700 flex items-center justify-center font-bold text-[10px]">
                                ${u.fullName ? u.fullName.charAt(0).toUpperCase() : 'U'}
                            </div>
                            <span>${u.fullName}</span>
                        </div>
                    </td>
                    <td class="py-2.5 px-3">
                        <span class="block">${u.email}</span>
                        <span class="text-slate-400 text-[10px] block">${u.phone || 'N/A'}</span>
                    </td>
                    <td class="py-2.5 px-3 font-mono text-slate-600">
                        <span class="bg-slate-100 px-1.5 py-0.5 rounded border border-slate-200">${u.password}</span>
                    </td>
                    <td class="py-2.5 px-3">
                        ${u.isVerified 
                            ? '<span class="px-2 py-0.5 bg-emerald-100 text-emerald-800 text-[10px] font-bold rounded-full flex items-center w-fit"><i class="fa-solid fa-check-circle mr-1"></i> Đã xác thực OTP</span>' 
                            : '<span class="px-2 py-0.5 bg-amber-100 text-amber-800 text-[10px] font-bold rounded-full w-fit">Chưa xác thực</span>'}
                    </td>
                    <td class="py-2.5 px-3 text-slate-500 text-[10px]">${u.createdAt || 'N/A'}</td>
                    <td class="py-2.5 px-3 text-right space-x-1 whitespace-nowrap">
                        <button onclick="loginAsUserFromDb('${u.id}')" class="px-2.5 py-1 bg-sky-100 hover:bg-sky-200 text-sky-800 rounded-lg text-[11px] font-bold transition">
                            <i class="fa-solid fa-arrow-right-to-bracket mr-1"></i> Đăng nhập
                        </button>
                        <button onclick="deleteUserFromDb('${u.id}')" class="px-2 py-1 bg-rose-50 hover:bg-rose-100 text-rose-600 rounded-lg text-[11px] font-bold transition" title="Xóa khỏi Database">
                            <i class="fa-solid fa-trash"></i>
                        </button>
                    </td>
                `;
                tableBody.appendChild(tr);
            });
        };

        window.filterDatabaseTable = () => {
            const query = document.getElementById('db-search-input').value.toLowerCase().trim();
            const allUsers = TauNhanhDB.getAllUsers();
            if (!query) {
                renderDatabaseTable(allUsers);
                return;
            }
            const filtered = allUsers.filter(u => 
                (u.fullName && u.fullName.toLowerCase().includes(query)) ||
                (u.email && u.email.toLowerCase().includes(query)) ||
                (u.phone && u.phone.includes(query)) ||
                (u.id && u.id.toLowerCase().includes(query))
            );
            renderDatabaseTable(filtered);
        };

        window.loginAsUserFromDb = (userId) => {
            const users = TauNhanhDB.getAllUsers();
            const user = users.find(u => u.id === userId);
            if (!user) return;

            currentUser = user;
            localStorage.setItem(TauNhanhDB.sessionKey, JSON.stringify(currentUser));
            renderAuthUI();
            closeDatabaseManagerModal();

            Swal.fire({
                icon: 'success',
                title: 'Đã Chuyển Đổi Tài Khoản!',
                html: `Hiện đang đăng nhập với: <strong>${user.fullName}</strong> (${user.email}) từ Database.`,
                timer: 1800,
                showConfirmButton: false
            });
        };

        window.deleteUserFromDb = (userId) => {
            const users = TauNhanhDB.getAllUsers();
            const user = users.find(u => u.id === userId);
            if (!user) return;

            Swal.fire({
                title: `Xác nhận xóa tài khoản?`,
                html: `Bạn có chắc muốn xóa <strong>${user.fullName}</strong> (${user.email}) vĩnh viễn khỏi Database?`,
                icon: 'warning',
                showCancelButton: true,
                confirmButtonColor: '#e11d48',
                confirmButtonText: 'Đồng ý xóa',
                cancelButtonText: 'Hủy'
            }).then(res => {
                if (res.isConfirmed) {
                    TauNhanhDB.deleteUser(userId);
                    if (currentUser && currentUser.id === userId) {
                        currentUser = null;
                        localStorage.removeItem(TauNhanhDB.sessionKey);
                        renderAuthUI();
                    }
                    renderDatabaseTable();
                    Swal.fire('Đã xóa', 'Tài khoản đã được xóa khỏi cơ sở dữ liệu.', 'success');
                }
            });
        };

        window.exportDatabaseJSON = () => {
            const users = TauNhanhDB.getAllUsers();
            const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(users, null, 2));
            const dlAnchor = document.createElement('a');
            dlAnchor.setAttribute("href", dataStr);
            dlAnchor.setAttribute("download", `taunhanh_users_database_${Date.now()}.json`);
            dlAnchor.click();
            Swal.fire('Thành công', 'Đã tải xuống tệp sao lưu JSON của cơ sở dữ liệu tài khoản.', 'success');
        };

        window.resetDatabaseToDefault = () => {
            Swal.fire({
                title: 'Khôi phục Database gốc?',
                text: 'Hệ thống sẽ nạp lại 3 tài khoản mặc định và đặt lại dữ liệu.',
                icon: 'question',
                showCancelButton: true,
                confirmButtonColor: '#0284c7',
                confirmButtonText: 'Đồng ý'
            }).then(res => {
                if (res.isConfirmed) {
                    TauNhanhDB.resetToDefault();
                    renderDatabaseTable();
                    Swal.fire('Đã khôi phục', 'Cơ sở dữ liệu đã trở về trạng thái tiêu chuẩn.', 'success');
                }
            });
        };

        window.switchTab = (tabId) => {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            document.getElementById('seat-selection-view').classList.add('hidden');
            
            const targetEl = document.getElementById(tabId);
            if (targetEl) targetEl.classList.remove('hidden');

            if (tabId === 'tracker-tab') {
                updateLiveTracker();
                setTimeout(() => {
                    initRailwayMap();
                    if (activeLeafletMap) activeLeafletMap.invalidateSize();
                }, 200);
            }

            // Highlight nav
            const navMap = {
                'search-tab': 'nav-search',
                'tracker-tab': 'nav-tracker',
                'smart-notify-tab': 'nav-notify',
                'tickets-tab': 'nav-tickets',
                'history-tab': 'nav-history'
            };

            Object.entries(navMap).forEach(([tid, nid]) => {
                const btn = document.getElementById(nid);
                if (btn) {
                    if (tid === tabId) {
                        btn.className = "px-3.5 py-2 rounded-lg text-sm font-semibold text-sky-700 bg-sky-50 transition";
                    } else {
                        btn.className = "px-3.5 py-2 rounded-lg text-sm font-semibold text-slate-600 hover:text-sky-700 hover:bg-slate-50 transition";
                    }
                }
            });
        };

        function getTodayISOString() {
            return new Date().toISOString().split('T')[0];
        }

        function formatDateVN(dateStr) {
            if (!dateStr) return '';
            const [y, m, d] = dateStr.split('-');
            return `${d}/${m}/${y}`;
        }

        function triggerPushNotification() {
            setTimeout(() => {
                const toast = document.getElementById('notification-toast');
                toast.classList.remove('translate-y-24', 'opacity-0');
            }, 2500);
        }

        window.dismissToast = () => {
            const toast = document.getElementById('notification-toast');
            toast.classList.add('translate-y-24', 'opacity-0');
        };

        // =========================================================================
        // WINDOW INITIALIZATION
        // =========================================================================
        window.onload = function () {
            renderAuthUI();
            
            const today = getTodayISOString();
            document.getElementById('search-date').value = today;

            // Chạy Geolocation
            updateNearestStations();
            
            // Render giao diện tìm kiếm & đề xuất
            renderFlexibleDateBar(today);
            filterAndRenderTrains();

            // Kiểm tra lịch sử chuyến cũ để cá nhân hóa đề xuất
            checkPastTripsAndRecommend();
            renderMyTicketsUI();
            renderHistoryUI();

            // Khởi tạo Live Tracker
            updateLiveTracker();

            // Bật thông báo Toast
            triggerPushNotification();
        };
    </script>
</body>
</html>
