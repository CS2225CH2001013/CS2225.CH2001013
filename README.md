# CS2225.CH2001013
**BÁO CÁO ĐỒ ÁN CUỐI KỲ MÔN: NHẬN DIỆN THÔNG TIN THỊ GIÁC
*Tên đồ án: Nhận diện đối tượng qua hình ảnh hoặc video clip
 - Giảng viên Hướng dẫn: PGS.TS. Lê Đình Duy
 - **Nhóm N004, gồm 03 thành viên:
   - 1. Trần Văn San _ CH2001013
   - 2. Vũ Linh _ CH2004008
   - 3. Cao Nguyễn Nam Hiền _ CH2001005
 **Link báo cáo:** https://docs.google.com/presentation/d/1CZ8HF3MNDnRTJM6zI9vS-8Elnj9pWSl3_P9i1QFFleg/edit?usp=sharing
 **Link Youtube:** 
   - Giới thiệu: https://youtu.be/W9_efYf1DQU
   - Demo các kết quả: https://youtube.com/playlist?list=PLl1c-nvyWcI8TZHrWjAaXO9LYzSu_0rJB

   
 **Sau buổi hướng dẫn ngày 13/9/2020, Nhóm tự tạo các Github cá nhân, trong đó nhóm Trưởng tạo Github nhóm với địa chỉ:**
  - 1. Trần Văn San: https://github.com/CS2225CH2001013/
   - 2. Vũ Linh: https://github.com/vulinhhiast
   - 3. Cao Nguyễn Nam Hiền : https://github.com/HienCaoHCMUP
   - Repository nhóm: https://github.com/CS2225CH2001013/CS2225.CH2001013/
   **Đồng thời nhóm cùng tìm hiểu về lập trình Python, sử dụng Google Colab theo hướng dẫn của Thầy Duy; Tham gia Class CSx101 - Tư duy lập trình Python theo yeu cầu để làm quen và thêm điểm quá trình.
   Trong quá trình nhóm đã chi sẻ, thảo luạn để nâng cao trình độ tiếp cận ngôn ngữ Python trong Deep Learning, minh chứng qua các taid liệu trao đổi đăng taie trong Issues (4 tài liệu)

**MÔ TẢ ĐỒ ÁN CUỐI KỲ:**
Ngày 27/9/2020, nhóm nộp mô tả đồ án cuối kỳ lần đầu với nội dung:
- Đề tài: Nhận dạng phương tiện giao thông
 + đầu vào là ảnh hoặc video giao thông
 + đầu ra: đếm số xe có trong ảnh, clip
 
 **Sau quá trình nghiên cứu, thảo luận Nhóm quyết định chọn tên Đề tài cuối kỳ: 
 - Nhận diện đối tượng qua hình ảnh hoặc video clip
 - Loại bài toán: Object Detection
 
 **QÚA TRÌNH THỰC HIỆN:
 - Sử dụng YOLO 3 ĐỂ ỨNG DỤNG TRONG NHẬN DIỆN ĐỐI TƯỢNG QUA HÌNH ẢNH, VIDEO CLIP
 - Nguồn tham khảo: 
    + https://github.com/AlexeyAB/darknet/#how-to-improve-object-detection
     + https://github.com/ledduy610/yolov3_deepsort
       +https://phamdinhkhanh.github.io/2020/03/10/DarknetGoogleColab.html
  - Bộ dữ liệu huấn luyện: Yolo Coco dataset: https://pjreddie.com/media/files/yolov3.weights
  - Nhóm sử dụng Google Colab để chạy Yolo 3 theo các nguồn tham khảo ở trên.
  
  **Nhận diện đối tượng qua Clip:**
  
  1. Tải ảnh lên :
    from google.colab import files
    uploaded = files.upload()
    
   2. Khởi chạy Yolo 3 để phân tích:
    !./darknet detector demo cfg/coco.data cfg/yolov3.cfg yolov3.weights -dont_show test.mp4 -i 0 -out_filename output.avi -thresh 0.7
    
   3. Hiển thị kết quả:
    #THÊM TRÌNH HỖ TRỢ HIỂN THỊ VIDEO QUA HTML:
from IPython.display import HTML
from base64 import b64encode
mp4 = open('output.mp4','rb').read()
data_url = "data:video/mp4;base64," + b64encode(mp4).decode()

#HIỂN THỊ VIDEO:
HTML("""
<video controls>
      <source src="%s" type="video/mp4">
</video>
""" % data_url)
       
         
  **Nhận diện đối tượng qua ảnh**
  
  1. Đưa ảnh cần Test vào thư mục data trên Darnet,
  
  # run darknet detection
  
   #di chuyển tới thư mục data, tải lên các ảnh để dự đoán
   
   
   2. Chạy Yolo 3 để phân tích ảnh:
   
      !./darknet detect cfg/yolov3.cfg yolov3.weights data/person1.jpg
      
   3. Hiển thị ảnh kết quả sau khi phan tích:
   
    # show image using our helper function
    
        imShow('predictions.jpg')
        
 **ĐÁNH GIÁ:
 - Với bộ dữ liệu train khá lớn của Darknet (hơn 20.000 ảnh), 80 class, các đối tượng được nhận diện với độ chính xác lên đến 95 - 100%
 
 **NHỮNG VẤN ĐỀ NHÓM ĐÃ LÀM ĐƯỢC:
 - Có thể sử dụng tốt Google Colab, Github và lập trình Python, Yolo trong việc nhận diện đối tượng
 - Nhận diện được đối tượng qua ảnh, video clip
 - 
 *NHỮNG VẤN ĐỀ CHƯA LÀM ĐƯỢC:
 - TÙY BIẾN CODE YOLO 3 ĐỂ NHẬN DIỆN MỘT SỐ ĐÓI TƯỢNG CỤ THỂ. Đây cũng là hướng để nhóm nghiên cứu, phát triển thêm.
 
