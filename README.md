<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تصميم لي</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700&display=swap');
        
        body {
            font-family: 'Tajawal', sans-serif;
        }
        
        .notification-badge {
            position: absolute;
            top: -5px;
            right: -5px;
            width: 18px;
            height: 18px;
            background-color: #ef4444;
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 10px;
        }
        
        .lecture-card {
            transition: all 0.3s ease;
        }
        
        .lecture-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
        
        .sidebar {
            transition: all 0.3s ease;
        }
        
        @media (max-width: 768px) {
            .sidebar {
                transform: translateX(100%);
                position: fixed;
                top: 0;
                right: 0;
                height: 100vh;
                z-index: 50;
            }
            
            .sidebar.open {
                transform: translateX(0);
            }
        }
        
        .overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 40;
        }
        
        .overlay.active {
            display: block;
        }
        
        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        
        ::-webkit-scrollbar-track {
            background: #f1f1f1;
        }
        
        ::-webkit-scrollbar-thumb {
            background: #888;
            border-radius: 4px;
        }
        
        ::-webkit-scrollbar-thumb:hover {
            background: #555;
        }
    </style>
</head>
<body class="bg-gray-50 text-gray-800">
    <!-- Overlay for mobile sidebar -->
    <div class="overlay" id="overlay"></div>
    
    <!-- Header -->
    <header class="bg-white shadow-sm sticky top-0 z-30">
        <div class="container mx-auto px-4 py-3 flex items-center justify-between">
            <div class="flex items-center space-x-2">
                <button id="sidebarToggle" class="md:hidden text-gray-600">
                    <i class="fas fa-bars text-xl"></i>
                </button>
                <h1 class="text-xl font-bold text-green-600">تصميم لي</h1>
            </div>
            
            <div class="flex items-center space-x-4">
                <button id="adminAccessBtn" class="text-gray-600 hover:text-green-600 md:hidden">
                    <i class="fas fa-lock text-xl"></i>
                </button>
                <div class="relative">
                    <button id="notificationsBtn" class="text-gray-600 hover:text-green-600">
                        <i class="far fa-bell text-xl"></i>
                        <span class="notification-badge">3</span>
                    </button>
                </div>
                <div class="hidden md:flex items-center space-x-2">
                    <img src="https://ui-avatars.com/api/?name=مصمم+محترف&background=4CAF50&color=fff" alt="User" class="w-8 h-8 rounded-full">
                    <span class="font-medium">مصمم محترف</span>
                </div>
            </div>
        </div>
    </header>
    
    <!-- Main Content -->
    <div class="flex">
        <!-- Sidebar -->
        <aside class="sidebar bg-white w-64 shadow-md md:shadow-none md:translate-x-0" id="sidebar">
            <div class="p-4">
                <div class="flex items-center space-x-3 mb-8">
                    <img src="https://ui-avatars.com/api/?name=مصمم+محترف&background=4CAF50&color=fff" alt="User" class="w-10 h-10 rounded-full">
                    <div>
                        <h3 class="font-bold">مصمم محترف</h3>
                        <span class="text-xs text-gray-500">مصمم جرافيك</span>
                    </div>
                </div>
                
                <nav>
                    <ul class="space-y-2">
                        <li>
                            <a href="#" class="nav-link flex items-center space-x-3 p-2 rounded-lg bg-green-50 text-green-600" data-section="home">
                                <i class="fas fa-home"></i>
                                <span>الصفحة الرئيسية</span>
                            </a>
                        </li>
                        <li>
                            <a href="#" class="nav-link flex items-center space-x-3 p-2 rounded-lg hover:bg-gray-100" data-section="services">
                                <i class="fas fa-palette"></i>
                                <span>الخدمات</span>
                            </a>
                        </li>
                        <li>
                            <a href="#" class="nav-link flex items-center space-x-3 p-2 rounded-lg hover:bg-gray-100" data-section="portfolio">
                                <i class="fas fa-images"></i>
                                <span>معرض الأعمال</span>
                            </a>
                        </li>
                        <li>
                            <a href="#" class="nav-link flex items-center space-x-3 p-2 rounded-lg hover:bg-gray-100" data-section="orders">
                                <i class="fas fa-shopping-cart"></i>
                                <span>طلباتي</span>
                            </a>
                        </li>
                        <li>
                            <a href="#" class="nav-link flex items-center space-x-3 p-2 rounded-lg hover:bg-gray-100" data-section="wallet">
                                <i class="fas fa-wallet"></i>
                                <span>المحفظة</span>
                            </a>
                        </li>
                        <li>
                            <a href="#" class="nav-link flex items-center space-x-3 p-2 rounded-lg hover:bg-gray-100" data-section="settings">
                                <i class="fas fa-cog"></i>
                                <span>الإعدادات</span>
                            </a>
                        </li>
                    </ul>
                </nav>
                
                <div class="mt-8">
                    <h4 class="font-bold mb-2 text-gray-600">الطلبات النشطة</h4>
                    <div class="space-y-2">
                        <div class="bg-blue-50 p-3 rounded-lg">
                            <p class="text-sm font-medium">تصميم بوست</p>
                            <p class="text-xs text-gray-500">قيد التنفيذ</p>
                        </div>
                        <div class="bg-purple-50 p-3 rounded-lg">
                            <p class="text-sm font-medium">تصميم ستوري</p>
                            <p class="text-xs text-gray-500">بانتظار الموافقة</p>
                        </div>
                    </div>
                </div>
            </div>
        </aside>
        
        <!-- Main Content Area -->
        <main class="flex-1 p-4 md:p-6">
            <!-- Welcome Section -->
            <div class="bg-gradient-to-r from-green-500 to-green-600 text-white p-6 rounded-xl mb-6">
                <h2 class="text-2xl font-bold mb-2">مرحباً بك في منصة تصميم لي</h2>
                <p class="mb-4">منصة رقمية عراقية متخصصة في التصاميم الجذابة للبوستات، الستوريات، الفيديو والإعلانات الممولة</p>
                <div class="flex flex-wrap gap-3">
                    <div class="bg-white bg-opacity-20 px-4 py-2 rounded-full flex items-center">
                        <i class="fas fa-user-graduate mr-2"></i>
                        <span>500+ عميل راضي</span>
                    </div>
                    <div class="bg-white bg-opacity-20 px-4 py-2 rounded-full flex items-center">
                        <i class="fas fa-book mr-2"></i>
                        <span>42 خدمة متاحة</span>
                    </div>
                    <div class="bg-white bg-opacity-20 px-4 py-2 rounded-full flex items-center">
                        <i class="fas fa-chalkboard-teacher mr-2"></i>
                        <span>6 مصممين محترفين</span>
                    </div>
                </div>
            </div>
            
            <!-- Services Section -->
            <div class="mb-8">
                <div class="flex items-center justify-between mb-4">
                    <h2 class="text-xl font-bold">خدماتنا</h2>
                    <a href="#" class="text-green-600 text-sm">عرض الكل</a>
                </div>
                
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                    <!-- Service 1 - Design Posts -->
                    <div class="lecture-card bg-white rounded-xl shadow-sm overflow-hidden border border-gray-100">
                        <div class="p-4">
                            <div class="bg-green-100 text-green-600 w-12 h-12 rounded-full flex items-center justify-center mb-3">
                                <i class="fas fa-image text-xl"></i>
                            </div>
                            <h3 class="font-bold mb-1">تصميم بوستات</h3>
                            <p class="text-gray-500 text-sm mb-3">تصاميم احترافية لمواقع التواصل الاجتماعي</p>
                            <div class="flex justify-between items-center">
                                <span class="text-sm font-medium text-green-600">3,000 - 5,000 د.ع</span>
                                <button class="order-btn bg-green-600 hover:bg-green-700 text-white px-3 py-1 rounded-full text-sm flex items-center" data-service="تصميم بوست" data-price="4000">
                                    <i class="fas fa-shopping-cart mr-1"></i>
                                    <span>اطلب الآن</span>
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Service 2 - Design Stories -->
                    <div class="lecture-card bg-white rounded-xl shadow-sm overflow-hidden border border-gray-100">
                        <div class="p-4">
                            <div class="bg-blue-100 text-blue-600 w-12 h-12 rounded-full flex items-center justify-center mb-3">
                                <i class="fas fa-mobile-alt text-xl"></i>
                            </div>
                            <h3 class="font-bold mb-1">تصميم ستوريات</h3>
                            <p class="text-gray-500 text-sm mb-3">تصاميم مخصصة لقصص إنستغرام وفيسبوك</p>
                            <div class="flex justify-between items-center">
                                <span class="text-sm font-medium text-green-600">2,000 - 4,000 د.ع</span>
                                <button class="order-btn bg-green-600 hover:bg-green-700 text-white px-3 py-1 rounded-full text-sm flex items-center" data-service="تصميم ستوري" data-price="3000">
                                    <i class="fas fa-shopping-cart mr-1"></i>
                                    <span>اطلب الآن</span>
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Service 3 - Video Editing -->
                    <div class="lecture-card bg-white rounded-xl shadow-sm overflow-hidden border border-gray-100">
                        <div class="p-4">
                            <div class="bg-purple-100 text-purple-600 w-12 h-12 rounded-full flex items-center justify-center mb-3">
                                <i class="fas fa-video text-xl"></i>
                            </div>
                            <h3 class="font-bold mb-1">مونتاج فيديو</h3>
                            <p class="text-gray-500 text-sm mb-3">مونتاج احترافي لفيديوهات الريلز والتيك توك</p>
                            <div class="flex justify-between items-center">
                                <span class="text-sm font-medium text-green-600">8,000 - 15,000 د.ع</span>
                                <button class="order-btn bg-green-600 hover:bg-green-700 text-white px-3 py-1 rounded-full text-sm flex items-center" data-service="مونتاج فيديو" data-price="12000">
                                    <i class="fas fa-shopping-cart mr-1"></i>
                                    <span>اطلب الآن</span>
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Portfolio Gallery -->
            <div class="mb-8">
                <div class="flex items-center justify-between mb-4">
                    <h2 class="text-xl font-bold">معرض الأعمال</h2>
                    <a href="#" class="text-green-600 text-sm">عرض الكل</a>
                </div>
                
                <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
                    <div class="portfolio-item">
                        <img src="https://images.unsplash.com/photo-1611162617474-5b21e879e113?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="Design 1" class="w-full h-48 object-cover rounded-lg">
                        <p class="text-center mt-2 font-medium">تصميم بوست</p>
                    </div>
                    <div class="portfolio-item">
                        <img src="https://images.unsplash.com/photo-1616469829479-1be7207f0e19?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="Design 2" class="w-full h-48 object-cover rounded-lg">
                        <p class="text-center mt-2 font-medium">تصميم ستوري</p>
                    </div>
                    <div class="portfolio-item">
                        <img src="https://images.unsplash.com/photo-1573167101669-476636b96b8a?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="Design 3" class="w-full h-48 object-cover rounded-lg">
                        <p class="text-center mt-2 font-medium">مونتاج فيديو</p>
                    </div>
                    <div class="portfolio-item">
                        <img src="https://images.unsplash.com/photo-1607082348824-0a96f2a4b9da?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="Design 4" class="w-full h-48 object-cover rounded-lg">
                        <p class="text-center mt-2 font-medium">تصميم إعلان</p>
                    </div>
                </div>
            </div>
            
            <!-- Wallet Section -->
            <div class="mb-8">
                <h2 class="text-xl font-bold mb-4">محفظتي</h2>
                <div class="bg-white rounded-xl shadow-sm p-6">
                    <div class="flex items-center justify-between mb-4">
                        <h3 class="font-medium">الرصيد الحالي</h3>
                        <span id="walletBalance" class="text-2xl font-bold text-green-600">25,000 د.ع</span>
                    </div>
                    
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                        <button id="rechargeBtn" class="bg-green-100 text-green-600 hover:bg-green-200 p-4 rounded-lg flex flex-col items-center">
                            <i class="fas fa-plus-circle text-2xl mb-2"></i>
                            <span>شحن المحفظة</span>
                        </button>
                        
                        <button id="transactionsBtn" class="bg-blue-100 text-blue-600 hover:bg-blue-200 p-4 rounded-lg flex flex-col items-center">
                            <i class="fas fa-exchange-alt text-2xl mb-2"></i>
                            <span>سجل المعاملات</span>
                        </button>
                        
                        <button id="paymentMethodsBtn" class="bg-purple-100 text-purple-600 hover:bg-purple-200 p-4 rounded-lg flex flex-col items-center">
                            <i class="fas fa-qrcode text-2xl mb-2"></i>
                            <span>طرق الدفع</span>
                        </button>
                    </div>
                </div>
            </div>
        </main>
    </div>
    
    <!-- Admin Panel (Hidden by default) -->
    <div class="fixed inset-0 bg-gray-100 z-50 hidden" id="adminPanel">
        <div class="h-full flex flex-col">
            <!-- Admin Header -->
            <header class="bg-green-700 text-white shadow-sm">
                <div class="container mx-auto px-4 py-3 flex items-center justify-between">
                    <div class="flex items-center space-x-2">
                        <h1 class="text-xl font-bold">لوحة تحكم تصميم لي</h1>
                    </div>
                    
                    <div class="flex items-center space-x-4">
                        <button id="logoutAdmin" class="bg-white text-green-700 hover:bg-gray-100 px-3 py-1 rounded-md text-sm font-medium">
                            تسجيل الخروج
                        </button>
                    </div>
                </div>
            </header>
            
            <!-- Admin Content -->
            <div class="flex flex-1 overflow-hidden">
                <!-- Admin Sidebar -->
                <aside class="bg-white w-64 border-l border-gray-200 overflow-y-auto">
                    <div class="p-4">
                        <div class="flex items-center space-x-3 mb-8">
                            <img src="https://ui-avatars.com/api/?name=مسؤول+النظام&background=fff&color=4CAF50" alt="Admin" class="w-10 h-10 rounded-full border-2 border-green-500">
                            <div>
                                <h3 class="font-bold">مسؤول النظام</h3>
                                <span class="text-xs text-gray-500">مدير المنصة</span>
                            </div>
                        </div>
                        
                        <nav>
                            <ul class="space-y-2">
                                <li>
                                    <a href="#" class="admin-nav-item active" data-section="dashboard">
                                        <i class="fas fa-tachometer-alt"></i>
                                        <span>لوحة التحكم</span>
                                    </a>
                                </li>
                                <li>
                                    <a href="#" class="admin-nav-item" data-section="orders">
                                        <i class="fas fa-shopping-cart"></i>
                                        <span>إدارة الطلبات</span>
                                    </a>
                                </li>
                                <li>
                                    <a href="#" class="admin-nav-item" data-section="designers">
                                        <i class="fas fa-users"></i>
                                        <span>إدارة المصممين</span>
                                    </a>
                                </li>
                                <li>
                                    <a href="#" class="admin-nav-item" data-section="wallet">
                                        <i class="fas fa-wallet"></i>
                                        <span>إدارة المحفظة</span>
                                    </a>
                                </li>
                                <li>
                                    <a href="#" class="admin-nav-item" data-section="portfolio">
                                        <i class="fas fa-images"></i>
                                        <span>معرض الأعمال</span>
                                    </a>
                                </li>
                            </ul>
                        </nav>
                    </div>
                </aside>
                
                <!-- Admin Main Content -->
                <main class="flex-1 overflow-y-auto p-6">
                    <div id="adminDashboardSection">
                        <h2 class="text-2xl font-bold mb-6">نظرة عامة</h2>
                    
                    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
                        <!-- Stats Card 1 -->
                        <div class="bg-white rounded-xl shadow-sm p-6 border border-gray-100">
                            <div class="flex items-center justify-between">
                                <div>
                                    <p class="text-gray-500 text-sm">إجمالي الطلبات</p>
                                    <h3 class="text-2xl font-bold mt-1">42</h3>
                                </div>
                                <div class="bg-green-100 text-green-600 p-3 rounded-full">
                                    <i class="fas fa-shopping-cart text-xl"></i>
                                </div>
                            </div>
                        </div>
                        
                        <!-- Stats Card 2 -->
                        <div class="bg-white rounded-xl shadow-sm p-6 border border-gray-100">
                            <div class="flex items-center justify-between">
                                <div>
                                    <p class="text-gray-500 text-sm">المصممين النشطين</p>
                                    <h3 class="text-2xl font-bold mt-1">6</h3>
                                </div>
                                <div class="bg-blue-100 text-blue-600 p-3 rounded-full">
                                    <i class="fas fa-users text-xl"></i>
                                </div>
                            </div>
                        </div>
                        
                        <!-- Stats Card 3 -->
                        <div class="bg-white rounded-xl shadow-sm p-6 border border-gray-100">
                            <div class="flex items-center justify-between">
                                <div>
                                    <p class="text-gray-500 text-sm">إجمالي الإيرادات</p>
                                    <h3 class="text-2xl font-bold mt-1">250,000 د.ع</h3>
                                </div>
                                <div class="bg-purple-100 text-purple-600 p-3 rounded-full">
                                    <i class="fas fa-money-bill-wave text-xl"></i>
                                </div>
                            </div>
                        </div>
                        
                        <!-- Stats Card 4 -->
                        <div class="bg-white rounded-xl shadow-sm p-6 border border-gray-100">
                            <div class="flex items-center justify-between">
                                <div>
                                    <p class="text-gray-500 text-sm">طلبات قيد التنفيذ</p>
                                    <h3 class="text-2xl font-bold mt-1">8</h3>
                                </div>
                                <div class="bg-yellow-100 text-yellow-600 p-3 rounded-full">
                                    <i class="fas fa-tasks text-xl"></i>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Recent Orders -->
                    <div>
                        <h3 class="text-xl font-bold mb-4">أحدث الطلبات</h3>
                        <div class="bg-white rounded-xl shadow-sm overflow-hidden border border-gray-100">
                            <div class="overflow-x-auto">
                                <table class="min-w-full divide-y divide-gray-200">
                                    <thead class="bg-gray-50">
                                        <tr>
                                            <th class="px-6 py-3 text-right text-xs font-medium text-gray-500 uppercase tracking-wider">العميل</th>
                                            <th class="px-6 py-3 text-right text-xs font-medium text-gray-500 uppercase tracking-wider">الخدمة</th>
                                            <th class="px-6 py-3 text-right text-xs font-medium text-gray-500 uppercase tracking-wider">الحالة</th>
                                            <th class="px-6 py-3 text-right text-xs font-medium text-gray-500 uppercase tracking-wider">المبلغ</th>
                                        </tr>
                                    </thead>
                                    <tbody class="bg-white divide-y divide-gray-200">
                                        <tr>
                                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">علي حسن</td>
                                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">تصميم بوست</td>
                                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500"><span class="bg-green-100 text-green-800 px-2 py-1 rounded-full text-xs">مكتمل</span></td>
                                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">5,000 د.ع</td>
                                        </tr>
                                        <tr>
                                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">ليلى أحمد</td>
                                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">تصميم ستوري</td>
                                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500"><span class="bg-yellow-100 text-yellow-800 px-2 py-1 rounded-full text-xs">قيد التنفيذ</span></td>
                                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">3,500 د.ع</td>
                                        </tr>
                                        <tr>
                                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">محمد كريم</td>
                                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">مونتاج فيديو</td>
                                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500"><span class="bg-blue-100 text-blue-800 px-2 py-1 rounded-full text-xs">جديد</span></td>
                                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">12,000 د.ع</td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </main>
            </div>
        </div>
    </div>
    
    <!-- Admin Access Button (Hidden in the corner) -->
    <button id="adminAccessBtn" class="fixed bottom-4 left-4 bg-green-600 text-white p-3 rounded-full shadow-lg hover:bg-green-700 z-40">
        <i class="fas fa-lock"></i>
    </button>
    
    <!-- Order Modal -->
    <div id="orderModal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 hidden">
        <div class="bg-white rounded-lg p-6 w-full max-w-md">
            <div class="flex justify-between items-center mb-4">
                <h3 class="text-lg font-bold" id="modalTitle">طلب تصميم</h3>
                <button id="closeOrderModal" class="text-gray-500 hover:text-gray-700">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <form id="orderForm">
                <input type="hidden" id="serviceType">
                <input type="hidden" id="servicePrice">
                
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-1">تفاصيل الطلب</label>
                    <textarea id="orderDetails" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-green-500" rows="3" required></textarea>
                </div>
                
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-1">المرفقات (اختياري)</label>
                    <input type="file" class="w-full">
                </div>
                
                <button type="submit" class="w-full bg-green-600 hover:bg-green-700 text-white py-2 px-4 rounded-md font-medium">
                    تأكيد الطلب - <span id="orderPrice"></span> د.ع
                </button>
            </form>
        </div>
    </div>

    <!-- WhatsApp Contact Button -->
    <a href="https://wa.me/07818843499" target="_blank" class="fixed bottom-4 right-4 bg-green-600 text-white p-3 rounded-full shadow-lg hover:bg-green-700 z-40">
        <i class="fab fa-whatsapp text-2xl"></i>
    </a>

    <script>
        // Mobile sidebar toggle
        const sidebarToggle = document.getElementById('sidebarToggle');
        const sidebar = document.getElementById('sidebar');
        const overlay = document.getElementById('overlay');
        
        sidebarToggle.addEventListener('click', () => {
            sidebar.classList.toggle('open');
            overlay.classList.toggle('active');
        });
        
        overlay.addEventListener('click', () => {
            sidebar.classList.remove('open');
            overlay.classList.remove('active');
        });

        // Admin access functionality
        const adminAccessBtn = document.getElementById('adminAccessBtn');
        const adminPanel = document.getElementById('adminPanel');
        const logoutAdmin = document.getElementById('logoutAdmin');
        
        adminAccessBtn.addEventListener('click', () => {
            adminPanel.classList.remove('hidden');
        });
        
        logoutAdmin.addEventListener('click', () => {
            adminPanel.classList.add('hidden');
        });

        // Section switching functionality
        const sections = {
            home: document.querySelector('main'),
            services: createSection('الخدمات', 'services-content'),
            portfolio: createSection('معرض الأعمال', 'portfolio-content'),
            orders: createSection('طلباتي', 'orders-content'),
            wallet: createSection('المحفظة', 'wallet-content'),
            settings: createSection('الإعدادات', 'settings-content')
        };

        function createSection(title, id) {
            const section = document.createElement('div');
            section.id = id;
            section.className = 'p-4 md:p-6';
            section.innerHTML = `
                <h2 class="text-2xl font-bold mb-6">${title}</h2>
                <p>هذا قسم ${title}. سيتم عرض المحتوى هنا عند اكتمال التطبيق.</p>
            `;
            return section;
        }

        document.querySelectorAll('.nav-link').forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                const sectionId = link.getAttribute('data-section');
                
                // Update active link
                document.querySelectorAll('.nav-link').forEach(l => {
                    l.classList.remove('bg-green-50', 'text-green-600');
                    l.classList.add('hover:bg-gray-100');
                });
                link.classList.add('bg-green-50', 'text-green-600');
                link.classList.remove('hover:bg-gray-100');
                
                // Show selected section
                const main = document.querySelector('main');
                main.innerHTML = '';
                main.appendChild(sections[sectionId]);
                
                // Close mobile sidebar if open
                sidebar.classList.remove('open');
                overlay.classList.remove('active');
            });
        });

        // Order functionality
        const orderModal = document.getElementById('orderModal');
        const modalTitle = document.getElementById('modalTitle');
        const orderPrice = document.getElementById('orderPrice');
        const serviceTypeInput = document.getElementById('serviceType');
        const servicePriceInput = document.getElementById('servicePrice');
        const closeOrderModal = document.getElementById('closeOrderModal');
        
        document.querySelectorAll('.order-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                const service = btn.getAttribute('data-service');
                const price = btn.getAttribute('data-price');
                
                modalTitle.textContent = `طلب ${service}`;
                orderPrice.textContent = price;
                serviceTypeInput.value = service;
                servicePriceInput.value = price;
                
                orderModal.classList.remove('hidden');
            });
        });
        
        closeOrderModal.addEventListener('click', () => {
            orderModal.classList.add('hidden');
        });
        
        document.getElementById('orderForm').addEventListener('submit', (e) => {
            e.preventDefault();
            alert('تم تقديم طلبك بنجاح! سيتم التواصل معك قريباً.');
            orderModal.classList.add('hidden');
        });

        // Wallet functionality
        const walletBalance = document.getElementById('walletBalance');
        const rechargeBtn = document.getElementById('rechargeBtn');
        const transactionsBtn = document.getElementById('transactionsBtn');
        const paymentMethodsBtn = document.getElementById('paymentMethodsBtn');
        
        rechargeBtn.addEventListener('click', () => {
            const amount = prompt('أدخل المبلغ المطلوب شحنه:');
            if (amount && !isNaN(amount)) {
                const currentBalance = parseInt(walletBalance.textContent.replace(/\D/g,''));
                const newBalance = currentBalance + parseInt(amount);
                walletBalance.textContent = newBalance.toLocaleString() + ' د.ع';
                alert(`تم شحن ${amount} دينار بنجاح!`);
            }
        });
        
        transactionsBtn.addEventListener('click', () => {
            alert('سجل المعاملات:\n\n1. +25,000 د.ع - شحن محفظة\n2. -5,000 د.ع - طلب تصميم بوست');
        });
        
        paymentMethodsBtn.addEventListener('click', () => {
            alert('طرق الدفع المتاحة:\n\n1. زين كاش\n2. آسيا كاش\n3. ماستر كارد\n4. كارت رصيد');
        });

        // Admin navigation
        document.querySelectorAll('.admin-nav-item').forEach(item => {
            item.addEventListener('click', (e) => {
                e.preventDefault();
                const section = item.getAttribute('data-section');
                alert(`فتح قسم ${section} في لوحة التحكم`);
            });
        });
    </script>
</body>
</html>
