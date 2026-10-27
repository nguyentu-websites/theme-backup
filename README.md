# theme-backup — Bản sao dự phòng theme Nguyễn Tú

**Nguồn:** https://github.com/thuexemayhanoi/theme  
**Đích:** https://github.com/nguyentu-websites/theme-backup

## Trạng thái
Chưa xác nhận sao lưu xong. Repository này có workflow sao lưu một lần ở `.github/workflows/backup-theme-once.yml`. Không xem README hoặc workflow là bằng chứng backup đã hoàn thành; chỉ công nhận khi GitHub Actions báo `success` và số nhánh + SHA được đối chiếu.

## Thiết lập an toàn
1. Vào Settings > General > Danger Zone > Change repository visibility, chuyển **theme-backup thành Private**.
2. Tạo GitHub fine-grained personal access token với quyền **Contents: Read-only** và phạm vi **chỉ** repo `thuexemayhanoi/theme`.
3. Vào `theme-backup > Settings > Secrets and variables > Actions > New repository secret`; đặt tên `THEME_SOURCE_READ_TOKEN`. Không ghi token vào README, issue hoặc file mã nguồn.
4. Vào Actions > **Snapshot source theme repository (one time)** > Run workflow.
5. Kiểm tra run thành công và các branch dưới `snapshots/2026-10-28/*`. Lần kiểm kê ban đầu: 71 nhánh ở repo nguồn.

## Nguyên tắc
- Không chỉnh sửa repo nguồn.
- Không ghi đè nhánh `main` hiện tại của repo backup; snapshot lưu ở nhánh có tiền tố `snapshots/`.
- Không force-push hay xóa nhánh cũ.
- Bảo mật token và thu hồi token khi không cần nữa.
- Đây là backup Git repo, **không phải** backup database/media WordPress trên hosting.
