# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): Lê Tiến Bình  
Người kiểm (học viên): Ninh Hải Nam  
Ngày: 21/11/2026  
Phiên bản guideline: Road v1.0  
File được kiểm: `letienbinh-front.zip`, `letienbinh-fisheye.zip` (chưa có manifest kèm theo nên chưa xác nhận được revision)  
Số ảnh kiểm: 6 (A01, A05, A08, B02, B03, B05; 0 ảnh thêm)  
Số nhãn đã kiểm (shape + tag): 99

Mẫu gồm 3 ảnh front và 3 ảnh fisheye.

## Tổng hợp theo mã

| Mã                                   | Loại lỗi                              | Số mục kiểm | Số lỗi | Mức                           |
| ------------------------------------ | ------------------------------------- | ----------: | -----: | ----------------------------- |
| QC1-01 tag camera                    | sai thuộc tính / bỏ sót               |          24 |      0 | nặng (camera); nhẹ (tag khác) |
| QC1-02 đủ L1, R1                     | bỏ sót                                |          10 |      0 | nặng                          |
| QC1-03 position                      | sai thuộc tính / thừa                 |          16 |      0 | nặng                          |
| QC1-04 tâm vạch, chiều, điểm dừng    | sai phạm vi / bỏ sót                  |          16 |      3 | chính                         |
| QC1-05 vạch đứt, che                 | sai phạm vi / sai thuộc tính          |          16 |      1 | chính                         |
| QC1-06 style, color, kind            | sai thuộc tính                        |          16 |      0 | chính                         |
| QC1-07 vùng lái                      | sai phạm vi / bỏ sót / thừa           |          17 |      0 | chính                         |
| QC1-08 đèn, màu                      | bỏ sót / sai phạm vi / sai thuộc tính |          12 |      0 | nặng / chính                  |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính                        |          19 |      0 | chính                         |
| QC1-10 hình in, đủ biển              | bỏ sót / sai phạm vi                  |          19 |      0 | chính                         |
| QC1-11 fisheye                       | sai phạm vi / sai thuộc tính          |          29 |      5 | chính                         |
| QC1-12 file                          | lỗi file                              |           2 |      0 | nhẹ / nặng                    |

## Danh sách lỗi (mỗi lỗi một dòng)

|   # | Mã     | Ảnh | Nhãn (label, id)                     | Mức   | Mô tả ngắn                                                                                                    |
| --: | ------ | --- | ------------------------------------ | ----- | ------------------------------------------------------------------------------------------------------------- |
|   1 | QC1-05 | A01 | lane, hai shape position=L2          | chính | Cùng một vạch trắng đôi được vẽ thành hai polyline sát nhau; nên gộp thành một polyline và đặt `kind=double`. |
|   2 | QC1-04 | A08 | lane, điểm đầu (772,317)             | chính | Polyline bắt đầu ở phía xa rồi đi về gần; cần đảo chiều để điểm đầu ở gần xe.                                 |
|   3 | QC1-04 | A08 | lane, điểm đầu (655,321)             | chính | Polyline bắt đầu ở phía xa rồi đi về gần; cần đảo chiều.                                                      |
|   4 | QC1-04 | A08 | lane, điểm đầu (644,310)             | chính | Polyline bắt đầu ở phía xa rồi đi về gần; cần đảo chiều.                                                      |
|   5 | QC1-11 | B02 | traffic_light, box bắt đầu (1076,73) | chính | Tâm box nằm trong vùng rìa fisheye nhưng `edge_zone` đang tắt.                                                |
|   6 | QC1-11 | B02 | traffic_light, box bắt đầu (113,113) | chính | Tâm box nằm trong vùng rìa fisheye nhưng `edge_zone` đang tắt.                                                |
|   7 | QC1-11 | B03 | traffic_sign, box bắt đầu (1130,361) | chính | Tâm box nằm ngoài ngưỡng 80% bán kính; cần bật `edge_zone`.                                                   |
|   8 | QC1-11 | B05 | traffic_sign, box bắt đầu (420,5)    | chính | Tâm box nằm trong vùng rìa fisheye nhưng `edge_zone` đang tắt.                                                |
|   9 | QC1-11 | B05 | traffic_sign, box bắt đầu (354,39)   | chính | Tâm box nằm trong vùng rìa fisheye nhưng `edge_zone` đang tắt.                                                |

## Ca mơ hồ

| Ảnh | Câu hỏi cho lead                                                                                                    | Lời đáp (nếu có) |
| --- | ------------------------------------------------------------------------------------------------------------------- | ---------------- |
| A05 | Ảnh không thấy vạch phân làn sơn rõ. Coach xác nhận giúp trường hợp thiếu L1/R1 này được miễn theo guideline không? | Chờ xác nhận     |

## Quyết định

Lỗi nặng: 0  
Lỗi chính: 9 / 99 nhãn = 9,1%  
Lỗi nhẹ: 0  
Ca chờ lead: 1  
Quyết định: **Rework**  
Lý do: Tỉ lệ lỗi chính trong mẫu vượt 5% (9/99). Ca A05 cần coach xác nhận nhưng không làm thay đổi quyết định này.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](docs/qc_severity_road_v1.0.md).
