---
title: Lớp Slideshow
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-12-25T00:44:42.803Z
---

# Lớp Slideshow

## Giới thiệu

Lớp `Slideshow` được dùng để đặt nhiều `PresenceData` và "trình chiếu" chúng mỗi x mili giây (tối thiểu: 5000).

Xem thêm về phương thức [`createSlideshow`](/dev/presence/class#createslideshow) trong lớp [`Presence`](/dev/presence/class) để biết cách tạo một `Slideshow`.

## Thuộc tính

### `currentSlide`

Đưa trả đối tượng [`PresenceData`](/dev/presence/class#presencedata-interface) của những gì presence/slide hiện tại đang hiển thị.

```ts
const currentSlide = slideshow.currentSlide
console.log(currentSlide.details) // Sẽ ghi lại nhật ký các chi tiết của PresenceData
```

## Phương pháp

### `addSlide(String, PresenceData, Number)`

Thêm một slide mới vào `Slideshow` dựa trên thông tin được cung cấp.

Tham số đầu tiên yêu cầu một `String` để làm chuỗi định danh độc nhất cho slide.

Tham số thứ hai yêu cầu một [giao diện `PresenceData`](/dev/presence/class#presencedata-interface) để lấy tất cả thông tin bạn cần để hiển thị trên slide.

Tham số thứ ba yêu cầu một `Số` dùng làm khoảng thời gian viết dưới dạng mili giây (tối thiểu: 5000) mà slide sẽ được chiếu.

### `getSlides()`

Đưa trả tất cả các slide được lưu trong `Slideshow` dưới dạng một `Array` của [`SlideshowSlide`](#slideshowslide-class).

### `updateSlide(String, PresenceData, Number)`

Cập nhật slide với `id` cho sẵn dựa trên dữ liệu được cung cấp.

Tham số đầu tiên yêu cầu một `String` được dùng làm chuỗi định danh độc nhất của slide bạn muốn cập nhật.

Tham số thứ hai yêu cầu một [giao diện `PresenceData`](/dev/presence/class#presencedata-interface) để lấy tất cả thông tin bạn cần để hiển thị trên slide.

Tham số thứ ba yêu cầu một `Số` dùng làm khoảng thời gian viết dưới dạng mili giây (tối thiểu: 5000) mà slide sẽ được chiếu.

### `hasSlide(String)`

Đưa trả một `Boolean` xác định xem slide có được thêm vào `Slideshow` không.

### `deleteSlide(String)`

Xoá slide với `id` được cho sẵn khỏi `Slideshow`.

Tham số đầu tiên yêu cầu một `String` được dùng làm chuỗi định danh độc nhất của slide bạn muốn xoá.

### `deleteAllSlides()`

Xoá tất cả các slide khỏi `Slideshow`.

# Lớp SlideshowSlide

## Giới thiệu

`SlideshowSlide` là cách biểu diễn nội bộ của mỗi slide trong một `Slideshow`.

## Thuộc tính

### `id`

Đưa trả một `String` của id của slide.

### `data`

Đưa trả đối tượng [`PresenceData`](/dev/presence/class#presencedata-interface) của `PresenceData` được lưu trong slide.

## Phương pháp

### `updateData(PresenceData)`

Đặt dữ liệu của slide dựa trên dữ liệu đã được cung cấp.

Bạn phải cung cấp một giao diện `PresenceData` để lấy tất cả các thông tin bạn cần được hiển thị lên hồ sơ của bạn.

### `updateInterval(Number)`

Đặt một khoảng thời gian cho slide hiển thị cách nhau dựa trên dữ liệu được cung cấp.

Bạn phải cung cấp một `Số` để dùng làm khoảng thời gian dưới dạng mili giây (tối thiểu: 5000) mà slide sẽ chiếu.
