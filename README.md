
<!DOCTYPE html>
<html dir="rtl" lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مشروع الوعي الثقافي للحجاج والمعتمرين</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY=" crossorigin=""/>
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js" integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo=" crossorigin=""></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700&display=swap');
        body {
            font-family: 'Tajawal', sans-serif;
        }
        .copy-btn {
            transition: all 0.3s ease;
            position: relative; /* Needed for the pseudo-element */
        }
        .copy-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }
        .copy-btn:active {
            transform: translateY(0);
            box-shadow: 0 1px 2px rgba(0,0,0,0.1);
        }
        .copied::after {
            content: "تم النسخ!";
            position: absolute;
            bottom: 110%; /* Position above the button */
            left: 50%;
            transform: translateX(-50%);
            background-color: #4CAF50;
            color: white;
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 12px;
            white-space: nowrap;
            opacity: 0;
            animation: fadeInOut 1.5s ease-in-out;
            z-index: 10;
        }
        @keyframes fadeInOut {
            0%, 100% { opacity: 0; transform: translateX(-50%) translateY(5px); }
            10%, 90% { opacity: 1; transform: translateX(-50%) translateY(0); }
        }
        #demo-map {
            height: 350px; /* Increased height */
            width: 100%;
            border-radius: 0.75rem; /* Slightly larger radius */
            border: 1px solid #e5e7eb; /* Added subtle border */
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }
        .leaflet-popup-content-wrapper {
             border-radius: 8px !important;
        }
        .leaflet-popup-content {
             font-family: 'Tajawal', sans-serif !important;
             font-size: 13px !important;
             line-height: 1.6 !important;
        }
    </style>
</head>
<body class="bg-gray-100">
    <div class="container mx-auto px-4 py-10 max-w-7xl">
        <header class="text-center mb-10">
            <div class="bg-gradient-to-r from-green-700 to-green-500 rounded-xl shadow-lg p-8 text-white">
                 <div class="flex justify-center items-center mb-4 gap-4">
                     <img src="/api/placeholder/80/80" alt="شعار جامعة الملك عبد العزيز" class="h-16 bg-white p-1 rounded-full">
                     <img src="/api/placeholder/80/80" alt="شعار كلية السياحة" class="h-16 bg-white p-1 rounded-full">
                 </div>
                <h1 class="text-4xl font-bold mb-3">دور الذكاء الاصطناعي ونظم المعلومات الجغرافية</h1>
                <h2 class="text-2xl font-light mb-5">في تعزيز الوعي الثقافي لدى الحجاج والمعتمرين</h2>
                <p class="text-green-100 max-w-4xl mx-auto text-lg">منصة مركزية للمشروع البحثي تجمع كافة المكونات التفاعلية والمحتوى الداعم لتحسين تجربة ضيوف الرحمن</p>
                <div class="mt-6 text-sm flex flex-wrap justify-center items-center gap-3">
                    <span class="bg-white text-green-800 px-4 py-1 rounded-full font-medium shadow">جامعة الملك عبد العزيز</span>
                    <span class="bg-white text-green-800 px-4 py-1 rounded-full font-medium shadow">كلية السياحة</span>
                    <span class="bg-white text-green-800 px-4 py-1 rounded-full font-medium shadow">قسم إدارة الضيافة</span>
                    <span class="bg-white text-green-800 px-4 py-1 rounded-full font-medium shadow">ماجستير إدارة خدمات الحج والعمرة</span>
                </div>
            </div>
        </header>

        <!-- قسم معاينة الخريطة التفاعلية -->
        <section class="mb-10 bg-white rounded-xl shadow-md p-6">
            <h2 class="text-2xl font-bold text-gray-800 mb-5 text-center border-b pb-3 border-gray-200">معاينة الخريطة التفاعلية للمواقع التراثية</h2>
            <div id="demo-map" class="mb-4"></div>
            <p class="text-center text-gray-600">خريطة توضيحية باستخدام Leaflet للمواقع التراثية الهامة وتوسعات المسجد الحرام.</p>
        </section>

        <main class="mb-10">
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- 1. العرض التقديمي الرئيسي -->
                <div class="bg-white rounded-xl shadow-md overflow-hidden flex flex-col transform transition duration-300 hover:scale-105 hover:shadow-lg">
                    <div class="h-48 bg-gradient-to-br from-green-500 to-teal-500 flex items-center justify-center p-4">
                        <div class="text-white text-center">
                            <span class="text-6xl font-bold block mb-2 opacity-80">1</span>
                            <h3 class="text-xl font-semibold">العرض التقديمي الرئيسي</h3>
                            <p class="text-sm text-green-100">Google Slides</p>
                        </div>
                    </div>
                    <div class="p-6 flex-grow flex flex-col justify-between">
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2" for="presentation-link">رابط العرض:</label>
                            <div class="flex mb-4">
                                <input id="presentation-link" class="shadow-inner appearance-none border rounded-r-lg w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-green-300 focus:border-transparent text-sm" type="text" placeholder="أضف رابط Google Slides هنا">
                                <a href="https://docs.google.com/presentation/" target="_blank" title="فتح Google Slides لإنشاء العرض" class="bg-green-600 hover:bg-green-700 text-white font-bold py-2 px-4 rounded-l-lg transition duration-300 flex items-center justify-center">
                                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14" /></svg>
                                </a>
                            </div>
                        </div>
                        <button id="copy-presentation" class="copy-btn w-full bg-gray-200 hover:bg-gray-300 text-gray-800 font-bold py-2 px-4 rounded transition duration-300 flex items-center justify-center text-sm">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 5H6a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2v-1M8 5a2 2 0 002 2h2a2 2 0 002-2M8 5a2 2 0 012-2h2a2 2 0 012 2m0 0h2a2 2 0 012 2v3m2 4H10m0 0l3-3m-3 3l3 3" /></svg>
                            نسخ محتوى العرض
                        </button>
                    </div>
                </div>

                <!-- 2. نموذج التطبيق الذكي -->
                <div class="bg-white rounded-xl shadow-md overflow-hidden flex flex-col transform transition duration-300 hover:scale-105 hover:shadow-lg">
                    <div class="h-48 bg-gradient-to-br from-blue-500 to-cyan-500 flex items-center justify-center p-4">
                         <div class="text-white text-center">
                             <span class="text-6xl font-bold block mb-2 opacity-80">2</span>
                             <h3 class="text-xl font-semibold">نموذج التطبيق الذكي</h3>
                             <p class="text-sm text-blue-100">CodePen (React)</p>
                        </div>
                    </div>
                    <div class="p-6 flex-grow flex flex-col justify-between">
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2" for="app-link">رابط التطبيق:</label>
                            <div class="flex mb-4">
                                <input id="app-link" class="shadow-inner appearance-none border rounded-r-lg w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-blue-300 focus:border-transparent text-sm" type="text" placeholder="أضف رابط CodePen هنا">
                                <a href="https://codepen.io/pen/" target="_blank" title="فتح CodePen لإنشاء التطبيق" class="bg-blue-600 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-l-lg transition duration-300 flex items-center justify-center">
                                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14" /></svg>
                                </a>
                            </div>
                        </div>
                        <button id="copy-app" class="copy-btn w-full bg-gray-200 hover:bg-gray-300 text-gray-800 font-bold py-2 px-4 rounded transition duration-300 flex items-center justify-center text-sm">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4" /></svg>
                            نسخ كود التطبيق (React)
                        </button>
                    </div>
                </div>

                 <!-- 3. خريطة توزيع الحجاج (الجنسيات) -->
                <div class="bg-white rounded-xl shadow-md overflow-hidden flex flex-col transform transition duration-300 hover:scale-105 hover:shadow-lg">
                    <div class="h-48 bg-gradient-to-br from-yellow-400 to-orange-500 flex items-center justify-center p-4">
                         <div class="text-white text-center">
                             <span class="text-6xl font-bold block mb-2 opacity-80">3</span>
                             <h3 class="text-xl font-semibold">خريطة توزيع الحجاج (الجنسيات)</h3>
                             <p class="text-sm text-yellow-100">JSFiddle (Chart.js)</p>
                        </div>
                    </div>
                    <div class="p-6 flex-grow flex flex-col justify-between">
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2" for="nationality-map-link">رابط الخريطة:</label>
                            <div class="flex mb-4">
                                <input id="nationality-map-link" class="shadow-inner appearance-none border rounded-r-lg w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-yellow-300 focus:border-transparent text-sm" type="text" placeholder="أضف رابط JSFiddle هنا">
                                <a href="https://jsfiddle.net/" target="_blank" title="فتح JSFiddle لإنشاء الخريطة" class="bg-yellow-500 hover:bg-yellow-600 text-white font-bold py-2 px-4 rounded-l-lg transition duration-300 flex items-center justify-center">
                                     <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14" /></svg>
                                </a>
                            </div>
                        </div>
                        <button id="copy-nationality-map" class="copy-btn w-full bg-gray-200 hover:bg-gray-300 text-gray-800 font-bold py-2 px-4 rounded transition duration-300 flex items-center justify-center text-sm">
                           <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" /></svg>
                            نسخ كود خريطة الجنسيات
                        </button>
                    </div>
                </div>

                <!-- 4. خريطة توزيع الحجاج (اللغات) -->
                 <div class="bg-white rounded-xl shadow-md overflow-hidden flex flex-col transform transition duration-300 hover:scale-105 hover:shadow-lg">
                    <div class="h-48 bg-gradient-to-br from-purple-500 to-pink-500 flex items-center justify-center p-4">
                         <div class="text-white text-center">
                             <span class="text-6xl font-bold block mb-2 opacity-80">4</span>
                             <h3 class="text-xl font-semibold">خريطة توزيع الحجاج (اللغات)</h3>
                             <p class="text-sm text-purple-100">CodeSandbox (Chart.js)</p>
                        </div>
                    </div>
                    <div class="p-6 flex-grow flex flex-col justify-between">
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2" for="language-map-link">رابط الخريطة:</label>
                            <div class="flex mb-4">
                                <input id="language-map-link" class="shadow-inner appearance-none border rounded-r-lg w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-purple-300 focus:border-transparent text-sm" type="text" placeholder="أضف رابط CodeSandbox هنا">
                                <a href="https://codesandbox.io/s/" target="_blank" title="فتح CodeSandbox لإنشاء الخريطة" class="bg-purple-600 hover:bg-purple-700 text-white font-bold py-2 px-4 rounded-l-lg transition duration-300 flex items-center justify-center">
                                     <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14" /></svg>
                                </a>
                            </div>
                        </div>
                        <button id="copy-language-map" class="copy-btn w-full bg-gray-200 hover:bg-gray-300 text-gray-800 font-bold py-2 px-4 rounded transition duration-300 flex items-center justify-center text-sm">
                           <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" /></svg>
                            نسخ كود خريطة اللغات
                        </button>
                    </div>
                </div>

                 <!-- 5. تصميم تفاعلي للتطبيق -->
                 <div class="bg-white rounded-xl shadow-md overflow-hidden flex flex-col transform transition duration-300 hover:scale-105 hover:shadow-lg">
                    <div class="h-48 bg-gradient-to-br from-red-500 to-pink-600 flex items-center justify-center p-4">
                         <div class="text-white text-center">
                             <span class="text-6xl font-bold block mb-2 opacity-80">5</span>
                             <h3 class="text-xl font-semibold">تصميم تفاعلي للتطبيق</h3>
                             <p class="text-sm text-red-100">Figma</p>
                        </div>
                    </div>
                    <div class="p-6 flex-grow flex flex-col justify-between">
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2" for="figma-link">رابط التصميم:</label>
                            <div class="flex mb-4">
                                <input id="figma-link" class="shadow-inner appearance-none border rounded-r-lg w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-red-300 focus:border-transparent text-sm" type="text" placeholder="أضف رابط Figma هنا">
                                <a href="https://www.figma.com/" target="_blank" title="فتح Figma لإنشاء التصميم" class="bg-red-600 hover:bg-red-700 text-white font-bold py-2 px-4 rounded-l-lg transition duration-300 flex items-center justify-center">
                                     <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14" /></svg>
                                </a>
                            </div>
                        </div>
                         <button id="copy-figma" class="copy-btn w-full bg-gray-200 hover:bg-gray-300 text-gray-800 font-bold py-2 px-4 rounded transition duration-300 flex items-center justify-center text-sm">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M4 3a2 2 0 00-2 2v10a2 2 0 002 2h12a2 2 0 002-2V5a2 2 0 00-2-2H4zm3 2h6v4H7V5zm8 6H5v2h10v-2z" clip-rule="evenodd" /></svg>
                            نسخ مكونات التصميم
                        </button>
                    </div>
                </div>

                <!-- 6. خريطة المواقع التراثية (الكاملة) -->
                <div class="bg-white rounded-xl shadow-md overflow-hidden flex flex-col transform transition duration-300 hover:scale-105 hover:shadow-lg">
                    <div class="h-48 bg-gradient-to-br from-indigo-500 to-purple-600 flex items-center justify-center p-4">
                         <div class="text-white text-center">
                             <span class="text-6xl font-bold block mb-2 opacity-80">6</span>
                             <h3 class="text-xl font-semibold">خريطة المواقع التراثية</h3>
                             <p class="text-sm text-indigo-100">Replit (HTML/Leaflet)</p>
                        </div>
                    </div>
                    <div class="p-6 flex-grow flex flex-col justify-between">
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2" for="heritage-map-link">رابط الخريطة:</label>
                            <div class="flex mb-4">
                                <input id="heritage-map-link" class="shadow-inner appearance-none border rounded-r-lg w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-indigo-300 focus:border-transparent text-sm" type="text" placeholder="أضف رابط Replit هنا">
                                <a href="https://replit.com/new/html" target="_blank" title="فتح Replit لإنشاء الخريطة" class="bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-2 px-4 rounded-l-lg transition duration-300 flex items-center justify-center">
                                     <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14" /></svg>
                                </a>
                            </div>
                        </div>
                        <button id="copy-heritage-map" class="copy-btn w-full bg-gray-200 hover:bg-gray-300 text-gray-800 font-bold py-2 px-4 rounded transition duration-300 flex items-center justify-center text-sm">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M12 7a1 1 0 110-2h5a1 1 0 011 1v5a1 1 0 11-2 0V8.414l-4.293 4.293a1 1 0 01-1.414 0L8 10.414l-4.293 4.293a1 1 0 01-1.414-1.414l5-5a1 1 0 011.414 0L12 11.586l3.293-3.293A1 1 0 0116 8h-4zm-4 7a1 1 0 011-1h5a1 1 0 110 2H9a1 1 0 01-1-1z" clip-rule="evenodd" /></svg>
                            نسخ كود خريطة التراث
                        </button>
                    </div>
                </div>
            </div>
        </main>

        <!-- قسم تعليمات الاستخدام -->
        <section class="bg-white rounded-xl shadow-md p-6 mb-10">
            <h2 class="text-2xl font-bold text-gray-800 mb-4 border-b pb-2">تعليمات الاستخدام</h2>
            <ol class="list-decimal list-inside space-y-3 text-gray-700">
                <li>انقر على أيقونة <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 inline -mt-1" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14" /></svg> بجانب حقل الرابط للانتقال إلى المنصة المناسبة (Google Slides, CodePen, etc.).</li>
                <li>استخدم زر "نسخ ..." أسفل كل قسم للحصول على المحتوى أو الكود المطلوب للصقه في المنصة.</li>
                <li>بعد إنشاء كل جزء (العرض، التطبيق، الخرائط) على منصته، انسخ الرابط الذي توفره المنصة والصقه في الحقل المخصص له في هذه الصفحة.</li>
                <li>**للحصول على الرابط النهائي لهذه الصفحة:** اتبع خطوات الاستضافة على GitHub Pages المذكورة سابقًا (احفظ هذا الملف كـ `index.html` وارفع للمستودع).</li>
                <li>الرابط الذي ستحصل عليه من GitHub Pages هو الرابط الوحيد الذي يمكنك مشاركته وسيحتوي على كل هذه المكونات والروابط الأخرى.</li>
            </ol>
        </section>

        <!-- قسم الأكواد المساعدة -->
        <section class="bg-white rounded-xl shadow-md p-6 mb-10">
            <h2 class="text-2xl font-bold text-gray-800 mb-4 border-b pb-2">كود الخريطة التفاعلية (Leaflet)</h2>
            <p class="text-sm text-gray-600 mb-3">هذا الكود مدمج بالفعل في المعاينة أعلاه، وهو مخصص لقسم "خريطة المواقع التراثية" عند إنشائه على Replit.</p>
            <div class="bg-gray-800 text-gray-100 p-4 rounded-lg mb-4 overflow-auto max-h-60 font-mono text-xs">
                <pre class="whitespace-pre-wrap" dir="ltr">
// Sample Leaflet initialization (add inside script tags)
var map = L.map('demo-map').setView([21.4225, 39.8262], 14); // Masjid al-Haram coordinates

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
    attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
}).addTo(map);

// --- Example Markers ---
// Masjid al-Haram
var haramMarker = L.marker([21.4225, 39.8262]).addTo(map)
    .bindPopup('<b>المسجد الحرام</b><br>قلب مكة النابض ومقصد الحجاج والمعتمرين.');

// Jannat al-Mu'alla Cemetery
var muallaMarker = L.marker([21.4367, 39.8343]).addTo(map)
    .bindPopup("<b>مقبرة المعلاة</b><br>مقبرة تاريخية تضم رفات العديد من الصحابة وأهل بيت النبي ﷺ.");

// Cave of Hira (Jabal al-Nour)
var hiraMarker = L.marker([21.4574, 39.8854]).addTo(map)
    .bindPopup("<b>غار حراء (جبل النور)</b><br>مكان نزول الوحي الأول على النبي محمد ﷺ.");

// Masjid al-Jinn
var jinnMarker = L.marker([21.4311, 39.8306]).addTo(map)
    .bindPopup("<b>مسجد الجن</b><br>المكان الذي استمع فيه الجن للقرآن من النبي ﷺ.");

// Add more markers for Medina and historical expansions...
// Example: Masjid an-Nabawi (Medina)
// L.marker([24.4686, 39.6141]).addTo(map).bindPopup("<b>المسجد النبوي</b><br> ثاني أقدس المساجد في الإسلام.");

// Optional: Add layer control if using different layers for expansions
</pre>
            </div>
            <button id="copy-leaflet" class="copy-btn bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-2 px-4 rounded transition duration-300 flex items-center justify-center text-sm">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 5H6a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2v-1M8 5a2 2 0 002 2h2a2 2 0 002-2M8 5a2 2 0 012-2h2a2 2 0 012 2m0 0h2a2 2 0 012 2v3m2 4H10m0 0l3-3m-3 3l3 3" /></svg>
                نسخ كود Leaflet النموذجي
            </button>
        </section>

        <footer class="text-center mt-12 text-gray-500 text-sm">
            <p>© 1446هـ / 2025م - جميع الحقوق محفوظة لفريق البحث</p>
            <p>جامعة الملك عبد العزيز - كلية السياحة - قسم إدارة الضيافة</p>
        </footer>
    </div>

    <script>
        // --- Leaflet Map Initialization ---
        var map = L.map('demo-map').setView([21.4225, 39.8262], 14); // مركز الخريطة على المسجد الحرام

        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            maxZoom: 19,
            attribution: '&copy; <a href="http://www.openstreetmap.org/copyright" target="_blank" rel="noopener noreferrer">OpenStreetMap</a> contributors'
        }).addTo(map);

        // أيقونة مخصصة للمسجد
        var mosqueIcon = L.icon({
            iconUrl: '/api/placeholder/32/48', // Placeholder icon
            iconSize:     [32, 48], // size of the icon
            iconAnchor:   [16, 48], // point of the icon which will correspond to marker's location
            popupAnchor:  [0, -50] // point from which the popup should open relative to the iconAnchor
        });
        
         // أيقونة مخصصة لموقع تاريخي
        var heritageIcon = L.icon({
            iconUrl: '/api/placeholder/32/32', // Placeholder icon
            iconSize:     [32, 32], 
            iconAnchor:   [16, 32], 
            popupAnchor:  [0, -34] 
        });

        // --- Markers ---
        // مكة المكرمة
        L.marker([21.4225, 39.8262], {icon: mosqueIcon}).addTo(map)
            .bindPopup('<b>المسجد الحرام</b><br>الوجهة الرئيسية للحج والعمرة.');

        L.marker([21.4367, 39.8343], {icon: heritageIcon}).addTo(map)
            .bindPopup("<b>مقبرة المعلاة</b><br>مقبرة تاريخية هامة في مكة.");

        L.marker([21.4574, 39.8854], {icon: heritageIcon}).addTo(map)
            .bindPopup("<b>غار حراء (جبل النور)</b><br>مكان نزول الوحي الأول.");

        L.marker([21.4311, 39.8306], {icon: mosqueIcon}).addTo(map)
            .bindPopup("<b>مسجد الجن</b>");

        // المدينة المنورة (قد تحتاج لتغيير مركز الخريطة والتكبير لرؤيتها بوضوح)
         L.marker([24.4686, 39.6141], {icon: mosqueIcon}).addTo(map)
             .bindPopup("<b>المسجد النبوي</b><br>ثاني أقدس المساجد.");
             
         L.marker([24.4523, 39.6125], {icon: heritageIcon}).addTo(map)
             .bindPopup("<b>مقبرة البقيع</b><br>مقبرة رئيسية في المدينة المنورة.");
             
         L.marker([24.5010, 39.5781], {icon: mosqueIcon}).addTo(map)
             .bindPopup("<b>مسجد قباء</b><br>أول مسجد بني في الإسلام.");
             
         L.marker([24.4831, 39.5944], {icon: mosqueIcon}).addTo(map)
             .bindPopup("<b>مسجد القبلتين</b>");
             
        // --- Copy Button Functionality ---
        const buttons = document.querySelectorAll('.copy-btn');
        buttons.forEach(button => {
            button.addEventListener('click', function() {
                let contentToCopy = '';
                const id = this.id;

                if (id === 'copy-presentation') {
                    contentToCopy = `# دور الذكاء الاصطناعي ونظم المعلومات الجغرافية في تعزيز الوعي الثقافي لدى الحجاج والمعتمرين
## "دراسة تطبيقية على مدينتي مكة المكرمة والمدينة المنورة"

### فريق البحث
- بــدر كامل مرزا (2403482)
- بندر مريزيق الحارثي (2403351)
- عبد الله إبراهيم النعمي (2403800)
- محمد عبد المجيد داغستاني (2403341)
- محمد هاشم خوج (2403481)

### تحت إشراف
الدكتور/ عبد العزيز محمد شودري

**جامعة الملك عبد العزيز – كلية السياحة**  
**قسم إدارة الضيافة**  
**الماجستير التنفيذي في إدارة خدمات الحج والعمرة**

### الملخص
يهدف هذا المشروع إلى... (أكمل الملخص)

### المحتويات
1. المقدمة
2. أهمية الوعي الثقافي
3. دور الذكاء الاصطناعي ونظم المعلومات الجغرافية
4. التطبيقات المقترحة (الخريطة التفاعلية، التطبيق الذكي)
5. تحليل البيانات (توزيع الجنسيات واللغات)
6. التحديات والفرص
7. التوصيات
8. الخاتمة`;
                } else if (id === 'copy-app') {
                    contentToCopy = `// --- نموذج كود React لتطبيق دليل الحاج الثقافي ---
// ملاحظة: هذا الكود يتطلب بيئة React ومكتبات مثل lucide-react و recharts
// انسخ هذا الكود وضعه في ملف .jsx ضمن مشروع React على CodePen أو بيئة محلية

import { useState, useEffect } from "react";
import { Camera, Map, Globe, Users, BookOpen, MessageSquare, Navigation, Calendar, Info, Menu, X, Languages, Sun, Moon } from "lucide-react";
import { PieChart, Pie, BarChart, Bar, XAxis, YAxis, CartesianGrid, Tooltip, Legend, Cell, ResponsiveContainer } from "recharts";

// --- بيانات افتراضية ---
const culturalInfo = {
  ar: {
    greeting: "السلام عليكم",
    thanks: "شكراً لك",
    respect: "إظهار الاحترام لكبار السن والعلماء.",
    dress: "الالتزام باللباس المحتشم خاصة في الأماكن المقدسة."
  },
  en: {
    greeting: "Assalamu Alaikum",
    thanks: "Thank you",
    respect: "Show respect to elders and scholars.",
    dress: "Adhere to modest dress, especially in holy places."
  }
};

const nationalityData = [
  { name: 'إندونيسيا', value: 400 }, { name: 'باكستان', value: 300 },
  { name: 'الهند', value: 250 }, { name: 'بنغلاديش', value: 200 },
  { name: 'مصر', value: 150 }, { name: 'أخرى', value: 350 },
];
const COLORS = ['#0088FE', '#00C49F', '#FFBB28', '#FF8042', '#AF19FF', '#FF1919'];

export default function SmartCulturalApp() {
  const [currentTab, setCurrentTab] = useState("home");
  const [language, setLanguage] = useState("ar");
  const [showMenu, setShowMenu] = useState(false);
  const [loading, setLoading] = useState(true);
  const [darkMode, setDarkMode] = useState(false);

  useEffect(() => {
    const timer = setTimeout(() => setLoading(false), 1500);
    document.documentElement.lang = language;
    document.documentElement.dir = language === 'ar' ? 'rtl' : 'ltr';
    if (darkMode) {
      document.documentElement.classList.add('dark');
    } else {
      document.documentElement.classList.remove('dark');
    }
    return () => clearTimeout(timer);
  }, [language, darkMode]);

  const toggleDarkMode = () => setDarkMode(!darkMode);

  const T = (key) => {
    const translations = {
      ar: {
        title: "دليل الحاج الثقافي الذكي", home: "الرئيسية", map: "الخريطة", info: "معلومات ثقافية", translator: "مترجم", calendar: "المناسك", welcome: "مرحباً بك", desc: "مساعدك لتجربة حج وعمرة واعية ثقافياً", nearby: "أماكن قريبة", tips: "نصائح ثقافية", services: "الخدمات", langSelect: "اختر اللغة", loading: "جار التحميل...", dark: "داكن", light: "فاتح", greeting: "تحية", thanks: "شكر", respect: "احترام", dress: "لباس"
      },
      en: {
         title: "Smart Cultural Hajj Guide", home: "Home", map: "Map", info: "Cultural Info", translator: "Translator", calendar: "Rituals", welcome: "Welcome", desc: "Your guide for a culturally aware Hajj & Umrah", nearby: "Nearby Places", tips: "Cultural Tips", services: "Services", langSelect: "Select Language", loading: "Loading...", dark: "Dark", light: "Light", greeting: "Greeting", thanks: "Thanks", respect: "Respect", dress: "Dress"
      }
    };
    return translations[language][key] || key;
  };

  if (loading) {
    return <div className="flex justify-center items-center h-screen bg-gray-100 dark:bg-gray-900"><div className="text-xl font-semibold text-gray-700 dark:text-gray-300 animate-pulse">{T('loading')}</div></div>;
  }

  return (
    <div className={\`flex flex-col h-screen font-['Tajawal'] \${darkMode ? 'dark' : ''}\`}>
      {/* Header */}
      <header className="bg-green-600 dark:bg-green-800 text-white p-4 flex justify-between items-center shadow-md">
        <button onClick={() => setShowMenu(!showMenu)} className="p-2 rounded-md hover:bg-green-700 dark:hover:bg-green-900 transition"><Menu /></button>
        <h1 className="text-lg font-bold">{T('title')}</h1>
        <div className="flex items-center gap-2">
           <button onClick={toggleDarkMode} className="p-2 rounded-md hover:bg-green-700 dark:hover:bg-green-900 transition">
                {darkMode ? <Sun size={20} /> : <Moon size={20} />}
            </button>
          <select value={language} onChange={(e) => setLanguage(e.target.value)} className="bg-transparent border-none text-white focus:outline-none p-1 rounded text-sm">
            <option value="ar" className="text-black">العربية</option>
            <option value="en" className="text-black">English</option>
             {/* Add more languages */}
          </select>
        </div>
      </header>

      {/* Sidebar Menu */}
      <div className={\`fixed inset-y-0 \${language === 'ar' ? 'right-0' : 'left-0'} z-30 w-64 bg-white dark:bg-gray-800 shadow-lg transform transition-transform duration-300 ease-in-out \${showMenu ? 'translate-x-0' : (language === 'ar' ? 'translate-x-full' : '-translate-x-full')}\`}>
         <div className="p-4 flex justify-between items-center border-b dark:border-gray-700">
            <h2 className="font-semibold text-gray-800 dark:text-gray-200">{T('menu')}</h2>
            <button onClick={() => setShowMenu(false)} className="text-gray-600 dark:text-gray-400 hover:text-red-500"><X /></button>
         </div>
         <nav className="p-4 space-y-2">
            {['home', 'map', 'info', 'translator', 'calendar'].map(tab => (
              <button key={tab} onClick={() => { setCurrentTab(tab); setShowMenu(false); }}
                      className={\`w-full text-right dark:text-gray-300 px-4 py-2 rounded flex items-center gap-3 \${currentTab === tab ? 'bg-green-100 dark:bg-green-900 text-green-700 dark:text-green-300 font-semibold' : 'hover:bg-gray-100 dark:hover:bg-gray-700'}\`}>
                 {tab === 'home' && <Users size={18} />} {tab === 'map' && <Map size={18} />} {tab === 'info' && <Info size={18} />} {tab === 'translator' && <Languages size={18} />} {tab === 'calendar' && <Calendar size={18} />}
                 {T(tab)}
              </button>
            ))}
         </nav>
      </div>
       {/* Overlay */}
       {showMenu && <div className="fixed inset-0 bg-black bg-opacity-50 z-20" onClick={() => setShowMenu(false)}></div>}


      {/* Main Content */}
      <main className="flex-grow overflow-y-auto bg-gray-100 dark:bg-gray-900 p-4">
        {currentTab === 'home' && (
          <div className="space-y-6">
            <div className="bg-white dark:bg-gray-800 p-6 rounded-lg shadow">
              <h2 className="text-2xl font-semibold mb-2 text-gray-800 dark:text-gray-200">{T('welcome')}!</h2>
              <p className="text-gray-600 dark:text-gray-400">{T('desc')}</p>
            </div>
            <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
               <div className="bg-white dark:bg-gray-800 p-4 rounded-lg shadow">
                  <h3 className="font-semibold mb-3 text-gray-700 dark:text-gray-300">{T('nearby')}</h3>
                  {/* Placeholder for nearby places */}
                  <ul className="space-y-2 text-sm text-gray-600 dark:text-gray-400">
                     <li className="flex items-center gap-2"><Navigation size={16} className="text-blue-500"/> المسجد الحرام (500 م)</li>
                     <li className="flex items-center gap-2"><Navigation size={16} className="text-blue-500"/> مطعم البركة (200 م)</li>
                  </ul>
               </div>
                <div className="bg-white dark:bg-gray-800 p-4 rounded-lg shadow">
                  <h3 className="font-semibold mb-3 text-gray-700 dark:text-gray-300">{T('tips')}</h3>
                  {/* Placeholder for cultural tips */}
                   <ul className="space-y-2 text-sm text-gray-600 dark:text-gray-400">
                     <li className="flex items-center gap-2"><Info size={16} className="text-green-500"/> {culturalInfo[language].respect}</li>
                     <li className="flex items-center gap-2"><Info size={16} className="text-green-500"/> {culturalInfo[language].dress}</li>
                  </ul>
               </div>
            </div>
             <div className="bg-white dark:bg-gray-800 p-4 rounded-lg shadow">
                  <h3 className="font-semibold mb-3 text-gray-700 dark:text-gray-300">توزيع الحجاج (نموذج)</h3>
                   <div style={{ width: '100%', height: 250 }}>
                     <ResponsiveContainer>
                       <PieChart>
                         <Pie data={nationalityData} dataKey="value" nameKey="name" cx="50%" cy="50%" outerRadius={80} label>
                            {nationalityData.map((entry, index) => <Cell key={\`cell-\${index}\`} fill={COLORS[index % COLORS.length]} />)}
                         </Pie>
                         <Tooltip />
                         <Legend />
                       </PieChart>
                     </ResponsiveContainer>
                   </div>
               </div>
          </div>
        )}
         {currentTab === 'map' && <div className="bg-white dark:bg-gray-800 p-4 rounded-lg shadow h-full"><h2 className="font-semibold text-xl mb-4 dark:text-gray-200">{T('map')}</h2><p className="text-gray-600 dark:text-gray-400">سيتم عرض خريطة تفاعلية هنا...</p><div className="h-64 bg-gray-200 dark:bg-gray-700 rounded mt-4 flex items-center justify-center text-gray-500 dark:text-gray-400">Map Placeholder</div></div>}
         {currentTab === 'info' && <div className="bg-white dark:bg-gray-800 p-4 rounded-lg shadow"><h2 className="font-semibold text-xl mb-4 dark:text-gray-200">{T('info')}</h2><div className="space-y-3 text-gray-700 dark:text-gray-300"><p><strong>{T('greeting')}:</strong> {culturalInfo[language].greeting}</p><p><strong>{T('thanks')}:</strong> {culturalInfo[language].thanks}</p><p><strong>{T('respect')}:</strong> {culturalInfo[language].respect}</p><p><strong>{T('dress')}:</strong> {culturalInfo[language].dress}</p></div></div>}
         {currentTab === 'translator' && <div className="bg-white dark:bg-gray-800 p-4 rounded-lg shadow"><h2 className="font-semibold text-xl mb-4 dark:text-gray-200">{T('translator')}</h2><textarea className="w-full p-2 border rounded dark:bg-gray-700 dark:border-gray-600 dark:text-gray-200" rows="4" placeholder="اكتب النص للترجمة..."></textarea><button className="mt-2 bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600 transition">ترجمة</button></div>}
         {currentTab === 'calendar' && <div className="bg-white dark:bg-gray-800 p-4 rounded-lg shadow"><h2 className="font-semibold text-xl mb-4 dark:text-gray-200">{T('calendar')}</h2><p className="text-gray-600 dark:text-gray-400">جدول المناسك والأحداث...</p></div>}
      </main>

      {/* Bottom Navigation (Optional, can use sidebar instead) */}
      {/* ... */}
    </div>
  );
}
`;
                } else if (id === 'copy-nationality-map') {
                    contentToCopy = `<!DOCTYPE html>
<html dir="rtl" lang="ar">
<head>
    <meta charset="UTF-8">
    <title>توزيع الحجاج حسب الجنسيات</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style> body { font-family: sans-serif; padding: 20px; } </style>
</head>
<body>
    <h1>توزيع الحجاج حسب الجنسيات (نموذج)</h1>
    <div style="width: 80%; max-width: 600px; margin: auto;">
        <canvas id="nationalityChart"></canvas>
    </div>
    <script>
        const ctx = document.getElementById('nationalityChart').getContext('2d');
        const nationalityChart = new Chart(ctx, {
            type: 'pie', // أو 'doughnut'
            data: {
                labels: ['إندونيسيا', 'باكستان', 'الهند', 'بنغلاديش', 'مصر', 'نيجيريا', 'تركيا', 'أخرى'],
                datasets: [{
                    label: 'عدد الحجاج (تقديري)',
                    data: [221000, 179210, 170025, 127298, 90000, 95000, 83430, 500000], // بيانات تقديرية
                    backgroundColor: [
                        'rgba(255, 99, 132, 0.7)', 'rgba(54, 162, 235, 0.7)',
                        'rgba(255, 206, 86, 0.7)', 'rgba(75, 192, 192, 0.7)',
                        'rgba(153, 102, 255, 0.7)', 'rgba(255, 159, 64, 0.7)',
                        'rgba(199, 199, 199, 0.7)', 'rgba(83, 102, 255, 0.7)'
                    ],
                    borderColor: '#fff',
                    borderWidth: 1
                }]
            },
            options: {
                responsive: true,
                plugins: {
                    legend: { position: 'top', },
                    title: { display: true, text: 'توزيع الحجاج حسب الجنسيات الكبرى' }
                }
            }
        });
    </script>
</body>
</html>`;
                } else if (id === 'copy-language-map') {
                     contentToCopy = `<!DOCTYPE html>
<html dir="rtl" lang="ar">
<head>
    <meta charset="UTF-8">
    <title>توزيع الحجاج حسب اللغات</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
     <style> body { font-family: sans-serif; padding: 20px; } </style>
</head>
<body>
    <h1>توزيع الحجاج حسب اللغات الرئيسية (نموذج)</h1>
     <div style="width: 80%; max-width: 700px; margin: auto;">
        <canvas id="languageChart"></canvas>
    </div>
    <script>
        const ctxLang = document.getElementById('languageChart').getContext('2d');
        const languageChart = new Chart(ctxLang, {
            type: 'bar', // Bar chart might be better for languages
            data: {
                labels: ['العربية', 'الأردية', 'الإندونيسية/الملايو', 'البنغالية', 'الإنجليزية', 'التركية', 'الهوسا', 'الفارسية'],
                datasets: [{
                    label: 'عدد الناطقين (تقديري)',
                    data: [420000, 300000, 250000, 150000, 180000, 90000, 100000, 70000], // بيانات تقديرية
                    backgroundColor: [
                        'rgba(75, 192, 192, 0.7)', 'rgba(54, 162, 235, 0.7)',
                        'rgba(255, 99, 132, 0.7)', 'rgba(255, 206, 86, 0.7)',
                        'rgba(153, 102, 255, 0.7)', 'rgba(255, 159, 64, 0.7)',
                        'rgba(199, 199, 199, 0.7)', 'rgba(83, 102, 255, 0.7)'
                    ],
                     borderColor: [ // Adding borders for bars
                        'rgba(75, 192, 192, 1)','rgba(54, 162, 235, 1)','rgba(255, 99, 132, 1)',
                        'rgba(255, 206, 86, 1)','rgba(153, 102, 255, 1)','rgba(255, 159, 64, 1)',
                        'rgba(199, 199, 199, 1)','rgba(83, 102, 255, 1)'
                    ],
                    borderWidth: 1
                }]
            },
            options: {
                indexAxis: 'y', // Make it a horizontal bar chart for better readability
                responsive: true,
                 scales: {
                    x: { beginAtZero: true }
                },
                plugins: {
                    legend: { display: false }, // Legend might be redundant for bar charts with labels
                    title: { display: true, text: 'توزيع اللغات الرئيسية بين الحجاج' }
                }
            }
        });
    </script>
</body>
</html>`;
                } else if (id === 'copy-figma') {
                    contentToCopy = `مكونات تصميم لتطبيق "دليل الحاج الثقافي" على Figma:

1.  **نظام الألوان (Color Palette):**
    *   الأخضر الأساسي (للعناصر الرئيسية والترويج): #10B981
    *   الأزرق (للخرائط والمعلومات الجغرافية): #3B82F6
    *   الأصفر/البرتقالي (للتنبيهات والنصائح): #F59E0B
    *   البنفسجي (للمعلومات الثقافية): #8B5CF6
    *   الرمادي الفاتح (للخلفيات): #F3F4F6
    *   الرمادي الداكن (للنصوص): #1F2937

2.  **الخطوط (Typography):**
    *   استخدام خط عربي واضح مثل "Tajawal" أو "Cairo" للعناوين والنصوص.
    *   استخدام خط لاتيني متناسق مثل "Inter" أو "Poppins" للإنجليزية.

3.  **مكونات الواجهة (UI Components):**
    *   **بطاقات (Cards):** بتصميم نظيف وحواف دائرية وظلال خفيفة لعرض المعلومات (نصائح، أماكن قريبة).
    *   **أزرار (Buttons):** بألوان النظام الأساسية، مع حالات مختلفة (hover, active).
    *   **شريط التنقل السفلي (Bottom Navigation):** أيقونات واضحة (رئيسية، خريطة، معلومات، ترجمة، مناسك) مع تمييز للعنصر النشط.
    *   **شريط علوي (Top Bar):** عنوان الصفحة، زر القائمة الجانبية، زر تغيير اللغة/الوضع الداكن.
    *   **حقول الإدخال (Input Fields):** للبحث والترجمة.
    *   **قوائم (Lists):** لعرض الأماكن، النصائح، المناسك.
    *   **رسوم بيانية (Charts):** استخدام أنماط نظيفة ومتناسقة (كما في Recharts).
    *   **أيقونات (Icons):** استخدام مكتبة Lucide React أو ما يماثلها للاتساق.

4.  **تصميم الشاشات الرئيسية (Key Screens Layout):**
    *   **الرئيسية:** بطاقة ترحيب، وصول سريع للخريطة والنصائح، موجز توزيع الحجاج.
    *   **الخريطة:** عرض خريطة Leaflet مع علامات للمواقع الهامة، طبقات اختيارية للتوسعات، شريط بحث.
    *   **المعلومات الثقافية:** تقسيم للمعلومات باستخدام بطاقات أو تبويبات (عادات، لغة، تاريخ).
    *   **المترجم:** حقل إدخال، اختيار لغات، عرض الترجمة، زر للترجمة الصوتية.
    *   **المناسك:** جدول زمني أو قائمة بالمناسك مع شروحات مختصرة.`;
                } else if (id === 'copy-heritage-map') {
                    contentToCopy = `<!DOCTYPE html>
<html dir="rtl" lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>الخريطة التفاعلية للمواقع التراثية</title>
    <!-- Include Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Include Leaflet CSS and JS -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY=" crossorigin=""/>
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js" integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo=" crossorigin=""></script>
    <style>
        #map { height: 80vh; /* Adjust height as needed */ width: 100%; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.1); }
        body { font-family: 'Tajawal', sans-serif; background-color: #f9fafb; padding: 20px; }
        .leaflet-popup-content-wrapper { border-radius: 8px !important; }
        .leaflet-popup-content { font-family: 'Tajawal', sans-serif !important; font-size: 14px !important; line-height: 1.6 !important; max-width: 250px !important; }
        h1 { text-align: center; color: #1f2937; margin-bottom: 20px; font-size: 1.75rem; font-weight: 700; }
        /* Custom Icon Style (Optional) */
        .mosque-icon { /* Style for mosque icon div if using L.divIcon */ }
        .heritage-icon { /* Style for heritage icon div */ }
    </style>
</head>
<body>
    <h1 class="text-2xl font-bold text-center text-gray-800 mb-6">خريطة المواقع التراثية وتوسعات المسجد الحرام</h1>
    <div id="map"></div>

    <script>
        // Initialize the map, centered on Masjid al-Haram
        var map = L.map('map').setView([21.4225, 39.8262], 14);

        // Add OpenStreetMap tile layer
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            maxZoom: 19,
            attribution: '&copy; <a href="http://www.openstreetmap.org/copyright" target="_blank" rel="noopener noreferrer">OpenStreetMap</a> contributors'
        }).addTo(map);

        // --- Custom Icons (using placeholders for simplicity, replace with actual image URLs or L.divIcon) ---
         var mosqueIcon = L.icon({
            iconUrl: '/api/placeholder/32/48', // Placeholder
            iconSize: [32, 48], iconAnchor: [16, 48], popupAnchor: [0, -50]
        });
        var heritageIcon = L.icon({
            iconUrl: '/api/placeholder/32/32', // Placeholder
            iconSize: [32, 32], iconAnchor: [16, 32], popupAnchor: [0, -34]
        });

        // --- Markers Data (Add more sites as needed) ---
        const sites = [
            { coords: [21.4225, 39.8262], name: "المسجد الحرام", desc: "قبلة المسلمين ووجهة الحج والعمرة.", type: "mosque" },
            { coords: [21.4367, 39.8343], name: "مقبرة المعلاة", desc: "مقبرة تاريخية تضم رفات شخصيات هامة.", type: "heritage" },
            { coords: [21.4574, 39.8854], name: "غار حراء (جبل النور)", desc: "مكان نزول الوحي الأول على النبي محمد ﷺ.", type: "heritage" },
            { coords: [21.4311, 39.8306], name: "مسجد الجن", desc: "موقع تاريخي مرتبط بسورة الجن.", type: "mosque" },
            // Medina Sites (Map needs recentering/zooming to see them clearly)
            { coords: [24.4686, 39.6141], name: "المسجد النبوي", desc: "ثاني أقدس المساجد في الإسلام.", type: "mosque" },
            { coords: [24.4523, 39.6125], name: "مقبرة البقيع", desc: "مقبرة رئيسية في المدينة تضم رفات صحابة.", type: "heritage" },
            { coords: [24.5010, 39.5781], name: "مسجد قباء", desc: "أول مسجد بني في الإسلام.", type: "mosque" },
            { coords: [24.4831, 39.5944], name: "مسجد القبلتين", desc: "المسجد الذي شهد تحويل القبلة.", type: "mosque" },
            // Add historical expansion phases as polygons or layers if data is available
            // Example (Placeholder Polygon for an expansion):
            // L.polygon([[lat1, lng1], [lat2, lng2], [lat3, lng3]], {color: 'blue'}).addTo(map).bindPopup("التوسعة السعودية الأولى");
        ];

        // --- Add Markers to Map ---
        sites.forEach(site => {
            let icon = site.type === "mosque" ? mosqueIcon : heritageIcon;
            L.marker(site.coords, { icon: icon })
              .addTo(map)
              .bindPopup(\`<b>\${site.name}</b><br>\${site.desc}\`);
        });

        // Optional: Add layer control if you have different layers (e.g., Makkah sites, Medina sites, Expansions)
        // var makkahLayer = L.layerGroup([... markers for Makkah ...]);
        // var medinaLayer = L.layerGroup([... markers for Medina ...]);
        // L.control.layers(null, {"مواقع مكة": makkahLayer, "مواقع المدينة": medinaLayer}).addTo(map);

    </script>
</body>
</html>`;
                } else if (id === 'copy-leaflet') {
                    contentToCopy = `// Sample Leaflet initialization (add inside script tags in your HTML file)
var map = L.map('map').setView([21.4225, 39.8262], 14); // Centered on Masjid al-Haram

// Add Tile Layer (e.g., OpenStreetMap)
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
    attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);

// --- Example Markers ---
// Define icons (optional, but recommended)
 var mosqueIcon = L.icon({ iconUrl: '/api/placeholder/32/48', iconSize: [32, 48], iconAnchor: [16, 48], popupAnchor: [0, -50] });
 var heritageIcon = L.icon({ iconUrl: '/api/placeholder/32/32', iconSize: [32, 32], iconAnchor: [16, 32], popupAnchor: [0, -34] });

// Add markers with popups
L.marker([21.4225, 39.8262], {icon: mosqueIcon}).addTo(map)
    .bindPopup('<b>المسجد الحرام</b><br>الوجهة الرئيسية للحج والعمرة.');

L.marker([21.4367, 39.8343], {icon: heritageIcon}).addTo(map)
    .bindPopup("<b>مقبرة المعلاة</b><br>مقبرة تاريخية هامة في مكة.");

L.marker([21.4574, 39.8854], {icon: heritageIcon}).addTo(map)
    .bindPopup("<b>غار حراء (جبل النور)</b><br>مكان نزول الوحي الأول.");

L.marker([24.4686, 39.6141], {icon: mosqueIcon}).addTo(map) // Masjid Nabawi
     .bindPopup("<b>المسجد النبوي</b><br>ثاني أقدس المساجد.");

// Add more markers as needed...

// --- Example Polygon (for expansions) ---
// Define coordinates for the expansion area polygon
// var expansionCoords = [ [lat1, lng1], [lat2, lng2], [lat3, lng3], ... ];
// L.polygon(expansionCoords, {color: 'red', fillColor: '#f03', fillOpacity: 0.3})
//  .addTo(map)
//  .bindPopup("مرحلة التوسعة X");

// --- Layer Control (Optional) ---
// Create layer groups
// var makkahMarkers = L.layerGroup([... array of Makkah markers ...]);
// var medinaMarkers = L.layerGroup([... array of Medina markers ...]);
// var expansionLayers = L.layerGroup([... array of expansion polygons ...]);

// Add control to map
// L.control.layers(null, {
//    "مواقع مكة": makkahMarkers,
//    "مواقع المدينة": medinaMarkers,
//    "مراحل التوسعة": expansionLayers
// }).addTo(map);`;
                }

                if (contentToCopy) {
                    copyToClipboard(contentToCopy);
                    animateCopyButton(this); // Animate the button
                }
            });
        });

        // Helper functions
        function copyToClipboard(text) {
            if (navigator.clipboard && window.isSecureContext) {
                navigator.clipboard.writeText(text).then(() => {
                    console.log('Copied to clipboard!');
                }).catch(err => {
                    console.error('Failed to copy: ', err);
                    fallbackCopyTextToClipboard(text); // Fallback for browsers that might fail
                });
            } else {
                 fallbackCopyTextToClipboard(text); // Fallback for non-secure contexts or older browsers
            }
        }

        function fallbackCopyTextToClipboard(text) {
             const textarea = document.createElement('textarea');
             textarea.value = text;
             textarea.style.position = 'fixed'; // Prevent scrolling to bottom of page in MS Edge.
             textarea.style.left = '-9999px';
             document.body.appendChild(textarea);
             textarea.select();
             try {
                 document.execCommand('copy');
                 console.log('Copied to clipboard using fallback!');
             } catch (err) {
                 console.error('Fallback copy failed: ', err);
             }
             document.body.removeChild(textarea);
         }


        function animateCopyButton(button) {
            // Check if animation is already running
            if (button.classList.contains('is-copying')) {
                return;
            }
            button.classList.add('is-copying'); // Add class to prevent re-triggering
            button.classList.add('copied');
            setTimeout(() => {
                button.classList.remove('copied');
                button.classList.remove('is-copying'); // Remove class after animation
            }, 1500);
        }

    </script>
</body>
</html>
