**Tuấn, Hiệu, Song Hoàng**
1. **Thu thập dữ liệu**
1. **Các thư viện và phần mềm cần cài đặt**
- Tải Chrome Driver tương ứng với phiên bản trên máy tính tại trang web: <https://chromedriver.chromium.org/downloads> 
- Tải thư viện Selenium và Beautiful Soup 4:
  - ! pip install selenium
  - ! pip install bs4
1. **Chạy chương trình**
- Thu thập đường dẫn của dữ liệu:
  - Sử dụng Selenium để xử lí các trường hợp kéo xuống và nút nhấn See more để tải thêm dữ liệu trên trang web
  - Do việc thu thập dựa vào 10 loại Shape của kim cương nên cần truyền tham số đầu vào cho hàm Collect_Href_of_Diamonds(shape, num) gồm giá trị Shape tương ứng và số lượng mẫu cần thu thập. Tuy nhiên, đôi lúc do việc khởi động trang web trong quá trình thu thập thì số lượng có thể ít hơn hoặc nhiều hơn dữ liệu cần thu thập
  - Sau khi thu thập được đường dẫn, ghi vào file .txt tương ứng với Shape
- Thu thập dữ liệu:
  - Sau khi có được các đường dẫn, tiến hành truy cập vào đường dẫn và lấy thông tin dữ liệu bằng BeautifulSoup thông qua hàm Collect_Raw_Data(url)
- Sau 2 bước thu thập trên, thu được dữ liệu thô (Raw_Data) dưới dạng file .txt. Sử dụng hàm Convert line to CSV(line, columns) với tham số là dòng dữ liệu trong file và danh sách các cột dữ liệu để chuyển đổi dưới định dạng file .csv

**II.   Xử lý và phân tích dữ liệu**

Chạy file ***3_1_Visualize_Analyst_(small).ipynb cho small_data***, file ***3_2_Visualize_Analyst_(big).ipynb cho big_data*** theo các bước sau:

- Chạy cell Import & function để import các thư viện và hàm cần thiết
- Chạy cell Overview để load data , xem các thông tin chung
- Chạy cell EDA để thực hiện xử lí data, phân tích data, tương quan và các mối quan hệ giữa các biến
- Chạy cell Feature selection để lựa chọn đặc trưng
- Chạy cell Label Encoder để chuyển các biến phân loại thành dạng số
- Chạy cell Feature transform để transform các biến

**III. Mô hình dự đoán**

Chạy file ***4.Model.ipynb*** để thực hiện mô hình dự đoán giá kim cương

1. Load dữ liệu từ 2 file: ***data_small_clean.csv*** (dành cho data 1000 samples) hoặc ***data_big_clean.csv*** (dành cho data 10000 samples).
1. Import các thư viện cần thiết
1. Chạy các cell code theo từng cụm đã chia sẵn từ trên xuống dưới.
- **Chú ý:** 
+ Ở những cell có ***“final_result”*** thì bỏ chú thích và run cell. Chú ý, chỉ chạy 1 lần để tránh bị nhầm lẫn kết quả. Ví dụ:

# temp_lr_df = ['10.000', 'Random Forest Regression (RandomizedSearchCV)', run_time_big[1], improved_model_r2_compare_big.iloc[2, 1]*100]

# final_result.append(temp_lr_df)

final_result

+ Tương tự với cell mô hình trong phần  ***“Hyperparamter Tuning using RandomizedSearchCV và GridSearchCV”***, chỉ chạy 1 lần với mỗi cell. Nếu muốn không bị ghi quá nhiều kết quả dự đoán vào List kết quả thì hãy chạy lại những cell này trên mỗi tập dữ liệu tương ứng:

from sklearn.model_selection import RandomizedSearchCV, GridSearchCV

rf_base_r2_big = max(result_r2_compare_df_big.sort_values(by='R2 Testing Score', ascending=False)['R2 Testing Score'])

# List of improvement R2 Score using Grid Search with Cross Validation

improved_test_r2_score_big = [rf_base_r2_big]

# List to track the run time of improvement models

run_time_big = []


+ Khi chạy cell ở ***“Hyperparamter Tuning using RandomizedSearchCV và GridSearchCV”*** sẽ tốn khá nhiều thời gian thực thi. Nếu muốn thì có thể dùng sẵn Hyperparameter đã thử nghiệm để tiết kiệm thời gian.

**Thansk Allurez Website**
