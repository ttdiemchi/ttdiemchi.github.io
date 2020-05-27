---
layout: post
title: "Linear data structure"
categories:
  - "Data structure"
---

Data structure là các phương thức cụ thể để tổ chức dữ liệu nhằm sử dụng nó một cách hiệu quả.

Bài này mình sẽ đi sâu vào tìm hiểu bản chất chứ không bao gồm cách implement nó như nào.

### Array

Là một block memory, dùng để chứa các phần tử có cùng kiểu dữ liệu ở vị trí liền kề nhau trong block đó. Kích thước của array phải được chỉ ra trước khi được lưu trữ và nó luôn cố định.

_Array in memory_

Khi một array `A` được khởi tạo với `N` phần thử, và mỗi phần tử có độ dài `M` bytes.

- Trình biên dịch sẽ cấp phát `N * M` bytes cho array này, phần tử đầu tiên được chứa trong `M` bytes đầu, lần lượt với các phần tử tiếp theo.
- Trình biên dịch sẽ lưu lại địa chỉ trong bộ nhớ của byte đầu tiên của phần tử đầu tiên - cũng được xem như là địa chỉ của array. Vì các phần tử có kích thước bằng nhau và nằm liên tiếp bộ nhớ, nên nó có thể truy cập đến được các phần tử bất kì trong array bằng `index`.
- Cần truy cập vào địa chỉ `A[n]`. Trình biên dịch sẽ đến vị trí `n*M` bytes và lấy ra M bytes sau đó. Đây cũng là 1 lý do tại sao index của array lại bắt đầu từ `0`.

### Linked List

Chứa các phần tử là object (node) bao gồm 2 phần:

- dữ liệu (data)
- reference đến node tiếp theo / node trước đó (pointer)

Khi một phần tử được thêm vào list, trình biên dịch sẽ cấp phát bộ nhớ cho node mới này ở 1 địa chỉ bất kì, sau đó link địa chỉ mới này với list. Điều này đồng nghĩa với việc CPU không thể cache nội dung của 1 linked list như array, do đó nó thường không được sử dụng để implement `queue`.

Một nhược điểm nữa của linked list đó là `không thực sự nhanh trong việc truy cập phần tử`. Muốn truy cập vào phần tử thứ N thì luôn cần phải duyệt qua N node từ node đầu tiên.

Một số loại linked list:

_Single Linked List_

A → B → C

Từ một node có thể xác định được node kề sau nó.

_Double Linked List_

A ↔ B ↔ C

Từ một node có thể xác định được node kề trước và kề sau nó.

_Cicular Linked List_

A → B → C → A hoặc A ↔ B ↔ C ↔ A

### Stack

![](/images/stack.png)

Stack (xếp chồng) hay còn có 1 tên gọi khác là LIFO (last in first out) là 1 collection hoạt động trên cơ chế `phần tử vào đầu thì ra cuối, phần tử vào cuối thì ra đầu`.

Một số trường hợp có thể sử dụng `stack`:

- Backtracking: Cần `undo` lại hành động trước đó: back lại trang trước đó ...
- Thuật toán đệ quy

### Queue

![](/images/queue.png)

Hay còn được gọi với tên khác là FIFO (first in first out) là 1 collection hoạt động trên cơ chế `phần tử vào trước thì sẽ được lấy ra trước`.

Một số trường hợp có thể dùng `queue`:

- First Come First Serve: App của bạn nhận rất nhiều request nhưng mỗi lần chỉ xử lý đc một vài cái. Lúc này có thể tạo 1 queue để nhận request và xử lý dần, request nào đến trước thì xử lý trước, cái nào đến sau thì xử lý sau
- Cache
- Breadth First Search

Cả `Stack` và `Queue` có thể được implement bằng array hoặc linked list
