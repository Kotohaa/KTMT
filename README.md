


> [!NOTE] Tổng quan
> Trường đại học thường sd do nó dễ, phù hợp với lại lập trình nhúng.
> HIểu rõ CPU hoạt động ntn là điều quan trọng nhất !
> 
> Kỹ thuật lập trình nên biết. Khi ta chạy 1 phần mềm thì có thể gọi tới và chạy 1 file .exe khác. 
> 
> CÓ thể nén code và mở khóa code = 7z. 



> [!WARNING] Thi
> - Có đặt tính rồi tự tính các kiểu số theo kiểu gì đó (float, IEEE bao nhiêu đó)
> - Hỏi kiến thức về những cái bth như là ISA là gì ? Kiến trúc máy tính là làm gì (Lý thuyết cần hiểu)
> - Đoc code assembly.( mã giả c/c++ tương ứng, input, output là gì? )
>   
>   
>   Độ khó cuối kỳ nó cao hơn.  ( chỉ binary -> Ra mã assembly )
>   
>   
>   2 câu cuối khó nhất. 3 điểm !  ( 1 cái tính toán và 1cái đọc code)
>   
>   **Cố gắng mỗi câu 1 p để nấu tự luận !**
> 
> 
>   Đề giữa kỳ
> - 20 trắc nghiệm. 
>   
>   Viết mã hex ra, đừng viết hết binary ra !
>   
>   KHi nào biết số khoảng đề đảo little endian ? Đề cho. 4,8,... Byte little endian. Nếu đề không nói gì cả thì ta phải GHI 2 TH ! NGHĨA LÀ LITTLE ENDIAN GHI GÌ, BIG ENDIAN GHI GÌ !
>   
>   Nếu có dấu thì xét bit đầu. Nếu 0 thì không quan tâm. CỨ ghi ra. 
>   Nếu là 1 thì phải reverse ( bù 1) . -1 rồi đảo bit ! 

Cache tính theo đơn vị KB. Ram thì to. Rom thì có bộ nhở

Cache -> Register -> Ram -> Rom -> Port -> Disk 

ALU đơn vị luận lý logic ( Arightmetic Logic Unit ). Không load lệnh nhưng sd để tính toán !

Pipeline 
[Pipeline](https://www.google.com/search?q=Pipeline&oq=c%C6%A1+ch%E1%BA%BF+pipeline+trong+cpu+ki%E1%BA%BFn+tr%C3%BAc+m%C3%A1y+t%C3%ADnh+l%C3%A0+g%C3%AC+%3F&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIGCAEQLhhA0gEJMTQxMDBqMGoxqAIAsAIA&sourceid=chrome&ie=UTF-8&mstk=AUtExfDvP_7RLsoWxI68-IW0CqVY9rd7Mlrd3cPiAMYosRiLYKEynkuCfJBF5y7YodOtqsZkV2z6ezLtbNntas9-MbYkJt7N9OoL3kTXJztmdIFWtNppvwJxSx5z8-mIAbxR9__KPArW95T7JkU1Gb6OfCqumOmZGn2UQwMU2myT4e9Cp968Y0uLK47vFMtMkiaoBNo-wV4OjM4OzmqiSJYS-STST0sc5tAEIrON1rMqyC7Qi4GhQ4pHZHXRtK7iZEy51yLpM9LR4svf9iUjHcXP4GKn&csui=3&ved=2ahUKEwi4z4f6lM6TAxWana8BHdZlHrkQgK4QegQIARAB) (đường ống) trong CPU ==là kỹ thuật tối ưu hóa hiệu suất bằng cách chia quy trình thực hiện lệnh thành các giai đoạn nhỏ (nạp, giải mã, thực thi, ghi kết quả) và xử lý nhiều lệnh gối đầu nhau song song==. Điều này cho phép CPU thực hiện nhiều lệnh cùng lúc thay vì chờ từng lệnh hoàn tất, giúp tăng tốc độ xử lý tổng thể của máy tín

System V ABI là chuẩn truyền tham số. 
Trong x86_64 System V ABI (thường dùng trên Linux/macOS), tham số thứ 1 (tham số đầu tiên) của một hàm được truyền qua thanh ghi **`%rdi`**.

Chi tiết các thanh ghi truyền tham số (theo thứ tự):

1. **Tham số 1: `%rdi`**
2. Tham số 2: `%rsi`
3. Tham số 3: `%rdx`
4. Tham số 4: `%rcx`
5. Tham số 5: `%r8`
6. Tham số 6: `%r9`

WIndows x64: RCX RDX R8 R9 nhiều hơn thì stack
windows x86: Sd stack 
## Tong quan về MIPS
- là kiến trúc thuộc loại RISC ( reduced Instruction Set Computer )
- Tập lệnh ít, đơn giản và thực hiện rất nhanh
- Mỗi lệnh thường dài 32 bit. 
### THanh ghi và biến
```asm

$zero
$v0-1 ( value trả về )
$a0-3 ( arguments )
$t0-9 ( biến lưu tạm )
$s0-7 ( biến lưu lâu )
$sp ( stack pointer )
$ra ( return address )

``` 

### Các loại lệnh chính
#### Số học 
có 3 tham số. Ngầm định rõ ràng luôn. Thằng nào với thằng nào và lưu vào thằng nào. 
```
add $t0, $t1, $t2 # t0 = t1 + t2
sub $t0, $t1, $tr2 # t0 = t1 - t2 
```

#### Lệnh load/store
MIPS không thao tác trực tiếp trên RAM -> PHải load qua register
```asm
lw $t0, 0($t1) # load word. COn số 0 trước dấu ngoặc là offset và nó phải là bội của 4 vì32 bit 


``` 

#### Lệnh rẽ nhánh
```asm
beq $t0, $t1, label ( branch if equa)
bne $t0, $t1, label (branch if not equal )
```

#### Lệnh nhảy 
```asm
j label # nhảy vào một label
jal func # gọi một hàm 
jr # giống return trong x86_64. DÙng để trả về và nhảy về 1 hàm
``` 

#### Syscall 

```asm
li $v0, 1 #service: print int
li $a0, 10 # load arguments
syscall  # gọi hàm syscall

```

Với MIPs thì không cần biết ngắt và hàm gì . Vì m
THoát chương trình. 
```asm
``` 


#### Một vài bảng hàm thông dụng
- Gọi Hàm = cách thêm `syscall`

- 1 là in số nguyên tại $a0
- 2,3 là in số thực f và double tại %f12 
- 10 thoát chương trình
- 17 thoát có mã trả về
- 5 vào `$v0` hàm nhập, giá trị sẽ nằm trong `$v0` 


Trong source code, gọi 1 file exe để chạy. 

#### Tạo biến
```asm
.data
<Tên biến>: .asciiz "nội dung "
```

#### Nhóm lệnh bitwise
```asm
and $d, $s, %t # luôn luôn gán vào thằng đầu. Lấy hai thằng sau tính. 
or $d, $s, %t
xor $d, $s, %t
nor $d, $s, %t
s
```

#### Nhóm lệnh so sánh
```asm
slt $d, $s, $t     ( less than. Nếu đúng thì gán d = 1. Nếu )
slti $t, $s, imm   ( less than nhưng dùng cho giá rị số thay vì thanh ghi)
```
