# Mẫu Nộp Dự Án Mini Hackathon
## Sui Learning Tour x Đại Học Văn Hiến

Vui lòng hoàn thành tất cả các phần dưới đây. Thông tin được cung cấp sẽ được sử dụng để đánh giá dự án, cung cấp phản hồi và lựa chọn dự án đạt tiêu chuẩn cho hackathon.

---

## 1. Thông Tin Đội Tuyển

**Tên Đội:**
Charity DApp Development Team

**Thành Viên Đội (Tên – Vai Trò):**
- [Tên Người Dùng] – Lập Trình Viên Full-Stack
- [Thành Viên 2] – Lập Trình Viên Smart Contract
- [Thành Viên 3] – Thiết Kế UI/UX (nếu có)

**Trường Đại Học / Tổ Chức:**
Đại Học Văn Hiến

**Liên Hệ Chính (Tên & Email):**
- Tên: [Tên của bạn]
- Email: [your.email@vanhien.edu.vn]

---

## 2. Tổng Quan Dự Án

**Tên Dự Án:**
Charity DApp - Nền Tảng Gây Quỹ Phi Tập Trung

**Theo Dõi / Danh Mục:** 
Web3 DApp / Ứng Dụng Blockchain

**Mô Tả Ngắn (1-2 câu):**
Một nền tảng gây quỹ từ thiện phi tập trung được xây dựng trên blockchain Sui, cho phép những người sáng lập chiến dịch, nhận quyên góp SUI theo thời gian thực, và cho phép các người hưởng lợi rút tiền một cách minh bạch. Nền tảng sử dụng shared objects và cơ chế Balance để quản lý quỹ an toàn và không cần tin tưởng trung gian.

---

## 3. Vấn Đề & Giải Pháp

**Phát Biểu Vấn Đề:**
Các nền tảng từ thiện truyền thống gặp phải những vấn đề:
- **Thiếu minh bạch**: Các nhà tài trợ không thể xác minh tiền đi đâu
- **Chi phí cao**: Các nền tảng tập trung tính phí lớn cho mỗi giao dịch
- **Hạn chế địa lý**: Không thể chuyển tiền quốc tế một cách dễ dàng
- **Khó theo dõi**: Không có cách để xác minh quỹ được sử dụng đúng cách
- **Không có kết nối trực tiếp**: Người quyên góp không biết tiền của họ đi đâu

**Giải Pháp của Chúng Tôi:**
Charity DApp tận dụng kiến trúc shared object của Sui để tạo nền tảng từ thiện phi tập trung minh bạch, chi phí thấp:
- **Smart Contracts (Move)**: Quản lý các chiến dịch dưới dạng shared objects, cho phép bất kỳ ai quyên góp ngay lập tức
- **Quản Lý Quỹ Minh Bạch**: Tất cả các quyên góp được ghi lại trên blockchain và có thể nhìn thấy bởi tất cả người tham gia
- **Không Có Trung Gian**: Chuyển tiền trực tiếp từ nhà tài trợ đến người hưởng lợi với giao dịch được đảm bảo thông qua tính chắc chắn của Sui
- **Cập Nhật Theo Thời Gian Thực**: Frontend đồng bộ hóa với trạng thái blockchain để theo dõi chiến dịch trực tiếp
- **Rút Tiền An Toàn**: Chỉ những người sáng lập hoặc người hưởng lợi mới có thể rút tiền, được thực thi ở cấp smart contract

---

## 4. Kiến Trúc Kỹ Thuật

### Smart Contract:

**Các Mô Đun / Gói Chính:**
- `charity::charity_platform` - Mô đun cốt lõi chứa:
  - Tạo và quản lý chiến dịch
  - Xử lý quyên góp
  - Cơ chế rút tiền

**Các Đối Tượng Chính (NFT, Shared Object, v.v.):**

1. **CampaignRegistry** (Shared Object):
   - Lưu trữ danh sách tất cả các ID chiến dịch hoạt động
   - Điểm vào để khám phá các chiến dịch
   - Một thể hiện shared duy nhất trên toàn bộ mạng

2. **Campaign** (Shared Object):
   - Chứa siêu dữ liệu chiến dịch (tiêu đề, mô tả, mục tiêu, hạn chót)
   - Duy trì Balance<SUI> cho các quỹ được thu thập
   - Lưu trữ địa chỉ người sáng lập và người hưởng lợi
   - Theo dõi dấu thời gian tạo

**Chiến Lược Nâng Cấp:**
- Sử dụng hệ thống nâng cấp gói của Sui để triển khai các phiên bản mới
- Các hợp đồng chiến dịch duy trì khả năng tương thích ngược
- Các chiến dịch lịch sử vẫn có thể truy cập được sau khi nâng cấp
- Các tính năng mới được triển khai thông qua các phiên bản mô đun được nâng cấp

**Cân Nhắc Bảo Mật:**
- **Xác Thực**:
  - Mục tiêu phải > 0
  - Hạn chót phải là trong tương lai
  - Tiêu đề không được rỗng
  - Số tiền quyên góp phải > 0
  - Thực thi hạn chót trước khi chấp nhận quyên góp
  
- **Kiểm Soát Truy Cập**:
  - Chỉ người sáng lập chiến dịch hoặc người hưởng lợi mới có thể rút tiền
  - Các lệnh assert ngăn chặn chuyển tiền trái phép
  - Bối cảnh Tx xác thực danh tính người gửi
  
- **Lựa Chọn Thiết Kế**:
  - Các shared objects cho chiến dịch cho phép quyên góp đồng thời
  - Balance<SUI> ngăn chặn mất coin vô tình
  - Các sự kiện phát hành để minh bạch (CampaignCreated, DonationReceived, FundsWithdrawn)
  - Lịch sử chiến dịch bất biến để kiểm toán

---

## 5. Sản Phẩm & Luồng Người Dùng

**Người Dùng Mục Tiêu:**
- Những người tổ chức từ thiện và gây quỹ
- Các nhà tài trợ riêng lẻ có ví crypto
- Các tổ chức phi lợi nhuận
- Những thành viên cộng đồng hỗ trợ các nguyên nhân xã hội
- Người dùng tìm kiếm theo dõi quyên góp minh bạch

**Luồng Người Dùng (Từng Bước):**

1. **Kết Nối Ví**
   - Người dùng truy cập frontend Charity DApp
   - Kết nối ví Sui (Sui Wallet, Martian, v.v.)
   - Xác thực thông qua DApp Kit

2. **Duyệt Các Chiến Dịch** (HomePage)
   - Xem tất cả các chiến dịch hoạt động
   - Xem thẻ chiến dịch với: tiêu đề, mục tiêu, số tiền đã gây được, thanh tiến độ, hạn chót
   - Chức năng lọc và tìm kiếm

3. **Tạo Chiến Dịch** (CreateCampaignPage)
   - Nhấp vào nút "Tạo Chiến Dịch"
   - Điền vào biểu mẫu: tiêu đề, mô tả, mục tiêu (SUI), địa chỉ người hưởng lợi, hạn chót
   - Gửi giao dịch thông qua smart contract
   - Campaign Registry được cập nhật với ID chiến dịch mới
   - Nhận xác nhận với ID chiến dịch

4. **Quyên Góp Cho Chiến Dịch** (CampaignCard → DonateModal)
   - Chọn một chiến dịch
   - Nhấp vào nút "Quyên Góp"
   - Nhập số tiền quyên góp
   - Xác nhận giao dịch ví
   - Các đồng tiền SUI được chuyển đổi thành Balance và thêm vào chiến dịch
   - Sự kiện DonationReceived được phát hành
   - Giao diện người dùng cập nhật với tổng số đã gây được mới

5. **Theo Dõi Tiến Độ Chiến Dịch**
   - Cập nhật theo thời gian thực về số tiền đã gây được
   - Thanh tiến độ trực quan cho thấy % mục tiêu đạt được
   - Bộ đếm ngược cho hạn chót
   - Danh sách nhà tài trợ (nếu có)

6. **Rút Tiền**
   - Người sáng lập chiến dịch / người hưởng lợi gọi hàm rút
   - Kiểm tra xác thực danh tính người gửi
   - Tiền được chuyển đến địa chỉ nhận
   - Sự kiện FundsWithdrawn được ghi lại
   - Số dư chiến dịch được cập nhật

**Các Tính Năng Chính:**
- ✅ Tạo các chiến dịch từ thiện với mục tiêu và hạn chót tùy chỉnh
- ✅ Theo dõi quyên góp theo thời gian thực với smart contracts Sui
- ✅ Quản lý quỹ minh bạch bằng Balance<SUI>
- ✅ Hỗ trợ nhiều ví thông qua Sui DApp Kit
- ✅ Bảng điều khiển thống kê chiến dịch (tổng đã gây được, chiến dịch hoạt động, v.v.)
- ✅ Các khoảng thời gian chiến dịch được thực thi bởi hạn chót
- ✅ Rút tiền an toàn cho người dùng được phép
- ✅ Ghi lại sự kiện trên chuỗi để minh bạch hoàn toàn
- ✅ Giao diện React đáp ứng với TypeScript
- ✅ Lưu trữ chiến dịch liên tục thông qua shared objects

---

## 6. Thông Tin Demo

**Luồng Demo Trực Tiếp:**
1. **Kết Nối Ví** (15 giây)
   - Hiển thị kết nối ví Sui
   - Chứng minh ủy quyền DApp

2. **Duyệt Các Chiến Dịch Hiện Có** (30 giây)
   - Hiển thị CampaignList với nhiều chiến dịch
   - Làm nổi bật các thống kê chiến dịch

3. **Tạo Chiến Dịch Mới** (45 giây)
   - Điền vào CreateCampaignForm
   - Gửi giao dịch
   - Xác nhận tạo trên blockchain
   - Hiển thị chiến dịch xuất hiện trong danh sách

4. **Thực Hiện Quyên Góp** (45 giây)
   - Chọn một chiến dịch
   - Mở DonateModal
   - Nhập số tiền quyên góp
   - Xác nhận giao dịch Sui
   - Hiển thị số dư chiến dịch được cập nhật theo thời gian thực
   - Hiển thị sự kiện DonationReceived

5. **Xem Chi Tiết Chiến Dịch** (30 giây)
   - Hiển thị thanh tiến độ chiến dịch
   - Hiển thị đã gây được vs mục tiêu
   - Hiển thị bộ đếm ngược cho hạn chót
   - Làm nổi bật thông tin người hưởng lợi

6. **Tùy Chọn: Rút Tiền** (nếu còn thời gian)
   - Hiển thị rút tiền của người sáng lập / người hưởng lợi
   - Xác nhận sự kiện FundsWithdrawn
   - Hiển thị số dư được cập nhật

**URL Demo:** [URL testnet/devnet của bạn - nếu đã triển khai]

**Testnet / Devnet Được Sử Dụng:**
- Sui Testnet (devnet có sẵn)
- Mạng: testnet | devnet
- Địa chỉ Gói Smart Contract: [Sẽ được điền sau khi triển khai]

---

## 7. Kho Lưu Trữ & Tài Nguyên

**Kho Lưu Trữ Mã Nguồn (GitHub):**
- [URL Kho Lưu Trữ GitHub của bạn]
- Ví dụ: `https://github.com/yourusername/charity-dapp`

**Kho Lưu Trữ Frontend (nếu tách riêng):**
- `/frontend` - Ứng dụng React + TypeScript với tích hợp Sui DApp Kit

**Địa Chỉ Gói Smart Contract:**
- Sẽ được điền sau khi triển khai trên testnet
- Định dạng: `0x[64-ký tự-hex]`

---

## 8. Trạng Thái Hiện Tại

**Trạng Thái Dự Án:** MVP (Gần Hoàn Thành)

**Những Gì Đang Hoạt Động:**
- ✅ Triển khai Smart Contract trên testnet
- ✅ Tạo chiến dịch với xác thực
- ✅ Chức năng quyên góp với cập nhật Balance
- ✅ Cơ chế rút tiền với kiểm soát truy cập
- ✅ Phát hành sự kiện để theo dõi chiến dịch
- ✅ Giao diện React Frontend với TypeScript
- ✅ Tích hợp ví Sui thông qua DApp Kit
- ✅ Hiển thị danh sách chiến dịch
- ✅ Modal quyên góp với xử lý giao dịch
- ✅ Biểu mẫu tạo chiến dịch
- ✅ Cập nhật số dư theo thời gian thực
- ✅ Trang chủ với thống kê

**Những Gì Đang Tiến Hành / Được Lên Kế Hoạch:**
- 🔄 Chức năng lọc và tìm kiếm chiến dịch
- 🔄 Hiển thị lịch sử / bảng xếp hạng nhà tài trợ
- 🔄 Hệ thống danh mục / thẻ chiến dịch
- 🔄 Thông báo email cho cập nhật chiến dịch
- 🔄 Bảng điều khiển phân tích nâng cao
- 🔄 Rút tiền với nhiều chữ ký cho số tiền lớn
- 🔄 Chức năng tạm dừng / mở rộng chiến dịch
- 🔄 Hệ thống xác minh từ thiện
- 🔄 Tối ưu hóa đáp ứng di động (đang tiến hành)
- 🔄 Kiểm tra đơn vị cho smart contracts
- 🔄 Kiểm tra tích hợp cho tương tác frontend-contract

---

## 9. Sẵn Sàng Cho Hackathon

**Tại Sao Đội Của Bạn Sẵn Sàng Cho Một Hackathon?**

1. **Nền Tảng Kỹ Thuật**
   - Hiểu rõ về mô hình đối tượng Sui và shared objects
   - Kinh nghiệm phát triển smart contract Move
   - Kỹ năng phát triển frontend React / TypeScript
   - Xử lý giao dịch blockchain và tích hợp ví

2. **Tính Hoàn Chỉnh Dự Án**
   - MVP chức năng với tất cả các tính năng cốt lõi được thực hiện
   - Smart Contracts hoạt động được triển khai trên testnet
   - Giao diện frontend chuyên nghiệp với giao diện thân thiện với người dùng
   - Phân tách rõ ràng các mối quan tâm (Move / React)

3. **Xác Thực Vấn Đề**
   - Giải quyết nhu cầu thực tế trong lĩnh vực từ thiện
   - Tận dụng điểm mạnh của Sui (shared objects, tính chắc chắn nhanh)
   - Lựa chọn thay thế minh bạch, tiết kiệm chi phí cho các nền tảng truyền thống

4. **Sẵn Sàng Demo**
   - Các hợp đồng có thể triển khai trực tiếp
   - Giao diện người dùng hoàn toàn chức năng
   - Có thể chứng minh luồng người dùng từ đầu đến cuối
   - Giá trị đề xuất rõ ràng

5. **Quản Lý Thời Gian**
   - Các tính năng cốt lõi hoàn thành và được kiểm tra
   - Sẵn sàng để trình bày và lặp lại theo phản hồi
   - Khả năng cải thiện phút chót

**Các Tính Năng Tiếp Theo Nếu Có Nhiều Thời Gian Hơn:**

1. **Ngắn Hạn (1-2 tuần):**
   - Triển khai lọc chiến dịch (theo trạng thái, hạn chót, danh mục)
   - Thêm badge xác minh nhà tài trợ
   - Tạo phần bảng xếp hạng / xu hướng chiến dịch
   - Thêm kiểm tra đơn vị cho hợp đồng Move

2. **Trung Hạn (2-4 tuần):**
   - Xây dựng bảng điều khiển phân tích
   - Triển khai rút tiền với nhiều chữ ký
   - Thêm cơ chế tạm dừng / mở rộng chiến dịch
   - Tạo hệ thống xác minh từ thiện
   - Thêm hệ thống thông báo email

3. **Dài Hạn (1-3 tháng):**
   - Tích hợp cầu nối chuỗi chéo
   - Quản trị DAO cho các quyết định nền tảng
   - Kiểm tra từ thiện tự động
   - Tích hợp với các tổ chức từ thiện chính
   - Ứng dụng di động
   - Phát hiện gian lận dựa trên ML nâng cao

---

## 10. Ghi Chú Bổ Sung (Tùy Chọn)

**Những Thách Thức Gặp Phải:**
- **Đường Cong Học Tập Mô Hình Đối Tượng Sui**: Hiểu rõ về shared objects vs owned objects ban đầu cần phải học sâu về tài liệu Sui
- **Bảo Mật Loại Balance<T>**: Đảm bảo xử lý thích hợp các loại Balance để ngăn chặn mất quỹ
- **Đồng Bộ Hóa Frontend-Contract**: Triển khai cập nhật giao diện người dùng theo thời gian thực phản ánh thay đổi trạng thái trên chuỗi
- **Tối Ưu Hóa Gas**: Tối ưu hóa chi phí giao dịch cho các quyên góp nhỏ
- **Xử Lý Dấu Thời Gian**: Quản lý xác thực hạn chót trên các dấu thời gian epoch khác nhau

**Những Bài Học Rút Ra:**
- Mô hình shared object của Sui rất mạnh nhưng yêu cầu tư duy khác với các hợp đồng EVM truyền thống
- Kiến trúc dựa trên sự kiện rất quan trọng cho các ứng dụng blockchain minh bạch
- Di chuyển logic phức tạp đến smart contracts (vs frontend) cải thiện bảo mật
- Sự kết hợp React Query + DApp Kit hoạt động tốt cho quản lý trạng thái
- Kiểm tra trên testnet rất cần thiết trước khi triển khai mainnet
- Xử lý lỗi rõ ràng và các tin nhắn xác thực cải thiện trải nghiệm người dùng

**Bất Cứ Điều Gì Mà Các Giám Khảo Nên Biết:**
- Dự án này chứng minh sử dụng thích hợp các tính năng độc đáo của Sui (shared objects, Balance<T>)
- Mã được chú thích rõ ràng bằng tiếng Việt cho đội địa phương và tiếng Anh cho đối tượng rộng hơn
- Kiến trúc có khả năng mở rộng: có thể dễ dàng thêm nhiều tính năng hơn mà không làm hỏng logic hiện tại
- Tất cả các giao dịch được hoàn tất và bất biến trên chuỗi để minh bạch hoàn toàn
- Dự án này có giá trị giáo dục để học cách phát triển Sui
- Đội tuân theo các thực hành tốt nhất của Sui cho việc sử dụng mô hình đối tượng
- Hiệu suất tối ưu hóa cho các giao dịch tần số cao nhỏ (quyên góp nhỏ)

---

## 📌 Tuyên Bố

Bằng cách nộp biểu mẫu này, đội xác nhận rằng:
- ✅ Dự án là sản phẩm gốc của họ
- ✅ Tất cả mã được viết bởi các thành viên của đội
- ✅ Đội đồng ý tham gia vào quá trình đánh giá Mini Hackathon
- ✅ Đội hiểu các quy tắc và yêu cầu Mini Hackathon
- ✅ Đội sẽ trình bày công việc của họ nếu được chọn vào danh sách đạt tiêu chuẩn

**Ngày Nộp:** [Ngày Hiện Tại]
**Chữ Ký Trưởng Đội:** _________________________
**Ngày:** _________________________

---

## Tài Nguyên Bổ Sung

### Cấu Trúc Dự Án
```
charity-dapp/
├── move/
│   ├── sources/
│   │   └── charity.move              # Smart contract chính
│   ├── tests/
│   │   └── charity_tests.move        # Kiểm tra smart contract
│   └── Move.toml                     # Kê khai gói
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── CampaignCard.tsx
│   │   │   ├── CampaignList.tsx
│   │   │   ├── CreateCampaignForm.tsx
│   │   │   ├── DonateModal.tsx
│   │   │   ├── Features.tsx
│   │   │   ├── Footer.tsx
│   │   │   ├── Hero.tsx
│   │   │   ├── Navbar.tsx
│   │   │   └── StatsBar.tsx
│   │   ├── pages/
│   │   ├── context/
│   │   ├── hooks/
│   │   └── utils/
│   ├── public/
│   └── package.json
│
└── docs/
    ├── DEMO.md
    └── PITCH.md
```

### Các Công Nghệ Chính
- **Blockchain**: Sui Network
- **Smart Contracts**: Move Language
- **Frontend**: React 18, TypeScript
- **Blockchain SDK**: @mysten/sui, @mysten/dapp-kit
- **Quản Lý Trạng Thái**: React Context, React Query
- **Tạo Kiểu**: CSS

### Hướng Dẫn Triển Khai
1. Triển khai hợp đồng Move: `sui move build && sui client publish`
2. Cài đặt phụ thuộc frontend: `npm install --legacy-peer-deps`
3. Cập nhật địa chỉ hợp đồng trong cấu hình frontend
4. Chạy frontend: `npm start`

---

**Chúc bạn may mắn với việc nộp Mini Hackathon! 🚀**
