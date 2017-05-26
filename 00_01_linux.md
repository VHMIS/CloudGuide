# Một số thao tác dòng lệnh với các hệ điều hành Linux/Unix

## Soạn thảo, chỉnh sửa nội dung file (CentOS, Redhat, Ubuntu)

Để chỉnh sửa nội dung file (cấu hình, thiết lập...), sử dụng công cụ ``nano`` để dễ thao tác.
Trong trường hợp bất khả kháng thì sử dụng ``vi`` thì một số câu lệnh cần thiết để chỉnh sửa gồm

 - Di chuyển con trỏ: Sử dụng 4 phím mũi tên
 - Chỉnh sửa:
 - Lưu file và thoát: ``:x``
 
 ## Cấu hình mạng (CentOS, Redhat, Ubuntu)
 
 Cấu hình mạng thông qua các file cấu hình nằm trong thư mục ``/etc/sysconfig/network-scripts``,
 các file cấu hình cho từng card mạng có dạng ``ifcfg-[tên card mạng]``
 
     cd /etc/sysconfig/network-scripts
     cat ifcfg-p3p1 # xem cấu hình card p3p1
     nano ifcfg-p3p1 # mở trình chỉnh sửa để cấu hình card p3p1
     
     # hoặc
     
     vi /etc/sysconfig/network-scripts/ifcfg-em3 # mở trình chỉnh sửa vi để cấu hình card em3

## Route

Để thêm vào một route cho 1 gateway, sử dụng lệnh ``ip route add``

    ip route add 192.168.101.0/24 via 192.168.10.1
    
Lệnh trên sẽ đưa các truy cập vào gw 192.168.101.1 thông qua gw 192.168.10.1

## Thêm ổ cứng mới

Sau khi server được cấp ổ cứng mới, các thao tác để máy nhận diện và sử dụng ổ cứng mới gồm có phần vùng, định dạng, và mount

 - Sử dụng lệnh ``fdisk -l`` để xem tên ổ cứng mới thêm vào
 - Phân vùng ổ cứng bằng lệnh ``fdisk /path/new/disk``
 - Format ổ cứng sau khi phân vùng ``mkfs.xfs /path/new/pdisk`` cho định dạng xfs hoặc ``mkfs.ext4 /path/new/pdisk`` cho định dạng ext4
 - Mount ổ cứng vào một thư mục để sử dụng ``mount /path/new/pdisk /path/directory``
 - Khai báo mount cho lần khởi động tiếp theo, mở file ``/etc/fstab`` thêm dòng ``/path/new/pdisk /path/directory xfs defaults  0 0``
   
