
# Gợi ý phim sử dụng(Recommendation system): Sử dụng LightGCN và Content-based

## 1. Graph Neural Networks(GNNs)
Mạng Nơ-ron Đồ Thị (Graph Neural Network - GNN) là một loại mô hình học máy được thiết kế đặc biệt để làm việc với dữ liệu đồ thị. GNN có khả năng mở rộng và áp dụng trên các đồ thị có cấu trúc phức tạp, như mạng xã hội, mạng lưới giao thông, hay bất kỳ hệ thống nào có mối quan hệ giữa các đối tượng.



## 2. LightGCN( Graph Convolutional Networks)
Nhìn thấy tiềm năng từ việc đánh giá của user đối với items và liên tưởng tới cạnh của đồ thị, nên tôi sử dụng mô hình mạng nơ-ron đồ thị. Cụ thể là mô hình nơ-ron tích chập LightGCN(phù hợp với dữ liệu implicit). Mô hình dựa trên phương pháp lọc cộng tác( Collaborative Filtering - Users có sở thích tương tự nhau trong quá khứ, cũng sẽ có sở thích tương tự trong tương lai).
- Hình ảnh biểu diễn quá trình của mô hình:

![App Screenshot](https://miro.medium.com/v2/resize:fit:1100/format:webp/0*-Yh0lvb0yb1HDjaZ)

### Data:
- Sử dụng file dữ liệu 100,000 đánh giá của movielens.
- https://files.grouplens.org/datasets/movielens/ml-100k.zip: của 943 users và 1682 items.
- Dữ liệu gồm 4 cột: userID, itemID, rating, timestamp:
![data](https://cdn-images-1.medium.com/max/800/1*OZLI7a0ueujHzj5NG3oRlQ.png)



## 3. Content-based( lọc dựa trên nội dung)
- Phương pháp học dựa trên nội dung: những người thích xem bộ phim trước đó có thể thích những phim có nội dung tương tự.
![content](https://miro.medium.com/v2/resize:fit:562/format:webp/1*qw5w1ClAW0DEdGzI5kUs2g.png)
- Tìm độ tương đồng bằng công thức tính cosin vector embedding:
![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*0n2aHtmTwDolc5Y7dSm-OA.png)
![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*4ub83DgxaqIWtNtyWxGchQ.png)
### Data:
- Sử dụng tập dữ liệu 5000 phim bao gồm các mục: thể loại, tóm tắt, diễn viên, ý kiến.... 

## Note:
-Mô hình LightGCN(sử dụng thư viện PyG - Pytorch Geometric):
- Cài đặt thư viện PyG 
- Khi cài đặt thư viện scatter và sparse có thể sử dụng câu lệnh sau để tăng tốc: 
```bash
!pip install torch_scatter torch_sparse -f https://data.pyg.org/whl/<torch-version>.html
```
- Ví dụ kiểm tra version: 
```bash
import torch
print(torch.__version__)
```
Nếu ra: 
```bash
=>2.1.0+cu121
```
Run:
```bash
!pip install torch_scatter torch_sparse -f https://data.pyg.org/whl/torch-2.1.0+cu121.html
```

