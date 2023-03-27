## Tài liệu tham khảo:
- https://viblo.asia/p/hoc-regex-co-ban-GrLZDvxV5k0
- https://viblo.asia/p/phan-tich-mot-so-doan-regex-thuong-gap-va-cu-phap-regex-dac-biet-bJzKmLmE59N
- https://www.hongkiat.com/blog/regex-web-developers/

#### Regex tham khảo
- Password: `^(?=.*[A-Z].*[A-Z])(?=.*[!@#$&*])(?=.*[0-9].*[0-9])(?=.*[a-z].*[a-z].*[a-z]).{8}$`
  + ^                         Start anchor
  + (?=.*[A-Z].*[A-Z])        Ensure string has two uppercase letters.
  + (?=.*[!@#$&*])            Ensure string has one special case letter.
  + (?=.*[0-9].*[0-9])        Ensure string has two digits.
  + (?=.*[a-z].*[a-z].*[a-z]) Ensure string has three lowercase letters.
  + .{8}                      Ensure string is of length 8.
  + $                         End anchor.


## Quy tắc cơ bản
### Ký tự thể hiện vị trí  ^ và $
- Chúng ta sẽ làm ví dụng với chuỗi The end

- `^The` Khớp với từ The nhưng nó phải đứng ở đầu chuỗi
- `end$` Khớp với từ end nhưng nó phải đứng ở cuối chuỗi
- `^The` end$ Khớp với chuỗi The end
- `end` Khớp với từ end ở bất kỳ vị trí nào

### Ký tự thể hiện số lượng  * + ? và {}
- Chuỗi ví dụ abc

- `abc*` Khớp với từ ab và có nhiều hoặc không có ký tự c đắng sau (ab, abc ,abccccc...)
- `abc+` Khớp với từ ab và có một hoặc nhiều ký tự c đằng sau (abc, abcccc....)
- `abc?` Khớp với từ ab và có 1 hoặc không có ký tự c đắng sau(ab, abc)
- `abc{2}` Khớp với từ ab và có 2 ký tự c đắng sau(abcc)
- `abc{2,}` Khớp với từ ab và có từ 2 ký tự c đắng sau(abcc, abccccc...) *abc{2,5} Khớp với từ abvà có từ 2 đến 5 ký tự c đắng sau(abcc,baccc..)
- `a(bc)*` Khớp với từ a và có nhiều hoặc không có ký tự bc đắng sau(a, abc ,abcbc...)
- `a(bc){2,5}` Khớp với từ a và có từ 2 đến 5 ký tự bc đắng sau(abcbc, abcbc....)

### Toán tử hoặc | và []
- `a(b|c)` Khớp với từ 'a' và có 1 ký tự c hoặc b đắng sau(ab, ac)
- `a[bc]` Kết quả như trên

### Ký tự phân loại \d \w \s và .
- `\d` Khớp với 1 ký tự số(từ 0 đến 9)
- `\w` Khớp với bất kỳ ký 1 tự số hoặc chữ hoặc dấu gạch dưới _
- `\s` Khớp với ký tự khoảng trăng(bap gồm cả tab, xuống dòng)
- `.` Khớp với bất kỳ ký tự nào ->
#### \d, \w, \s còn có phủ định của nó \D, \W, \S

- `\D` Khớp với 1 ký tự không phải là số->
- `\W` Khớp với bất kỳ ký tự không phải là 1 số, chữ hoặc dấu gạch dưới '_'
- `\S` Khớp với ký tự không phải là khoảng trăng(bap gồm cả tab, xuống dòng)

### Flags
Chúng ta sử dụng regex nhưng thường không chú ý đến một khái niệm cơ bản là flag(cờ). Biểu thức chính quy có dạng /abc/ và sau nó là flag với 3 giá trị sau:
- `g (global)` tìm tất cả các đoạn ký tự khớp với mẫu tìm kiếm, nếu không có cờ g thì việc tìm kiếm sẽ dừng lại ở lần khớp đầu tiên.
- `m (multi line)` khi có ^ và $ thì ^ sẽ là bắt đầu 1 dòng và $ là kết thúc 1 dòng trong chuỗi, nếu không có cờ m thì ^ và $ là bắt đầu và kết thúc của cả chuỗi
- `i (insensitive)` không phân biệt chữ hoa chữ thường(vd:aBc sẽ khớp với pattern /abc/i ).

## Quy tắc nâng cao
### Ký hiệu phân nhóm ()
- a(bc) trong cặp dấu ngoặc là một group, giá trị trong group sẽ được capture lại 
- a(?:bc)* giá trị trong group sẽ không được capture lại
- a(?<foo>bc) đặt tên cho group, mặc địng group sẽ có chỉ số là group[0], group[1], trường hợp này group sẽ là group[foo].
- Đây là một quy tắc rất hữu ích nếu bạn bần trích xuất data từ một chuỗi. Bất kì thông tin nào được match sẽ được trích xuất vào trong một mảng, và ta có thể lấy nó thông qua chỉ mục của các group hoặc tên của group nếu đặt tên. Nếu không muốn bắt thông tin trong group, ta dùng ?:, khi đó group chỉ đơn thuần là một điều kiện và giá trị trong đó xẽ không được trích xuất.
  
### Kí hiệu chỉ phạm vi []
- `[abc]` khớp với 1 ký tự a hoặc b hoặc c -> tương tự cách dùng a|b|c 
- `[a-c]` tác dụng như trên
- `[a-fA-F0-9]` khớp với 1 ký tự nằm trong khoảng từ a -> z hoặc A -> Z hoặc 0 -> 9(đây chính là đoạn regex để bắt ký tự trong hệ HEX)
- `[0-9]%` khớp với 1 ký tự từ 0 ->9 và theo sau nó là ký tự %
- `[^a-zA-Z]` khớp với ký tự không nằm nằm trong a -> z và A -> Z
  `Chú ý: Chức năng của một ký tự đặc biệt nào đó sẽ thay đổi khi nó nằm ở các vị trí khác nhau trong partten. ở ví dụ cuối cùng, ký tự ^ nằm trong [] thể hiện sự phủ định, chứ không phải xác định bắt đầu chuỗi. Nên cần chú ý vị trí của ký tự đặc biệt để biết chức năng của nó`.

  
 ### Back-references  \1
- `([abc])\1` sử dụng \1 sẽ match khi có 1 kí tự tiếp theo giống với kí tự được match trong group đầu tiên. Hơi khó hiểu, bạn xem ví dụ sẽ rõ hơn nhé
- `([abc])([de])\2\1` Chúng ta có thể xử dụng \2,\3 để math kí tự giống với group thứ 2, 3 
- `(?<foo>[abc])\k<foo>` Có thể đặt tên cho group thay cho số thứ tự 
  
 ### Look-ahead and Look-behind (?=) và (?<=)
- `d(?=r)` match với d và theo sau d là r, nhưng r sẽ không nằm trong data được match 
- `(?<=r)d` match với d và trước d là r , tất nhiên r cũng hông nằm trong data được match
#### Nó cũng có toán tử phủ định

- `d(?!r)` match với d và theo sau d là 1 ký tự không phải là r. 
- `(?<!r)d` match với d và trước d là 1 ký tự không phải r 
