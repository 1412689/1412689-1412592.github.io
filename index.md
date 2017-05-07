# ĐỀ TÀI TÌM HIỂU Backend - Play(Scala)

## Thông tin nhóm

|   MSSV  |        Họ Tên      | Nội Dung Đóng Góp | Đánh Giá |
| :--------- | :-------------------- | :------------------- | :---------- |
| 1412689 | Hoàng Thị Bích Vân |                   |          |
| 1412592 | Võ Hiếu Trung      |                   |          |

## Sơ lược công nghệ hiện nay về Backend
### Kiến trúc MVC – Model-View-Controller

Kiến trúc MVC là một kiến trúc dành cho ứng dụng web, được áp dụng rộng rãi trong nhiều ngôn ngữ và framework khác nhau. Việc áp dụng kiến trúc MVC nhằm mục tiêu phân tách rõ ràng giữa ba thành phần của hầu hết các ứng dụng web.

Kiến trúc MVC có ba lớp (layer):

- Model: quy định cấu trúc của dữ liệu, chứa dữ liệu và các thao tác truy xuất, cập nhật trên chúng. Ngoài ra model còn giao tiếp với các lớp khác (cung cấp các phương thức đăng ký và hủy đăng ký view, Thông báo đến view khi trạng thái bị thay đổi)

- View: đóng vai trò hiển thị các model ra bên ngoài cho người dùng xem. Có thể có nhiều view cho cùng một model. View sẽ được thông báo nếu các model của nó thay đổi và view sẽ cập nhật khi cần thiết. View còn có nhiệm vụ chuyển thông tin nhập liệu đến controller.

- Controller: giao tiếp với người dùng và chuyển những hành động của người dùng cùng các nhập liệu thành các lời gọi hàm đến thành phần model và thay đổi trạng thái của model, bên cạnh đó thành phần này còn có vai trò chọn thành phần view phù hợp dựa trên các cấu hình của người dùng và gián tiếp làm thay đổi view thông qua model.

Từ đó kiến trúc MVC chia ứng dụng ra ba thành phần tương ứng là:

- Thành phần dữ liệu

- Thành phần hiển thị

- Thành phần xử lý [1]
<blockquote class="imgur-embed-pub" lang="en" data-id="iIz7mb5"><a href="//imgur.com/iIz7mb5"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>

Thứ tự tác động giữa các lớp từ lúc có hành động cần xử lý từ phía người dùng cho đến lúc đáp ứng:

1. Người dùng thực hiện hành động

2. Controller được thông báo

3. Controller yêu cầu thay đổi model nếu cần thiết

4. Controller yêu cầu đến view cập nhật

5. Model thông báo cho view rằng nodel có thay đổi

6. View lấy thông tin dữ liệu cần thiết từ model

7. View cập nhật hiển thị cho người dùng

Kiến trúc MVC có rất nhiều ưu điểm:

- Tách biệt model với view: dễ bảo trì, chọn lựa view phù hợp trong lúc thực thi dựa trên luồng làm việc, cài đặt của người dùng, hoặc trạng thái của model.

- Tách biệt controller với model: linh hoạt trong việc lựa chọn phương thức của model đáp ứng hành động của người dùng.

- Ứng dụng đa hiển thị hỗ trợ cho nhiều nền tảng.

- Bảo trì, nâng cấp, kiểm thử độc lập giữa các lớp.

- Dễ dàng thêm vào hiển thị của dữ liệu khi kỹ thuật phát triển.

- Xử lý linh động lúc chạy.

- Tái sử dụng mã nguồn (1 view có thể được sử dụng cho nhiều model).

### Ajax – Asynchronous JavaScript and XML

Ajax là một tập hợp các công nghệ phát triển web dành cho phía máy trạm để tạo các ứng dụng web động hay các ứng dụng giàu tính Internet (rich Internet application). Từ Ajax được ông Jesse James Garrett đưa ra và dùng lần đầu tiên vào tháng 2 năm 2005 để chỉ kỹ thuật này, mặc dù các hỗ trợ cho Ajax đã có trên các chương trình duyệt từ 10 năm trước. Với Ajax, ứng dụng web có thể gửi và nhận dữ liệu ngầm không đồng bộ từ máy chủ mà không ảnh hưởng đến trang web hiện hành. Bằng cách tách riêng thành phần dữ liệu với thành phần hiển thị, ngữ cảnh được thay đổi liên tục để thích ứng mà không cần phải tải lại toàn bộ trang web. Trong thực tế, XML thường đươc thay thế bởi JSON (sẽ nói rõ trong phần sau) bởi những thuận lợi mà JavaScript mang lại.

Ajax không phải là một kỹ thuật đơn lẻ mà là một nhóm các kỹ thuật phát triển web có tính tương tác cao bằng cách kết hợp các ngôn ngữ:

- HTML (hoặc XHTML) với CSS trong việc hiển thị thông tin

- Mô hình DOM (Document Object Model), được thực hiện thông qua JavaScript, nhằm hiển thị thông tin động và tương tác với những thông tin được hiển thị

- Đối tượng XMLHttpRequest để trao đổi dữ liệu một cách không đồng bộ với máy chủ web

- XML thường là định dạng cho dữ liệu truyền, mặc dầu bất cứ định dạng nào cũng có thể dùng, bao gồm HTML định dạng trước, văn bản thuần (plain text), Json và ngay cả EBML

Giống như DHTML, LAMP hay SPA, Ajax tự nó không phải là một công nghệ mà là một thuật ngữ mô tả việc sử dụng kết hợp một nhóm nhiều công nghệ với nhau. Trong đó, HTML và CSS được kết hợp với nhau để đánh dấu và định kiểu thông tin. DOM và JavaScript kết hợp lại để hiển thị thông tin động và cho phép người dùng tương tác với các thông tin này. JavaScript cùng với đối tượng XMLHttpRequest hỗ trợ việc trao đổi dữ liệu bất đồng bộ giữa trình duyệt và máy chủ nhằm hạn chế việc tải lại nguyên trang. [2]

**Ưu điểm**

- Trong nhiều trường hợp, các trang web chứa rất nhiều nội dung thông thường trong trang. Nếu sử dụng các phương pháp truyền thống, những nội dung đó sẽ phải nạp lại toàn bộ với từng yêu cầu. Tuy nhiên, nếu sử dụng Ajax, một ứng dụng web có thể chỉ yêu cầu cho các nội dung cần thiết phải cập nhật, do đó giảm lượng lớn băng thông và thời gian nạp trang.

- Việc dùng các yêu cầu không đồng bộ (asynchronous request) cho phép giao diện người dùng của ứng dụng hiển thị trên trình duyệt giúp người dùng trải nghiệm sự tương tác cao, với nhiều phần riêng lẻ.

- Việc sử dụng Ajax có thể làm giảm các kết nối đến server, do các mã kịch bản (script) và các style sheet chỉ phải yêu cầu một lần.

**Nhược điểm**

- Các trang web được tạo động không được ghi vào bộ lưu lịch sử lướt web của trình duyệt, do đó nút "back" (quay lui) của trình duyệt sẽ mất tác dụng quay lại trang thái trước đó của trang sử dụng Ajax, thay vào đó sẽ quay lại trang web trước đó mà người dùng ghé thăm. Để khắc phục có thể dùng các IFrame không hiển thị để gây ra sự thay đổi trong lịch sử trình duyệt và thay đổi phần neo của URL (bằng mã a #) khi chạy Ajax và theo dõi những sự thay đổi của nó.

- Việc cập nhật các trang web động cũng gây khó khăn cho người dùng trong việc bookmark (đánh dấu địa chỉ yêu thích) một trạng thái nào đó của ứng dụng. Cũng có những cách khắc phục cho vấn đề này, một số trong đó sử dụng mã xác định đoạn (fragment identifier) URL (phần URL ở sau dấu '#') để lưu vết, và cho phép người dùng đánh dấu và quay lại một trạng thái nào đó của ứng dụng.

- Do hầu hết các web crawler không thực thi mã JavaScript, các ứng dụng web sẽ cung cấp một phương thức thay thế để truy cập nội dung thông thường được truy cập bằng Ajax, để cho phép các máy tìm kiếm lập chỉ mục chúng.

- Bất kỳ người dùng nào có trình duyệt không hỗ trợ Ajax hay JavaScript, hoặc đơn giản là đã bị vô hiệu hóa JavaScript, sẽ đương nhiên không thể sử dụng Ajax. Tương tự, các thiết bị như điện thoại di động, PDA, và thiết bị đọc màn hình (screen reader) có thể không hỗ trợ JavaScript hay đối tượng XMLHttp được yêu cầu. Ngoài ra, các thiết bị đọc màn hình nếu có thể sử dụng Ajax đi nữa cũng vẫn có thể không đọc chính xác các nội dung động.

- Chế độ same origin policy (chế độ gốc đơn điệu) có thể không cho phép sử dụng Ajax thông qua các tên miền, mặc dù W3C đã có một đồ án sơ thảo để cho phép điều này.

- Việc thiếu các chuẩn cơ bản của Ajax đồng nghĩa với việc không có nhiều sự chọn lựa thực tiễn tốt nhất để kiểm tra các ứng dụng Ajax. Các công cụ kiểm thử cho Ajax thường không hiểu các mô hình sự kiện, mô hình dữ liệu và giao thức của Ajax.

- Mở ra một cách thức khác cho việc tấn công của các đoạn mã độc mà những nhà phát triển web có thể không kiểm thử hết được. [3]

### Json web API

Web API là một công nghệ giúp xây dựng các dịch vụ thành phân tán, hỗ trợ cho mô hình MVC.

Json là một kiểu dữ liệu tuân theo quy luật nhất định, hầu hết các ngôn ngữ lập trình hiện nay đều có thể đọc được. Là kiểu dữ liệu dùng để trao đổi trong các ứng dụng web. JSON được xây dựng trên 2 cấu trúc:

- Là tập hợp của các cặp tên và giá trị name-value. Trong những ngôn ngữ khác nhau, đây được nhận thấy như là 1 đối tượng (object), sự ghi (record), cấu trúc (struct), từ điển (dictionary), bảng băm (hash table), danh sách khoá (keyed list), hay mảng liên hợp.

- Là 1 tập hợp các giá trị đã được sắp xếp. Trong hầu hết các ngôn ngữ, this được nhận thấy như là 1 mảng, véc tơ, tập hợp hay là 1 dãy sequence.

Đây là 1 cấu trúc dữ liệu phổ dụng. Hầu như tất cả các ngôn ngữ lập trình hiện đại đều hổ trợ chúng trong 1 hình thức nào đó. Chúng tạo nên ý nghĩa của 1 định dạng hoán vị dữ liệu với các ngôn ngữ lập trình cũng đã được cơ sở hoá trên cấu trúc này. [4]

### Session

Session là một khái niệm phổ biến trong quá trình lập trình web có kết nối với cơ sở dữ liệu database. Đặc biệt chức năng như đăng nhập, đăng xuất giúp người dùng dễ thao tác hơn. Là cách để lưu dữ liệu của người dùng khi sử dụng website. Giá trị của session sẽ được lưu vào tập tin khó nhớ và được sinh ra ngâu nhiên là session id trên máy chủ, đồng thời trên máy tính client cũng được sinh ra 1 file cookie có nội dung đúng với session id (nhằm so khớp giá trị session nào là của client nào).Có thể sử dụng session trong nhiều ngôn ngữ khác nhau.

Session giúp giải quyết vấn đề phân biện giữa các trình duyệt (máy tính) khác nhau trong quá trình giao tiếp. Khi mà việc giao tiếp giữa các trình duyệt (máy tính) và webserver hàng ngày được diễn ra thông qua hàng loạt những giao thức trên internet.

- Phân biệt khi nào bạn đăng nhập vào facebook bằng máy tính của bạn và khi nào bạn đăng nhập facebook bằng máy tính khác.

- Lưu tạm thời sản phẩm mà bạn chọn mua trên website vào giỏ hàng.

Phân biệt session với cookie:

|                 Session                          |                    Cookie                  |
| :-------------------------------------------------- | :-------------------------------------------- |
|- Được lưu trữ ở server                           |-Được lưu trữ trên trình duyệt (máy tính)   |
|- Khi đã đăng nhập vào một trang web và mở tab mới trên trình duyệt thì không cần đăng nhập lại lần nữa, phiên làm việc sẽ kết thúc khi ta tắt trình duyệt đi. Và khi mở trình duyệt lên lại vào lại web đó thì ta lại phải đăng nhập lại.|- Còn với cookie thì chỉ cần đăng nhập một lần và dùng cookie lưu thông tin đăng nhập thì lần sau bạn bạn mở trang web đó nó sẽ tự động đăng nhập mà mình không cần thao tác đăng nhập lại.|
|- Có tính bảo mật cao hơn.                        |- Nếu sơ hở sẽ dễ bị đánh cấp thông tin.|

Việc lựa chọn sử dụng session hay cookie phụ thuộc vào lập trình viên.

## Giới thiệu về play(scala)
###Scala:
Là một dạng ngôn ngữ hàm, kết thừa toàn bộ những gì đã có ở java. Có thể dùng toàn bộ những API của java trong app Scala
###Play framework:
- là một framework cho built một web app với java hoặc Scala
- Có kiến trúc theo mô hình MVC
- Tương tự với JSF hay JEE, Play định nghĩa ra một số biến đặc biệt:
<ul>
  <li>controllers : Quản lý tất cả các object thuộc về namespace (package) Controller</li>
  <li>views : Quản lý tất cả các object thuộc về namespace (package) View</li>
  <li>models : Quản lý tất cả các object thuộc về namespace (package) Model</li>
  <li>routes : Quản lý các path trong việc định nghĩa URL</li>
  <li>request (play.api.mvc.Http) quản lý các request từ client lên server (lấy ra các params từ client gửi lên) => Tương tự việc ta lấy params trong Rails </li>
</ul>

**Những loại database play có thể kết nối**
- MySQL
- DB2
- Derby
- HSQLDB
- MS SQL
- Oracle
- PostgreSQL
...

**/conf/application.conf**: Thư mục này là nơi để bạn define toàn bộ conf của mình như kết nối database, akka...
**/conf/routes**: Đây sẽ là nơi bạn define toàn bộ URI và match với action của hệ thống.
