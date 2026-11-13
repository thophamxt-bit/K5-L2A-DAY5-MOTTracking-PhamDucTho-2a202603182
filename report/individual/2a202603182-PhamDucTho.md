# Báo cáo cá nhân — HoVaTen-MSSV

Đổi tên file theo quy tắc `MSSV_HoTen.md`. Ví dụ: `20241234_NguyenVanAn.md`.

Đoạn video: MOT17-09, 150 frame (frame 1–150), nguồn MOTChallenge, giấy phép CC BY-NC-SA 3.0.

## 0. Thông tin học viên

- Họ tên: Phạm Đức Thọ
- MSSV:2a202603182
- Mã đề (A/B/C):B
- Email:Thophamxt@gmail.com
- Link repository:
- Giờ bắt đầu:16h30
- Giờ kết thúc:19h

## 1. Xem trước đoạn video (CP0)

Ghi **trước khi vẽ**, mỗi người một dòng.

| Mã | Frame xuất hiện | Frame cuối thấy được | Rẽ / dừng / đổi tốc độ ở frame | Bị che ở frame | Ghi chú |
|---|---|---|---|---|---|
| P1 | | | | | |
| P2 | | | | | |
| P3 | | | | | |
| P4 | | | | | |
| P5 | | | | | |

## 2. Keyframe và thời gian (CP1, CP4)

Số keyframe lấy từ kết quả `src/check_submission.py`.
| Mã (Track CVAT) | Số keyframe | Keyframe ở frame | Số frame có mặt | Keyframe / 100 frame | Thời gian (phút) | Chỗ khó |
|---|---:|---|---:|---:|---:|---|
| Track 0 (MOT 1) | 81 | `[0, 4, 5, 7, 9, 10, 11, 14, 15, 16, 17, 18, 19, 20, 21, 23, 24, 25, 26, 27, 28, 29, 30, 32, 33, 34, 37, 40, 53, 60, 64, 67, 69, 70, 71, 75, 79, 80, 82, 83, 84, 85, 90, 91, 92, 95, 96, 97, 98, 99, 100, 101, 103, 104, 105, 107, 108, 110, 118, 119, 120, 121, 122, 124, 125, 126, 127, 128, 129, 130, 131, 132, 133, 134, 135, 136, 137, 139, 140, 141, 149]` | 150 | 54.0 | | Cảnh báo `> 50 KF / 100 frame` |
| Track 1 (MOT 2) | 17 | `[0, 10, 20, 40, 70, 71, 90, 100, 105, 106, 110, 123, 125, 126, 133, 136, 138]` | 124 | 13.7 | | 34 frame `occluded`, 3 lần `outside` (107–109, 111–122) |
| Track 2 (MOT 3) | 15 | `[0, 10, 20, 40, 58, 66, 78, 90, 99, 105, 106, 110, 111, 135, 147]` | 125 | 12.0 | | 20 frame `occluded`, 2 lần `outside` (112–134) |
| Track 3 (MOT 4) | 31 | `[0, 10, 20, 30, 40, 41, 47, 60, 70, 72, 75, 78, 80, 82, 90, 94, 99, 100, 103, 110, 120, 122, 125, 129, 130, 137, 139, 140, 142, 143, 149]` | 150 | 20.7 | | |
| Track 4 (MOT 5) | 39 | `[0, 11, 16, 20, 23, 24, 25, 42, 44, 50, 55, 56, 57, 60, 63, 65, 66, 67, 69, 70, 71, 72, 74, 75, 79, 84, 85, 86, 87, 88, 89, 92, 95, 96, 97, 105, 106, 135, 149]` | 149 | 26.2 | | 54 frame `occluded`, 1 lần `outside` (frame 43) |
| **Tổng** | **183** | — | **698** | **26.2** | | |

Keyframe / 100 frame của cả bài = `183 ÷ 698 × 100 = 26.2`

Bạn đặt keyframe nhiều nhất ở người nào? Vì sao (người đó rẽ, dừng, lại gần camera hay bị che)?

Theo kết quả xuất hiện tại, người có nhiều keyframe nhất là **Track 0** (`81` keyframe, `54.0` keyframe / 100 frame, xuất hiện đủ `150` frame).
- Lý do: nội suy tuyến tính của CVAT chỉ chính xác khi đối tượng di chuyển thẳng với tốc độ đều; khi người đó **đổi hướng (rẽ), thay đổi tốc độ bước đi, hoặc tiến lại gần / ra xa camera** làm kích thước box thay đổi liên tục, box nội suy bị trôi khỏi thân người nên phải đặt thêm keyframe (nhất là ở các đoạn `14–34`, `95–108`, `118–141`). *(Lưu ý: Track 0 đang bị cảnh báo `> 50 keyframe / 100 frame`;

## 3. Đoạn bị che (CP2)

Người bị che: `P_`

| Mốc | Frame |
|---|---:|
| Bắt đầu bị che một phần (bật `occluded`) | |
| Mất hẳn (bật `outside`) | |
| Hiện lại (tắt `outside`) | |
| Thấy rõ trở lại (tắt `occluded`) | |

- Thời gian khuất hẳn: ___ frame = ___ giây.
- Quyết định: giữ cùng ID / tạo track mới.
- Lý do (trả lời 3 câu: khuất bao lâu so với 60 frame, ngoại hình có khớp, chỗ hiện lại có đúng hướng và tốc độ):

...

Ảnh chụp màn hình:

![Trước khi che](images/che_1_truoc.png)
![Giữa đoạn che, thấy cờ trên panel object](images/che_2_giua.png)
![Sau khi hiện lại, cùng ID](images/che_3_sau.png)

## 4. Tự review ID (CP3)

Lượt 1 theo người (đi ngược từ frame 149 về 0 trên CVAT), lượt 2 theo cảnh (nhảy 10 frame). Ít nhất 3 dòng; không có lỗi thì ghi một dòng "đã kiểm hai lượt, không lỗi".

Loại lỗi dùng đúng một trong 7 mã: `id_switch`, `fragmentation`, `lost`, `merge`, `false_track`, `drift`, `flag`.

| Frame | Mã người | Loại lỗi | Mô tả một câu | Phát hiện ở lượt | Đã sửa? |
|---:|---|---|---|---|---|
| | | | | | |
| | | | | | |
| | | | | | |

Tổng hợp số lỗi theo loại:

| `id_switch` | `fragmentation` | `lost` | `merge` | `false_track` | `drift` | `flag` |
|---:|---:|---:|---:|---:|---:|---:|
| | | | | | | |

Lỗi nào chỉ lượt 2 (theo cảnh) mới thấy, lượt 1 (theo người) không thấy? Vì sao?

 Ở **lượt 1 (theo từng người)**, ta chỉ tập trung vào một track riêng lẻ nên dễ phát hiện các lỗi nội tại của track đó như `drift` (box bị trôi), `fragmentation` hoặc `flag` (quên bật/tắt `occluded`, `outside`).
- Ở **lượt 2 (theo cảnh, nhìn cả 5 box cùng lúc)**, mới dễ phát hiện các lỗi liên quan đến **tương quan giữa nhiều người trong cùng khung hình**, đặc biệt là **`id_switch`** (hai người đi sát hoặc cắt ngang nhau làm 2 ID bị tráo đổi) hoặc **`merge` / `false_track` / `lost`** ở cấp toàn cảnh (nhìn một người riêng lẻ vẫn thấy có box bám theo nên dễ bỏ qua, nhưng nhìn cả 5 box cùng lúc sẽ thấy ngay ID bị đổi chủ hoặc thừa/thiếu người).

## 5. File xuất và kết quả tự kiểm (CP4)

| Kiểm tra | Kết quả |
|---|---|
| Tên file MOT 1.1 | `src/exports/PhamDucTho_mot.zip` |
| Tên file CVAT for video 1.1 | `src/exports/PhamDucTho_cvat_video.zip` |
| Số track ID khác nhau trong `gt/gt.txt` (phải là 5) | `5` |
| Frame `outside` không có dòng trong `gt.txt` (đúng / sai) | `Đúng` |
| Job đã completed trên CVAT máy cá nhân | *(đánh dấu Đã completed sau khi xong trên CVAT)* |

Dán phần tóm tắt in ra từ `src/check_submission.py`:

```text
=== File MOT 1.1: PhamDucTho_mot.zip ===
  Số track ID: 5   |   Tổng số box: 698
  [OK]        Đúng 5 track ID.

=== File CVAT for video 1.1: PhamDucTho_cvat_video.zip ===
  Tổng: 183 keyframe / 698 frame có mặt = 26.2 keyframe / 100 frame
  [OK]        Đọc được 5 track từ annotations.xml.

=== Tóm tắt ===
  Lỗi: 0   |   Cảnh báo: 1
  Không có lỗi định dạng. Mở CVAT xem lại từng [CẢNH BÁO]; cảnh báo đúng ý bạn thì ghi lý do vào báo cáo.
```
## 6. Ba câu kết

1. Nếu được gán lại, bạn sẽ đặt keyframe khác ở đâu? Vì sao?

   ...

2. Có chỗ nào bạn không chắc "cùng ID hay ID mới"? Bạn đã quyết định và ghi chú thế nào?

   ...

3. Một lỗi ID trong job của bạn (nếu không còn sót, chọn lỗi đã sửa) có thể làm xe tự lái dự đoán sai chuyển động của người đó như thế nào? Lỗi đó ảnh hưởng MOTA hay IDF1 nhiều hơn?

   ...

## Bonus (nếu làm)

### B1 — Hai người đi sát

...

### B2 — So cách đặt keyframe

| Cách đặt | Số keyframe | Frame trôi nhất | Ghi chú |
|---|---:|---:|---|
| Đều mỗi 30 frame | | | |
| Theo chỗ đổi hướng | | | |

...

### B3 — So với tracker có sẵn

| Frame | Mã người | Tracker làm gì | Nhãn của bạn | Giải thích (đoán rồi sửa / ghép IoU / box score thấp / ngoại hình) |
|---:|---|---|---|---|
| | | | | |
| | | | | |

## 7. Tài liệu tham khảo và công cụ AI đã dùng

...
