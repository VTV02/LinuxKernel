# Viết character device driver cơ bản hiển thị log khi load và unload driver
```cpp
#include<linux/kernel.h>
#include<linux/init.h>
#include<linux/module.h>

MODULE_AUTHOR("VTV02");
MODULE_LICENSE("GPL");

static int __init simple_init(void)
{
        printk(KERN_INFO "HELLO SIMPLE CHARACTER DEVICE DRIVER\n");
        return 0;
}
static void __exit simple_exit(void)
{
        printk(KERN_INFO "GOODBEY CHARDEV\n");
}
module_init(simple_init);
module_exit(simple_exit);
```
- Tiến hành include những header file của kernel cần thiết vào
- Thực hiện ghi tên tác giả và khai báo LICENSE là GPL
- Viết hàm init(hàm này sẽ được chạy dầu tiên khi module được load lên và nó sẽ in ra dòng chữ ).
- Viết hàm để exit(sẽ được chạy khi người dùng unload module)
- Tiến hành đăng ký hàm với kernel bằng cách truyền tên hàm vào
### **Lưu ý: Cần tuân thủ đúng các prototype của kernel từ hàm init đến exit chỉ được tùy chỉnh tên hàm**
![image](https://github.com/user-attachments/assets/b72a4bac-a678-43b5-920f-94ef05bd7a1d)

  
