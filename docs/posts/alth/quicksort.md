---
title: Quicksort
nav_tile: Quicksort
draft: true 
date: 2024-05-04
categories:
  - sort
---
# Quicksort: Khi "Chia để trị" trở thành nghệ thuật sắp xếp

Quicksort, nghe có vẻ "nhanh" như chính cái tên của nó, là một trong những thuật toán sắp xếp được ưa chuộng nhất trong giới lập trình. Sở dĩ được yêu thích như vậy là bởi quicksort không chỉ đơn giản mà còn sở hữu hiệu năng cao, giúp giải quyết bài toán sắp xếp một cách nhanh chóng và hiệu quả.

Vũ khí bí mật của quicksort nằm ở chiến lược "chia để trị". Thay vì cố gắng sắp xếp toàn bộ mảng cùng một lúc, quicksort chia nhỏ mảng thành các phần nhỏ hơn, dễ quản lý hơn. Sau đó, nó lần lượt sắp xếp từng phần nhỏ và cuối cùng ghép chúng lại để tạo ra một mảng hoàn chỉnh đã được sắp xếp gọn gàng.

Vậy quicksort hoạt động như thế nào? Hãy tưởng tượng bạn đang dọn dẹp một căn phòng bừa bộn. Thay vì dọn tất cả mọi thứ cùng lúc, bạn sẽ chia phòng thành các khu vực nhỏ hơn, chẳng hạn như khu vực giường ngủ, khu vực bàn làm việc, v.v. Sau đó, bạn dọn dẹp từng khu vực một cách cẩn thận và cuối cùng, cả căn phòng sẽ trở nên ngăn nắp. Quicksort cũng hoạt động tương tự như vậy!

## Hoạt động 

**Thuật toán này hoạt động theo các bước sau**:

1. **Chọn "người chỉ huy" (pivot)**: Lựa chọn một phần tử bất kỳ trong mảng để làm phần tử chốt. Phần tử này sẽ đóng vai trò như "người chỉ huy", giúp phân chia mảng thành hai phần.

2. **Phân chia đội hình (partition)**: Sắp xếp lại mảng sao cho tất cả các phần tử "yếu hơn" người chỉ huy (có giá trị nhỏ hơn) đứng bên trái, còn các phần tử "mạnh hơn" (có giá trị lớn hơn) đứng bên phải. Sau khi phân chia, vị trí của "người chỉ huy" chính là vị trí cuối cùng của nó trong mảng đã được sắp xếp.
3. **Huấn luyện từng đội (đệ quy)**: Tiếp tục áp dụng quicksort cho hai đội hình nhỏ hơn (hai mảng con) được tạo ra từ bước phân chia. Quá trình này sẽ được lặp lại cho đến khi từng phần tử trong mảng đều đứng đúng vị trí của mình.
4. **Hợp nhất đội quân**: Cuối cùng, khi tất cả các đội hình nhỏ đều đã được sắp xếp, chúng ta chỉ cần ghép chúng lại để tạo thành một đội quân hùng mạnh, đã được sắp xếp hoàn hảo!

> Quicksort sở hữu hiệu năng đáng nể trong trường hợp trung bình, tương đương với mergesort. Tuy nhiên, cũng như mọi vị tướng tài, quicksort cũng có điểm yếu. Nếu "người chỉ huy" luôn là người yếu nhất hoặc mạnh nhất, hiệu năng của thuật toán sẽ giảm sút. Để khắc phục điều này, chúng ta có thể lựa chọn "người chỉ huy" một cách ngẫu nhiên hoặc sử dụng phương pháp median-of-three.

## Ưu điểm của quicksort:

- **Hiệu suất cao**: Như đã nói, quicksort là một thuật toán "nhanh" trong trường hợp trung bình.
- **Đơn giản**: Việc triển khai quicksort khá dễ dàng, ngay cả với những người mới bắt đầu.
- **Tiết kiệm không gian**: Quicksort sắp xếp tại chỗ, không cần sử dụng nhiều bộ nhớ phụ trợ.

## Nhược điểm của quicksort:

- **Trường hợp xấu nhất**: Hiệu năng có thể giảm sút nếu chọn "người chỉ huy" không phù hợp.
- **Không ổn định**: Quicksort có thể thay đổi thứ tự tương đối của các phần tử có cùng giá trị, điều này có thể không mong muốn trong một số ứng dụng.

Quicksort được ứng dụng rộng rãi trong nhiều lĩnh vực, từ hệ thống cơ sở dữ liệu, thuật toán đồ họa đến xử lý hình ảnh và các ứng dụng thương mại.

> Tóm lại, quicksort là một thuật toán sắp xếp hiệu quả và linh hoạt, xứng đáng được coi là một "nghệ thuật sắp xếp" trong khoa học máy tính.

## Ví dụ code Quicksort sử dụng .NET Core

Dưới đây là ví dụ code triển khai thuật toán Quicksort trong C# sử dụng .NET Core:

```cs
public class QuickSort
{
    public static void Sort<T>(T[] arr, int low, int high) where T : IComparable<T>
    {
        if (low < high)
        {
            int pivotIndex = Partition(arr, low, high);

            // Sắp xếp đệ quy hai mảng con
            Sort(arr, low, pivotIndex - 1);
            Sort(arr, pivotIndex + 1, high);
        }
    }

    private static int Partition<T>(T[] arr, int low, int high) where T : IComparable<T>
    {
        T pivot = arr[high];
        int i = (low - 1);

        for (int j = low; j < high; j++)
        {
            if (arr[j].CompareTo(pivot) <= 0)
            {
                i++;
                Swap(arr, i, j);
            }
        }

        Swap(arr, i + 1, high);
        return i + 1;
    }

    private static void Swap<T>(T[] arr, int i, int j)
    {
        T temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
```

Cách sử dụng:

```cs
// Mảng cần sắp xếp
int[] arr = { 10, 7, 8, 9, 1, 5 };

// Sắp xếp mảng sử dụng Quicksort
QuickSort.Sort(arr, 0, arr.Length - 1);

// In mảng đã sắp xếp
Console.WriteLine(string.Join(", ", arr));
```

**Giải thích**:
Code sử dụng generic type T để cho phép sắp xếp các loại dữ liệu khác nhau, miễn là chúng triển khai interface IComparable<T>.
Phương thức Sort thực hiện sắp xếp đệ quy mảng con dựa trên vị trí của phần tử chốt sau khi phân vùng.
Phương thức Partition thực hiện phân vùng mảng, đưa phần tử chốt vào vị trí đúng và đảm bảo các phần tử nhỏ hơn nằm bên trái, phần tử lớn hơn nằm bên phải.
Phương thức Swap đơn giản là trao đổi vị trí của hai phần tử trong mảng.
Lưu ý:
Ví dụ code này sử dụng phương pháp chọn phần tử chốt là phần tử cuối cùng của mảng. Bạn có thể thay đổi cách chọn phần tử chốt để cải thiện hiệu năng hoặc phù hợp với yêu cầu cụ thể.
Bạn có thể thêm các kỹ thuật cải tiến như cutoff to insertion sort, median-of-three partitioning để tối ưu hóa hiệu năng của quicksort.