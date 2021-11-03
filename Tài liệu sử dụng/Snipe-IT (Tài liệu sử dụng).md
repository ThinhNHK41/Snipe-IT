**Hướng dẫn sử dụng Snipe-IT cơ bản**

**I. Thiết lập tài khoản**

**1. Tạo user và phân quyền**

\- Để quản lý user chúng ta vào tab People, để tạo user mình bấm tiếp
vào Create New.

![](.//media/image1.png)


![](.//media/image2.png)


![](.//media/image3.png)


\- Sau khi tạo user thì Admin có thể cấp quyền cho user đó và tùy chỉnh
các thông số của tài khoản đó.

![](.//media/image4.png)


![](.//media/image5.png)


\- Ở mục Permission bạn sẽ thấy user tạo ra sẽ được sở hữu một trong 3
quyền:

-   **SuperAdmin**: Có thể chỉnh sửa các cài đặt quản trị, tạo nhóm, vị
    trí, gán, trạng thái tài sản,\... và không bị ràng buộc bởi cấu hình
    \"Full company support\".

-   **Admin**: Không thể truy cập vào Admin Setting và bị ràng buộc bởi
    cấu hình \"Full company support\". Còn lại tất cả các chức năng như
    thêm, sửa, xóa trên các khía cạnh khác đều sử dụng được.

-   **Khác**: Không thể truy cập vào Admin Setting. Các quyền khác được
    cấp dựa trên group hoặc được cấp riêng cho các nhân ấy sở hữu.

\- Ở quyền là \"Khác (other)\" chẳng hạn như thêm hoặc xem user, quyền
tạo, sửa, xóa tài sản,\... đều được giả định ở quyền admin/superadmin
mặc dù bạn đang không có quyền như vậy. Nói dễ hiểu là ví dụ bạn gán
quyền xóa tài sản cho user thì nó thực hiện quyền xóa ở cấp độ
admin/superadmin (mượn quyền để xóa).

\- Ngoài ra bạn cũng có thể sử dụng quyền của Group để quản lý các user
thuộc chung vai trò cụ thể nào đó. Ví dụ như user của phòng kỹ thuật thì
đưa chung vào nhóm kỹ thuật. Và tất nhiên quyền của group ra sao thì
user được kế thừa như vậy.

![](.//media/image6.png)


![](.//media/image7.png)


**2. Lựa chọn ngôn ngữ hiển thị**

\- Cộng đồng mạng luôn là điểm tuyệt nhất của mã nguồn mở và Snipe-IT
cũng không ngoại lệ. Bằng sự hỗ trợ của cộng đồng và nhóm tình nguyện
viên vì Snipe-IT được dịch ra nhiều ngôn ngữ khác nhau, bạn có thể thay
đổi ngôn ngữ hiển thị bằng cách vào: **Admin \>\> Setting \>\>
Localization Language, date display**

![](.//media/image8.png)


\- Ngoài ra bạn cũng có thể thay đổi được cách hiển thị thời gian, đơn
vị tiền gán cho tài sản và thay đổi được cả ngôn ngữ Tiếng Việt. Ngoài
thay đổi ngôn ngữ, bạn có thể thay đổi cách hiển thị thời gian và đơn vị
tiền tệ.

![](.//media/image9.png)


\- Sau khi bạn đăng xuất ra khỏi tài khoản Admin thì nó sẽ kích hoạt lại
ngôn ngữ Tiếng Việt

![](.//media/image10.png)


\- Sau đó để có Dashboard Tiếng Việt sau khi đăng nhập ta cần tùy chỉnh
ngôn ngữ trong profile của từng user sau đó Save lại

![](.//media/image11.png)


![](.//media/image12.png)


\- Như vậy ta đã có dashboard cho user với Tiếng Việt

![](.//media/image13.png)


![](.//media/image14.png)


**3. Email Alert**

\- Khi bạn là người quản lý tài sản công ty và bạn cần \"ai đó\" nhắc
mình rằng tài sản bàn giao cho nhân viên gần hết hạn hay license phần
mềm nào đó gần hết hạn thì chức năng này là giải pháp.

\- Bằng cách vào : Admin \>\> Setting \>\> Notifications (Email Alerts)
và bạn có thể thiết lập tại đây.

![](.//media/image15.png)


![](.//media/image16.png)


**Lưu ý**: Ta có thể thêm vào một hay nhiều địa chỉ mail để nhận thông
báo hết hạn, miễn là ngăn cách bởi dấu \",\" là được.

**4. Google Authenticator**

\- Kê từ phiên bản 3.6, Snipe-IT hỗ trợ xác thực 2 bước của Google. Để
bật tính năng này bạn vào: **Admin \>\> Setting \>\> Security
(Two-factor, Password Restrictions)**.

![](.//media/image17.png)


![](.//media/image18.png)


\- Có 3 lựa chọn sẵn có như sau:

-   **Disabled**: Chức năng 2 bước sẽ không được thực hiện với bất kỳ
    user nào.

-   **Selective**: User có thể lựa chọn bật chức năng 2 bước hay không
    trong profile của họ nếu quá trình tạo user hoặc group có bật tính
    năng này.

-   **Required**: Tất cả user đều phải bật tính năng 2 bước này.

\- Ngoài ra còn một số ràng buộc về quy định đặt password như: độ dài,
yêu cầu phải có ký tự đặc biệt, số, chữ hoa, thường,\...

![](.//media/image19.png)


\- Cách hoạt động của chức năng 2 bước này tương tự như xác thực của
google mail nếu bạn từng sử dụng. Đầu tiên khi user đăng nhập, một mã QR
code xuất hiện, bạn phải sử dụng app google authenticator trên
smartphone của mình để quét mã vạch, mã 6 số xuất hiện và bạn điền số
vào trang đăng nhập để login vào.

![](.//media/image20.png)


**II. Thiết lập để sử dụng**

\- Đầu tiên chúng ta cần xem các trường bắt buộc và nên có của 1 tài sản
là những gì:

-   Công ty

-   Thẻ tài sản

-   Kiểu tài sản

-   TÌnh trạng

-   Tên tài sản

-   Ngày mua

-   Nhà cung cấp

-   Vị trí mặc định

-   Hình

-   Người đang sử dụng

VD: Công ty Gaming, văn phòng tại HCM - Hàn Thuyên, Màn hình DELL 24
inch, mua tại Phong Vũ, nhân viên Annlt đang sử dụng, mua ngày
25/10/2021.

Sau đây ta bắt đầu tạo các thông tin cần thiết để đưa được tài sản vào
phần mềm

**1. Công ty**

\- Các bạn có thể tạo nhiều công ty dựa theo quy mô và cách tổ chức của
công ty cần sử dụng. Như ở đây mình tạo 1 công ty để làm mẫu - Công ty
Gaming

-   **Cài đặt > Các công ty > Tạo mới**

![](.//media/image21.png)


![](.//media/image22.png)

![](.//media/image23.png)


**2. Danh mục tài sản**

\- Chúng ta xác định màn hình này thuộc về đống tài sản Gaming - tùy vào
tài sản mà bạn cần quản lý thuộc danh mục nào mà tạo (VD: nội ngoại
thất, dụng cụ văn phòng, vật liệu xây dựng,\...), nên sẽ tạo danh mục
như sau:

-   **Cài đặt > Danh mục > Tạo mới**

![](.//media/image24.png)

\- Nhập tên danh mục (Thiết bị Gaming) \> Loại (Ở đây có nhiều loại tùy
theo mà các bạn chọn, ở đây mình chọn nó là Asset) \> Lưu (Phần này
không cần có hình cũng được)

\- \"Loại\" ở đây ta có thể thay đổi ví dụ như bản quyền, phụ kiện hay
vật tư, tùy theo mình muốn quản lý cái gì, ở đây chủ yếu mình chỉ quản
lý tài sản (Asset).

![](.//media/image25.png)


![](.//media/image26.png)

**3. Nhà sản xuất**

-   **Cài đặt > Nhà sản xuất > Tạo mới**

![](.//media/image27.png)


![](.//media/image28.png)


![](.//media/image29.png)


**4. Kiểu tài sản**

\- Phần này thì tùy mình xác định theo các loại thiết bị trong công ty
mình. VD: Công ty mình chỉ có màn hình 24 inch nhưng sẽ có nhiều hãng

-   **Cài đặt > Kiểu tài sản > Tạo mới**

![](.//media/image30.png)


\- Điền tên tài sản (Màn hình 24 inch) \> Chọn nhà sản xuất (DELL - đã
tạo phía trên) \> Chọn tên hạng mục (Thiết bị Gaming - Đã tạo ở phần
danh mục) \> Lưu

![](.//media/image31.png)


**5. Nhà cung cấp**

\- Tạo đơn vị cung cấp thiết bị - ở đây sẽ là Phong Vũ

-   **Cài đặt > Nhà cung cấp > Tạo mới**

![](.//media/image32.png)


\- Điền tên nhà cung cấp (Phong Vũ) \> Lưu

![](.//media/image33.png)


**6. Địa phương**

\- Tạo địa chỉ công ty bạn, nếu có chi nhánh khác thì tạo thêm, hoặc
dạng tập đoàn đứng tên nhiều công ty thì bạn tạo thêm công ty ở phần 1

-   **Cài đặt > Địa phương > Tạo mới**

![](.//media/image34.png)


\- Điền tên địa phương (Hàn Thuyên) \> Lưu

![](.//media/image34.png)


**7. Thành viên**

\- Về cơ bản thì tạo người dùng để gán tài sản là chính, ngoài ra còn có
một số tính năng khác mình sẽ giới thiệu thêm sau

-   **Thành viên**

![](.//media/image35.png)


\- Những thông tin có dấu cam phía sau là bắt buộc

![](.//media/image36.png)


**8. Tạo tài sản**

\- Bắt đầu tạo tài sản dựa theo thông tin đã tạo.

![](.//media/image37.png)


\- **Lưu ý:**

-   Thẻ tài sản bạn phải tư duy hoặc thống nhất theo chuẩn bên kế toán
    đã lưu để sau này kiểm kê trích xuất dữ liệu cho đồng bộ 2 bên dễ
    dàng kiểm tra.

-   Kiểm tài sản bạn sẽ thấy có tùy chọn theo các thông tin đã tạo bên
    trên với logic: danh mục - hãng / kiểu tài sản (còn ở phần cài đặt -
    kiểu tài sản thì hiển thị sẽ không giống).

-   Tình trạng: thì thường sẽ là ready to deploy do hiện tại chúng ta
    kiểm kê và nhập liệu cho tài sản đang sử dụng được, khác cái là ta
    có check out vào đối tượng nào hay chưa - nếu chưa check out thì xem
    như đó là hàng tồn kho chờ được cấp, phần này bạn nhập chừng 10-20
    thiết bị thì sẽ thấy được. Và bạn có thể tạo thêm nhiều tình trạng
    tài sản khác tùy theo nhu cầu của bạn tại Cài đặt > Tình trạng nhãn.

-   Check out đến: thì thường bạn sẽ tạo danh sách thành viên cho toàn
    bộ nhân viên trong công ty rồi check out tài sản theo người dùng,
    hoặc tùy nhu cầu mà check out theo địa phương.

-   Tên tài sản: Ở đây bạn có thể ghi cho đầy đủ thông tin cơ bản của
    tài sản để nhìn vào biết cơ bản đó là món gì, thông tin này có thể
    giống nhau giữa các tài sản.

-   Nên có hình ảnh cho từng tài sản để kiểm kê dễ hơn.

![](.//media/image38.png)


![](.//media/image39.png)


![](.//media/image40.png)


**9. Import file**

\- Về cơ bản thì ta đã nhập liệu cho tài sản, sau khi nhập thủ công để
nắm cơ chế hoạt động. Nhưng để tiện lợi và nhanh gọn hơn, ta sẽ cùng tìm
hiểu về cách import file vào hàng loạt với sample csv. Ở mục Nhập

![](.//media/image41.png)


\- Ở đây ta sẽ sử dụng 1 file excel để nhập thông tin cần thiết và
import vào Snipe-IT

![](.//media/image42.png)


![](.//media/image43.png)


![](.//media/image44.png)


Ngoài ra, còn có rất nhiều các chức năng hữu ích khác mà Snipe-IT mang
lại cho ta để giúp việc quản lý khối tài sản \"khổng lồ\" về phần cứng
và phần mềm một cách đơn giản mà hiệu quả. Bạn cần trực tiếp sử dụng
Snipe-IT để có cái nhìn trực quan nhất về các tiện ích mà nó mang lại.

**10. Tùy chỉnh Việt Hóa**

\- Ở đây, ta có thể sử dụng ngôn ngữ Tiếng Việt dựa vào cài đặt ngôn ngữ
cho từng User. Ngoài ra, ta có thể tự thiết lập nội dung Tiếng Việt theo
ý mình thông qua các tập tin trên local

\- Ta sẽ truy cập vào đường dẫn sau và có thể thấy tất cả các file cài
đặt của Snipt-IT:

![](.//media/image45.png)

![](.//media/image46.png)

\- Sau đó ta vào thư mục resources:

![](.//media/image47.png)


\- Tiếp theo đến thư mục lang là thư mục chứa file nội dung của các ngôn
ngữ khác nhau (ở đây tiếng việt ở trong thư mục vi):

![](.//media/image48.png)


\- ở thư mục vi ta có thể tùy chỉnh các nội dung tiếng việt cho Snipe-IT
của mình thông qua các file .php:

![](.//media/image49.png)


![](.//media/image50.png)


![](.//media/image51.png)


![](.//media/image52.png)


**Tài liệu tham khảo**

https://itforvn.com/snipeit-huong-dan-su-dung-p1-co-ban/

https://snipe-it.readme.io/docs/importing
