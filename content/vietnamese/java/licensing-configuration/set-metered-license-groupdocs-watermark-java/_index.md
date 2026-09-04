---
date: '2026-01-21'
description: Tìm hiểu cách thiết lập giấy phép cho GroupDocs Watermark trong Java,
  bao gồm cách áp dụng watermark PDF và quản lý việc sử dụng với giấy phép tính theo
  mức.
keywords:
- metered license GroupDocs Watermark Java
- GroupDocs.Watermark setup Java
- Java document security watermarks
title: Cách thiết lập giấy phép cho GroupDocs Watermark (Theo lượt) trong Java
type: docs
url: /vi/java/licensing-configuration/set-metered-license-groupdocs-watermark-java/
weight: 1
---

# Cách Đặt Giấy Phép cho GroupDocs Watermark (Metered) trong Java

Bảo vệ tài sản trí tuệ là ưu tiên hàng đầu của các doanh nghiệp hiện đại, và watermark là cách đã được chứng minh để thực hiện điều đó. Trong hướng dẫn này, bạn sẽ học **cách đặt giấy phép** cho GroupDocs.Watermark bằng phương pháp metered, để có thể **thêm watermark vào file pdf** trong khi vẫn kiểm soát đầy đủ việc sử dụng. Chúng tôi sẽ hướng dẫn từ các yêu cầu trước đến các kịch bản thực tế, và chỉ cho bạn chính xác nơi **sử dụng public private keys** để kích hoạt giấy phép.

## Câu Hỏi Nhanh
- **Giấy phép metered là gì?** Mô hình cấp phép dựa trên mức độ sử dụng, theo dõi mỗi lần gọi API.  
- **Có cần file giấy phép không?** Không – bạn kích hoạt bằng public và private keys.  
- **Yêu cầu phiên bản Java nào?** Java 8 trở lên.  
- **Có thể thêm watermark vào tài liệu pdf không?** Có, API hỗ trợ PDF, DOCX, PPTX và hình ảnh.  
- **Phương pháp này có an toàn không?** Có, các key được truyền qua HTTPS và không bao giờ lưu dưới dạng văn bản thuần.

## Giấy Phép Metered là Gì và Tại Sao Nên Sử Dụng?
Giấy phép metered cho phép bạn trả tiền chỉ cho những gì thực sự tiêu thụ, rất phù hợp cho kiến trúc SaaS hoặc micro‑service. Nó cung cấp khả năng **document security watermark** mà không cần quản lý các file giấy phép truyền thống, và bạn có thể mở rộng hoặc thu hẹp mức sử dụng ngay lập tức.

## Yêu Cầu Trước
Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

1. **GroupDocs.Watermark for Java** ≥ 24.11 (bản phát hành mới nhất).  
2. **JDK 8+** đã được cài đặt và cấu hình `JAVA_HOME`.  
3. **Public và private keys** lấy từ tài khoản GroupDocs của bạn (sẽ dùng trong mã).

## Cài Đặt GroupDocs.Watermark cho Java

### Thông Tin Cài Đặt
Tích hợp GroupDocs.Watermark vào dự án Maven của bạn:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/watermark/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-watermark</artifactId>
      <version>24.11</version>
   </dependency>
</dependencies>
```

> **Mẹo:** URL kho lưu trữ giống nhau cũng được dùng cho tùy chọn tải trực tiếp bên dưới.

#### Tải Trực Tiếp
Tải JAR mới nhất từ trang phát hành chính thức: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Nhận Giấy Phép
Để mở khóa các tính năng cao cấp, bạn cần giấy phép tạm thời hoặc dùng thử. Đăng ký tại [trang web GroupDocs](https://purchase.groupdocs.com/temporary-license/) và sao chép các public/private keys mà họ cung cấp.

### Khởi Tạo Cơ Bản
Khi thư viện đã có trong classpath, bạn có thể khởi tạo như sau:

```java
import com.groupdocs.watermark.License;

public class InitializeWatermark {
    public static void main(String[] args) throws Exception {
        License license = new License();
        // Apply the license using your path to the license file
        license.setLicense("path/to/your/license/file.lic");
    }
}
```

> **Tại sao điều này quan trọng:** Ngay cả khi bạn sử dụng giấy phép metered, việc khởi tạo đối tượng `License` giúp SDK sẵn sàng nhận kích hoạt dựa trên key trong các bước tiếp theo.

## Hướng Dẫn Triển Khai

### Đặt Giấy Phép Metered

#### Bước 1: Định Nghĩa Public và Private Keys
```java
// Step 1: Define the public and private keys for the metered license.
String publicKey = "*****"; // Replace with your actual public key
String privateKey = "*****"; // Replace with your actual private key
```
Các key này **sử dụng public private keys** để xác thực tài khoản của bạn một cách an toàn.

#### Bước 2: Tạo Instance của Lớp Metered
```java
// Step 2: Create an instance of Metered class.
Metered metered = new Metered();
```
Lớp `Metered` chịu trách nhiệm theo dõi việc sử dụng phía sau.

#### Bước 3: Đặt Giấy Phép Metered Bằng Các Key Đã Cung Cấp
```java
// Step 3: Set the metered license using the provided keys.
metered.setMeteredKey(publicKey, privateKey);
```
Sau lệnh này, SDK đã được cấp phép đầy đủ và bạn có thể bắt đầu **thêm watermark pdf** hoặc **tạo tài liệu có watermark**.

### Tại Sao Nên Dùng Public/Private Keys Thay Vì File Giấy Phép?
- **Bảo mật:** Các key không bao giờ được ghi vào đĩa dưới dạng văn bản thuần.  
- **Linh hoạt:** Chuyển môi trường (dev, test, prod) mà không cần sao chép file.  
- **Mở rộng:** Lý tưởng cho các triển khai cloud‑native nơi container không thay đổi.

## Ứng Dụng Thực Tiễn

1. **Document Security:** Nhúng watermark hiển thị hoặc ẩn trong PDF để ngăn chặn việc phân phối trái phép.  
2. **Theo Dõi Sử Dụng:** Giám sát số lượng tài liệu được xử lý mỗi tháng, giúp bạn duy trì trong hạn mức metered.  
3. **Tích Hợp CMS:** Tự động **áp dụng watermark pdf** cho mọi file tải lên trong hệ thống quản lý nội dung.

## Các Lưu Ý Về Hiệu Suất

- **Chỉ áp dụng watermark khi cần** – tránh xử lý các batch lớn không cần thiết.  
- **Tái sử dụng instance `Metered`** giữa các yêu cầu để giảm chi phí tạo đối tượng.  
- **Giám sát bộ nhớ** khi xử lý hình ảnh độ phân giải cao; SDK cung cấp API streaming để giảm footprint.

## Các Vấn Đề Thường Gặp và Giải Pháp
| Vấn đề | Giải pháp |
|-------|----------|
| Keys bị từ chối | Kiểm tra lại xem có khoảng trắng hoặc ngắt dòng thừa trong chuỗi không. |
| Giấy phép không được kích hoạt | Đảm bảo bạn đã gọi `metered.setMeteredKey(...)` **trước** bất kỳ thao tác watermark nào. |
| Lỗi out‑of‑memory với PDF lớn | Dùng `WatermarkOptions.setUseMemoryCache(true)` để chuyển xử lý sang đĩa. |

## Câu Hỏi Thường Gặp

**H: Giấy phép metered là gì, và tại sao tôi nên dùng?**  
Đ: Giấy phép metered theo dõi mỗi lần gọi API, cho phép bạn chỉ trả tiền cho mức sử dụng thực tế và dễ dàng mở rộng ứng dụng.

**H: Tôi có thể chuyển đổi giữa file giấy phép dùng thử và key metered không?**  
Đ: Có. Chỉ cần gọi `license.setLicense("path/to/file.lic")` cho bản dùng thử, sau đó thay bằng `metered.setMeteredKey(...)`.

**H: Điều gì sẽ xảy ra nếu tôi nhập sai public hoặc private key?**  
Đ: SDK sẽ ném ngoại lệ xác thực và chặn truy cập vào các tính năng cao cấp.

**H: Có giới hạn số watermark tôi có thể thêm mỗi tháng không?**  
Đ: Giới hạn phụ thuộc vào thỏa thuận với GroupDocs; kiểm tra bảng điều khiển của bạn để biết quota cụ thể.

**H: Phương pháp này có hoạt động với file ảnh không chỉ PDF?**  
Đ: Hoàn toàn có. API tương tự hỗ trợ JPEG, PNG, BMP và các định dạng ảnh phổ biến khác.

## Tài Nguyên

- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)

---

**Cập nhật lần cuối:** 2026-01-21  
**Đã kiểm tra với:** GroupDocs.Watermark 24.11 for Java  
**Tác giả:** GroupDocs