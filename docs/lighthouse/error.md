---
sidebar_position: 2
---
# Các lỗi thường gặp

### Các đường liên kết không thể thu thập thông tin ###
- Thay `href="javascript:void(0);"` bằng `href="#" onclick="return false;"`

### Các phần tử liên kết không có tên có thể nhận rõ ###
- Đối với thẻ a: Thêm `aria-label: nội dung`
- Đối với thẻ button, input: Thêm `title: nội dung`

### Không sử dụng trình nghe bị động để cải thiện hiệu suất cuộn ###
``` js
if(window.noPS){
  jQuery.event.special.touchstart = {
		setup: function( _, ns, handle ) {
			this.addEventListener("touchstart", handle, { passive: !ns.includes("noPreventDefault") });
		}
	};
	jQuery.event.special.touchmove = {
		setup: function( _, ns, handle ) {
			this.addEventListener("touchmove", handle, { passive: !ns.includes("noPreventDefault") });
		}
	};
}
```