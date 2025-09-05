<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>لینکدونی - نسخه نهایی</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.5/font/bootstrap-icons.css">
    <style>
        :root {
            --primary-color: #6a11cb;
            --secondary-color: #2575fc;
            --light-bg: #f8f9fa;
            --dark-bg: #1a1a2e;
            --light-text: #f8f9fa;
            --dark-text: #212529;
            --card-light: #ffffff;
            --card-dark: #2d2d44;
            --gradient: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
        }

        body {
            background-color: var(--light-bg);
            color: var(--dark-text);
            transition: all 0.3s ease;
            min-height: 100vh;
            padding-bottom: 60px;
            font-family: 'Vazirmatn', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body.dark-mode {
            background-color: var(--dark-bg);
            color: var(--light-text);
        }

        .navbar {
            background: var(--gradient) !important;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }

        .card {
            transition: all 0.3s ease;
            margin-bottom: 20px;
            border: none;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        .light-mode .card {
            background-color: var(--card-light);
            color: var(--dark-text);
        }

        .dark-mode .card {
            background-color: var(--card-dark);
            color: var(--light-text);
        }

        .notification-badge {
            background-color: #ff4757;
            color: white;
            border-radius: 50%;
            padding: 2px 6px;
            font-size: 12px;
            margin-right: 5px;
        }

        .page {
            display: none;
            padding: 20px;
            animation: fadeIn 0.5s;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .page.active {
            display: block;
        }

        .fullscreen-chat {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: white;
            z-index: 1000;
            display: none;
            flex-direction: column;
        }

        .dark-mode .fullscreen-chat {
            background-color: var(--dark-bg);
            color: var(--light-text);
        }

        .chat-header {
            padding: 15px;
            background: var(--gradient);
            color: white;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .chat-messages {
            flex: 1;
            padding: 15px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
        }

        .message {
            max-width: 70%;
            padding: 10px 15px;
            margin-bottom: 10px;
            border-radius: 18px;
            word-break: break-word;
        }

        .message.user {
            align-self: flex-start;
            background-color: #e6e6e6;
        }

        .dark-mode .message.user {
            background-color: #3d3d5c;
        }

        .message.admin {
            align-self: flex-end;
            background: var(--gradient);
            color: white;
        }

        .chat-input {
            padding: 15px;
            border-top: 1px solid #ddd;
            display: flex;
        }

        .dark-mode .chat-input {
            border-top: 1px solid #444;
        }

        .admin-panel {
            background-color: #f8f9fa;
            border-radius: 10px;
            padding: 20px;
            margin-top: 20px;
        }

        .dark-mode .admin-panel {
            background-color: #2d2d44;
        }

        .chat-list {
            max-height: 400px;
            overflow-y: auto;
        }

        .chat-item {
            padding: 10px;
            border-bottom: 1px solid #ddd;
            cursor: pointer;
            transition: background-color 0.2s;
        }

        .dark-mode .chat-item {
            border-bottom: 1px solid #444;
        }

        .chat-item:hover {
            background-color: rgba(0, 0, 0, 0.05);
        }

        .dark-mode .chat-item:hover {
            background-color: rgba(255, 255, 255, 0.05);
        }

        .support-btn {
            background: var(--gradient);
            border: none;
            color: white;
            padding: 8px 15px;
            border-radius: 20px;
            display: flex;
            align-items: center;
            gap: 5px;
            transition: opacity 0.3s;
        }

        .support-btn:hover {
            opacity: 0.9;
        }

        .close-chat {
            cursor: pointer;
            font-size: 24px;
        }

        .banner-card {
            transition: transform 0.3s;
            overflow: hidden;
        }

        .banner-card:hover {
            transform: translateY(-5px);
        }

        .banner-img {
            height: 180px;
            object-fit: cover;
        }

        .category-badge {
            background: var(--gradient);
            color: white;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 12px;
            margin-left: 5px;
        }

        .user-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            object-fit: cover;
        }

        .admin-sidebar {
            background-color: #f8f9fa;
            border-radius: 10px;
            padding: 20px;
            height: fit-content;
        }

        .dark-mode .admin-sidebar {
            background-color: #2d2d44;
        }

        .admin-menu {
            list-style: none;
            padding: 0;
        }

        .admin-menu li {
            padding: 10px 0;
            border-bottom: 1px solid #ddd;
        }

        .dark-mode .admin-menu li {
            border-bottom: 1px solid #444;
        }

        .admin-menu li a {
            color: var(--dark-text);
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .dark-mode .admin-menu li a {
            color: var(--light-text);
        }

        .admin-menu li a:hover {
            color: var(--primary-color);
        }

        .stats-card {
            text-align: center;
            padding: 20px;
        }

        .stats-number {
            font-size: 2.5rem;
            font-weight: bold;
            background: var(--gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .link-card {
            transition: all 0.3s;
        }

        .link-card:hover {
            box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
        }

        .social-icons a {
            color: var(--dark-text);
            font-size: 1.5rem;
            margin-left: 15px;
            transition: color 0.3s;
        }

        .dark-mode .social-icons a {
            color: var(--light-text);
        }

        .social-icons a:hover {
            color: var(--primary-color);
        }

        .footer {
            background: var(--gradient);
            color: white;
            padding: 30px 0;
            margin-top: 50px;
        }

        @media (max-width: 768px) {
            .navbar-nav {
                text-align: right;
            }
            
            .page {
                padding: 10px;
            }
            
            .message {
                max-width: 85%;
            }
        }
    </style>
</head>
<body class="light-mode">
    <!-- نوار ناوبری -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
        <div class="container">
            <a class="navbar-brand" href="#" onclick="showPage('home')">
                <i class="bi bi-link-45deg"></i> لینکدونی
            </a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav me-auto">
                    <li class="nav-item">
                        <a class="nav-link active" href="#" onclick="showPage('home')">
                            <i class="bi bi-house"></i> صفحه اصلی
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" onclick="showPage('banner-register')">
                            <i class="bi bi-plus-square"></i> ثبت بنر
                        </a>
                    </li>
                    <li class="nav-item">
                        <button class="nav-link support-btn" onclick="openFullscreenChat()">
                            <i class="bi bi-headset"></i> پشتیبانی
                        </button>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" onclick="showPage('message-inbox')">
                            <i class="bi bi-inbox"></i> صندوق پیام
                            <span class="notification-badge" id="message-notification">0</span>
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" onclick="showPage('profile')">
                            <i class="bi bi-person"></i> پروفایل
                        </a>
                    </li>
                </ul>
                <div class="d-flex">
                    <button class="btn btn-outline-light me-2" onclick="toggleTheme()">
                        <i class="bi bi-moon"></i>
                    </button>
                    <div id="admin-nav-item">
                        <button class="btn btn-outline-light" onclick="showPage('admin-login')">
                            <i class="bi bi-shield-lock"></i> ورود ادمین
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </nav>

    <!-- محتوای اصلی -->
    <div class="container mt-4">
        <!-- صفحه اصلی -->
        <div id="home" class="page active">
            <h2 class="mb-4">صفحه اصلی لینکدونی</h2>
            
            <div class="row mb-4">
                <div class="col-md-8">
                    <div class="input-group">
                        <input type="text" class="form-control" placeholder="جستجو در لینک ها..." id="search-input">
                        <button class="btn btn-primary" onclick="searchLinks()">
                            <i class="bi bi-search"></i> جستجو
                        </button>
                    </div>
                </div>
                <div class="col-md-4">
                    <select class="form-select" id="category-filter">
                        <option value="">همه دسته‌بندی‌ها</option>
                        <option value="technology">تکنولوژی</option>
                        <option value="education">آموزشی</option>
                        <option value="shopping">خرید</option>
                        <option value="news">اخبار</option>
                    </select>
                </div>
            </div>
            
            <div class="row">
                <div class="col-md-4 mb-4">
                    <div class="card banner-card">
                        <img src="https://via.placeholder.com/300x180/6a11cb/ffffff?text=تبلیغ+۱" class="card-img-top banner-img" alt="بنر تبلیغاتی">
                        <div class="card-body">
                            <h5 class="card-title">فروشگاه اینترنتی</h5>
                            <p class="card-text">بهترین محصولات با قیمت مناسب</p>
                            <div class="d-flex justify-content-between align-items-center">
                                <span class="category-badge">خرید</span>
                                <a href="#" class="btn btn-sm btn-outline-primary">مشاهده</a>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="col-md-4 mb-4">
                    <div class="card banner-card">
                        <img src="https://via.placeholder.com/300x180/2575fc/ffffff?text=تبلیغ+۲" class="card-img-top banner-img" alt="بنر تبلیغاتی">
                        <div class="card-body">
                            <h5 class="card-title">آموزش برنامه نویسی</h5>
                            <p class="card-text">یادگیری برنامه نویسی از صفر تا صد</p>
                            <div class="d-flex justify-content-between align-items-center">
                                <span class="category-badge">آموزشی</span>
                                <a href="#" class="btn btn-sm btn-outline-primary">مشاهده</a>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="col-md-4 mb-4">
                    <div class="card banner-card">
                        <img src="https://via.placeholder.com/300x180/4caf50/ffffff?text=تبلیغ+۳" class="card-img-top banner-img" alt="بنر تبلیغاتی">
                        <div class="card-body">
                            <h5 class="card-title">اخبار تکنولوژی</h5>
                            <p class="card-text">آخرین اخبار دنیای تکنولوژی</p>
                            <div class="d-flex justify-content-between align-items-center">
                                <span class="category-badge">اخبار</span>
                                <a href="#" class="btn btn-sm btn-outline-primary">مشاهده</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="row mt-4">
                <div class="col-12">
                    <h4 class="mb-3">لینک های پرطرفدار</h4>
                    <div class="list-group">
                        <a href="#" class="list-group-item list-group-item-action">
                            <div class="d-flex w-100 justify-content-between">
                                <h5 class="mb-1">سایت آموزشی راکت</h5>
                                <small>۳ روز پیش</small>
                            </div>
                            <p class="mb-1">آموزش برنامه نویسی وب و موبایل</p>
                            <small class="text-muted">دسته‌بندی: آموزشی</small>
                        </a>
                        <a href="#" class="list-group-item list-group-item-action">
                            <div class="d-flex w-100 justify-content-between">
                                <h5 class="mb-1">دیجی کالا</h5>
                                <small>۱ هفته پیش</small>
                            </div>
                            <p class="mb-1">فروشگاه اینترنتی با میلیون ها محصول</p>
                            <small class="text-muted">دسته‌بندی: خرید</small>
                        </a>
                    </div>
                </div>
            </div>
        </div>

        <!-- ثبت بنر -->
        <div id="banner-register" class="page">
            <h2 class="mb-4">ثبت بنر جدید</h2>
            <div class="row">
                <div class="col-md-8">
                    <div class="card">
                        <div class="card-body">
                            <form id="banner-form">
                                <div class="mb-3">
                                    <label for="banner-title" class="form-label">عنوان بنر</label>
                                    <input type="text" class="form-control" id="banner-title" required>
                                </div>
                                <div class="mb-3">
                                    <label for="banner-url" class="form-label">آدرس URL</label>
                                    <input type="url" class="form-control" id="banner-url" required>
                                </div>
                                <div class="mb-3">
                                    <label for="banner-category" class="form-label">دسته‌بندی</label>
                                    <select class="form-select" id="banner-category" required>
                                        <option value="">انتخاب دسته‌بندی</option>
                                        <option value="technology">تکنولوژی</option>
                                        <option value="education">آموزشی</option>
                                        <option value="shopping">خرید</option>
                                        <option value="news">اخبار</option>
                                        <option value="entertainment">سرگرمی</option>
                                    </select>
                                </div>
                                <div class="mb-3">
                                    <label for="banner-description" class="form-label">توضیحات</label>
                                    <textarea class="form-control" id="banner-description" rows="3"></textarea>
                                </div>
                                <div class="mb-3">
                                    <label for="banner-image" class="form-label">آپلود تصویر</label>
                                    <input type="file" class="form-control" id="banner-image" accept="image/*" required>
                                    <div class="form-text">حداکثر حجم فایل: 2MB</div>
                                </div>
                                <div class="form-check mb-3">
                                    <input class="form-check-input" type="checkbox" id="banner-terms" required>
                                    <label class="form-check-label" for="banner-terms">
                                        با قوانین و شرایط سایت موافقم
                                    </label>
                                </div>
                                <button type="submit" class="btn btn-primary">ثبت بنر</button>
                            </form>
                        </div>
                    </div>
                </div>
                <div class="col-md-4">
                    <div class="card">
                        <div class="card-body">
                            <h5 class="card-title">راهنما</h5>
                            <ul class="list-group list-group-flush">
                                <li class="list-group-item">تصویر باید با ابعاد 300x180 پیکسل باشد</li>
                                <li class="list-group-item">لینک باید متعلق به خودتان باشد</li>
                                <li class="list-group-item">محتوای تبلیغاتی نباید مغایر با قوانین باشد</li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- صندوق پیام -->
        <div id="message-inbox" class="page">
            <h2 class="mb-4">صندوق پیام</h2>
            <div class="row">
                <div class="col-md-4">
                    <div class="list-group" id="message-list">
                        <a href="#" class="list-group-item list-group-item-action active">
                            <div class="d-flex w-100 justify-content-between">
                                <h5 class="mb-1">پشتیبانی لینکدونی</h5>
                                <small>امروز</small>
                            </div>
                            <p class="mb-1">بنر شما تایید شد</p>
                        </a>
                        <a href="#" class="list-group-item list-group-item-action">
                            <div class="d-flex w-100 justify-content-between">
                                <h5 class="mb-1">سیستم اطلاع رسانی</h5>
                                <small>دیروز</small>
                            </div>
                            <p class="mb-1">بروزرسانی جدید</p>
                        </a>
                    </div>
                </div>
                <div class="col-md-8">
                    <div class="card">
                        <div class="card-header">
                            <h5 class="mb-0">بنر شما تایید شد</h5>
                        </div>
                        <div class="card-body">
                            <p>با سلام،</p>
                            <p>بنر شما با عنوان "فروشگاه اینترنتی" بررسی و تایید شد. هم اکنون در صفحه اصلی سایت در حال نمایش است.</p>
                            <p>با تشکر، تیم پشتیبانی لینکدونی</p>
                            <hr>
                            <form>
                                <div class="mb-3">
                                    <label for="reply-message" class="form-label">پاسخ</label>
                                    <textarea class="form-control" id="reply-message" rows="3"></textarea>
                                </div>
                                <button type="submit" class="btn btn-primary">ارسال پاسخ</button>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- پروفایل -->
        <div id="profile" class="page">
            <h2 class="mb-4">پروفایل کاربری</h2>
            <div class="row">
                <div class="col-md-4">
                    <div class="card">
                        <div class="card-body text-center">
                            <img src="https://via.placeholder.com/150/6a11cb/ffffff?text=USER" class="rounded-circle mb-3" alt="پروفایل" width="150" height="150">
                            <h4>کاربر لینکدونی</h4>
                            <p class="text-muted">عضو since 1402</p>
                            <div class="d-grid gap-2">
                                <button class="btn btn-outline-primary">تغییر تصویر</button>
                            </div>
                        </div>
                    </div>
                    <div class="card mt-4">
                        <div class="card-body">
                            <h5 class="card-title">آمار فعالیت</h5>
                            <ul class="list-group list-group-flush">
                                <li class="list-group-item d-flex justify-content-between align-items-center">
                                    بنرهای ثبت شده
                                    <span class="badge bg-primary rounded-pill">5</span>
                                </li>
                                <li class="list-group-item d-flex justify-content-between align-items-center">
                                    بازدید کل
                                    <span class="badge bg-primary rounded-pill">1,243</span>
                                </li>
                                <li class="list-group-item d-flex justify-content-between align-items-center">
                                    لینک های فعال
                                    <span class="badge bg-primary rounded-pill">3</span>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
                <div class="col-md-8">
                    <div class="card">
                        <div class="card-body">
                            <form id="profile-form">
                                <div class="row mb-3">
                                    <div class="col-md-6">
                                        <label for="profile-name" class="form-label">نام کامل</label>
                                        <input type="text" class="form-control" id="profile-name" value="کاربر لینکدونی">
                                    </div>
                                    <div class="col-md-6">
                                        <label for="profile-email" class="form-label">ایمیل</label>
                                        <input type="email" class="form-control" id="profile-email" value="user@linkdooni.com">
                                    </div>
                                </div>
                                <div class="mb-3">
                                    <label for="profile-username" class="form-label">نام کاربری</label>
                                    <input type="text" class="form-control" id="profile-username" value="user123">
                                </div>
                                <div class="mb-3">
                                    <label for="profile-bio" class="form-label">بیوگرافی</label>
                                    <textarea class="form-control" id="profile-bio" rows="3">علاقمند به اشتراک گذاری لینک های مفید</textarea>
                                </div>
                                <hr>
                                <h5 class="mb-3">تغییر رمز عبور</h5>
                                <div class="row mb-3">
                                    <div class="col-md-6">
                                        <label for="profile-password" class="form-label">رمز عبور جدید</label>
                                        <input type="password" class="form-control" id="profile-password">
                                    </div>
                                    <div class="col-md-6">
                                        <label for="profile-confirm-password" class="form-label">تکرار رمز عبور</label>
                                        <input type="password" class="form-control" id="profile-confirm-password">
                                    </div>
                                </div>
                                <button type="submit" class="btn btn-primary">ذخیره تغییرات</button>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- ورود ادمین -->
        <div id="admin-login" class="page">
            <h2 class="mb-4">ورود ادمین</h2>
            <div class="row justify-content-center">
                <div class="col-md-6">
                    <div class="card">
                        <div class="card-body">
                            <form id="admin-login-form">
                                <div class="text-center mb-4">
                                    <i class="bi bi-shield-lock" style="font-size: 3rem; color: var(--primary-color);"></i>
                                    <h3 class="mt-2">پنل مدیریت</h3>
                                </div>
                                <div class="mb-3">
                                    <label for="admin-username" class="form-label">نام کاربری</label>
                                    <input type="text" class="form-control" id="admin-username" required>
                                </div>
                                <div class="mb-3">
                                    <label for="admin-password" class="form-label">رمز عبور</label>
                                    <input type="password" class="form-control" id="admin-password" required>
                                </div>
                                <div class="form-check mb-3">
                                    <input class="form-check-input" type="checkbox" id="admin-remember">
                                    <label class="form-check-label" for="admin-remember">
                                        مرا به خاطر بسپار
                                    </label>
                                </div>
                                <button type="submit" class="btn btn-primary w-100">ورود به پنل ادمین</button>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- پنل ادمین -->
        <div id="admin-panel" class="page">
            <h2 class="mb-4">پنل مدیریت ادمین</h2>
            
            <div class="row">
                <div class="col-md-3">
                    <div class="admin-sidebar">
                        <h4 class="mb-3">منوی مدیریت</h4>
                        <ul class="admin-menu">
                            <li><a href="#"><i class="bi bi-speedometer2"></i> پیشخوان</a></li>
                            <li><a href="#"><i class="bi bi-images"></i> مدیریت بنرها</a></li>
                            <li><a href="#"><i class="bi bi-people"></i> مدیریت کاربران</a></li>
                            <li><a href="#" class="active"><i class="bi bi-chat-dots"></i> مدیریت چت ها</a></li>
                            <li><a href="#"><i class="bi bi-envelope"></i> پیام ها</a></li>
                            <li><a href="#"><i class="bi bi-gear"></i> تنظیمات</a></li>
                            <li><a href="#" onclick="showPage('home')"><i class="bi bi-box-arrow-left"></i> خروج</a></li>
                        </ul>
                    </div>
                </div>
                <div class="col-md-9">
                    <div class="admin-panel">
                        <div class="d-flex justify-content-between align-items-center mb-4">
                            <h4>مدیریت چت های پشتیبانی</h4>
                            <div class="d-flex">
                                <input type="text" class="form-control me-2" placeholder="جستجو در چت ها...">
                                <button class="btn btn-primary">
                                    <i class="bi bi-search"></i>
                                </button>
                            </div>
                        </div>
                        
                        <div class="row mb-4">
                            <div class="col-md-3">
                                <div class="card stats-card">
                                    <div class="card-body">
                                        <i class="bi bi-chat-dots" style="font-size: 2rem;"></i>
                                        <div class="stats-number">24</div>
                                        <div>چت های فعال</div>
                                    </div>
                                </div>
                            </div>
                            <div class="col-md-3">
                                <div class="card stats-card">
                                    <div class="card-body">
                                        <i class="bi bi-people" style="font-size: 2rem;"></i>
                                        <div class="stats-number">18</div>
                                        <div>کاربران آنلاین</div>
                                    </div>
                                </div>
                            </div>
                            <div class="col-md-3">
                                <div class="card stats-card">
                                    <div class="card-body">
                                        <i class="bi bi-clock-history" style="font-size: 2rem;"></i>
                                        <div class="stats-number">5</div>
                                        <div>در انتظار پاسخ</div>
                                    </div>
                                </div>
                            </div>
                            <div class="col-md-3">
                                <div class="card stats-card">
                                    <div class="card-body">
                                        <i class="bi bi-check-circle" style="font-size: 2rem;"></i>
                                        <div class="stats-number">127</div>
                                        <div>چت های پایان یافته</div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <h5 class="mb-3">چت های فعال</h5>
                        <div class="chat-list mb-4">
                            <div class="chat-item" onclick="selectChat(1)">
                                <div class="d-flex justify-content-between align-items-center">
                                    <div class="d-flex align-items-center">
                                        <img src="https://via.placeholder.com/40/6a11cb/ffffff?text=U1" class="user-avatar me-3" alt="User 1">
                                        <div>
                                            <strong>کاربر ۱</strong>
                                            <p class="mb-0">لطفا در تنظیمات به من کمک کنید...</p>
                                        </div>
                                    </div>
                                    <span class="badge bg-primary">3 پیام جدید</span>
                                </div>
                            </div>
                            <div class="chat-item" onclick="selectChat(2)">
                                <div class="d-flex justify-content-between align-items-center">
                                    <div class="d-flex align-items-center">
                                        <img src="https://via.placeholder.com/40/2575fc/ffffff?text=U2" class="user-avatar me-3" alt="User 2">
                                        <div>
                                            <strong>کاربر ۲</strong>
                                            <p class="mb-0">چگونه می توانم بنر اضافه کنم؟...</p>
                                        </div>
                                    </div>
                                    <span class="badge bg-primary">1 پیام جدید</span>
                                </div>
                            </div>
                            <div class="chat-item" onclick="selectChat(3)">
                                <div class="d-flex justify-content-between align-items-center">
                                    <div class="d-flex align-items-center">
                                        <img src="https://via.placeholder.com/40/4caf50/ffffff?text=U3" class="user-avatar me-3" alt="User 3">
                                        <div>
                                            <strong>کاربر ۳</strong>
                                            <p class="mb-0">از پشتیبانی شما متشکرم...</p>
                                        </div>
                                    </div>
                                    <span class="badge bg-secondary">بدون پیام جدید</span>
                                </div>
                            </div>
                        </div>
                        
                        <div id="admin-chat-area">
                            <h5>چت با <span id="current-chat-user">کاربر ۱</span></h5>
                            <div class="chat-messages mb-3" style="height: 300px; border: 1px solid #ddd; border-radius: 5px; padding: 15px;">
                                <div class="message user">
                                    <strong>کاربر ۱:</strong> لطفا در تنظیمات به من کمک کنید
                                </div>
                                <div class="message admin">
                                    <strong>ادمین:</strong> حتما، چه مشکلی دارید؟
                                </div>
                                <div class="message user">
                                    <strong>کاربر ۱:</strong> نمی توانم تصویر پروفایل را تغییر دهم
                                </div>
                                <div class="message admin">
                                    <strong>ادمین:</strong> لطفا از قسمت پروفایل اقدام کنید و تصویر با فرمت JPG یا PNG باشد
                                </div>
                                <div class="message user">
                                    <strong>کاربر ۱:</strong> ممنون، مشکل حل شد
                                </div>
                            </div>
                            
                            <div class="chat-input">
                                <input type="text" class="form-control" placeholder="پیام خود را بنویسید...">
                                <button class="btn btn-primary ms-2">ارسال</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- چت تمام صفحه -->
    <div class="fullscreen-chat" id="fullscreen-chat">
        <div class="chat-header">
            <h5 class="mb-0">پشتیبانی آنلاین لینکدونی</h5>
            <span class="close-chat" onclick="closeFullscreenChat()">&times;</span>
        </div>
        <div class="chat-messages" id="chat-messages">
            <div class="message admin">
                <strong>پشتیبان:</strong> سلام! چگونه می توانم به شما کمک کنم؟
            </div>
            <div class="message user">
                <strong>شما:</strong> سلام، من در ثبت بنر مشکل دارم
            </div>
            <div class="message admin">
                <strong>پشتیبان:</strong> لطفا مشکل خود را دقیقتر شرح دهید
            </div>
        </div>
        <div class="chat-input">
            <input type="text" class="form-control" id="chat-input-field" placeholder="پیام خود را بنویسید...">
            <button class="btn btn-primary ms-2" onclick="sendMessage()">ارسال</button>
        </div>
    </div>

    <!-- فوتر -->
    <footer class="footer mt-5">
        <div class="container">
            <div class="row">
                <div class="col-md-4 mb-4">
                    <h5>لینکدونی</h5>
                    <p>سامانه اشتراک گذاری لینک و بنرهای تبلیغاتی</p>
                    <div class="social-icons">
                        <a href="#"><i class="bi bi-telegram"></i></a>
                        <a href="#"><i class="bi bi-instagram"></i></a>
                        <a href="#"><i class="bi bi-twitter"></i></a>
                        <a href="#"><i class="bi bi-linkedin"></i></a>
                    </div>
                </div>
                <div class="col-md-2 mb-4">
                    <h5>لینک های مفید</h5>
                    <ul class="list-unstyled">
                        <li><a href="#" class="text-light">درباره ما</a></li>
                        <li><a href="#" class="text-light">قوانین و مقررات</a></li>
                        <li><a href="#" class="text-light">سوالات متداول</a></li>
                        <li><a href="#" class="text-light">تماس با ما</a></li>
                    </ul>
                </div>
                <div class="col-md-3 mb-4">
                    <h5>دسته بندی ها</h5>
                    <ul class="list-unstyled">
                        <li><a href="#" class="text-light">تکنولوژی</a></li>
                        <li><a href="#" class="text-light">آموزشی</a></li>
                        <li><a href="#" class="text-light">خرید</a></li>
                        <li><a href="#" class="text-light">اخبار</a></li>
                    </ul>
                </div>
                <div class="col-md-3 mb-4">
                    <h5>تماس با ما</h5>
                    <ul class="list-unstyled">
                        <li><i class="bi bi-geo-alt"></i> تهران، خیابان آزادی</li>
                        <li><i class="bi bi-telephone"></i> ۰۲۱-۱۲۳۴۵۶۷۸</li>
                        <li><i class="bi bi-envelope"></i> info@linkdooni.ir</li>
                    </ul>
                </div>
            </div>
            <hr class="mt-0 mb-4">
            <div class="text-center">
                <p class="mb-0">© ۱۴۰۲ لینکدونی. تمام حقوق محفوظ است.</p>
            </div>
        </div>
    </footer>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    <script>
        // نمایش صفحه مورد نظر
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active');
            });
            document.getElementById(pageId).classList.add('active');
            
            // اگر صفحه ادمین است، منوی چت را فعال کن
            if (pageId === 'admin-panel') {
                document.querySelectorAll('.admin-menu li a').forEach(item => {
                    item.classList.remove('active');
                });
                document.querySelector('.admin-menu li:nth-child(4) a').classList.add('active');
            }
            
            // اسکرول به بالا
            window.scrollTo(0, 0);
        }

        // تغییر تم
        function toggleTheme() {
            const body = document.body;
            const themeIcon = document.querySelector('.btn-outline-light i');
            
            if (body.classList.contains('dark-mode')) {
                body.classList.remove('dark-mode');
                body.classList.add('light-mode');
                themeIcon.classList.remove('bi-sun');
                themeIcon.classList.add('bi-moon');
                localStorage.setItem('theme', 'light');
            } else {
                body.classList.remove('light-mode');
                body.classList.add('dark-mode');
                themeIcon.classList.remove('bi-moon');
                themeIcon.classList.add('bi-sun');
                localStorage.setItem('theme', 'dark');
            }
        }

        // باز کردن چت تمام صفحه
        function openFullscreenChat() {
            document.getElementById('fullscreen-chat').style.display = 'flex';
            document.getElementById('chat-input-field').focus();
        }

        // بستن چت تمام صفحه
        function closeFullscreenChat() {
            document.getElementById('fullscreen-chat').style.display = 'none';
        }

        // ارسال پیام در چت
        function sendMessage() {
            const inputField = document.getElementById('chat-input-field');
            const message = inputField.value.trim();
            
            if (message !== '') {
                const chatMessages = document.getElementById('chat-messages');
                const newMessage = document.createElement('div');
                newMessage.className = 'message user';
                newMessage.innerHTML = `<strong>شما:</strong> ${message}`;
                
                chatMessages.appendChild(newMessage);
                inputField.value = '';
                
                // اسکرول به پایین
                chatMessages.scrollTop = chatMessages.scrollHeight;
                
                // شبیه سازی پاسخ ادمین پس از 1 ثانیه
                setTimeout(() => {
                    const adminReply = document.createElement('div');
                    adminReply.className = 'message admin';
                    adminReply.innerHTML = `<strong>پشتیبان:</strong> پیام شما دریافت شد. به زودی پاسخ داده خواهد شد.`;
                    chatMessages.appendChild(adminReply);
                    
                    // اسکرول به پایین
                    chatMessages.scrollTop = chatMessages.scrollHeight;
                }, 1000);
            }
        }

        // مدیریت فرم ورود ادمین
        document.getElementById('admin-login-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const username = document.getElementById('admin-username').value;
            const password = document.getElementById('admin-password').value;
            
            // در حالت واقعی باید با سرور چک شود
            if (username === 'admin' && password === 'admin123') {
                showPage('admin-panel');
            } else {
                alert('نام کاربری یا رمز عبور اشتباه است');
            }
        });

        // انتخاب چت در پنل ادمین
        function selectChat(chatId) {
            document.querySelectorAll('.chat-item').forEach(item => {
                item.classList.remove('active');
            });
            document.querySelector(`.chat-item:nth-child(${chatId})`).classList.add('active');
            
            // به روزرسانی نام کاربر در بالای چت
            document.getElementById('current-chat-user').textContent = `کاربر ${chatId}`;
        }

        // مدیریت ارسال فرم ثبت بنر
        document.getElementById('banner-form').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('بنر شما با موفقیت ثبت شد و پس از تایید نمایش داده خواهد شد.');
            this.reset();
        });

        // مدیریت ارسال فرم پروفایل
        document.getElementById('profile-form').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('تغییرات پروفایل با موفقیت ذخیره شد.');
        });

        // جستجوی لینک ها
        function searchLinks() {
            const searchTerm = document.getElementById('search-input').value;
            const category = document.getElementById('category-filter').value;
            
            if (searchTerm || category) {
                alert(`جستجو برای: ${searchTerm} ${category ? 'در دسته‌بندی: ' + category : ''}`);
            } else {
                alert('لطفا عبارت جستجو یا دسته‌بندی را انتخاب کنید.');
            }
        }

        // بارگذاری تم ذخیره شده
        document.addEventListener('DOMContentLoaded', function() {
            const savedTheme = localStorage.getItem('theme');
            const themeIcon = document.querySelector('.btn-outline-light i');
            
            if (savedTheme === 'dark') {
                document.body.classList.remove('light-mode');
                document.body.classList.add('dark-mode');
                themeIcon.classList.remove('bi-moon');
                themeIcon.classList.add('bi-sun');
            }
            
            // شبیه سازی اعلان های جدید
            setTimeout(() => {
                document.getElementById('message-notification').textContent = '2';
            }, 3000);
            
            // فعال کردن ارسال چت با دکمه Enter
            document.getElementById('chat-input-field').addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    sendMessage();
                }
            });
        });
    </script>
</body>
</html>
