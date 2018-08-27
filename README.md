# Functional-programing

[Source](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0 "Permalink to Master the JavaScript Interview: What is Functional Programming?")

# Master the JavaScript Interview Lập trình hướng chức năng là gì?


![][1]

Cấu trúc Synth—Orihaus (CC BY 2.0)

> "Master the JavaScript Interview" là 1 series các bài viết được thiết kế để chuẩn bị ứng viên cho những câu hỏi phổ biến mà họ rất dễ gặp khi ứng tuyển cho các vị trí Javascript từ level mid đến senior. Đây đều là những câu hỏi tôi thường sử dụng trong phỏng vấn thực tế.

Lập trình hướng chức năng đã trở thành 1 chủ đề cực kỳ hot trong giới JavaScript.  Chỉ vài năm trước đây, chỉ 1 số ít lập trình viên JavaScript đã biết lập trình hướng chức năng là gì, nhưng tất cả các codebase của các ứng dụng lớn tôi thấy trong 3 năm gần đây  sử dụng rất nhiều tư tưởng của  lập trình hướng chức năng.

**Functional programming** (thường được viết tắt là FP)  là 1 quá trình xây dựng phần mềm bằng cách tạo ra các  **pure functions**, tránh việc **shared state,** **mutable data, ** và **side-effects**. Lập trình hướng chức năng **declarative** hơn là **imperative**, và các trạng thái của ứng dụng sẽ đi theo các pure function.  Các contrast với lập trình hướng đối tượng, các trạng thái của ứng dụng thường được chia sẻ và  được đặt chung với các phương thức trong đối tượng.

Lập trình hướng chức năng là  1 mô hình   lập trình, có nghĩa là đây là 1 cách suy nghĩ về việc xây dựng phần mềm dựa trên 1 vài  nguyên tắc được định nghĩa cơ bản ( được liệt kê bên dưới_. Những ví dụ khác về các mô hình lập trình bao gồm lập trình  hướng đối tượng và lập trình  hướng thủ tục.

Lập trình hướng chức năng có xu hướng ngắn gọn hơn,  dễ đoán hơn, và dễ dàng kiểm thử hơn lập trình imperative hay hướng đổi tượng -  nhưng nếu bạn không quen với nó  cũng như các cấu trúc phổ thông liên quan với nó, lập trình hướng chức năng có thể  dày hơn, và nội dung sẽ bị khó đọc với những người mới.

Nếu bạn bắt đầu tra google  cụm từ lập trình hướng chức năng, bạn sẽ  nhanh  chóng gặp những trở ngại  trong việc tìm kiếm các lý thuyết liên quan , thứ có thể trở nên cực kỳ đáng sợ cho người mới bắt đầu.  Sẽ là nói dối nếu bảo có cách nhanh chóng để học chúng. Nếu bạn đã lập trình Javascript 1 thời gian, bạn sẽ có thuận lợi khi có thể sử dụng nhiều khái niệm và tiện ích lập trình hướng chức năng trong phần mềm thực tế.

> Đừng để những từ ngữ mới  làm bạn sợ . Nó dễ hơn bạn nghĩ nhiều.

Phần khó nhất là  để hiểu được những từ vựng lạ lẫm. Có rất nhiều ý tưởng   trong những định nghĩa vu vơ bên trên mà bạn cần phải hiểu rõ trước khi bạn bắt đầu  hiểu được ý nghĩa của lập trình hướng chức năng:

* Pure functions
* Function composition
* Avoid shared state
* Avoid mutating state
* Avoid side effects

Nói 1 cách khác, nếu bạn muốn biết ý nghĩa của lập trình chức năng trong thực tế, bạn phải bắt đầu với việc tìm hiểu những khái niệm căn bản sau:

1 **pure function** là 1 hàm mà:
* Cùng 1 đầu vào, luôn luôn cho cùng 1 đầu ra.
* Không bị ảnh hưởng bên ngoài.


Các pure function có nhiều tính chất quan trọng trong lập trình hướng chức năng, bào gồm **referential transparency** ( bạn có thể thay thế 1 lời gọi hàm với kết quả trả về của nó mà không phải thay đổi ý nghĩa của chương trinh). Đọc ["Pure Function là gì?"][2] để rõ hơn.

**Function composition ** là 1 quá trình gộp 2 hay nhiều hàm để tạo ra 1 hàm mới  hay  thực hiện 1 vài tính toán. Ví dụ gộp hàm `f .g ` (dấu chấm có nghĩa là  "hợp với") tương đương với `f(g(x))` trong Javascript. Hiểu về function composition là 1 bước quan trọng để hiểu cách xây dựng phần mềm sử dụng lập trình hướng chức năng. Đọc  ["Function Composition là gì?"][3] để rõ hơn.

### Shared State

**Shared state** là bất cứ biến, đối tượng, hay vùng bộ nhớ nào tồn tại trong 1 scope được chia sẻ, hay là 1 thuộc tính của 1 đối tượng được truyền trong 1 scope. 1 scope được chia sẽ bao gồm scope global hay 1 scope closure. Thông thường trong lập trình hướng đối tượng, các đối tượng được chia sẻ trong scope bằng cách thêm các thuộc tính vào các đối tượng khác.


Ví dụ, 1 trò chơi máy tính có thể có 1 đối tượng game chính, với các nhân vật và các item trò chơi được lưu thành các thuộc tính trong đối tượng đó. Lập trình hướng chức năng hạn chế việc shared state - thay vì  dựa vào  các  cấu trúc dữ liệu không thay đổi và các phép tính thuần để lấy được các dữ liệu mới  từ các dữ liệu sẵn có.  Chí tiết hơn về cách mà phần mềm hướng chức năng có thể xử lý các trạng thái của ứng dụng, xem cuốn ["10 Tips for Better Redux Architecture"][4].

Vấn đề với shared state là để hiểu về hiệu quả của 1 hàm , bạn phải biết toàn bộ lịch sử của mỗi biến được chia sẻ mà hàm sử dụng hay tác động đến.

Hãy tưởng tượng rằng bạn có 1 đối tượng người dùng cần được lưu. hàm `saveUser()` của bạn tạo 1 request đến 1 API trên server. Trong khi điều này xảy ra, người dùng lại thay đổi ảnh đại diện với hàm `updateAvatar()` và gọi 1 request `saveUser()` khác. Khi được lưu, server trả về  1 đối tượng người dùng  được chấp nhận mà nên thay thế bất cứ thứ gì trong bộ nhớ để có thể đồng bộ với những thay đổi xảy ra trên server hay trong response đến 1 lời gọi API khác.

Thật không may, reponse thứ 2 lại được nhận trước response thứ nhất, vì vậy khi cái thứ nhất (giờ đã bị lỗi thời) được trả về, ảnh đại diện mới được lưu trong bộ nhớ và thay thế cho cacsi cũ. Đây là 1 ví dụ 1 của trường hợp  - lỗi rất phổ biến liên quan đến share state.

1 vấn đề phổ thông khác liên quan đến shared state là thay đổi thứ tự mà các hàm được gọi có thể dẫn tới việc những thất bại liên tục vì các hàm thực hiện trên shared state phụ thuộc vào thời gian:

Ví dụ phụ thuộc thời gian

Khi bạn tránh việc shared state, thời gian và thứ tự của các hàm gọi không thay đổi kết quả của việc gọi hàm. Với những hàm pure, cùng 1 đầu vào, bạn luốn có được cùng đầu ra. Điều này làm các lời gọi hạm hoàn toàn độc lập với các gọi hàm khác, hoàn toàn đơn giản hóa việc thay đổi  và tái cấu trúc. 1 thay đổi trên 1 hàm, hay thời gian hàm gọi không ảnh hưởng và phá vỡ các phần khác của chương trình.

Trong ví dụ bên trên, chúng tôi sử dụng `Object.assign()` và truyền nó trong 1 đối tượng rỗng như 1 tham số đầu tiên để sao chếp các thuộc tính của `x` thay vì  biến đổi nó bên trong. Trong trường hợp này, nó tương đương với việc tạo 1 đối tượng với từ  scratch, và không cần có `Object.assign()`, những đây là 1 ví dụ phổ biến trong Javascript để tạo 1 bản sao của trạng thái đang tồn tại thay vì sử dụng các chuyển đổi, mà chúng tôi đã mô tả trong ví dụ đầu tiên.

Nếu bạn để ý kĩ hơn trong `console.log()` trong ví dụ này, bạn sẽ nhận thấy 1 vài thứ đã được đề cập : function composition. Nhắc lại 1 chút, function composition giống như kiểu `f(g(x))`. Trong trường hợp này, húng ta thay `f()` và `g()` với `x1()` và `x2()` để cho phép gộp `x1.x2`

Tất nhiên, nếu bạn thay đổi thứ tự của phép gộp, đầu ra cũng sẽ thay đổi. Thứ tự của việc thực hiện  sẽ ảnh hưởng. `f(g(x))` không luôn băng `g(f(x)), nhưng những gì không ảnh hưởng nữa là những thứ xảy ra với các biến bên ngoài hàm - và đây là 1 canh bạc lớn. Với các hàm impure, không thể hoàn toàn hiểu được 1 hàm làm gì trừ khi bạn biết toàn bộ lịch sử của mỗi biến hàm sử dụng hoặc ảnh hưởng,

Loại bỏ các lời gọi hàm ảnh hưởng bởi thời gian, và loại trừ toàn bộ các lớp của  các lỗi tiềm năng.

### Sự bất biến

1 đối tượng **immutable** là 1 đối tượng mà không thể bị chỉnh sửa sau khi nó được tạo ra. Ngược lại 1 đối tượng  **mutable**  là bất kì đối tượng nào mà có thể chỉnh sửa sau khi được tạo ra.

Sự bát biến là 1 khái niệm trọng tâm của lập trình hướng chức năng vì nếu không có điều này, data flow trong chương trình của bạn  sẽ bị mất mát. Lịch sử trạng thái là điều cấm kị, và các lỗi lạ lẫm có thể  xuất hiện trọng phần mềm của bạn. Để hiểu hơn về ý nghĩa của sự bất biến, xem   ["The Dao of Immutability."][5].

Trong Javascript, điều quan trọng là không được nhầm lẫn về `conse`, với sự bất biến. `const` tạo 1 liên kết tên biến mà không thể bị gán lại sau khi tạo. `const` không tạo ra các đối tượng bất biến. Bạn không thể thay đổi đối tượng được liên kết trỏ tới, nhưng bạn vẫn có thể thay đổi thuộc tính của đối tượng, có nghia là các liên kết được tạo với `const` có thể thay đổi, chứ không phải bất biến.

Các đối tượng bất biến hoàn toàn không thể bị thay đổi. Bạn có thể tạo 1 giá trị hoàn toàn bất biến bằng cách deep freezing đối tượng. Javascript có 1 phương thức  có thể đóng băng đối tượng 1  mức:

Nhưng việc đóng băng đối tượng  chỉ là sự bất biến thô sơ mà thôi. Ví dụ, đối tượng sau là không bất biến:

Như bạn có thể thấy, các thuộc tính nguyên thủy cấp cao nhất của một đối tượng được đóng băng không thể thay đổi, nhưng bất kỳ thuộc tính nào cũng là một đối tượng (bao gồm mảng, vv…) vẫn có thể bị thay đổi - vì vậy ngay cả đối tượng bị đóng băng cũng không thay đổi trừ khi bạn duyệt qua toàn bộ cây đối tượng và đóng băng mọi thuộc tính đối tượng.

Trong nhiều ngôn ngữ lập trình chức năng, có cấu trúc dữ liệu bất biến đặc biệt gọi là cấu trúc dữ liệu trie (được phát âm là “cây”) được đóng băng một cách hiệu quả — là khi không có thuộc tính nào có thể thay đổi, bất kể mức độ của thuộc tính trong hệ thống phân cấp đối tượng.

Các trie sử dụng chia sẻ cấu trúc để chia sẻ các vị trí bộ nhớ tham chiếu cho tất cả các phần của đối tượng không thay đổi sau khi một đối tượng được sao chép bởi một toán tử, sử dụng ít bộ nhớ hơn và cho phép cải thiện hiệu suất đáng kể cho một số loại hoạt động.

Ví dụ, bạn có thể sử dụng so sánh định danh tại gốc của cây đối tượng để so sánh. Nếu định danh giống nhau, bạn không phải duyệt qua cả cây để kiểm tra sự khác biệt.

Có một số thư viện trong JavaScript tận dụng các trie, bao gồm Immutable.js và Mori.

Tôi đã thử nghiệm với cả hai, và có xu hướng sử dụng Immutable.js trong các dự án lớn đòi hỏi một lượng đáng kể trạng thái bất biến. Để biết thêm về điều đó, hãy xem ["10 Tips for Better Redux Architecture"][4].



### Các ảnh hưởng phụ

Một ảnh hưởng phụ là bất kỳ thay đổi trạng thái của ứng dụng nào mà có thể quan sát được bên ngoài hàm được gọi, ngoài giá trị trả về của nó. Các ảnh hưởng phụ bao gồm:

* Sửa đổi bất kỳ biến bên ngoài hoặc thuộc tính đối tượng nào (ví dụ: biến toàn cầu hoặc biến trong chuỗi phạm vi hàm chính)
* Ghi ra console
* Viết ra màn hình
* Viết ra 1 file
* Viết vào mạng
* Gọi 1 tiến trình bên ngoài
* Gọi các hàm khác với các ảnh hưởng phụ


Ảnh hưởng phụ là thứ nên tránh nhất trong lập trình chức năng, làm cho hiệu quả của một chương trình dễ hiểu hơn nhiều, và dễ dàng kiểm tra hơn nhiều.

Haskell và các ngôn ngữ chức năng khác thường xuyên cô lập và đóng gói các tác dụng phụ từ các hàm thuần túy bằng cách sử dụng monads. Chủ đề của các monads đủ sâu để viết một cuốn sách, vì vậy chúng tôi sẽ lưu lại cuốn sách đó sau này.

Những gì bạn cần biết ngay bây giờ là các tác vụ phụ cần phải được cô lập với phần còn lại của phần mềm của bạn. Nếu bạn giữ các hiệu ứng phụ tách biệt với phần còn lại của logic chương trình, phần mềm của bạn sẽ dễ dàng hơn để mở rộng, tái cấu trúc, gỡ lỗi, kiểm tra và bảo trì.

Đây là lý do mà hầu hết các framework front-end khuyến khích người dùng quản lý hiển thị trạng thái và thành phần trong các mô-đun riêng lẻ, tách biệt nhau.

### Khả năng tái sử dụng thông qua các chức năng bậc cao


Lập trình chức năng có xu hướng sử dụng lại một tập hợp các tiện ích chức năng phổ biến để xử lý dữ liệu. Lập trình hướng đối tượng có xu hướng sắp xếp phương thức và dữ liệu trong các đối tượng. Những phương pháp sắp xếp chỉ có thể hoạt động trên loại dữ liệu mà chúng được thiết kế để hoạt động và thường chỉ có dữ liệu chứa trong cá thể đối tượng cụ thể đó.

Trong lập trình chức năng, bất kỳ loại dữ liệu nào cũng được đối xử công bằng. Cùng một tiện ích map () có thể ánh xạ đối tượng, chuỗi, số hoặc bất kỳ kiểu dữ liệu nào khác vì nó lấy một hàm làm đối số xử lý thích hợp kiểu dữ liệu đã cho. FP rút ra thủ thuật tiện ích chung của nó bằng cách sử dụng các hàm bậc cao hơn.

JavaScript có **các hàm lớp đầu tiên**, cho phép chúng ta xử lý các hàm như dữ liệu - gán chúng cho các biến, chuyển chúng đến các hàm khác, trả về chúng từ các hàm, v.v ...

**Hàm bậc cao hơn** là bất kỳ hàm nào nhận hàm làm đối số, trả về 1 hàm hoặc cả hai. Các hàm bậc cao thường được sử dụng để:

* Các hành động tóm tắt hoặc cô lập , ảnh hưởng hoặc điều khiển luồng không đồng bộ bằng cách sử dụng chức năng gọi lại, lời hứa, monads, v.v.

* Tạo các tiện ích có thể hoạt động trên nhiều loại dữ liệu khác nhau

* Áp dụng một phần 1 hàm cho các đối số của nó hoặc tạo một hàm được kết hợp với mục đích sử dụng lại hoặc thành phần hàm

* Lấy danh sách các hàm và trả về một số thành phần của các hàm đầu vào đó

#### Containers, Functors, Lists, và Streams

Một functor là cái gì đó có thể được ánh xạ trên nó. Nói cách khác, nó là một container có một giao diện có thể được sử dụng để áp dụng một hàm cho các giá trị bên trong nó. Khi bạn thấy từ functor, bạn nên suy nghĩ "có thể điều chỉnh được"

Trước đó chúng ta đã học được rằng cùng một tiện ích map () có thể hoạt động trên nhiều kiểu dữ liệu khác nhau. Nó làm điều đó bằng cách nâng hoạt động ánh xạ để làm việc với một API functor. Các hoạt động kiểm soát lưu lượng quan trọng được sử dụng bởi map () tận dụng giao diện đó. Trong trường hợp của Array.prototype.map (), vùng chứa là một mảng, nhưng các cấu trúc dữ liệu khác cũng có thể là các hàm functors - miễn là chúng cung cấp API 

 Array.prototype.map () cho phép bạn trừu tượng kiểu dữ liệu từ tiện ích ánh xạ để làm cho map () có thể sử dụng được với bất kỳ kiểu dữ liệu nào. Chúng ta sẽ tạo một ánh xạ đơn giản () đơn giản để nhân các giá trị được truyền cho 2:

Điều gì sẽ xảy ra nếu chúng ta muốn hoạt động trên các mục tiêu trong một trò chơi để tăng gấp đôi số điểm mà họ giành được? Tất cả những gì chúng ta phải làm là tạo một thay đổi tinh tế cho hàm double () mà chúng ta truyền vào map (), và mọi thứ vẫn hoạt động:

Khái niệm sử dụng các phép trừu tượng như hàm functors và các hàm bậc cao hơn để sử dụng các hàm tiện ích chung để thao tác với bất kỳ số lượng các kiểu dữ liệu khác nhau nào là quan trọng trong lập trình hàm. Bạn sẽ thấy một khái niệm tương tự được áp dụng theo tất cả các cách khác nhau.[9].

> "A list expressed over time is a stream."

Tất cả những gì bạn cần hiểu bây giờ là mảng và functors không phải là cách duy nhất khái niệm container và giá trị trong các container được áp dụng. Ví dụ, một mảng chỉ là một danh sách các thứ. Danh sách được thể hiện theo thời gian là luồng - vì vậy bạn có thể áp dụng cùng một loại tiện ích để xử lý luồng sự kiện đến - thứ mà bạn sẽ thấy rất nhiều khi bạn bắt đầu xây dựng phần mềm thực với FP.

### Declarative vs Imperative

Lập trình hàm là một mô hình khai báo, có nghĩa là logic chương trình được thể hiện mà không mô tả rõ ràng việc kiểm soát luồng.

Các chương trình bắt buộc sử dụng các dòng code mô tả các bước cụ thể được sử dụng để đạt được kết quả mong muốn - kiểm soát luồng: Làm thế nào để làm việc.

Các chương trình khai báo trừu tượng quá trình kiểm soát luồng, và thay vào đó chi tiêu các dòng mã mô tả luồng dữ liệu: Phải làm gì. Làm thế nào được trừu tượng đi.

Ví dụ, ánh xạ bắt buộc này lấy một mảng các số và trả về một mảng mới với mỗi số nhân với 2:

Imperative data mapping

Ánh xạ khai báo này thực hiện tương tự, nhưng tóm tắt điều khiển luồng bằng cách sử dụng tiện ích Array.prototype.map () chức năng, cho phép bạn thể hiện rõ ràng luồng dữ liệu:

Mã bắt buộc thường xuyên sử dụng các câu lệnh. Một câu lệnh là một đoạn mã thực hiện một số hành động. Ví dụ về các câu lệnh thường được sử dụng là `for`, `if`, `switch`, `throw`, etc…

Mã khai báo dựa nhiều hơn vào biểu thức. Biểu thức là một đoạn mã đánh giá một số giá trị. Biểu thức thường là một số kết hợp của các cuộc gọi hàm, giá trị và toán tử được đánh giá để tạo ra giá trị kết quả.

Đây là tất cả các ví dụ về các biểu thức:
    
    
    2 * 2  
    doubleMap([2, 3, 4])  
    Math.max(4, 3, 2)

Thông thường trong code, bạn sẽ thấy các biểu thức được gán cho một số nhận dạng, được trả về từ các hàm hoặc được chuyển vào một hàm. Trước khi được chỉ định, trả về, hoặc được thông qua, biểu thức được đánh giá đầu tiên và giá trị kết quả được sử dụng.

### Kết luận

Các dấu hiệu lập trình chức năng:

* Các hàm thuần túy thay vì các hiệu ứng phụ và trạng thái được chia sẻ
* Tính không thay đổi trên dữ liệu có thể thay đổi
* Thành phần chức năng trên điều khiển lưu lượng bắt buộc
* Rất nhiều tiện ích chung, có thể tái sử dụng sử dụng các hàm bậc cao hơn để hành động trên nhiều loại dữ liệu thay vì các phương thức chỉ hoạt động trên dữ liệu được phân bổ của chúng
* Tuyên bố chứ không phải là mã bắt buộc (phải làm gì, hơn là làm thế nào để làm điều đó)
* Biểu thức trên báo cáo
* Các hàm chứa và hàm bậc cao hơn trên đa hình ad-hoc

![][11]

[1]: https://cdn-images-1.medium.com/max/1600/1*1OxglOpkZHLITbIKEVCy2g.jpeg
[2]: https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976
[3]: https://medium.com/javascript-scene/master-the-javascript-interview-what-is-function-composition-20dfb109a1a0
[4]: https://medium.com/javascript-scene/10-tips-for-better-redux-architecture-69250425af44
[5]: https://medium.com/javascript-scene/the-dao-of-immutability-9f91a70c88cd
[6]: https://github.com/facebook/immutable-js
[7]: https://github.com/swannodette/mori
[8]: https://en.wikipedia.org/wiki/Monad_%28functional_programming%29
[9]: https://github.com/fantasyland/fantasy-land
[10]: http://ericelliottjs.com/product/lifetime-access-pass/
[11]: https://cdn-images-1.medium.com/max/1600/1*3njisYUeHOdyLCGZ8czt_w.jpeg
