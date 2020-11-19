# notes

## 1. Laravel API same session

Để sử dụng api sau khi login không cần Token thì trong config/session
chuyển `'same_site' => 'lax',` thanh `'same_site' => null,`
add
```
\App\Http\Middleware\EncryptCookies::class,
\Illuminate\Session\Middleware\StartSession::class,
```
to api in Kernel.php

## 2. Vấn đề khi chuyển hướng tới trang login khi sử dụng osiset/laravel-shopify

Thêm đoạn này vào router
```
Route::get('/login', function () {
  if(Auth::check()) {
    return \Redirect::route('home');
  }
  return view('login');
})->name('login');
Route::get('/', function () {
    return view('welcome');
})->middleware(['auth'])->name('home');
Route::get('/shop', function () {
    return redirect()->route('home');
})->middleware(['auth.shopify'])->name('shop');
```

