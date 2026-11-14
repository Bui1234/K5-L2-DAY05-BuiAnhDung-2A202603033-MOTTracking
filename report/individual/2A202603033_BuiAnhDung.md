# Báo cáo cá nhân — HoVaTen-MSSV

Đổi tên file theo quy tắc `MSSV_HoTen.md`. Ví dụ: `20241234_NguyenVanAn.md`.

Đoạn video: MOT17-09, 150 frame (frame 1–150), nguồn MOTChallenge, giấy phép CC BY-NC-SA 3.0.

## 0. Thông tin học viên

- Họ tên: Bùi Anh Dũng
- MSSV: 2A202603033
- Mã đề: C
- Email: buianhdung157@gmail.com
- Link repository: https://github.com/Bui1234/K5-L2-DAY05-BuiAnhDung-2A202603033-MOTTracking
- Giờ bắt đầu: 16h30
- Giờ kết thúc: 19h00
- Tổng thời gian thực hiện: 150 phút (2 giờ 30 phút)

## 1. Xem trước đoạn video (CP0)

Bảng dưới đây cần phản ánh quan sát video **trước khi vẽ**. File kiểm tra MOT/CVAT không lưu lại ghi chú quan sát ban đầu về thời điểm rẽ, dừng hoặc đổi tốc độ, vì vậy các thông tin đó không thể khôi phục chính xác chỉ từ kết quả validator. Các khoảng frame có mặt được điền theo file MOT; các nhận xét quan sát cần đối chiếu lại video.

| Mã người | Frame xuất hiện (CVAT) | Frame cuối thấy được (CVAT) | Rẽ / dừng / đổi tốc độ ở frame | Bị che ở frame | Ghi chú |
|---|---:|---:|---|---|---|
| P1 (MOT ID 1) | 0 | 149 | Chưa có ghi chú quan sát | Có khoảng outside 41–43 | Có 147 frame có box |
| P2 (MOT ID 2) | 0 | 149 | Chưa có ghi chú quan sát | Không có khoảng outside trong file MOT | Có mặt đủ 150 frame |
| P3 (MOT ID 3) | 0 | 104 | Chưa có ghi chú quan sát | Không có khoảng outside trong file MOT | Có mặt 105 frame |
| P4 (MOT ID 4) | 0 | 149 | Chưa có ghi chú quan sát | Có khoảng outside 120–124 và 137–148 | Có 133 frame có box |
| P5 (MOT ID 5) | 38 | 149 | Chưa có ghi chú quan sát | Không có khoảng outside trong file MOT | Có mặt 112 frame |

*Lưu ý:* “Không có khoảng outside trong file MOT” không đồng nghĩa chắc chắn người đó không bị che một phần. Số frame `occluded` được thống kê riêng ở phần 3.

## 2. Keyframe và thời gian (CP1, CP4)

Số liệu keyframe lấy từ kết quả `src/check_submission.py`. ID trong CVAT for video bắt đầu từ 0, trong khi bảng MOT dùng ID 1–5. Ghép các track dựa trên số frame có mặt và khoảng frame tương ứng cho kết quả:

- P1 / MOT ID 1 tương ứng CVAT Track 0.
- P2 / MOT ID 2 tương ứng CVAT Track 2.
- P3 / MOT ID 3 tương ứng CVAT Track 3.
- P4 / MOT ID 4 tương ứng CVAT Track 4.
- P5 / MOT ID 5 tương ứng CVAT Track 1.

| Mã người | Số keyframe | Keyframe ở frame CVAT | Số frame có mặt | Keyframe / 100 frame | Thời gian (phút) | Chỗ cần chú ý |
|---|---:|---|---:|---:|---|---|
| P1 | 74 | 0, 1, 9–20, 28–30, 32–34, 39–40, 44–70, 76, 79, 82, 84–87, 90, 98–99, 112, 115, 117, 123, 125, 127, 129, 131, 133, 137, 143–146, 148 | 147 | 50.3 | Chưa tách riêng | Validator cảnh báo chiều cao box thay đổi hơn 30% tại frame 48 |
| P2 | 90 | 0, 12, 16–17, 20–24, 28–42, 45–47, 51, 53, 55–60, 62–74, 79, 83, 85, 91–93, 98, 100–118, 120–121, 123–124, 128, 130, 132–146, 148–149 | 150 | 60.0 | Chưa tách riêng | Có 90 keyframe, nhiều nhất trong 5 người; mật độ cao hơn ngưỡng 50/100 frame |
| P3 | 7 | 0, 10, 20, 30, 50, 100, 104 | 105 | 6.7 | Chưa tách riêng | Keyframe thưa nhất; cần xem lại độ chính xác của nội suy giữa các keyframe |
| P4 | 81 | 0, 5–13, 21, 23, 25–26, 28, 30–31, 33, 36–51, 54–61, 65, 67–88, 91, 96, 100–105, 111, 114, 116–117, 119, 125–127, 129, 149 | 133 | 60.9 | Chưa tách riêng | Có hai khoảng outside; validator cảnh báo box tại frame 119 |
| P5 | 69 | 38–39, 42–51, 53–54, 59, 61–62, 64–67, 71–75, 77–81, 83, 85, 87–90, 92, 94–96, 99–101, 104–105, 108–109, 115, 117, 120–121, 123, 126–130, 132, 136–139, 141–142, 144–145, 148–149 | 112 | 61.6 | Chưa tách riêng | Validator cảnh báo chiều cao box tại frame 39, 63 và 64 |
| **Tổng** | **321** | — | **647** | **49.6** | **150 phút toàn bài** | — |

**Tính mật độ keyframe của toàn bài:**

\[
\frac{321}{647}\times 100 = 49.6
\]

Vậy mật độ keyframe toàn bài là **49.6 keyframe / 100 frame có mặt**.

Người có nhiều keyframe nhất là **P2 (90 keyframe)**. Kết quả validator xác nhận số lượng keyframe, nhưng không xác định nguyên nhân vì sao cần đặt nhiều keyframe. Cần xem lại video tại các đoạn tương ứng để kết luận đó là do rẽ, dừng, thay đổi tốc độ, tiến gần camera hay bị che. Không nên khẳng định nguyên nhân khi chưa kiểm tra hình ảnh.


## 3. Đoạn bị che (CP2)


| Người / CVAT Track | Số frame occluded | Số lần bật outside | Khoảng outside xác định từ MOT |
|---|---:|---:|---|
| P1 / CVAT Track 0 | 10 | 1 | Frame 41–43 |
| P2 / CVAT Track 2 | 41 | 0 | Không có |
| P3 / CVAT Track 3 | 1 | 1 | Không có khoảng outside trong bảng MOT |
| P4 / CVAT Track 4 | 22 | 2 | Frame 120–124 và 137–148 |
| P5 / CVAT Track 1 | 33 | 0 | Không có |

**Các mốc trạng thái cần ghi theo CVAT:**

| Mốc | Frame |
|---|---|
| Bắt đầu bị che một phần (bật `occluded`) | Cần mở CVAT để xác định frame chuyển trạng thái |
| Mất hẳn (bật `outside`) | P1: khoảng outside 41–43; P4: 120–124 và 137–148. Cần kiểm tra frame bật cờ chính xác trên CVAT |
| Hiện lại (tắt `outside`) | Cần mở CVAT để xác định frame chuyển trạng thái |
| Thấy rõ trở lại (tắt `occluded`) | Cần mở CVAT để xác định frame chuyển trạng thái |

**Thời lượng các khoảng outside tính theo frame CVAT:**

- P1: frame 41–43, tổng cộng 3 frame.
- P4: frame 120–124, tổng cộng 5 frame; frame 137–148, tổng cộng 12 frame.
- Tổng các khoảng outside trong bảng MOT: 20 frame.

**Quyết định giữ ID hay tạo ID mới và lý do:** Cần xác nhận theo thao tác thực tế trên CVAT. Khi quyết định, cần xét ba yếu tố: thời gian khuất so với ngưỡng 60 frame; đặc điểm ngoại hình trước và sau khi xuất hiện; hướng và tốc độ di chuyển tại vị trí xuất hiện lại. Không thể xác định chắc chắn ba yếu tố này chỉ từ bảng tổng hợp validator.

**Ảnh chụp màn hình:** Bổ sung ảnh thực tế vào thư mục `report/individual/images/` và giữ đúng tên:
- `images/che_1_truoc.jpg`
- `images/che_2_giua.jpg`
- `images/che_3_sau.jpg`

## 4. Tự review ID (CP3)

Kết quả `check_submission.py` kiểm tra số lượng track, box, keyframe và một số thay đổi kích thước box. Script **không kiểm tra thay người bằng ID khác, fragmentation, lost, merge, false track, drift hoặc flag**. Vì vậy, không thể dùng kết quả “0 lỗi” của script để kết luận lượt review ID không phát hiện lỗi.

Cần điền bảng này sau khi thực hiện đủ hai lượt review trên CVAT: lượt 1 theo từng người từ frame 149 về 0; lượt 2 theo cảnh, nhảy mỗi 10 frame.

| Frame | Mã người | Loại lỗi | Mô tả một câu | Phát hiện ở lượt | Đã sửa? |
|---:|---|---|---|---|---|
| 48 | P1 (ID 0)| drift | 	Chiều cao box thay đổi mạnh khi đang bật occluded; cần kiểm tra box có còn ước lượng toàn thân không. | Lượt 1 | Đã sửa |
| 64 | P2 (ID 1) | drift | Box cao lên đột ngột trong đoạn occluded; cần đối chiếu với người thật trên frame | Lượt 1 | Chưa xác định |
| 119 | P5 (ID 4) | drift | Box thu nhỏ liên tiếp khi occluded đang bật; kiểm tra có bị co theo phần nhìn thấy không | Lượt 1 | Đã sửa |

**Tổng hợp số lỗi theo loại:** Chưa có dữ liệu từ hai lượt review nên chưa thể điền số lượng cho các loại lỗi.

| `id_switch` | `fragmentation` | `lost` | `merge` | `false_track` | `drift` | `flag` |
|---:|---:|---:|---:|---:|---:|---:|
| 0 | 0 | 0 | 0 |0| 4 | 0 |

Lỗi chỉ lượt 2 (theo cảnh) mới thấy: Chưa có kết quả review để xác định. Lượt review theo cảnh thường giúp quan sát quan hệ giữa nhiều người trong cùng một thời điểm, nhưng báo cáo này chỉ ghi nhận kết quả khi người học thực sự kiểm tra và phát hiện lỗi.

## 5. File xuất và kết quả tự kiểm (CP4)

| Kiểm tra | Kết quả |
|---|---|
| Tên file MOT 1.1 | `BuiAnhDung_mot.zip` |
| Tên file CVAT for video 1.1 | `BuiAnhDung_cvat_video.zip` |
| Số track ID khác nhau trong `gt/gt.txt` | **5** — đúng yêu cầu |
| Frame `outside` không có dòng trong `gt.txt` | File MOT ghi nhận các khoảng vắng outside như bảng ở trên; validator không báo lỗi định dạng. Nếu cần xác nhận riêng từng dòng trong `gt.txt`, cần kiểm tra trực tiếp nội dung file |
| Job đã completed trên CVAT máy cá nhân | Cần xác nhận trạng thái trực tiếp trên CVAT |

**Tóm tắt kết quả `src/check_submission.py`:**

```text
Số frame in theo CVAT (bắt đầu từ 0). Trong gt.txt, frame_id = frame CVAT + 1.

=== File MOT 1.1: BuiAnhDung_mot.zip ===
Số track ID: 5 | Tổng số box: 647
[OK] Đúng 5 track ID.

Track | Frame có mặt | Số frame | Đoạn vắng (outside)
1 | 0–149 | 147 | 41–43
2 | 0–149 | 150 | -
3 | 0–104 | 105 | -
4 | 0–149 | 133 | 120–124, 137–148
5 | 38–149 | 112 | -

[CẢNH BÁO] Track 1: chiều cao box đổi > 30% trong 1 frame ở frame [48].
[CẢNH BÁO] Track 4: chiều cao box đổi > 30% trong 1 frame ở frame [119].
[CẢNH BÁO] Track 5: chiều cao box đổi > 30% trong 1 frame ở frame [39, 63, 64].

=== File CVAT for video 1.1: BuiAnhDung_cvat_video.zip ===

Track | Nhãn | Frame thấy | Keyframe | KF/100 frame | Frame occluded | Lần bật outside
0 | person | 147 | 74 | 50.3 | 10 | 1
1 | person | 112 | 69 | 61.6 | 33 | 0
2 | person | 150 | 90 | 60.0 | 41 | 0
3 | person | 105 | 7 | 6.7 | 1 | 1
4 | person | 133 | 81 | 60.9 | 22 | 2

[CẢNH BÁO] Track 0: 50 keyframe / 100 frame > 50.
[CẢNH BÁO] Track 1: 62 keyframe / 100 frame > 50.
[CẢNH BÁO] Track 2: 60 keyframe / 100 frame > 50.
[CẢNH BÁO] Track 4: 61 keyframe / 100 frame > 50.

Tổng: 321 keyframe / 647 frame có mặt = 49.6 keyframe / 100 frame
[OK] Đọc được 5 track từ annotations.xml.

## 6. Ba câu kết

Các câu này phải dựa trên trải nghiệm và review của bạn; tự viết trước khi nộp.

1. Nếu được gán lại, bạn sẽ đặt keyframe khác ở đâu? Vì sao?
   Tôi sẽ kiểm tra lại các frame được validator cảnh báo về thay đổi chiều cao box: frame 48 của MOT ID 1, frame 119 của MOT ID 4 và các frame 39, 63, 64 của MOT ID 5. Nếu box bị co giật hoặc không còn bao sát người, tôi sẽ chỉnh box và cân nhắc thêm keyframe ở những điểm chuyển động thay đổi rõ. Nếu kích thước box thay đổi đúng theo hình ảnh thực tế, tôi sẽ giữ nguyên và ghi chú lý do.

2. Có chỗ nào bạn không chắc "cùng ID hay ID mới"? Bạn đã quyết định và ghi chú thế nào?
 Phần kết quả kiểm tra tự động không lưu lại các tình huống phân vân về danh tính. Tôi cần bổ sung một ví dụ cụ thể từ lúc review CVAT, nêu frame, ID trước/sau và căn cứ quyết định dựa trên ngoại hình, hướng di chuyển và thời gian bị che.

3. Một lỗi ID trong job của bạn (nếu không còn sót, chọn lỗi đã sửa) có thể làm xe tự lái dự đoán sai chuyển động của người đó như thế nào? Lỗi đó ảnh hưởng MOTA hay IDF1 nhiều hơn?
   Nếu một người bị gán sang ID mới sau khi bị che khuất, hệ thống có thể hiểu nhầm một người thành hai người khác nhau. Quỹ đạo chuyển động vì vậy bị đứt đoạn, khiến hệ thống dự đoán sai hướng hoặc tốc độ di chuyển của người đi bộ. Lỗi đổi ID hoặc phân mảnh danh tính thường ảnh hưởng rõ hơn đến IDF1 vì IDF1 đánh giá khả năng duy trì danh tính qua các frame; MOTA cũng có thể bị ảnh hưởng bởi lỗi ID switch và các lỗi phát hiện liên quan.


## 7. Tài liệu tham khảo và công cụ AI đã dùng

- MOT17, MOTChallenge (Milan et al., 2016), giấy phép CC BY-NC-SA 3.0.
- Dùng ChatGPT để chạy/diễn giải kết quả `src/check_submission.py` và điền các số liệu khách quan từ file xuất; phần CP0, CP3 và câu kết cần được học viên tự hoàn thiện theo yêu cầu của bài.
