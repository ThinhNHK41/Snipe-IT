**Công cụ quản lý tài sản Snipe-IT**

**I. Các bước cài đặt Snipe-IT trên CentOS 8 (GUI)**

**Bước 1: Cập nhật phần phụ thuộc Máy chủ & Cài đặt của bạn**

\- Cập nhật hệ thống CentOS của bạn

**sudo dnf -y update**

![](.//media/image1.png)


\- Cài đặt git và thêm kho EPEL

**sudo dnf -y install epel-release vim git**

![](.//media/image2.png)


**Bước 2: Cài đặt máy chủ web Apache**

\- Máy chủ Apache httpd sẽ được sử dụng để lưu trữ ứng dụng web Snipe-IT
Asset Management trên CentOS 8. Cài đặt nó bằng cách chạy các lệnh sau:

**sudo dnf -y install httpd**

![](.//media/image3.png)

\- Khởi động và kích hoạt dịch vụ Apache httpd

**sudo systemctl start httpd.service**

**sudo systemctl enable httpd.service**

![](.//media/image4.png)


**Bước 3: Cài đặt PHP và các module**

\- PHP cũng cần thiết như một phụ thuộc chính. Làm theo hướng dẫn này để
cài đặt PHP 7.4 trên hệ thống của bạn

\- Các kho EPEL và REMI là những yêu cầu chính cho việc cài đặt này.
Thêm chúng vào hệ thống bằng cách chạy lệnh sau:

a\. Thêm kho EPEL và REMI:

**sudo yum -y install
<https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm>**

**sudo yum -y install
<https://rpms.remirepo.net/enterprise/remi-release-8.rpm>**

![](.//media/image5.png)


![](.//media/image6.png)


b\. Cài đặt PHP 7.4 trên CentOS 8:

**sudo dnf -y install dnf-utils**

**sudo dnf module install php:remi-7.4**

![](.//media/image7.png)


![](.//media/image8.png)


c\. Sử dụng lệnh tiếp theo để cài đặt các gói bổ sung:

**sudo dnf update**

![](.//media/image9.png)


Một số module PHP bổ sung được yêu cầu bởi Snipe-IT:

**sudo dnf -y install php-openssl php-pdo php-mbstring php-tokenizer
php-curl php-mysql php-ldap php-zip php-fileinfo php-gd php-dom
php-mcrypt php-bcmath**

![](.//media/image10.png)

**Bước 4: Cài đặt máy chủ cơ sở dữ liệu MariaDB**

a\. Cập nhật hệ thống:

**sudo dnf -y upgrade**

![](.//media/image11.png)


b\. Thêm kho lưu trữ MariaDB 10.4 vào CentOS 8

**sudo tee /etc/yum.repos.d/MariaDB.repo\<\<EOF**

\[mariadb\]

name = MariaDB

baseurl = <http://yum.mariadb.org/10.4/centos8-amd64>

gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB

gpgcheck=1

EOF

![](.//media/image12.png)


Sau khi copy xong nhấn enter để hoàn tất quá trình lưu trữ

c\. Cài đặt kho lưu trữ MariaDB 10.4 cho CentOS 8:

**sudo dnf install boost-program-options**

**sudo dnf install MariaDB-server MariaDB-client
\--disablerepo=AppStream**

![](.//media/image13.png)


![](.//media/image14.png)


\- Nếu bị lỗi các bạn hãy copy thêm dòng code sau để fix lỗi

**curl -sS https://downloads.mariadb.com/MariaDB/mariadb_repo_setup \|
sudo bash**

![](.//media/image15.png)


\- Sau đó hãy copy lại dòng code này để cài đặt:

**sudo dnf install MariaDB-server MariaDB-client
\--disablerepo=AppStream**

![](.//media/image16.png)


\- Tiếp theo hãy cài đặt như bình thường:

**sudo systemctl enable \--now mariadb**

![](.//media/image17.png)


d\. Bảo mật máy chủ cơ sở dữ liệu MariaDB: (Có thể bỏ qua)

**sudo mysql_secure_installation**

e\. Khởi động và kích hoạt MariaDB:

**sudo systemctl start mariadb.service**

**sudo systemctl enable mariadb.service**

![](.//media/image18.png)


**Bước 5: Tạo cơ sở dữ liệu Snipe-IT**

a\. Vào Mariadb để tạo cơ sở dữ liệu:

**mysql -u root -p**

![](.//media/image19.png)


b\. Tạo cơ sở dữ liệu:

CREATE DATABASE **snipeit**;

CREATE USER \'**snipeit**\'@\'localhost\' IDENTIFIED BY
\'**P\@ssw0rd**\'; \# Make sure you have used strong password here.

GRANT ALL PRIVILEGES ON **snipeit**.\* TO \'**snipeit**\'@\'localhost\';

FLUSH PRIVILEGES;

EXIT;

![](.//media/image20.png)


![](.//media/image21.png)


![](.//media/image22.png)


**Bước 6: Cài đặt PHP Composer**

\- Composer là một trình quản lý gói ứng dụng PHP được tạo ra để cung
cấp một định dạng tiêu chuẩn để quản lý các phần phụ thuộc của phần mềm
PHP và các thư viện bắt buộc.

a\. Cài đặt PHP và tải composer:

**sudo dnf install \@php**

**sudo dnf -y install wget**

**wget https://getcomposer.org/installer -O composer-installer.php**

![](.//media/image23.png)


![](.//media/image24.png)


![](.//media/image25.png)


b\. Cài đặt PHP Composer trên CentOS 8:

**sudo php composer-installer.php --filename=composer
--install-dir=/usr/local/bin**

**mv composer.phar /usr/local/bin/composer**

![](.//media/image26.png)


![](.//media/image27.png)

**Bước 7: Tải phần mềm Snipe-IT trên CentOS 8**

**sudo git clone https://github.com/snipe/snipe-it /var/www/html/snipe**

![](.//media/image28.png)


**Bước 8: Cấu hình Snipe-IT**

\- Sau khi bạn có bản sao của Snipe-IT trong máy chủ cục bộ của mình,
bây giờ ta hãy tiến hành cấu hình nó.

Tạo tệp: .env

\- Chúng ta đã có tệp .env.example từ các tệp tải đã tải xuống. Thay đổi
vào thư mục mà bạn đã tải xuống tệp từ git và chỉ cần sao chép
.env.example như được hiển thị bên dưới.

**cd /var/www/html/snipe**

**sudo cp .env.example .env**

![](.//media/image29.png)


\- Bây giờ hãy chỉnh sửa tệp .env cho phù hợp. Tệp có nhiều tùy chọn như
ta có thể thấy, nhưng những tùy chọn sau là quan trọng nhất hiện tại. Ta
có thể thêm phần còn lại theo ý thích của mình, chẳng hạn như cài đặt
máy chủ mail và phần còn lại.

**sudo vim .env**

APP_URL = **192.168.17.141** \# Nhập Địa chỉ IP hoặc FQDN của Ứng dụng
Snipe của bạn

APP_TIMEZONE = '**UTC**' \# Nhập nó để khớp với quốc gia bạn đang ở

DB_DATABASE = **snipeit** \# Nhập tên của cơ sở dữ liệu chúng tôi đã tạo
trước đó

DB_USERNAME = **snipeit** \# Nhập tên người dùng của cơ sở dữ liệu chúng
ta đã tạo trước đó

DB_PASSWORD = **P\@ssw0rd** \# Nhập mật khẩu của cơ sở dữ liệu chúng ta
đã tạo trước đó

![](.//media/image30.png)


![](.//media/image31.png)


![](.//media/image32.png)


![](.//media/image33.png)


\- Ở đây mình sử dụng SMTP của gmail để gửi mail đi, mail này sẽ đảm
nhiệm các chức năng như gửi mail welcome khi tạo user, mail reset
password, mail cảnh báo thời gian sử dụng tài sản,\...

\- Để cấu hình gmail gửi đi được bạn cần chỉnh vài cấu hình trong tài
khoản gmail mà bạn muốn thiết lập để gửi mail này.

-   Đăng nhập tài khoản gmail

-   Đi đến **https://myaccount.google.com/lesssecureapps** và bật
    \"**less secure**\"

-   Đi đến **https://accounts.google.com/b/0/DisplayUnlockCaptcha** và
    click \"**Continue**\"

\- Sau khi ta hoàn tất, trong khi vẫn còn thư mục ta đã tải xuống
Snipe-IT, hãy cấp cho các tệp của ta các quyền và quyền sở hữu phù hợp
như sau:

**sudo chown -R apache:apache storage public/uploads**

**sudo chmod -R 755 storage**

**sudo chmod -R 755 public/uploads**

**sudo chmod -R 755 bootstrap/cache**

![](.//media/image34.png)


**Bước 9: Cài đặt các gói cần thiết của PHP bằng Composer**

**sudo /usr/local/bin/composer install \--no-dev \--prefer-source**

![](.//media/image35.png)


**Bước 10: Tạo \"APP_Key\"**

**sudo php artisan key:generate**

Application In Production! \*

Do you really wish to run this command? (yes/no) \[no\]:

\> **yes**

Application key \[base64:yXaQTcuJo/rXHoNxG+C/X/aYyHQ6/Va3NHu4YUPpBAQ=\]
set successfully.

![](.//media/image36.png)

**Bước 11: Cấu hình Apache**

\- Cấu hình dịch vụ tường lửa của bạn để cho phép cổng http:

**sudo firewall-cmd \--permanent \--add-service=http**

**sudo firewall-cmd \--reload**

![](.//media/image37.png)


\- Điều hướng đến thư mục Apache và tạo máy chủ ảo SnipeIT

**cd /etc/httpd/conf.d/**

![](.//media/image38.png)


\- Tạo tệp cho máy chủ ảo của bạn và thêm cấu hình VirtualHost bình
thường tương tự như cấu hình được minh họa bên dưới

**sudo vim geeksnipe.conf**

\<VirtualHost \*:80>

ServerName **192.168.17.141**

DocumentRoot /var/www/html/snipe/public

\<Directory /var/www/html/snipe/public>

Options Indexes FollowSymLinks Multiviews

AllowOverride All

Order allow,deny

allow from all

\</Directory>

\</VirtualHost>

![](.//media/image39.png)


![](.//media/image40.png)

Khởi động lại apache:

**sudo systemctl restart httpd**

![](.//media/image41.png)


**Bước 12: Cấu hình SELinux**

**sudo yum provides /usr/sbin/semanage**

**sudo yum install policycoreutils-python-utils**

![](.//media/image42.png)


![](.//media/image43.png)


\- Sau khi nó được cài đặt, hãy điều hướng đến thư mục chứa các tệp
SnipeIT của bạn và chạy lệnh dưới đây với tư cách là thư mục gốc

**sudo semanage fcontext -a -t httpd_sys_rw_content_t
\"/var/www/html/snipe(/.\*)/?\"**

**sudo restorecon -R -v /var/www/html/snipe/**

**sudo semanage fcontext -a -t httpd_sys_rw_content_t
\"/var/www/html/snipe/storage(/.\*)?\"**

**sudo restorecon -RF /var/www/html/snipe/storage**

![](.//media/image44.png)


![](.//media/image45.png)


![](.//media/image46.png)


![](.//media/image47.png)


\- SELinux có thể ngăn Apache mở bất kỳ ổ cắm đi nào. Để cho phép nó,
hãy chạy lệnh sau với quyền root

**sudo setsebool -P httpd_can_network_connect on**

![](.//media/image48.png)


**Bước 13: Truy cập vào tên miền mà bạn đang host mã nguồn Snipe-IT.**

VD: http://192.168.17.141

![](.//media/image49.png)


![](.//media/image50.png)


![](.//media/image51.png)


\- Cấu hình các thông tin cần thiết trên giao diện Setup Snipe-IT

![](.//media/image52.png)


![](.//media/image53.png)


\- Lúc này bạn sẽ được đăng nhập thẳng Snipe-IT Dashboard

![](.//media/image54.png)


**II. Backup dữ liệu của Snipe-IT**

\- Ta sẽ sử dụng công cụ Rclone để back up dữ liệu của các server lên
Google Drive.

\- Rclone là một công cụ đồng bộ hóa dữ liệu tương tự Rsync nhưng lại
được tập trung phát triển chức năng kết nối với các dịch vụ lưu trữ đám
mây.

\- Ưu điểm của việc sử dụng dịch vụ lưu trữ đám mây đó là tốc độ cao (do
có server được đặt trên khắp thế giới), an toàn dữ liệu (không lo ngại
các vấn đề phần cứng, network) và nhất là hầu hết đều miễn phí.

\- Rclone hỗ trợ rất nhiều dịch vụ Cloud thông dụng như:

-   Google Drive

-   Amazon S3

-   Dropbox

-   Google Cloud Storage

-   Amazon Drive

-   The local filesystem

-   \...

\- Thay vì backup đưa lên VPS khác lưu trữ, ta chuyển sang sử dụng
Google Drive.

\- Ta sẽ tiến hành một script backup nhỏ sau để lưu trữ các server chat:

-   Sao lưu toàn bộ database MySQL, mỗi database một file .gz

-   Sao lưu toàn bộ code trong thư mục /home/domain.com/public_html/

-   Tổng hợp tất cả dữ liệu vào 1 folder

-   Upload file backup lên Google Drive vào lúc 2h sáng

\- Tự động xóa file backup trên VPS sau khi upload xong, xóa file backup
trên Cloud nếu quá 2 tuần.

**1. Cài đặt Rclone**

\- Cài đặt bản mới nhất với hệ điều hành Linux 64bit

cd /root/

wget https://downloads.rclone.org/rclone-current-linux-amd64.zip

unzip rclone-current-linux-amd64.zip

\\cp rclone-v\*-linux-amd64/rclone /usr/sbin/

rm -rf rclone-\*

![](.//media/image55.png)


![](.//media/image56.png)


![](.//media/image57.png)


**b. Back up dữ liệu lên Cloud với Rclone**

\- Tạo kết nối với Google Drive

-   Đầu tiên ta sẽ cấu hình kết nối Rclone với Google Drive, việc này
    chỉ phải làm 1 lần duy nhất. Kết nối được tạo tên **snipeit**

-   Chạy lệnh sau: rclone config

> ![](.//media/image58.png)
> 

-   Ta sẽ nhận được thông báo: No remotes found - make a new one, nhập n
    rồi nhấn Enter để tạo kết nối.

-   Ở dòng name bạn nhập **snipeit** để đặt tên cho kết nối, bạn có thể
    chọn tên nào cũng được

> ![](.//media/image59.png)
> 

-   Một danh sách các dịch vụ cloud xuất hiện, hãy chọn số 15, Google
    Drive rồi nhấn Enter.

> ![](.//media/image60.png)
> 
>
> ![](.//media/image61.png)
> 
>
> ![](.//media/image62.png)
> 

-   Ở 2 dòng tiếp theo Client ID và Client Secret bạn hãy để trống nhấn
    Enter

> ![](.//media/image63.png)
> 

-   Mục Scope that rclone should use when requesting access from drive
    chọn 1 - drive

> ![](.//media/image64.png)
> 

-   Tiếp theo, để trống với ID of the root folder và Service Account
    Credentials JSON file path

> ![](.//media/image65.png)
> 

-   Khi được hỏi Use auto config? hãy nhập n rồi nhấn Enter. Ngay lập
    tức, Rclone sẽ đưa ra 1 đường link, ta có thể click thẳng vào đó
    hoặc copy rồi paste vào trình duyệt

> ![](.//media/image66.png)
> 
>
> ![](.//media/image67.png)
> 
>
> ![](.//media/image68.png)
> 
>
> ![](.//media/image69.png)
> 

-   Chọn n tức no đối với Configure this as a team drive

> ![](.//media/image70.png)
> 

-   Rclone xác nhận thông tin một lần nữa, bạn nhấn y để đồng ý rồi nhấn
    q để thoát khỏi giao diện cấu hình kết nối

> ![](.//media/image71.png)
> 
>
> ![](.//media/image72.png)
> 

-   Vậy là xong, giờ bạn có thể test với lệnh liệt kê thư mục trong kết
    nối remote

> rclone lsd snipeit:
>
> ![](.//media/image73.png)
> 

**c. Script backup toàn bộ Zulip và upload lên Cloud**

\- Ta tạo file backup.sh và nhấp nối dung sau: (Lưu ý: ở phần
SERVER_NAME là tên thư mục bạn tạo trên Drive, REMOTE_NAME là zulip như
mình tạo ở trên, MYSQL_PASSWORD là mật khẩu mysql của bạn).

vi /root/backup.sh

#!/bin/bash

cwd=\$(pwd)

SERVER_NAME=Snipeit

REMOTE_NAME=snipeit

DATE=\`date +%Y-%m-%d\`

TIMESTAMP=\$(date +%F)

BAK_DIR=/data-backup/

BACKUP_DIR=\$BAK_DIR/\$TIMESTAMP

MYSQL_USER=\"root\"

MYSQL=/usr/bin/mysql

MYSQL_PASSWORD=1714168

Mysqldump=/usr/bin/mysqldump

rclone=/usr/sbin/rclone

SECONDS=0

exec \>\$BAK_DIR/logs/\$DATE.log

exec 2>&1

mkdir -p \"\$BACKUP_DIR/mysql\"

echo \"Starting Backup Database\";

databases=\`\$MYSQL -u \$MYSQL_USER -p\$MYSQL_PASSWORD -e \"SHOW
databases;\" \| grep -Ev \"(Database \|information_schema \|
performance_schema \| mysql \| sys)\" \`

for db in \$databases; do

echo \$db

\$Mysqldump -u \$MYSQL_USER -p\$MYSQL_PASSWORD \--databases \$db
\--quick \--lock-tables=false \| gzip> \"\$BACKUP_DIR/mysql/\$db.gz\"

done

echo \"Finished\";

echo \'\';

echo \"Starting Backup Website\";

mkdir -p \$BACKUP_DIR/data

domain=\$D##\*/ \# Domain name

echo \"-\" \$domain;

zip -r -y -q \$BACKUP_DIR/data/\$TIMESTAMP.zip /var/www/html/ #Exclude
cache

#fi

#done

echo \"Finished\";

echo \'\';

echo \"Starting compress file\";

size1=\$(du -sh \$BACKUP_DIR \| awk \'print \$1\')

cd \$BAK_DIR

tar -czf \$TIMESTAMP\".tgz\" \$TIMESTAMP

cd \$cwd

size2=\$(du -sh \$BACKUP_DIR\".tgz\"\| awk \'print \$1\')

rm -rf \$BACKUP_DIR

echo \"File compress from \"\$size1\" to \"\$size2

echo \"Finished\";

echo \'\';

echo \"Starting Backup Uploading\";

\$rclone copy \$BACKUP_DIR.tgz \"\$REMOTE_NAME:/\$SERVER_NAME/\"

#\$rclone -q delete \--min-age 1m \"\$REMOTE_NAME:/\$SERVER_NAME\"
#remove all backups older than 1 week

find \$BAK_DIR -mindepth 1 -mtime +6 -delete

echo \"Finished\";

echo \'\';

duration=\$SECONDS

echo \"Total \$size2, \$((\$duration/60)) minutes and
\$((\$duration%60)) seconds elapsed.\"

![](.//media/image74.png)


![](.//media/image75.png)


![](.//media/image76.png)


\- Sau khi tạo xong file ta chạy lệnh sau:

chmod +x /root/backup.sh

![](.//media/image77.png)


\- Ta chạy lệnh sau để tiến hành backup:

/root/backup.sh

![](.//media/image78.png)


![](.//media/image79.png)


\- Thử kiểm tra trên Cloud xem có thư mục mới với dữ liệu backup:

rclone lsl snipeit:Snipeit

![](.//media/image80.png)


![](.//media/image81.png)

**d. Tạo cronjob tự động backup hàng ngày**

crontab -e

0 2 \* \* \* /root/backup.sh \> /dev/null 2>&1

![](.//media/image82.png)


![](.//media/image83.png)


**e. Tải file backup từ Cloud xuống VPS**

\- Cách đơn giản nhất để bạn khôi phục lại dữ liệu đó là tỉa file backup
từ Cloud xuống máy tính, rồi tùy chọn theo như cầu mà up trở lại lên
VPS. Tuy nhiên, nếu muốn tải trực tiếp file backup về VPS, bạn có thể sử
dụng luôn Rclone với câu lệnh **copy**

VD: rclone copy \"snipeit:/Snipeit/2021-10-25.tgz\" /root/

![](.//media/image84.png)


Lệnh trên sẽ copy folder 2021-10-20 trong thư mục Zulip trên Cloud về
thư mục /root/ của VPS. Tốc độ upload và download từ Cloud đều rất
nhanh. Sau khi copy dữ liệu backup về VPS, ta tiến hành giải nén file
zip, copy thư mục web và nginx về đúng vị trí đồng thời tiến hành import
database.

**Tài liệu tham khảo**

https://itsystems.vn/huong-dan-cai-snipe-it-tren-centos-8/

https://cuongquach.com/cai-dat-snipe-it-tren-centos-quan-ly-tai-san-it.html

https://vietcalls.com/huong-dan-dung-rclone-backup-du-lieu-len-google-drive/

https://huongdan.azdigi.com/how-to-install-cai-dat-mysql-tren-ubuntu-2004/

https://hocvps.com/rclone/#script-2-voi-hocvps-script-phien-ban-1-8-tro-xuong-hoac-he-quan-tri-khac
