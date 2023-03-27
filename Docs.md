## Tài liệu tham khảo:
- https://viblo.asia/p/hoc-regex-co-ban-GrLZDvxV5k0
- https://viblo.asia/p/phan-tich-mot-so-doan-regex-thuong-gap-va-cu-phap-regex-dac-biet-bJzKmLmE59N
- https://www.hongkiat.com/blog/regex-web-developers/

## Quy tắc cơ bản
### Ký tự thể hiện vị trí  ^ và $
- Chúng ta sẽ làm ví dụng với chuỗi The end

- `^The` Khớp với từ The nhưng nó phải đứng ở đầu chuỗi -> Try it!
- `end$` Khớp với từ end nhưng nó phải đứng ở cuối chuỗi
- `^The` end$ Khớp với chuỗi The end
- `end` Khớp với từ end ở bất kỳ vị trí nào

### Ký tự thể hiện số lượng  * + ? và {}
- Chuỗi ví dụ abc

- `abc*` Khớp với từ ab và có nhiều hoặc không có ký tự c đắng sau (ab, abc ,abccccc...) -> Try it!
- `abc+` Khớp với từ ab và có một hoặc nhiều ký tự c đằng sau (abc, abcccc....)
- `abc?` Khớp với từ ab và có 1 hoặc không có ký tự c đắng sau(ab, abc)
- `abc{2}` Khớp với từ ab và có 2 ký tự c đắng sau(abcc)
- `abc{2,}` Khớp với từ ab và có từ 2 ký tự c đắng sau(abcc, abccccc...) *abc{2,5} Khớp với từ abvà có từ 2 đến 5 ký tự c đắng sau(abcc,baccc..)
- `a(bc)*` Khớp với từ a và có nhiều hoặc không có ký tự bc đắng sau(a, abc ,abcbc...)
- `a(bc){2,5}` Khớp với từ a và có từ 2 đến 5 ký tự bc đắng sau(abcbc, abcbc....)

### Toán tử hoặc | và []
- `a(b|c)` Khớp với từ 'a' và có 1 ký tự c hoặc b đắng sau(ab, ac) -> Try it!
- `a[bc]` Kết quả như trên

### Ký tự phân loại \d \w \s và .
- `\d` Khớp với 1 ký tự số(từ 0 đến 9) -> Try it!
- `\w` Khớp với bất kỳ ký 1 tự số hoặc chữ hoặc dấu gạch dưới _
- `\s` Khớp với ký tự khoảng trăng(bap gồm cả tab, xuống dòng)
- `.` Khớp với bất kỳ ký tự nào -> Try it!1
#### \d, \w, \s còn có phủ định của nó \D, \W, \S

- `\D` Khớp với 1 ký tự không phải là số-> Try it!
- `\W` Khớp với bất kỳ ký tự không phải là 1 số, chữ hoặc dấu gạch dưới '_'
- `\S` Khớp với ký tự không phải là khoảng trăng(bap gồm cả tab, xuống dòng)

### Flags
Chúng ta sử dụng regex nhưng thường không chú ý đến một khái niệm cơ bản là flag(cờ). Biểu thức chính quy có dạng /abc/ và sau nó là flag với 3 giá trị sau:
- `g (global)` tìm tất cả các đoạn ký tự khớp với mẫu tìm kiếm, nếu không có cờ g thì việc tìm kiếm sẽ dừng lại ở lần khớp đầu tiên.
- `m (multi line)` khi có ^ và $ thì ^ sẽ là bắt đầu 1 dòng và $ là kết thúc 1 dòng trong chuỗi, nếu không có cờ m thì ^ và $ là bắt đầu và kết thúc của cả chuỗi
- `i (insensitive)` không phân biệt chữ hoa chữ thường(vd:aBc sẽ khớp với pattern /abc/i )
