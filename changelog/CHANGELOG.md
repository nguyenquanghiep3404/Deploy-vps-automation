# Changelog

Mọi thay đổi đáng chú ý của Auto VPS Deploy CLI được ghi lại tại đây.

## Unreleased

### Added

- Sinh workflow deploy có lọc thay đổi theo thư mục trong monorepo. Mỗi workflow chỉ chạy khi thư mục của phần tương ứng thay đổi; thay đổi file workflow của chính nó vẫn kích hoạt chạy.
- Tự phát hiện các script `lint`, `typecheck` và `test` trong `package.json` của dự án Node.js/SPA.
- Chạy quality gate theo thứ tự `lint` → `typecheck` → `test` trước build và deploy. Khi một script thất bại, workflow dừng trước khi rsync lên VPS.
- Hỗ trợ quality script trong monorepo/workspace: ưu tiên script tại gốc repo (Turbo/workspaces), sau đó dùng script tại package frontend/backend.

### Changed

- Workflow ở gốc repo vẫn chạy với mọi thay đổi trên `main` hoặc `master`; chỉ workflow có `workingDir` là thư mục con mới dùng bộ lọc đường dẫn.
