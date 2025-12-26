# 🎯 Charity DApp - Nền Tảng Gây Quỹ Phi Tập Trung

![Sui Network](https://img.shields.io/badge/Sui-Network-1e90ff)
![Move Language](https://img.shields.io/badge/Move-Smart%20Contract-25b27a)
![React](https://img.shields.io/badge/React-18-61dafb)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178c6)
![License](https://img.shields.io/badge/License-MIT-green)

Charity DApp là một nền tảng gây quỹ từ thiện **phi tập trung** được xây dựng trên blockchain **Sui**, cho phép các chiến dịch từ thiện được tạo, quản lý, và nhận quyên góp một cách **minh bạch**, **an toàn** và **hiệu quả**.

## 🚀 Tính Năng Chính

### ✨ Cho Người Tạo Chiến Dịch
- 📝 **Tạo chiến dịch từ thiện** với mục tiêu và hạn chót tùy chỉnh
- 📊 **Theo dõi tiến độ** gây quỹ theo thời gian thực
- 💰 **Rút tiền an toàn** chỉ với xác thực người sáng lập/người hưởng lợi
- 🔍 **Minh bạch tuyệt đối** - Tất cả giao dịch được ghi lại trên blockchain

### 💎 Cho Nhà Tài Trợ
- 🎁 **Quyên góp dễ dàng** bằng Sui cryptocurrency
- ⏱️ **Quyên góp theo thời gian thực** - Cập nhật ngay lập tức
- 📱 **Theo dõi chiến dịch** - Xem tiến độ bất cứ lúc nào
- ✅ **Giao dịch được đảm bảo** - Không thể mất quỹ

### 🔐 Bảo Mật & Công Nghệ
- 🛡️ **Smart Contract xác thực** trên blockchain Sui
- 🔗 **Shared Objects** - Cho phép nhiều người tương tác cùng lúc
- ⚡ **Tính chắc chắn cao** - Giao dịch hoàn tất trong vài giây
- 🎯 **Không có middleman** - Chuyển tiền trực tiếp từ tài trợ → người hưởng lợi

---

## 📋 Cấu Trúc Dự Án

```
charity-dapp/
│
├── 📁 move/                          # Smart Contracts (Move Language)
│   ├── sources/
│   │   └── charity.move              # Hợp đồng chính
│   ├── tests/
│   │   └── charity_tests.move        # Kiểm tra đơn vị
│   ├── Move.toml                     # Tệp cấu hình gói
│   ├── README.md                     # Hướng dẫn Move
│   └── deploy_output.txt             # Kết quả triển khai
│
├── 📁 frontend/                      # Ứng dụng React Frontend
│   ├── src/
│   │   ├── components/
│   │   │   ├── CampaignCard.tsx      # Thẻ hiển thị chiến dịch
│   │   │   ├── CampaignList.tsx      # Danh sách chiến dịch
│   │   │   ├── CreateCampaignForm.tsx # Biểu mẫu tạo chiến dịch
│   │   │   ├── DonateModal.tsx       # Modal quyên góp
│   │   │   ├── Features.tsx          # Phần tính năng
│   │   │   ├── Footer.tsx            # Footer
│   │   │   ├── Hero.tsx              # Phần banner chính
│   │   │   ├── Navbar.tsx            # Thanh điều hướng
│   │   │   └── StatsBar.tsx          # Thanh thống kê
│   │   ├── pages/
│   │   │   ├── HomePage.tsx          # Trang chủ
│   │   │   └── CreateCampaignPage.tsx # Trang tạo chiến dịch
│   │   ├── context/
│   │   │   ├── SuiContext.tsx        # Context cho Sui
│   │   │   └── SuiProvider.tsx       # Provider cho Sui
│   │   ├── hooks/
│   │   │   └── useSui.ts             # Hook tùy chỉnh Sui
│   │   ├── utils/
│   │   │   ├── campaignManager.ts    # Quản lý chiến dịch
│   │   │   ├── constants.ts          # Hằng số
│   │   │   └── suiTransactions.ts    # Giao dịch Sui
│   │   ├── config/
│   │   │   └── constants.ts          # Cấu hình hằng số
│   │   ├── App.tsx                   # Thành phần chính
│   │   ├── index.tsx                 # Điểm vào
│   │   └── styles/
│   ├── public/                       # Tài nguyên tĩnh
│   ├── package.json                  # Dependencies
│   ├── tsconfig.json                 # Cấu hình TypeScript
│   └── README.md                     # Hướng dẫn Frontend
│
├── 📁 docs/                          # Tài liệu
│   ├── DEMO.md                       # Hướng dẫn demo
│   ├── PITCH.md                      # Pitch dự án
│   └── README.md                     # Tài liệu chung
│
├── 📄 package.json                   # Root package.json
├── 📄 STRUCTURE.md                   # Mô tả cấu trúc
├── 📄 HACKATHON_SUBMISSION.md        # Mẫu hackathon (Tiếng Anh)
├── 📄 HACKATHON_SUBMISSION_VI.md     # Mẫu hackathon (Tiếng Việt)
└── 📄 README_VI.md                   # Tệp này - Hướng dẫn chính

```

---

## 🛠️ Công Nghệ Sử Dụng

### Blockchain & Smart Contracts
- **Sui Network** - Blockchain Layer 1 hiệu suất cao
- **Move Language** - Ngôn ngữ lập trình hợp đồng thông minh an toàn
- **Shared Objects** - Kiến trúc cho phép truy cập đồng thời

### Frontend
- **React 18** - Thư viện giao diện người dùng
- **TypeScript** - Ngôn ngữ có kiểu an toàn
- **@mysten/dapp-kit** - SDK kết nối Sui DApp
- **@mysten/sui** - Thư viện Sui JavaScript
- **React Query** - Quản lý trạng thái và bộ nhớ đệm

### Công Cụ Phát Triển
- **Node.js** - Môi trường chạy JavaScript
- **npm** - Trình quản lý gói
- **Sui CLI** - Công cụ dòng lệnh Sui

---

## 📥 Cài Đặt & Thiết Lập

### Yêu Cầu Tiên Quyết
- **Node.js** v16 hoặc cao hơn
- **npm** hoặc **yarn**
- **Sui CLI** (cho phát triển smart contract)
- **Git**

### Bước 1: Clone Repository

```bash
git clone https://github.com/yourusername/charity-dapp.git
cd charity-dapp
```

### Bước 2: Cài Đặt Dependencies

```bash
# Cài đặt toàn bộ dự án (frontend + move)
npm install --legacy-peer-deps

# Hoặc cài đặt từng phần
# Frontend
cd frontend
npm install --legacy-peer-deps

# Move (nếu cần)
cd ../move
sui move build
```

### Bước 3: Cấu Hình Sui

```bash
# Thiết lập Sui (nếu chưa có)
sui client new

# Chọn testnet
# Chọn tạo ví mới hoặc sử dụng ví hiện tại
```

### Bước 4: Triển Khai Smart Contract

```bash
cd move

# Build contract
sui move build

# Publish contract trên testnet
sui client publish --gas-budget 100000000

# Lưu địa chỉ package từ output
# Cập nhật vào frontend/src/config/constants.ts
```

### Bước 5: Chạy Frontend

```bash
cd frontend
npm start

# Ứng dụng sẽ mở tại: http://localhost:3000
```

---

## 💻 Hướng Dẫn Sử Dụng

### Quy Trình Người Dùng Chính

#### 1️⃣ Kết Nối Ví Sui
```
1. Truy cập http://localhost:3000
2. Nhấp "Kết Nối Ví" (Connect Wallet)
3. Chọn ví Sui của bạn
4. Phê duyệt yêu cầu kết nối
```

#### 2️⃣ Tạo Chiến Dịch
```
1. Nhấp "Tạo Chiến Dịch" (Create Campaign)
2. Điền thông tin:
   - Tiêu đề: Tên chiến dịch từ thiện
   - Mô tả: Chi tiết về mục đích
   - Mục tiêu (SUI): Số tiền cần gây quỹ
   - Người hưởng lợi: Địa chỉ Sui nhận tiền
   - Hạn chót: Ngày kết thúc chiến dịch
3. Nhấp "Tạo"
4. Phê duyệt giao dịch trong ví
5. Chờ xác nhận (2-3 giây)
```

#### 3️⃣ Quyên Góp Cho Chiến Dịch
```
1. Xem danh sách chiến dịch trên trang chủ
2. Chọn chiến dịch muốn quyên góp
3. Nhấp nút "Quyên Góp" (Donate)
4. Nhập số tiền SUI
5. Phê duyệt giao dịch
6. Xem cập nhật số dư theo thời gian thực
```

#### 4️⃣ Rút Tiền (Chỉ Người Tạo/Người Hưởng Lợi)
```
1. Mở chiến dịch của bạn
2. Nhấp nút "Rút Tiền" (Withdraw)
3. Phê duyệt giao dịch
4. Tiền được chuyển đến ví người hưởng lợi
```

---

## 🔧 Phát Triển

### Làm Việc Với Smart Contracts

#### Chỉnh Sửa Hợp Đồng
```bash
cd move
# Chỉnh sửa sources/charity.move

# Build lại
sui move build

# Chạy tests
sui move test

# Publish
sui client publish --gas-budget 100000000
```

#### Cấu Trúc Move Contract

```move
module charity::charity_platform {
    // Hai struct chính:
    
    // 1. CampaignRegistry (Shared Object)
    //    - Lưu trữ danh sách tất cả campaign IDs
    
    // 2. Campaign (Shared Object)
    //    - Tiêu đề, mô tả, mục tiêu
    //    - Số tiền đã gây được (Balance<SUI>)
    //    - Hạn chót, người tạo, người hưởng lợi
    
    // Các hàm chính:
    // - create_campaign() - Tạo chiến dịch mới
    // - donate() - Quyên góp vào chiến dịch
    // - withdraw_funds() - Rút tiền (chỉ authorized users)
    // - get_campaign_info() - Lấy thông tin chiến dịch
}
```

### Làm Việc Với Frontend

#### Cấu Trúc Thành Phần

```typescript
// Homepage - Hiển thị danh sách chiến dịch
components/CampaignList.tsx

// Tạo chiến dịch
pages/CreateCampaignPage.tsx
components/CreateCampaignForm.tsx

// Chi tiết & quyên góp
components/CampaignCard.tsx
components/DonateModal.tsx

// Thống kê
components/StatsBar.tsx
```

#### Kết Nối Với Sui

```typescript
// Sử dụng Hook tùy chỉnh
import { useSui } from '../hooks/useSui';

function MyComponent() {
    const { wallet, connected } = useSui();
    
    // Gọi hàm smart contract
    const handleDonate = async (amount: string) => {
        // Tương tác với smart contract
    };
}
```

#### Gọi Smart Contract

```typescript
// utils/suiTransactions.ts
export async function createCampaign(
    title: string,
    description: string,
    goal: number,
    deadline: number,
    beneficiary: string
) {
    // Gọi move entry function: create_campaign
    // Trả về transaction ID
}

export async function donate(
    campaignId: string,
    amount: number
) {
    // Gọi move entry function: donate
}
```

---

## 🚀 Triển Khai

### Triển Khai Testnet

```bash
# 1. Build Move contracts
cd move
sui move build

# 2. Publish lên testnet
sui client publish --gas-budget 100000000

# 3. Lưu Package Address từ output
# Ví dụ: 0x1a2b3c4d5e6f...

# 4. Cập nhật frontend
# src/config/constants.ts
export const PACKAGE_ID = "0x1a2b3c4d5e6f...";
```

### Triển Khai Frontend (Mainnet)

```bash
cd frontend

# Build cho production
npm run build

# Output: build/ folder

# Deploy lên hosting
# - Vercel: vercel deploy
# - Netlify: netlify deploy
# - GitHub Pages: npm run build && git push
```

---

## 📊 API Reference

### Smart Contract Functions

#### `create_campaign`
Tạo chiến dịch từ thiện mới.

```move
public entry fun create_campaign(
    registry: &mut CampaignRegistry,
    title: vector<u8>,
    description: vector<u8>,
    goal: u64,
    deadline: u64,
    beneficiary: address,
    ctx: &mut TxContext
)
```

**Thông Số:**
- `title` - Tiêu đề chiến dịch (bytes)
- `goal` - Mục tiêu gây quỹ (SUI)
- `deadline` - Thời gian kết thúc (Unix timestamp)
- `beneficiary` - Người hưởng lợi

**Phát Hành Sự Kiện:**
- `CampaignCreated` - Ghi lại tạo chiến dịch

---

#### `donate`
Quyên góp vào chiến dịch.

```move
public entry fun donate(
    campaign: &mut Campaign,
    payment: Coin<SUI>,
    ctx: &mut TxContext
)
```

**Thông Số:**
- `campaign` - Chiến dịch nhận quyên góp
- `payment` - Đồng tiền SUI

**Phát Hành Sự Kiện:**
- `DonationReceived` - Ghi lại quyên góp

---

#### `withdraw_funds`
Rút tiền từ chiến dịch.

```move
public entry fun withdraw_funds(
    campaign: &mut Campaign,
    ctx: &mut TxContext
)
```

**Quyền:**
- Chỉ người tạo hoặc người hưởng lợi

**Phát Hành Sự Kiện:**
- `FundsWithdrawn` - Ghi lại rút tiền

---

#### `get_campaign_info`
Lấy thông tin chiến dịch.

```move
public fun get_campaign_info(campaign: &Campaign): (
    vector<u8>,  // title
    vector<u8>,  // description
    address,     // creator
    u64,         // goal
    u64,         // raised
    u64,         // deadline
    address,     // beneficiary
    u64          // created_at
)
```

---

## 🧪 Kiểm Tra

### Chạy Tests

```bash
cd move

# Chạy tất cả tests
sui move test

# Chạy test cụ thể
sui move test --filter test_create_campaign
```

### Tests Hiện Có

- `test_create_campaign` - Tạo chiến dịch
- `test_donate` - Quyên góp
- `test_withdraw_funds` - Rút tiền
- `test_validations` - Kiểm tra xác thực

---

## 🐛 Troubleshooting

### Lỗi: "Insufficient gas"
```bash
# Tăng gas budget
sui client publish --gas-budget 200000000
```

### Lỗi: "Wallet not connected"
```
1. Kiểm tra đã kết nối ví chưa
2. Chuyển sang testnet nếu cần
3. Reload trang
```

### Lỗi: "Contract address not found"
```
1. Đảm bảo đã publish contract
2. Cập nhật PACKAGE_ID trong constants.ts
3. Sử dụng địa chỉ từ `deploy_output.txt`
```

---

## 📚 Tài Liệu Bổ Sung

- [Sui Official Docs](https://docs.sui.io)
- [Move Language Guide](https://move-language.github.io)
- [Sui Testnet Faucet](https://faucet.testnet.sui.io)
- [Sui Explorer](https://testnet.suivision.xyz)

---

## 🤝 Đóng Góp

Chúng tôi hoan nghênh các đóng góp! Để bắt đầu:

1. Fork repository
2. Tạo branch feature (`git checkout -b feature/AmazingFeature`)
3. Commit thay đổi (`git commit -m 'Add AmazingFeature'`)
4. Push lên branch (`git push origin feature/AmazingFeature`)
5. Mở Pull Request

---

## 📝 Giấy Phép

Dự án này được cấp phép dưới giấy phép MIT. Xem file [LICENSE](LICENSE) để biết chi tiết.

---

## 👥 Tác Giả

**Charity DApp Development Team**
- Đại Học Văn Hiến
- Tham gia: Mini Hackathon - Sui Learning Tour

---

## 📞 Liên Hệ & Hỗ Trợ

- 📧 Email: [your.email@vanhien.edu.vn]
- 🐙 GitHub: [https://github.com/yourusername/charity-dapp]
- 💬 Discord: [Link cộng đồng nếu có]

---

## 🙏 Cảm Ơn

- **Sui Foundation** - Hỗ trợ và tài liệu
- **Van Hien University** - Tài trợ và hướng dẫn
- **Cộng đồng Sui** - Phản hồi và hỗ trợ

---

## 🎯 Roadmap Tương Lai

- [ ] Hệ thống danh mục chiến dịch
- [ ] Xếp hạng nhà tài trợ
- [ ] Thông báo email
- [ ] Bảng điều khiển phân tích
- [ ] Hỗ trợ đa ngôn ngữ
- [ ] Ứng dụng di động
- [ ] Tích hợp DAO

---

**Made with ❤️ for Charity and Blockchain Community**

---

## Changelog

### v1.0.0 (2025-12-26)
- ✅ MVP hoàn thành
- ✅ Smart contracts triển khai
- ✅ Frontend chính thức
- ✅ Tài liệu đầy đủ

