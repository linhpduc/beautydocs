# Phân biệt giữa data và pageData

Khi render dữ liệu hoặc xử lý logic trên js, mọi người sẽ rất hay nhìn thấy 2 object `#!php5 Client.pageData` và `Client.data`.

Hai object này chính là cách render dữ liệu từ server lên giao diện chính.

## pageData

Bạn load dữ liệu ra ra mảng `books`. Bạn gán nó vào key books bằng hàm `\Client::pageData`.
``` php
\Client::pageData("books", $books);
```

Sau đó bạn có thể sử dụng nó qua object `Client.pageData` ở phía JS.
```js title="script.js" linenums="1"
var html = AP.render(Client.pageData.books, function (book) {
    return `<div>${book.name}</div>`
}
```

## data

Bạn load dữ liệu ra mảng `books`. Bạn gán nó vào key books bằng hàm `\Client::data`.
``` php
\Client::data("books", $books);
```

Sau đó bạn có thể sử dụng nó qua object `Client` ở phía JS
```js title="script.js" linenums="1" hl_lines="1"
var html = AP.render(Client.books, function (book) {
    return `<div>${book.name}</div>`
}
```

!!! note "Sự khác biệt"

    Khác biệt ở chỗ Object `Client.data` sẽ chỉ phải load lần đầu khi mở trang.
    
    Khi bạn navigate giữa các đường link bên trong một app của Base, Base platform support chỉ load ajax, và fill html vào những content ở giữa, còn bản chất trang web không hề load lại.
    
    ⇒ Khi tình huống đó xảy ra, `Client.data` sẽ không load lại , trong khi object `Client.pageData` sẽ thay đổi tuỳ vào giữ liệu của trang.
    ⇒ đó cũng chính là lý do tại sao nó gọi là **pageData**, right ??
    
    Để load lại object `Client.data` thì ta chỉ cần đơn giản là load lại trạng web bằng cách F5 refresh.

## Sử dụng

Vậy khi nào thì sử dụng `Client.data` , khi nào sử dụng `Client.pageData`?

Thường những giữ liệu nào trang nào cũng dùng thì ta sẽ lưu vào `Client.data`, ví dụ chứa dữ liệu các notebooks để render ở menu như app Base wiki.

Trong khi `Client.pageData` thì sẽ chứa dữ liệu của riêng trang đó như dữ liệu comments, dữ liệu article khi vào trang chi tiết của 1 article.

## Tổng kết

| Client.data | Client.pageData |
| ----------- | ----------- |
| Load lần đầu khi tải trang,không thay đổi khi navigate giữa các trang trong một app | Mỗi khi sang trang mới trong một app |
| Sử dụng lưu những dữ liệu không thay đổi, <br /> trang nào cũng có | Lưu dữ liệu của riêng từng trang |