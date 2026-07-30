---
date: '2026-07-30'
description: Tìm hiểu cách thiết lập giấy phép cho GroupDocs.Watermark trong Java,
  bảo vệ tài liệu của bạn một cách hiệu quả và quản lý việc sử dụng một cách tối ưu.
keywords:
- how to set license
- GroupDocs Watermark Java
- metered licensing Java
lastmod: '2026-07-30'
og_description: Cách thiết lập giấy phép cho GroupDocs.Watermark trong Java. Hướng
  dẫn này sẽ đưa bạn qua quá trình cài đặt SDK, lấy khóa tính theo mức sử dụng, và
  cấu hình giấy phép để bảo vệ tài liệu của bạn.
og_image_alt: 'Guide: Set license for GroupDocs Watermark in Java'
og_title: Cách thiết lập giấy phép cho GroupDocs Watermark trong Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-30'
  description: Learn how to set license for GroupDocs.Watermark in Java, protect your
    documents effectively and manage usage efficiently.
  headline: How to Set License for GroupDocs Watermark in Java
  type: TechArticle
- description: Learn how to set license for GroupDocs.Watermark in Java, protect your
    documents effectively and manage usage efficiently.
  name: How to Set License for GroupDocs Watermark in Java
  steps:
  - name: Define the public and private keys
    text: Enter the keys you received after registering for a temporary license. `Metered`
      is the GroupDocs.Watermark class that handles metered licensing and usage tracking.
      *Place your keys in a secure location (environment variables, encrypted config,
      etc.) before using them in code.*
  - name: Create an instance of the Metered class
    text: Instantiate the `Metered` object with your keys. This object will be passed
      to the watermark engine during initialization.
  - name: Set the metered license using the provided keys
    text: Call the `setLicense` method (or the equivalent API call) with your public
      and private keys. Once set, all subsequent watermark operations will be billed
      according to your usage. > **Pro tip:** Keep the keys out of source control.
      Use a secrets manager or encrypted properties file to avoid accidenta
  type: HowTo
- questions:
  - answer: A temporary license is time‑limited and ideal for evaluation, while a
      perpetual license provides unlimited use without recurring fees.
    question: What is the difference between a temporary and a perpetual license?
  - answer: Yes—replace the metered key initialization with a call to `engine.setLicense("path/to/license/file")`.
    question: Can I switch from a metered license to a perpetual one without code
      changes?
  - answer: The SDK falls back to offline mode; watermarking continues but usage won’t
      be reported until connectivity is restored.
    question: What happens if the metered service is unreachable?
  - answer: The SDK can handle files up to 1 GB; larger files should be split or processed
      in streaming mode.
    question: Are there file‑size limits for watermarking?
  - answer: It works on any platform that supports Java 8+, including Windows, Linux,
      and macOS.
    question: Does the metered license work on all operating systems?
  type: FAQPage
tags:
- set license
- GroupDocs Watermark
- Java licensing
- metered license
- document security
title: Cách thiết lập giấy phép cho GroupDocs Watermark trong Java
type: docs
url: /vi/java/licensing-configuration/set-metered-license-groupdocs-watermark-java/
weight: 1
---

# Cách Đặt Giấy Phép cho GroupDocs Watermark trong Java

Bảo vệ sở hữu trí tuệ là ưu tiên hàng đầu cho các ứng dụng hiện đại, và watermark là cách đã được chứng minh để ngăn chặn việc phân phối trái phép. Nếu bạn đang sử dụng **GroupDocs.Watermark for Java**, bạn sẽ cần một giấy phép có thể theo dõi việc sử dụng và mở rộng theo nhu cầu. Hướng dẫn này giải thích **cách đặt giấy phép** cho GroupDocs.Watermark trong Java, từ việc cài đặt SDK đến cấu hình khóa metered báo cáo mức tiêu thụ trở lại dịch vụ.

## Câu trả lời nhanh
- **Giấy phép metered là gì?** Đó là một giấy phép dựa trên mức sử dụng, ghi lại mỗi cuộc gọi API, cho phép bạn chỉ trả tiền cho những gì bạn tiêu thụ.  
- **Tôi có cần dùng thử trước không?** Có, bạn có thể yêu cầu giấy phép tạm thời từ trang GroupDocs để đánh giá sản phẩm.  
- **Yêu cầu phiên bản Java nào?** Java 8 hoặc mới hơn; SDK được biên dịch cho JDK 8+.  
- **Tôi có thể chuyển sang giấy phép vĩnh viễn sau này không?** Chắc chắn – chỉ cần thay thế các khóa metered bằng tệp giấy phép vĩnh viễn.  
- **Cài đặt có tương thích với Maven không?** Có, các tọa độ Maven được cung cấp để quản lý phụ thuộc một cách liền mạch.

## Giấy phép metered cho GroupDocs Watermark là gì?
Giấy phép metered là một quyền sử dụng được kích hoạt trên đám mây do GroupDocs cung cấp, ghi lại mỗi thao tác watermark được thực hiện bởi SDK. Mỗi cuộc gọi API được ghi lại trên máy chủ cấp phép của GroupDocs, cho phép thanh toán theo mức sử dụng thực tế. Mô hình này cung cấp cho các nhà phát triển thông tin thời gian thực về mức tiêu thụ và giúp kiểm soát chi phí đồng thời đảm bảo truy cập đầy đủ các tính năng.

## Tại sao nên sử dụng giấy phép metered với GroupDocs Watermark?
GroupDocs.Watermark hỗ trợ hơn năm mươi định dạng đầu vào và đầu ra — bao gồm PDF, DOCX, PPTX và các loại hình ảnh khác — và có thể xử lý các tệp lên tới 1 GB mà không cần tải toàn bộ tài liệu vào bộ nhớ, giúp duy trì hiệu suất. Khi sử dụng giấy phép metered, bạn chỉ trả tiền cho các thao tác bạn thực sự thực hiện, cho phép giải pháp mở rộng một cách hiệu quả về chi phí trong khi vẫn giữ toàn bộ quyền truy cập vào mọi tính năng.

## Yêu cầu trước
- **GroupDocs.Watermark for Java** phiên bản 24.11 hoặc mới hơn.  
- Java Development Kit (JDK) 8 hoặc mới hơn đã được cài đặt và cấu hình.  
- Kiến thức cơ bản về Maven hoặc quản lý JAR thủ công.  
- Khóa giấy phép tạm thời hoặc vĩnh viễn từ cổng GroupDocs.

## Cách đặt giấy phép metered cho GroupDocs Watermark trong Java?
Tải các khóa công khai và riêng tư của bạn, tạo một thể hiện `Metered`, và áp dụng giấy phép — tất cả trong ba bước ngắn gọn. Cách tiếp cận này đảm bảo mỗi yêu cầu watermark đều được tính vào tài khoản của bạn, cung cấp cho bạn khả năng quan sát đầy đủ mức tiêu thụ.

### Bước 1: Xác định khóa công khai và khóa riêng tư
Nhập các khóa bạn nhận được sau khi đăng ký giấy phép tạm thời.

`Metered` là lớp của GroupDocs.Watermark chịu trách nhiệm quản lý giấy phép metered và theo dõi việc sử dụng.  
*Đặt các khóa của bạn ở vị trí an toàn (biến môi trường, cấu hình được mã hoá, v.v.) trước khi sử dụng chúng trong mã.*

### Bước 2: Tạo một thể hiện của lớp Metered
Khởi tạo đối tượng `Metered` với các khóa của bạn. Đối tượng này sẽ được truyền vào engine watermark trong quá trình khởi tạo.

```text
Metered metered = new Metered(System.getenv("GROUPDOCS_PUBLIC_KEY"),
                               System.getenv("GROUPDOCS_PRIVATE_KEY"));
```

### Bước 3: Đặt giấy phép metered bằng các khóa đã cung cấp
Gọi phương thức `setLicense` (hoặc cuộc gọi API tương đương) với khóa công khai và khóa riêng tư của bạn. Khi đã thiết lập, tất cả các thao tác watermark tiếp theo sẽ được tính phí dựa trên mức sử dụng của bạn.

```text
WatermarkEngine engine = new WatermarkEngine();
engine.setMeteredLicense(metered);
```

> **Mẹo chuyên nghiệp:** Giữ các khóa ra khỏi hệ thống kiểm soát mã nguồn. Sử dụng trình quản lý bí mật hoặc tệp cấu hình được mã hoá để tránh lộ ra ngoài một cách vô tình.

## Thiết lập GroupDocs.Watermark cho Java

### Thông tin Cài đặt

Tích hợp GroupDocs.Watermark vào dự án của bạn bằng Maven hoặc tải JAR trực tiếp.

**Cấu hình Maven:**  
Thêm cấu hình sau vào tệp `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>watermark</artifactId>
    <version>24.11</version>
</dependency>
```

**Tải trực tiếp:**  
Tải phiên bản mới nhất từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Nhận giấy phép

Để mở khóa toàn bộ chức năng, hãy lấy bản dùng thử miễn phí hoặc giấy phép tạm thời:

- Đăng ký trên [trang web GroupDocs](https://purchase.groupdocs.com/temporary-license/) để bắt đầu.  
- Sau khi có được các khóa, tích hợp chúng vào dự án của bạn như được mô tả trong hướng dẫn triển khai.

### Khởi tạo và Cấu hình Cơ bản

Khi SDK đã được thêm vào dự án, nhập các namespace cần thiết và tạo thể hiện engine watermark như đã minh họa trong các đoạn mã ở trên.

## Mẹo Khắc phục sự cố
- **Invalid keys:** Kiểm tra lại xem khóa công khai và khóa riêng tư có khớp chính xác không; một lỗi đánh máy duy nhất sẽ ngăn không cho kích hoạt.  
- **License file path errors:** Nếu bạn muốn sử dụng giấy phép dạng tệp, hãy đảm bảo đường dẫn tệp là tuyệt đối hoặc được giải quyết đúng tương đối với thư mục làm việc.  
- **Network issues:** Giấy phép metered yêu cầu các cuộc gọi HTTPS ra ngoài; xác nhận rằng tường lửa của bạn cho phép lưu lượng tới `api.groupdocs.com`.

## Ứng dụng Thực tiễn
1. **Document Security:** Thêm watermark hiển thị hoặc ẩn vào PDF, tài liệu Word và hình ảnh để bảo vệ dữ liệu nhạy cảm của công ty.  
2. **Usage Tracking:** Tạo báo cáo về số lượng tài liệu đã được watermark mỗi ngày, hữu ích cho việc lập ngân sách và tuân thủ.  
3. **CMS Integration:** Tự động chèn watermark trong quy trình xuất bản nội dung, với giấy phép được áp dụng tự động.

## Các yếu tố về Hiệu năng

**Tối ưu hoá Hiệu năng:**  
- Áp dụng watermark chỉ khi cần thiết; bỏ qua xử lý các tệp đã được bảo vệ.  
- Đối với các lô lớn, tái sử dụng cùng một thể hiện `WatermarkEngine` để tránh việc khởi tạo lặp lại.

**Thực hành tốt:**  
- Giám sát việc sử dụng heap của JVM khi xử lý các PDF có hàng trăm trang; cân nhắc các API streaming nếu bộ nhớ trở thành nút thắt.  
- Bật ghi log ở mức `INFO` để ghi lại các cuộc gọi giấy phép mà không làm đầy console.

## Kết luận

Trong hướng dẫn này, chúng tôi đã trình bày **cách đặt giấy phép** cho GroupDocs.Watermark trong Java, từ cài đặt Maven đến cấu hình khóa metered. Bằng cách thực hiện các bước, bạn sẽ có khả năng theo dõi sử dụng chính xác, thanh toán linh hoạt và bảo vệ tài liệu mạnh mẽ — tất cả mà không ảnh hưởng đến hiệu năng.

**Các bước tiếp theo:**  
- Thử nghiệm các kiểu watermark khác nhau (văn bản, hình ảnh, chéo).  
- Khám phá các tính năng nâng cao như watermark có điều kiện dựa trên vai trò người dùng.  
- Xem bảng điều khiển phân tích của GroupDocs để theo dõi xu hướng tiêu thụ.

Sẵn sàng bảo vệ tài liệu của bạn? Triển khai giải pháp ngay hôm nay và yên tâm vì tài sản của bạn được bảo vệ và chi phí giấy phép được minh bạch.

## Câu hỏi thường gặp

**Q: Sự khác nhau giữa giấy phép tạm thời và giấy phép vĩnh viễn là gì?**  
A: Giấy phép tạm thời có thời hạn và thích hợp cho việc đánh giá, trong khi giấy phép vĩnh viễn cung cấp việc sử dụng không giới hạn mà không có phí định kỳ.

**Q: Tôi có thể chuyển từ giấy phép metered sang giấy phép vĩnh viễn mà không thay đổi mã không?**  
A: Có — thay thế việc khởi tạo khóa metered bằng một lời gọi tới `engine.setLicense("path/to/license/file")`.

**Q: Điều gì sẽ xảy ra nếu dịch vụ metered không thể truy cập?**  
A: SDK sẽ chuyển sang chế độ offline; watermark vẫn tiếp tục nhưng mức sử dụng sẽ không được báo cáo cho đến khi kết nối được khôi phục.

**Q: Có giới hạn kích thước tệp cho việc watermark không?**  
A: SDK có thể xử lý các tệp lên tới 1 GB; các tệp lớn hơn nên được chia nhỏ hoặc xử lý ở chế độ streaming.

**Q: Giấy phép metered có hoạt động trên mọi hệ điều hành không?**  
A: Nó hoạt động trên bất kỳ nền tảng nào hỗ trợ Java 8+, bao gồm Windows, Linux và macOS.

---

**Last Updated:** 2026-07-30  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

**Tài nguyên**

- [Tài liệu](https://docs.groupdocs.com/watermark/java/)
- [Tham chiếu API](https://reference.groupdocs.com/watermark/java)
- [Tải xuống](https://releases.groupdocs.com/watermark/java/)
- [Kho GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Diễn đàn Hỗ trợ miễn phí](https://forum.groupdocs.com/c/watermark/10)
- [Mua giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/)

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

```java
// Step 1: Define the public and private keys for the metered license.
String publicKey = "*****"; // Replace with your actual public key
String privateKey = "*****"; // Replace with your actual private key
```

```java
// Step 2: Create an instance of Metered class.
Metered metered = new Metered();
```

```java
// Step 3: Set the metered license using the provided keys.
metered.setMeteredKey(publicKey, privateKey);
```

## Hướng dẫn liên quan

- [Hướng dẫn Cấp phép và Cấu hình GroupDocs.Watermark cho Java](/watermark/java/licensing-configuration/)
- [Cách Thiết lập Giấy phép GroupDocs.Watermark trong Java: Hướng dẫn Toàn diện](/watermark/java/licensing-configuration/groupdocs-watermark-licensing-java-guide/)
- [Hướng dẫn Watermark trong Java: Bảo mật Tài liệu với API GroupDocs.Watermark](/watermark/java/getting-started/java-watermark-groupdocs-guide/)