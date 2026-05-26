# Report Optimization Options Widgets Vault Phase 1

## Mục đích file này

Không phải file thực thi code.

File này trả lời 3 câu hỏi:

1. App đang gặp vấn đề gì?
2. Có những options tối ưu nào?
3. Nếu chọn từng option thì cần theo dõi chỉ số gì, mong muốn chỉ số tăng hay giảm ra sao?

## Thang mức độ nên update

- `1/5 - Không cần update`: chưa có lý do kinh doanh đủ mạnh để làm
- `2/5 - Theo dõi thêm`: có tín hiệu nhẹ, chưa đủ dữ liệu hoặc chưa phải lúc làm
- `3/5 - Có thể update`: có giá trị, có thể đưa vào backlog triển khai
- `4/5 - Nên update`: nên đưa vào danh sách triển khai gần
- `5/5 - Nên update ngay`: ưu tiên rất cao, nên xử lý trước các option khác

## Tóm tắt hiện trạng

### Tăng trưởng và retention

- Store visitors: `15,055`
- Store acquisitions: `3,558`
- Store CVR: `23.63%`
- First opens: `1.53K`, giảm `3%`
- Active users:
  - `1 day`: `303`
  - `7 day`: `1.4K`
  - `30 day`: `4.5K - 4.8K`
- Retention:
  - `D1`: `7.0%`
  - `D7`: `0.6%`
  - `D30`: gần như bằng `0`

Đánh giá:

- App không thiếu traffic ở mức phải ưu tiên `ASO / visibility`.
- Vấn đề chính là user có vào app nhưng không quay lại.
- Kết luận: bottleneck hiện tại nằm ở `first session`, `UX`, hoặc `core value delivery`.

### Monetization

- Tổng ad revenue 30 ngày: `$43.97`
- Revenue share:
  - `Native`: `56.63%`
  - `Interstitial`: `31.36%`
  - `Banner`: `7.96%`
  - `App Open`: `4.05%`
- eCPM:
  - `Interstitial`: `~$2.78`
  - `Native`: `~$1.21`
  - `App Open`: `~$1.01`
  - `Banner`: `~$0.35`

Đánh giá:

- App không thiếu ad placement.
- `Native` và `Interstitial` đang tạo phần lớn doanh thu.
- `Banner` phủ rộng nhưng yield thấp.
- Kết luận: vấn đề monetization không nằm ở số lượng placement, mà ở chất lượng placement, nhất là `banner`.

### Quality

- `Issue rate`: `3.34%`
- `Crash-free users`: `92.9%`
- `ANR rate`: `0.09%`
- Rating: `4.48`, đang giảm `0.06`

Đánh giá:

- Đây là tín hiệu xấu rõ ràng.
- `Issue rate` và `crash-free users` đã đủ xấu để ảnh hưởng trực tiếp đến retention, rating và doanh thu.
- Kết luận: `quality / crash` là vấn đề cấp cao, không phải việc phụ.

## Đọc nhanh số liệu hiện tại

### Traffic thấp + installs thấp

- Không phải tín hiệu chính.
- `15,055` visitors và `3,558` acquisitions chưa cho thấy vấn đề lớn nhất nằm ở `visibility / ASO / marketing`.

### Traffic tốt + conversion thấp

- Có tín hiệu nhẹ, nhưng chưa phải vấn đề số 1.
- `Store CVR 23.63%` chưa tệ; một số country còn khá ổn như `Brazil`, `Mexico`, `Philippines`.
- Kết luận: store page còn room để tối ưu, nhưng chưa phải bottleneck lớn nhất.

### Installs tốt + D1/D7 thấp

- Đây là tín hiệu xấu rõ nhất.
- `First opens 1.53K`, nhưng `D1 7.0%`, `D7 0.6%`, `D30` gần như `0`.
- Kết luận: app có người vào, nhưng không giữ được; vấn đề nhiều khả năng nằm ở `first-session UX`, `ad pressure sớm`, hoặc `core value` tới quá chậm.

### Retention tốt + revenue thấp

- Không áp dụng cho app này.
- Retention hiện không tốt, nên chưa thể kết luận revenue thấp là do monetization đơn thuần.

### Revenue cao nhưng rating xấu

- Có tín hiệu cảnh báo, nhưng chưa thể kết luận chỉ do ads.
- Review đã có phàn nàn về ads, nhưng app cũng đang có `Issue rate 3.34%` và `Crash-free users 92.9%`.
- Kết luận: rating xấu hiện tại có thể đến từ cả `ad pressure` lẫn `app quality / crash`.

## Kết luận từ số liệu hiện tại

- App chưa cho thấy dấu hiệu phải ưu tiên `ASO / visibility` trước.
- App đang có `2 vấn đề lớn nhất`:
  - `quality / crash`
  - `retention rất yếu`
- `Monetization cleanup` là hướng có giá trị để test, nhất là với `banner`.
- Nhưng nếu nhìn toàn bộ số liệu hiện tại, `monetization` chưa phải vấn đề gốc mạnh nhất.

## Kết luận nhanh

- App không thiếu ad placement.
- Ba vấn đề nổi bật nhất hiện tại là:
  - `crash / issue rate` còn cao
  - `retention` quá thấp
  - `banner yield` rất thấp
- Đã đủ dữ liệu để xếp ưu tiên.
- Không nên triển khai đồng thời nhiều hướng trong cùng một đợt đầu.

## Option 1: TỐI ƯU APP CRASH

### Chỉ số hiện tại

- `Crash-free users`: `92.9%`
- `Issue rate`: `3.34%`
- `ANR rate`: `0.09%`
- `Rating`: `4.48`, đang giảm `0.06`

### Tình trạng

- App đang crash ở một số flow quan trọng.
- Top crash group chạm vào:
  - widget update / render
  - main lifecycle
  - interstitial flow
  - widget selection flow
- Nếu chưa fix nhóm này, mọi rollout khác dễ bị méo kết quả.

### Mức độ nên update

- `5/5 - Nên update ngay`

### Cần làm

- Fix crash list
- Ưu tiên crash ảnh hưởng đến:
  - widget update / widget render
  - main activity lifecycle
  - interstitial flow
  - widget selection flow

### Mục đích

- Cải thiện `Crash-free users`
- Giảm `Issue rate`
- Giảm ảnh hưởng xấu lên retention, rating, DAU và ad revenue

### Triển khai

- Hoàn thành file:
  - [TODO_CRASHLIST_FIREBASE_PHASE1.md](/Users/remi/Documents/AndroidProjects/OneWidget/OneWidget/docs/optimization/TODO_CRASHLIST_FIREBASE_PHASE1.md)

### Theo dõi

- Theo dõi `Crash-free users`
- Theo dõi `Issue rate`
- Theo dõi top crash group theo ngày
- Theo dõi review phàn nàn về bug / crash

### Mong muốn

- `Crash-free users > 99%`
- `Issue rate < 1%`
- Không còn crash group lớn mới sau release

### Nhận xét

- Đây là option ưu tiên cao nhất.
- Nếu chưa xử lý crash mà đã sửa funnel hoặc ad mix, dữ liệu sau rollout sẽ dễ bị méo.

## Option 2: TỐI ƯU RETENTION FIRST SESSION

### Chỉ số hiện tại

- `D1`: `7.0%`
- `D7`: `0.6%`
- `D30`: gần như `0`
- `7-day active users`: `1.4K`
- `1-day active users`: `303`
- `Engaged sessions per active user`: `1.5`
- `Average engagement time per active user`: `3m 54s`

### Tình trạng

- Retention đang yếu.
- User vào app nhưng không quay lại đủ.
- First session còn quá dài trước khi user chạm giá trị chính.
- Dựa trên dữ liệu hiện có, các màn hình xuất hiện rất dày ở giai đoạn đầu gồm:
  - `SplashActivity`: `4,412` active users
  - `LanguageActivity`: `3,451` active users
  - `OnboardActivity`: `3,712` active users
  - `CateFavoriteActivity`: `2,584` active users
  - `MainActivity`: `2,583` active users
- Điều này cho thấy first session đang có quá nhiều bước trước khi user ổn định vào app.
- Chưa có funnel event đủ chi tiết để xác định chính xác bước rơi mạnh nhất.
- Với mục tiêu retention, đích cần tối ưu không phải là `vào Home`, mà là `hoàn thành widget đầu tiên và pin ra home screen` nhanh nhất có thể.

### Mức độ nên update

- `4/5 - Nên update`

### Cần làm

- Rút `first open` về flow ngắn nhất để user chạm `first widget success` nhanh nhất: bỏ `Language`, bỏ `Category Favorite`, vào `Home` và dẫn user tới flow tạo widget đầu tiên rồi `pin to home`
- Chuyển `Category/Favorites` sang `second open` như bước cá nhân hóa, còn `other open` đi thẳng vào `Home`; màn `Language` chỉ còn là tùy chọn trong `Settings`

### Mục đích

- Tăng `D1`
- Tăng `D7`
- Tăng returning users
- Tăng DAU và số impression từ user quay lại

### Triển khai

- Điều chỉnh route mở app trong source theo 3 tầng:
  - `first open`: không vào `Language`, không vào `CateFavorite`, đi thẳng tới `Home` và ưu tiên CTA dẫn tới flow tạo widget đầu tiên
  - `second open`: show `Favorites/Category`, sau khi user hoàn tất mới vào `Home`; nếu cần interstitial thì chỉ đặt ở đây, không đặt ở first open
  - `other open`: đi thẳng vào `Home`
- Điều chỉnh `Language` thành chức năng trong `Settings`, còn first open tự bám theo `device locale`
- Giảm ad pressure ở early flow:
  - không show interstitial trong `first open`
  - không đặt native/banner cản trở trước khi user chạm được flow widget đầu tiên
- Triển khai và QA theo file:
  - [TODO_RETENTION_FIRST_SESSION_PHASE1.md](/Users/remi/Documents/AndroidProjects/OneWidget/OneWidget/docs/optimization/TODO_RETENTION_FIRST_SESSION_PHASE1.md)
- Bổ sung tracking hỗ trợ để theo dõi hiệu quả rollout theo file:
  - [TODO_RETENTION_TRACKING_PHASE1.md](/Users/remi/Documents/AndroidProjects/OneWidget/OneWidget/docs/optimization/TODO_RETENTION_TRACKING_PHASE1.md)
- Sau khi hoàn tất các hạng mục trên và pass QA, app có thể publish để đo hiệu quả retention của first session mới

### Theo dõi

- `D1 retention`
- `D7 retention`
- `7-day active users`
- `Engaged sessions per active user`
- `Average engagement time per active user`
- Completion rate của:
  - `splash_open -> home_open`
  - `home_open -> first_widget_preview_open`
  - `preview -> customize`
  - `customize -> set_success`
  - `second_open -> favorites_open`
  - `favorites_open -> favorites_complete`
  - `favorites_complete -> home_open`
- Theo dõi ở level tổng app, chưa cần tách rollout theo country trong Phase 1; nếu cần segmentation thì ưu tiên theo `device locale` thay vì theo quốc gia

### Mong muốn

- `D1 > 10%`
- `D7 > 2%`
- `D30 > 1%`
- `7-day active users` tăng so với baseline `1.4K`
- `Engaged sessions per active user > 1.5`
- Tăng tỷ lệ user chạm được `first widget success` ngay từ first open

### Nhận xét

- Retention đang rất yếu.
- Nếu mục tiêu là tăng trưởng bền vững, đây là phương án đứng thứ 2 sau crash.

## Option 3: TỐI ƯU MONETIZATION CLEANUP

### Chỉ số hiện tại

- Tổng ad revenue 30 ngày: `$43.97`
- Revenue share:
  - `Native`: `56.63%`
  - `Interstitial`: `31.36%`
  - `Banner`: `7.96%`
  - `App Open`: `4.05%`
- eCPM:
  - `Interstitial`: `~$2.78`
  - `Native`: `~$1.21`
  - `App Open`: `~$1.01`
  - `Banner`: `~$0.35`

### Tình trạng

- Banner có độ phủ rộng nhưng yield rất thấp.
- Native và interstitial đang là 2 nhóm tạo giá trị chính.
- App không thiếu ad placement, vấn đề là placement nào đang kém hiệu quả.
- Trong source hiện tại, `Home`, `Special` và `Customize` đều đang dùng `ExpandedBanner`.
- `HOME_BANNER_ADS` và `SPECIAL_BANNER_ADS` còn đang dùng cùng `adUnitId` và cùng `HOME_BANNER_ID`.
- Điều này làm tăng khả năng banner đang chiếm diện tích lớn hơn mức cần thiết, trong khi `banner eCPM` hiện rất thấp.
- App hiện cũng đang show interstitial khi user click `bottom navigation menu`.
- Với `ACTIONS_FOR_SHOW = 3`, placement này dễ tạo cảm giác bị chặn ở các `second session` và `other open`, vì đây là hành vi điều hướng low-intent chứ không phải điểm chuyển đổi giá trị cao.
- Đây là placement nên cân nhắc bỏ trước vì:
  - user chỉ đang đổi tab để xem nội dung khác trong app, chưa phải lúc đã đạt một bước giá trị rõ như `preview -> customize` hoặc `customize -> save`
  - hành vi click menu có thể xảy ra nhiều lần trong một session, nên nếu chèn interstitial ở đây sẽ tạo cảm giác app chặn điều hướng cơ bản
  - interstitial ở `bottom navigation` dễ làm xấu `engagement`, `session depth`, `retention` và cảm nhận chung về app hơn so với interstitial ở các flow intent cao
  - hiện retention của app đang yếu, nên cần ưu tiên giữ trải nghiệm điều hướng chính mượt trước khi tối ưu thêm doanh thu từ placement này

### Mức độ nên update

- `3/5 - Có thể update`

### Cần làm

- Giảm mức độ xâm lấn của banner ở `Home`, ưu tiên thay `ExpandedBanner` bằng banner thường hoặc placement nhỏ hơn
- Bỏ interstitial ở `bottom navigation`, chỉ giữ interstitial ở các flow intent cao hơn
- Tách riêng chiến lược theo placement: test `Home banner` trước, sau đó mới quyết định có áp dụng tiếp cho `Special` hay không

### Mục đích

- Giảm ad pressure ở placement rộng nhưng yield thấp
- Giữ revenue từ placement mạnh hơn như `Native` và `Interstitial`
- Cải thiện user comfort
- Bảo vệ retention và rating

### Triển khai

- Chọn `Home` làm rollout đầu tiên cho banner cleanup
- Đổi `HOME_BANNER_ADS` khỏi kiểu `ExpandedBanner`, thay bằng banner ít chiếm diện tích hơn
- Gỡ interstitial khi user click `bottom navigation menu`
- Chưa đổi global `ACTIONS_FOR_SHOW = 3` ở đợt này; ưu tiên bỏ placement low-intent trước rồi mới đo lại
- Chưa đổi đồng loạt `Special` và `Customize` trong cùng đợt đầu để tránh nhiễu kết quả
- Nếu kết quả tốt, mới mở rộng sang `SPECIAL_BANNER_ADS`
- Triển khai và QA theo file:
  - [TODO_BANNER_CLEANUP_PHASE1.md](/Users/remi/Documents/AndroidProjects/OneWidget/OneWidget/docs/optimization/TODO_BANNER_CLEANUP_PHASE1.md)

### Theo dõi

- Total ad revenue
- Revenue by format
- Interstitial impressions
- ARPDAU
- Impressions per DAU
- Session depth
- Engagement time
- D1 / D7
- Rating trend

### Mong muốn

- Total ad revenue không giảm quá `10%`
- Banner revenue có thể giảm, nhưng engagement không xấu đi
- ARPDAU ổn định hoặc tăng
- D1 / D7 không giảm sau rollout
- Rating trend không xấu đi

### Nhận xét

- Đây là option dễ test nhanh nhất.
- Nhưng nếu crash và retention vẫn xấu, nó không giải quyết được vấn đề gốc.

## Option 4: TỐI ƯU STORE CONVERSION

### Chỉ số hiện tại

- Store visitors: `15,055`
- Store acquisitions: `3,558`
- Store CVR: `23.63%`
- First opens: `1.53K`, giảm `3%`
- Main country CVR:
  - `Brazil`: `25.4%`
  - `Turkey`: `23.22%`
  - `Mexico`: `26.72%`
  - `Indonesia`: `19.6%`
  - `United States`: `22.99%`
  - `Philippines`: `30.16%`

### Tình trạng

- Listing vẫn còn room để tối ưu.
- Asset listing chưa đầy đủ cho tablet / Chromebook.
- Tuy vậy, conversion không phải vấn đề cấp bách nhất nếu so với crash và retention.
- `Store CVR 23.63%` hiện chưa đủ xấu để coi store page là bottleneck chính.
- Nếu can thiệp vào phần này, cần có lý do kinh doanh rõ hơn là chỉ “listing còn tối ưu được”.

### Mức độ nên update

- `1/5 - Không cần update`

### Cần làm

- Chỉ đánh giá lại listing khi đã có mục tiêu rõ về tăng acquisition hoặc scale traffic
- Chỉ tối ưu thêm title, description, screenshots, feature graphic, tablet / Chromebook assets khi `Store CVR` trở thành bottleneck rõ hoặc khi cần chuẩn bị cho giai đoạn đẩy growth

### Mục đích

- Tăng `Store CVR`
- Tăng số install mới từ cùng một lượng traffic

### Triển khai

- Không phải rollout ưu tiên ở giai đoạn hiện tại
- Chỉ mở khi có một trong các điều kiện sau:
  - app đã ổn hơn về crash và retention
  - team cần đẩy acquisition
  - `Store CVR` giảm rõ hoặc kém rõ rệt ở các locale / country chính

### Theo dõi

- Store listing visitors
- Store acquisitions
- Store CVR
- CVR theo country
- First opens
- Rating trend sau khi tăng install

### Mong muốn

- `Store CVR > 23.63%`
- Tăng acquisition mà không làm xấu issue rate / rating

### Nhận xét

- Option này có giá trị.
- Nhưng đây là backlog chiến lược cấp sau, không phải việc nên ưu tiên can thiệp ngay lúc này.

## Xếp hạng options hiện tại

1. `TỐI ƯU APP CRASH`
2. `TỐI ƯU RETENTION FIRST SESSION`
3. `TỐI ƯU MONETIZATION CLEANUP`
4. `TỐI ƯU STORE CONVERSION`

## Gợi ý chọn options hiện tại

Nếu chỉ chọn `1` hướng:

- chọn `TỐI ƯU APP CRASH`

Nếu chọn `1 hướng chính + 1 test nhỏ`:

- hướng chính: `TỐI ƯU APP CRASH`
- test nhỏ sau đó: `TỐI ƯU MONETIZATION CLEANUP`

## Các chỉ số bị ảnh hưởng sau rollout

### Nếu triển khai `TỐI ƯU APP CRASH`

- Chỉ số chính bị ảnh hưởng:
  - `Crash-free users`
  - `Issue rate`
  - `ANR rate`
  - `Top crash groups`
- Chỉ số kéo theo cần nhìn:
  - `Rating trend`
  - `D1 / D7`
  - `1-day / 7-day active users`
  - `Total ad revenue`

### Nếu triển khai `TỐI ƯU RETENTION FIRST SESSION`

- Chỉ số chính bị ảnh hưởng:
  - `D1`
  - `D7`
  - `D30` nếu có
  - `1-day / 7-day / 30-day active users`
  - `Returning users`
  - `first_widget_set_success`
- Chỉ số kéo theo cần nhìn:
  - `Views per active user`
  - `Engagement time per active user`
  - `Engaged sessions per active user`
  - `Crash-free users`
  - `Issue rate`
  - `Total ad revenue`
  - `Revenue by format`

### Nếu triển khai `TỐI ƯU MONETIZATION CLEANUP`

- Chỉ số chính bị ảnh hưởng:
  - `Total ad revenue`
  - `Revenue by format`
  - `ARPDAU`
  - `Interstitial impressions`
  - `Impressions per DAU`
- Chỉ số kéo theo cần nhìn:
  - `D1 / D7`
  - `Views per active user`
  - `Engagement time per active user`
  - `Rating trend`
  - `Crash-free users`
  - `Issue rate`

### Nếu triển khai `TỐI ƯU STORE CONVERSION`

- Chỉ số chính bị ảnh hưởng:
  - `Store visitors`
  - `Store acquisitions`
  - `Store CVR`
  - `CVR theo country`
  - `First opens`
- Chỉ số kéo theo cần nhìn:
  - `D1 / D7`
  - `Rating trend`
  - `Issue rate`

## Mốc kiểm tra cố định sau publish

Mỗi phase mặc định phải có 3 mốc theo dõi:

- `3 days`
- `7 days`
- `14 days`

Chỉ phase đặc biệt mới dùng mốc khác.

### 3 days

- Đọc sớm các chỉ số nhạy nhất với action vừa rollout
- Mục tiêu:
  - phát hiện lỗi lớn
  - phát hiện tụt revenue mạnh
  - phát hiện tụt retention hoặc rating bất thường
- Ưu tiên xem:
  - `Crash-free users`
  - `Issue rate`
  - `Total ad revenue`
  - `ARPDAU`
  - `1-day active users`
  - `Rating trend` nếu có biến động bất thường

### 7 days

- Đây là mốc đọc chính của phase
- Phải đọc đủ:
  - chỉ số chính bị ảnh hưởng bởi action đã rollout
  - chỉ số kéo theo
  - guardrail về quality, retention, revenue
- Mục tiêu:
  - xác định rollout có đi đúng hướng hay không
  - xác định có cần chỉnh nhỏ hay không

### 14 days

- Đây là mốc kết luận phase
- Mục tiêu:
  - giữ rollout
  - chỉnh rollout
  - rollback
  - hoặc chuyển sang phase tiếp theo

## Đầu vào bắt buộc cho phase tiếp theo

Khi bắt đầu phase tiếp theo, phải đọc lại các kết quả sau của phase trước:

- action nào đã rollout
- các chỉ số chính bị ảnh hưởng của action đó
- kết quả tại `3 days`
- kết quả tại `7 days`
- kết quả tại `14 days`
- chỉ số nào tăng đúng kỳ vọng
- chỉ số nào giảm hoặc vi phạm guardrail
- có crash group mới hay không
- có review / rating xấu mới hay không
- kết luận cuối cùng:
  - giữ
  - chỉnh
  - rollback
  - hay chuyển phase
