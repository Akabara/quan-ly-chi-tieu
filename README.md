# Quản Lý Thu Chi Cá Nhân (Personal Finance Manager)

## 📋 Giới thiệu / Overview

Ứng dụng quản lý thu chi cá nhân thông minh với AI, giúp bạn theo dõi và phân tích các giao dịch tài chính hàng ngày một cách hiệu quả. Ứng dụng được xây dựng hoàn toàn bằng web technologies và tích hợp trí tuệ nhân tạo để đưa ra những lời khuyên tài chính hữu ích.

An intelligent personal finance management application with AI integration, helping you track and analyze your daily financial transactions effectively. Built with modern web technologies and AI-powered insights.

## ✨ Tính năng chính / Key Features

### 🎯 Quản lý giao dịch
- ✅ Thêm, sửa, xóa giao dịch thu chi
- ✅ Phân loại tự động bằng AI (Google Gemini)
- ✅ Hỗ trợ nhập liệu bằng giọng nói
- ✅ Quản lý hai nguồn tiền: tiền mặt và ngân hàng

### 🤖 Tích hợp AI
- ✅ Phân tích giao dịch thông minh
- ✅ Đánh giá tính cần thiết của chi tiêu
- ✅ Đưa ra lời khuyên tài chính cá nhân
- ✅ Tự động phân loại với emoji

### 📊 Theo dõi & Báo cáo
- ✅ Hiển thị số dư thời gian thực
- ✅ Lọc giao dịch theo ngày/tháng
- ✅ Phân trang dữ liệu thông minh
- ✅ Lịch sử giao dịch chi tiết

### 🔐 Bảo mật & Đồng bộ
- ✅ Xác thực Firebase Authentication
- ✅ Mã hóa dữ liệu cloud
- ✅ Đồng bộ thời gian thực
- ✅ Backup tự động

## 🛠 Công nghệ sử dụng / Technology Stack

### Frontend
- **HTML5** - Cấu trúc ứng dụng
- **CSS3** - Styling với Tailwind CSS
- **JavaScript (ES6+)** - Logic ứng dụng
- **Tailwind CSS** - Framework CSS utility-first
- **Google Fonts (Inter)** - Typography

### Backend & Services
- **Firebase Authentication** - Xác thực người dùng
- **Cloud Firestore** - Cơ sở dữ liệu NoSQL
- **Google Gemini AI** - Phân tích giao dịch thông minh
- **Web Speech API** - Nhập liệu bằng giọng nói

### APIs & Integration
- **Google Gemini 2.5 Flash Lite** - AI analysis
- **Firebase SDK 11.6.1** - Cloud services
- **Web Speech Recognition** - Voice input

## 🚀 Hướng dẫn triển khai / Deployment Instructions

### 1. Chuẩn bị môi trường / Prerequisites

```bash
# Không cần cài đặt dependencies - ứng dụng chạy hoàn toàn trên browser
# No dependencies required - runs entirely in browser
```

### 2. Cấu hình Firebase / Firebase Configuration

1. **Tạo Firebase Project:**
   ```bash
   # Truy cập https://console.firebase.google.com/
   # Tạo project mới với tên: quan-ly-chi-tieu
   ```

2. **Cấu hình Authentication:**
   ```javascript
   // Bật Email/Password authentication
   // Enable Email/Password authentication in Firebase Console
   ```

3. **Cấu hình Firestore:**
   ```javascript
   // Tạo database với rules:
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /artifacts/{appId}/users/{userId}/{document=**} {
         allow read, write: if request.auth != null && request.auth.uid == userId;
       }
     }
   }
   ```

### 3. Cấu hình API Keys / API Configuration

1. **Google Gemini AI API:**
   ```javascript
   // Thay thế API key trong file index.html (dòng 690)
   this.apiKey = "YOUR_GEMINI_API_KEY_HERE";
   ```

2. **Firebase Config:**
   ```javascript
   // Cập nhật firebaseConfig trong index.html (dòng 180-187)
   const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "your-project.firebaseapp.com",
     projectId: "your-project-id",
     storageBucket: "your-project.appspot.com",
     messagingSenderId: "123456789",
     appId: "your-app-id"
   };
   ```

### 4. Cấu hình tài khoản Master / Master Account Setup

```javascript
// Cập nhật thông tin tài khoản chủ trong index.html (dòng 190-191)
const MASTER_EMAIL = "your-email@gmail.com";
const MASTER_UID = "your-firebase-uid";
```

### 5. Triển khai ứng dụng / Application Deployment

#### Option 1: Local Development
```bash
# Chạy local server
python -m http.server 8000
# hoặc
npx serve .
# hoặc
live-server
```

#### Option 2: Firebase Hosting
```bash
# Cài đặt Firebase CLI
npm install -g firebase-tools

# Đăng nhập
firebase login

# Khởi tạo hosting
firebase init hosting

# Deploy
firebase deploy
```

#### Option 3: Netlify/Vercel
```bash
# Đơn giản kéo thả folder vào Netlify
# Hoặc connect GitHub repo với Vercel
```

#### Option 4: GitHub Pages
```bash
# Đẩy code lên GitHub
git add .
git commit -m "Initial commit"
git push origin main

# Bật GitHub Pages trong Settings
```

### 6. Cấu hình HTTPS / HTTPS Configuration

```javascript
// Ứng dụng yêu cầu HTTPS để sử dụng:
// - Web Speech API (voice input)
// - Firebase Authentication
// - Gemini AI API calls
```

## 📱 Hướng dẫn sử dụng / Usage Guide

### 1. Đăng nhập / Login
- Nhập mật khẩu tài khoản Firebase đã cấu hình
- Hệ thống sẽ lưu session tự động

### 2. Thêm giao dịch / Add Transaction
- **Nhập tay:** Gõ mô tả giao dịch (VD: "Ăn tối 50k")
- **Giọng nói:** Nhấn nút mic và nói
- **AI xử lý:** Tự động phân loại và gợi ý
- **Xác nhận:** Chỉnh sửa thông tin nếu cần

### 3. Quản lý dữ liệu / Data Management
- **Lọc:** Theo ngày hoặc tháng
- **Chỉnh sửa:** Nhấn nút bút chì
- **Xóa:** Nhấn nút thùng rác
- **Phân trang:** Điều hướng qua các trang

## 🔧 Cấu hình nâng cao / Advanced Configuration

### Environment Variables
```javascript
// Có thể sử dụng trong production
const appId = process.env.APP_ID || 'default-app-id';
const firebaseConfig = JSON.parse(process.env.FIREBASE_CONFIG);
```

### Custom Categories
```javascript
// Thêm categories mới trong TransactionManager.getCategoryOptions()
const categories = [
  { icon: '🍔', name: 'Đồ ăn' },
  { icon: '🚗', name: 'Xe cộ' },
  // Thêm category mới ở đây
];
```

### AI Prompts Customization
```javascript
// Tùy chỉnh prompt AI trong GeminiAI.analyzeTransaction()
const prompt = `
Phân tích giao dịch với ngữ cảnh Việt Nam...
// Chỉnh sửa prompt tại đây
`;
```

## 🐛 Xử lý lỗi / Troubleshooting

### Lỗi thường gặp:
1. **API Key không hợp lệ:** Kiểm tra Gemini API key
2. **Firebase lỗi:** Xác thực cấu hình Firebase
3. **Voice không hoạt động:** Cần HTTPS và microphone permission
4. **CORS errors:** Cần deploy trên server, không chạy file:// protocol

### Debug mode:
```javascript
// Bật console.log trong production để debug
console.log("Debug information here");
```

## 📄 License

Dự án này được phát triển cho mục đích cá nhân và học tập. Vui lòng tuân thủ các điều khoản sử dụng của:
- Firebase Terms of Service
- Google AI Terms of Service
- Tailwind CSS License

## 👨‍💻 Tác giả / Author

Developed with ❤️ for personal finance management

## 🤝 Đóng góp / Contributing

Mọi đóng góp và phản hồi đều được hoan nghênh! Hãy tạo issue hoặc pull request.

All contributions and feedback are welcome! Please create an issue or pull request.

---

⭐ Nếu project hữu ích, hãy cho 1 star nhé!

Star this project if you find it useful! ⭐ 