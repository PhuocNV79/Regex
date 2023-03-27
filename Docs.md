https://viblo.asia/p/hoc-regex-co-ban-GrLZDvxV5k0

## Quy tắc cơ bản
### Ký tự thể hiện vị trí  ^ và $
- Chúng ta sẽ làm ví dụng với chuỗi The end

- ^The Khớp với từ The nhưng nó phải đứng ở đầu chuỗi -> Try it!
- end$ Khớp với từ end nhưng nó phải đứng ở cuối chuỗi
- ^The end$ Khớp với chuỗi The end
- end Khớp với từ end ở bất kỳ vị trí nào

### Ký tự thể hiện số lượng  * + ? và {}
- Chuỗi ví dụ abc

- abc* Khớp với từ ab và có nhiều hoặc không có ký tự c đắng sau (ab, abc ,abccccc...) -> Try it!
- abc+ Khớp với từ ab và có một hoặc nhiều ký tự c đằng sau (abc, abcccc....)
- abc? Khớp với từ ab và có 1 hoặc không có ký tự c đắng sau(ab, abc)
- abc{2} Khớp với từ ab và có 2 ký tự c đắng sau(abcc)
- abc{2,} Khớp với từ ab và có từ 2 ký tự c đắng sau(abcc, abccccc...) *abc{2,5} Khớp với từ abvà có từ 2 đến 5 ký tự c đắng sau(abcc,baccc..)
- a(bc)* Khớp với từ a và có nhiều hoặc không có ký tự bc đắng sau(a, abc ,abcbc...)
- a(bc){2,5} Khớp với từ a và có từ 2 đến 5 ký tự bc đắng sau(abcbc, abcbc....)
