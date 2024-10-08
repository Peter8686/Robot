# Ứng dụng cảm biến quang trở trong dò đường cho Robot

## Intro

Đầu tiên, đây là 1 dự án miễn phí nhằm hỗ trợ các bạn học viên, sinh viên áp dụng công nghệ dò đường cho robot sử dụng cảm biến quang trở.

Công nghệ dò đường cho robot sử dụng các cảm biến quang trở hay hồng ngoại,...v.v đã có từ rất lâu. Tuy nhiên để có thể áp dụng một cách hiệu quả, lựa chọn được cảm biến có độ ổn định và chính xác cao thì đối với các bạn học viên, sinh viên có thể còn gặp nhiều khó khăn.

## Nguyên lý hoạt động của quang trở và ứng dụng trong dò đường robot

Quang trở là 1 cảm biến thay đổi giá trị điện trở theo cường độ ánh sáng chiếu vào nó. Cường độ ánh sáng càng mạnh thì điện trở của quang trở càng nhỏ và ngược lại.

Ánh sáng chiếu vào các màu sắc khác nhau sẽ bị hấp thụ 1 phần khác nhau, còn lại là chúng phản xạ trở lại dẫn đến cường độ ánh sáng phản xạ trở lại là khác nhau. Các robot dò đường thường có những đường "line" để đi theo. Và màu sắc của các đường "line" sẽ khác biệt với màu nền. Giả sử trong các sân chơi robot, màu "line" sẽ là màu trắng, màu nền sân là màu xanh lá. Nếu dùng 1 đèn led chiếu vào "line" và màu nền sân, để cảm biến quang trở gần đó thu lại ánh sáng phản xạ từ "line" và nền sân, ta sẽ thấy giá trị điện trở của quang trở sẽ có sự khác biệt, chính là bởi vì ánh sáng phản xạ của "line" và màu nền sân là khác nhau. Dựa vào nguyên lý như vậy, ta có thể áp dụng quang trở để phân biệt "line" và nền sân.

<div align="center">
    <img src="Image/FBline.png" alt="Schematic">
</div>

<div align="center">
    <p>Mô tả thực tế</p>
</div>

## Từ sự thay đổi về điện trở của quang trở, làm thế nào để vi điều khiển biết được?

Bằng cách mắc mạch theo kiểu cầu phân áp dưới đây, ta cấp cho cầu phân áp điện áp tham chiếu VREF, khi quang trở LDR9 có sự thay đổi về điện trở, điện áp rơi (ADCIN) trên quang trở cũng sẽ thay đổi theo. Đưa giá trị điện áp này vào ngoại vi ADC của vi điều khiển, chúng ta sẽ xác định được giá trị này.

<div align="center">
    <img src="Image/schematic_pcb.png" alt="Schematic_pcb" style="display: inline-block; margin-right: 10px;">
    <img src="Image/adc_conveter.png" alt="adcImage" style="display: inline-block;">
</div>

## Thiết kế dàn cảm biến quang trở và led chiếu sáng

Mỗi một cảm biến quang trở, mình sử dụng 2 đèn led để chiếu sáng. Mục đích là để tăng cường độ ánh sáng chiếu và ánh sáng phản xạ. Bởi nếu ánh sáng chiếu yếu, khi gặp các nguồn sáng mạnh hơn từ môi trường chiếu vào sẽ làm nhiễu cảm biến.

<div align="center">
    <img src="Image/8_led_sch.png" alt="8ledSchematic">
</div>

<div align="center">
    <p>Sơ đồ nguyên lý dàn cảm biến quang trở và led chiếu sáng</p>
</div>

Led và quang trở được bố trí như ở dưới đây, chỉ lưu ý khoảng cách giữa 2 cặp led và quang trở ở giữa nên được thay đổi khi độ rộng đường line thay đổi. Ví dụ độ rộng đường line là 3cm thì 2 cặp led và quang trở ở giữa các bạn nên để khoảng cách khoảng 2.8cm, để 2 cặp led và quang trở này nằm ở giữa vạch khi robot chạy giữa line.

<div align="center">
    <img src="Image/8led_pcb.png" alt="8ledpcb">
</div>

<div align="center">
    <p>Mạch in dàn cảm biến quang trở và led chiếu sáng</p>
</div>

Mạch in mình thiết kế là 2 lớp, các bạn có thể đặt mạch trực tiếp từ [Jlcpcb.com](jlcpcb.com). Các bạn cần có thẻ Visa để thanh toán và đặt hàng.

<div align="center">
    <img src="Image/pcbthucte.jpg" alt="8ledpcbtt">
</div>

<div align="center">
    <p>Mạch thực tế dàn cảm biến quang trở và led chiếu sáng</p>
</div>

Các bạn nên thiết kế thêm phần ngăn cách giữa các led và với bên ngoài môi trường để giảm sự ảnh hưởng bởi ánh sáng môi trường và ánh sáng của led bên cạnh gây nhiễu cảm biến. Mình đã thiết kế phần ngăn cách, in 3d và lắp ráp vào dàn cảm biến như thế này:

<div align="center">
    <img src="Image/solid.PNG" alt="solid">
</div>

<div align="center">
    <img src="Image/pcbb.jpg" alt="pcbb" width="400">
</div>

<div align="center">
    <p>Khối ngăn cách cảm biến</p>
</div>

Mời các bạn xem phần [Thiết kế mô đun xử lý tín hiệu cho dàn cảm biến quang trở và led chiếu sáng](https://github.com/Peter8686/Robot_ADCModule.git) để kết hợp 2 mô đun lại và biết cách sử dụng.

#### Mọi thắc mắc xin liên hệ qua địa chỉ email của tôi: thaohv1639x@gmail.com 
## Thanks for watching!


