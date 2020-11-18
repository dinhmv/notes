# notes

## 1. Laravel API same session

Để sử dụng api sau khi login không cần Token thì trong config/session
chuyển `'same_site' => 'lax',` thanh `'same_site' => null,`
