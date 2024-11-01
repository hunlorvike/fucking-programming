## LINQ - Tổng Quan và Hướng Dẫn Sử Dụng Chi Tiết

### 1. **Giới thiệu về LINQ**

LINQ (Language Integrated Query) là một tính năng mạnh mẽ trong C# cho phép bạn truy vấn và thao tác với dữ liệu một cách dễ dàng và hiệu quả. LINQ giúp việc xử lý dữ liệu trở nên trực quan hơn bằng cách cho phép bạn sử dụng cú pháp tương tự như SQL để truy vấn các nguồn dữ liệu khác nhau, từ mảng đơn giản đến cơ sở dữ liệu phức tạp.

#### 1.1 **Lợi ích của LINQ**

- **Cú pháp rõ ràng**: Cú pháp truy vấn của LINQ tương tự như SQL, giúp dễ hiểu hơn cho lập trình viên.
- **Tính mở rộng**: LINQ có thể làm việc với nhiều loại nguồn dữ liệu khác nhau, bao gồm cơ sở dữ liệu, XML, và các tập hợp dữ liệu trong bộ nhớ.
- **Tính linh hoạt**: LINQ cho phép bạn xây dựng các truy vấn phức tạp với các phép toán như lọc, sắp xếp và nhóm dữ liệu.

### 2. **Các loại LINQ**

LINQ có thể được phân loại thành các loại chính sau đây:

#### 2.1 **LINQ to Objects**

- **Định nghĩa**: LINQ to Objects cho phép bạn truy vấn các tập hợp dữ liệu trong bộ nhớ như mảng, danh sách, và các kiểu dữ liệu khác trong .NET.
- **Sử dụng**: Không cần kết nối đến cơ sở dữ liệu, bạn có thể truy vấn trực tiếp trên các tập hợp dữ liệu.

#### 2.2 **LINQ to SQL**

- **Định nghĩa**: LINQ to SQL cho phép bạn truy vấn cơ sở dữ liệu SQL Server bằng cách sử dụng các đối tượng C#.
- **Sử dụng**: Thực hiện truy vấn dữ liệu từ cơ sở dữ liệu và ánh xạ các bảng trong cơ sở dữ liệu thành các lớp trong C#.

#### 2.3 **LINQ to Entities (Entity Framework)**

- **Định nghĩa**: LINQ to Entities là một phần của Entity Framework, cho phép bạn truy vấn dữ liệu từ cơ sở dữ liệu theo cách hướng đối tượng.
- **Sử dụng**: Ánh xạ giữa các đối tượng C# và các bảng trong cơ sở dữ liệu, cho phép thực hiện các truy vấn phức tạp với các đối tượng liên kết.

#### 2.4 **LINQ to XML**

- **Định nghĩa**: LINQ to XML cho phép bạn truy vấn và thao tác với tài liệu XML một cách dễ dàng.
- **Sử dụng**: Thực hiện truy vấn, xây dựng, đọc, sửa đổi và lưu tài liệu XML.

#### 2.5 **LINQ to DataSet**

- **Định nghĩa**: LINQ to DataSet cho phép bạn truy vấn các đối tượng `DataSet` trong ADO.NET.
- **Sử dụng**: Dễ dàng xử lý dữ liệu trong bộ nhớ thông qua các bảng trong `DataSet`.

### 3. **Cú pháp cơ bản của LINQ**

LINQ có hai cú pháp chính: cú pháp truy vấn (Query Syntax) và cú pháp phương thức (Method Syntax).

#### 3.1 **Cú pháp truy vấn (Query Syntax)**

Cú pháp này tương tự như SQL và giúp lập trình viên dễ hiểu hơn.

**Ví dụ**:

```csharp
var query = from item in items
            where item.Price > 100
            select item;
```

#### 3.2 **Cú pháp phương thức (Method Syntax)**

Cú pháp này sử dụng các phương thức mở rộng và có thể linh hoạt hơn trong nhiều tình huống.

**Ví dụ**:

```csharp
var query = items.Where(item => item.Price > 100);
```

### 4. **Các phép toán trong LINQ**

LINQ cung cấp nhiều phép toán để truy vấn và thao tác với dữ liệu. Dưới đây là một số phép toán cơ bản cùng với mô tả chi tiết và ví dụ minh họa.

#### 4.1 **Where**

- **Mô tả**: Phép toán `Where` cho phép bạn lọc các phần tử trong một tập hợp dựa trên điều kiện cho trước.
- **Cú pháp**:
  ```csharp
  var result = collection.Where(item => condition);
  ```
- **Ví dụ**:
  ```csharp
  var evenNumbers = numbers.Where(n => n % 2 == 0);
  // Kết quả: [2, 4, 6, 8, 10]
  ```

#### 4.2 **Select**

- **Mô tả**: Phép toán `Select` cho phép bạn chọn một tập con thuộc tính từ các đối tượng trong tập hợp.
- **Cú pháp**:
  ```csharp
  var result = collection.Select(item => selectedProperty);
  ```
- **Ví dụ**:
  ```csharp
  var productNames = products.Select(p => p.Name);
  // Kết quả: ["Product 1", "Product 2", "Product 3"]
  ```

#### 4.3 **OrderBy**

- **Mô tả**: Phép toán `OrderBy` cho phép bạn sắp xếp các phần tử trong một tập hợp theo một hoặc nhiều thuộc tính.
- **Cú pháp**:
  ```csharp
  var result = collection.OrderBy(item => property);
  ```
- **Ví dụ**:
  ```csharp
  var sortedProducts = products.OrderBy(p => p.Price);
  // Kết quả: Danh sách sản phẩm được sắp xếp theo giá tăng dần
  ```

#### 4.4 **GroupBy**

- **Mô tả**: Phép toán `GroupBy` cho phép bạn nhóm các phần tử trong một tập hợp dựa trên một thuộc tính.
- **Cú pháp**:
  ```csharp
  var result = collection.GroupBy(item => property);
  ```
- **Ví dụ**:
  ```csharp
  var groupedByCategory = products.GroupBy(p => p.Category);
  // Kết quả: Các nhóm sản phẩm theo danh mục
  ```

#### 4.5 **Join**

- **Mô tả**: Phép toán `Join` cho phép bạn kết hợp hai tập dữ liệu dựa trên một khóa chung.
- **Cú pháp**:
  ```csharp
  var result = collection1.Join(collection2,
                                 outerKeySelector,
                                 innerKeySelector,
                                 resultSelector);
  ```
- **Ví dụ**:
  ```csharp
  var productOrders = products.Join(orders,
                                     p => p.ProductId,
                                     o => o.ProductId,
                                     (p, o) => new { p.Name, o.Quantity });
  // Kết quả: Danh sách tên sản phẩm cùng với số lượng đã đặt
  ```

#### 4.6 **Distinct**

- **Mô tả**: Phép toán `Distinct` cho phép bạn lấy các phần tử duy nhất từ một tập hợp, loại bỏ các phần tử trùng lặp.
- **Cú pháp**:
  ```csharp
  var result = collection.Distinct();
  ```
- **Ví dụ**:
  ```csharp
  var uniqueNumbers = numbers.Distinct();
  // Kết quả: Danh sách số duy nhất trong tập hợp
  ```

#### 4.7 **Count**

- **Mô tả**: Phép toán `Count` cho phép bạn đếm số phần tử trong một tập hợp.
- **Cú pháp**:
  ```csharp
  var count = collection.Count();
  var countWithCondition = collection.Count(item => condition);
  ```
- **Ví dụ**:
  ```csharp
  var totalProducts = products.Count();
  var expensiveProductsCount = products.Count(p => p.Price > 100);
  // Kết quả: Tổng số sản phẩm và số sản phẩm có giá lớn hơn 100
  ```

#### 4.8 **Sum**

- **Mô tả**: Phép toán `Sum` cho phép bạn tính tổng giá trị của một thuộc tính trong một tập hợp.
- **Cú pháp**:
  ```csharp
  var totalSum = collection.Sum(item => item.Property);
  ```
- **Ví dụ**:
  ```csharp
  var totalPrice = products.Sum(p => p.Price);
  // Kết quả: Tổng giá của tất cả sản phẩm
  ```

### 5. **IQueryable vs IEnumerable**

#### 5.1 **IEnumerable**

- **Mô tả**: `IEnumerable` đại diện cho tập hợp có thể lặp qua trong bộ nhớ, thường sử dụng cho các tập hợp trong bộ nhớ như mảng hoặc danh sách.
- **Tính năng**:
  - Không hỗ trợ ánh xạ biểu thức; tất cả truy vấn thực hiện trong bộ nhớ.
  - Phù hợp khi dữ liệu đã được tải vào bộ nhớ và cần thao tác.
  - Thực hiện truy vấn ở mức client; tất cả dữ liệu phải được tải vào bộ nhớ.
  - Chậm hơn với tập hợp lớn do phải tải toàn bộ dữ liệu trước.

**Ví dụ**:

```csharp
IEnumerable<Product> enumerableProducts = context.Products.ToList();
var expensiveProducts = enumerableProducts.Where(p => p.Price > 100);
```

#### 5.2 **IQueryable**

- **Mô tả**: `IQueryable` kế thừa từ `IEnumerable` và đại diện cho tập hợp có thể truy vấn. Nó cho phép thực hiện các truy vấn phức tạp trên dữ liệu ngoài bộ nhớ, như cơ sở dữ liệu.
- **Tính năng**:
  - Hỗ trợ ánh xạ biểu thức, chuyển đổi thành câu lệnh SQL.
  - Tối ưu hóa hiệu suất truy vấn bằng cách chuyển điều kiện về phía nguồn dữ liệu.
  - Thực hiện truy vấn trên server, chỉ tải dữ liệu cần thiết từ cơ sở dữ liệu.
  - Nhanh hơn với cơ sở dữ liệu vì chỉ truy xuất dữ liệu cần thiết.

**Ví dụ**:

```csharp
IQueryable<Product> queryableProducts = context.Products.AsQueryable();
var expensiveProducts = queryableProducts.Where(p => p.Price > 100);
```

#### 5.3 **So sánh giữa IQueryable và IEnumerable**

| Tính năng              | IQueryable                                                        | IEnumerable                                |
| ---------------------- | ----------------------------------------------------------------- | ------------------------------------------ |
| **Nguồn dữ liệu**      | Dữ liệu từ nhiều nguồn khác nhau (cơ sở dữ liệu, dịch vụ web,...) | Dữ liệu trong bộ nhớ (mảng, danh sách,...) |
| **Xử lý truy vấn**     | Xử lý truy vấn tại nguồn dữ liệu                                  | Xử lý truy vấn trong bộ nhớ                |
| **Biểu thức truy vấn** | Hỗ trợ ánh xạ biểu thức (expression tree)                         | Không hỗ trợ ánh xạ biểu thức              |
| **Hiệu suất**          | Tối ưu hơn với truy vấn phức tạp                                  | Có thể kém hơn với tập dữ liệu lớn         |
| **Cú pháp**            | Cú pháp linh hoạt với LINQ                                        | Cú pháp đơn giản với LINQ                  |

### 6. **Kết luận**

LINQ là một công cụ mạnh mẽ giúp lập trình viên C# thao tác với dữ liệu một cách hiệu quả và dễ dàng. Bằng cách sử dụng LINQ, bạn có thể thực hiện các truy vấn phức tạp trên nhiều nguồn dữ liệu khác nhau, đồng thời cải thiện độ rõ ràng và tính bảo trì của mã nguồn.
