##Làm sao để tôi có thể viết CSS dễ mở rộng và bảo trì? Đó là mối quan ngại của mọi Front-end. ITCSS sẽ trả lời cho bạn.

Năm ngoái khi chúng tôi bắt đầu kế hoạch thiết kế lại[HEROized](http://www.heroized.com/) và làm mới website Xfive.co,
tôi đã mong muốn cấu trúc của CSS cho phép dễ dàng trong việc phát triển và xa hơn là bảo trì.

[CSS Modules](https://www.sitepoint.com/understanding-css-modules-methodology/) lúc đó còn khá mới và lạ và tôi luôn luôn
 xem xét tính chất tương đồng của [Atomic Design](http://patternlab.io/) như là sự nhân tạo. Sau đó tôi lướt qua ITCSS của 
[Harry Roberts’s](http://csswizardry.com/) vào issue của 6/2015 của tạp trí [net magazine](http://www.creativebloq.com/web-design/manage-large-scale-web-projects-new-css-architecture-itcss-41514731) và ngay lập tức tôi 
đã yêu thích sự đơn giản và cách tiếp cận CSS này.

##ITCSS là gì?

ITCSS là viết tắt của Inverted Triangle CSS và nó giúp bạn tổ chức file CSS của dự án theo cách mà bạn có thể giải quyết
tốt hơn CSS thật cụ thể ví dụ như(Không phải lúc nào cũng là cách đơn giản nhất)__global namespace, cascade and selectors specificity__.

ITCSS có thể sử dụng với tiền sử lý hoặc không, và nó tương thích với các luồng CSS như BEM, SMACSS hay OOCSS.

Một trong những nguyên tắc chính của ITCSS là nó chia mã nguồn CSS cơ bản của bạn thành các phần (gọi là các layer), có thiết kế tam giác ngược:

![ITCSS form](https://www.xfivecdn.com/xfive/wp-content/uploads/2016/02/01083650/itcss-layers2.svg)

Những layer đó được thể hiện như sau:

* __Setting__:được sử dụng với tiền xử lý và chứa font, định nghĩa màu sắc,...
* __Tool__: tất cả đều được sử dụng mixin và function. Đưa ra bất kì CSS nào trong 2 layer đầu đều không quan trọng.
* __Generic__: reset và(hoặc) bình thường hóa các style, định nghĩa các box-sizing. Nó là layer đầu tiên thực sự tạo ra CSS
* __Elements__: Tạo kiểu cho các thành phần Html trống (như là H1,A,v.v..).
Những thứ này đi kèm với những thiết kế mặc định của trình duyệt vì vậy chúng ra có thể thiết kế lại chúng ở đây.
* __Objects__: những bộ chọn class cơ bản định nghĩa những mẫu thiết kế không rõ ràng. Ví dụ như những đối tượng media
được biết đến bởi OOCSS.
* __Components__ - Các thành phần UI cụ thể. Nó là nơi mà hầu hết các công việc của chúng ta diễn ra và các thành phần UI
của chúng ta thường chứa Objects và Components.
* __Utilities__ - Các lớp tiện ích hay trợ giúp với khả năng ghi đè bất cứ thứ gì có trước trong tam giác, ví dụ như ẩn
đi lớp trợ giúp.

Tam giác cũng hiển thị cách trình bày mẫu bằng các bộ chọn được sắp xếp trong kết quả CSS: từ các kiểu mẫu chung tới từng
cái cụ thể, từ những bộ chọn có tính cụ thể thấp tới từng cái cụ thể hơn (nhưng vẫn *không quá* cụ thể, những ID không
được cho phép) và từ những cái xa đến cái gần.  
![reach](https://www.xfivecdn.com/xfive/wp-content/uploads/2016/02/10154630/itcss-key-metrics.svg)  
Tổ chức CSS như vậy sẽ giúp bạn tránh Specificity Wars và nó đại diên bởi một [biểu đồ đặc trưng khỏe mạnh](https://jonassebastianohlsson.com/specificity-graph/)  
##Documentation
Cập nhật ngày 27/10/2016: báo mạng đã vừa cho tái bản nguyên bản từ bản in (xem mã nguồn phía dưới).  
Thông thường, ở điểm này tôi sẽ bảo bạn tới [trang web ITCSS](https://itcss.io/) để học thêm nữa. Tuy nhiên, không tồn
tại tài liệu mã nguồn mở nào cả.  
ITCSS vẫn còn bản quyền một phần, và nếu bạn muốn sử dụng đầy đủ nó, bạn nên học phần giới thiệu nguyên trên báo mạng.
Tôi không ở đây để phán xét những ý tưởng của tác giả (tôi cảm ơn đến anh ấy vì những hiểu biết mà anh ấy chia sẻ), nhưng
tôi nghĩ nó sẽ ngăn cản ITCSS rộng hơn (điều mà có thể là chủ ý, sau tất cả).  
"Những kí tự độc quyền một phần của ITCSS ngăn chặn nó mở rộng".  
Nó sẽ không ngăn cản bạn từ lúc bắt đầu sử dụng nó trong dự án của bạn, tuy nhiên, nếu bạn thực sự thấy thích thú khi
làm như vậy. [Thấy được các vấn đề](https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/) của báo mạng
để học về ITCSS cơ bản, và học từ các nguồn online có sẵn, và các ví dụ sẽ giúp bạn với sự mở rộng của nó trong các dự
án thực tế.  
## Mã nguồn
Tôi đã sử dụng ITCSS trong 4 dự án tính cho đến nay (bao gồm Xfive.co) và các nguồn dưới đây đã giúp tôi hiểu tốt hơn về nó:
* [Manage large CSS projects with ITCSS](https://www.creativebloq.com/web-design/manage-large-css-projects-itcss-101517528)- 
Giới thiệu về ITCSS của Harry Roberts (bài tái bản nguyên từ bản in, còn thiếu các cột ngắn ở các biểu đồ cụ thể và tiền xử lý)
* [Manage large-scale web projects with new CSS architecture ITCSS ](https://www.creativebloq.com/web-design/manage-large-scale-web-projects-new-css-architecture-itcss-41514731) -
Giới thiệu và phỏng vấn với Harry Roberts
* [Harry Roberts – Managing CSS Projects with ITCSS](https://www.youtube.com/watch?v=1OKZOV-iLj4) - cuộc trò chuyện bởi
Harry ở DaFED và [trang trình bày kèm theo nó](https://www.youtube.com/watch?v=1OKZOV-iLj4)
* [Manage large CSS projects with ITCSS](https://www.youtube.com/watch?v=hz76JIU_xB0) - cái nhìn cho các bài báo mạng
* [ITCSS Screencast code](https://github.com/itcss/itcss-netmag) - mã nguồn từ cái nhìn trên Github
* [Another ITCSS project example](https://github.com/csswizardry/frcss)
* Bài viết tại csswizardry.com và đặc biệt là những thứ dưới đây:
    * [BEMIT: Nói về các bước đặt tên của BEM](https://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/)
    * [mã nguồn sạch hơn với tên trắng](https://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/)
    * [CSS bất biến](https://csswizardry.com/2015/03/immutable-css/)
    * [Biểu đồ đặc trưng](https://csswizardry.com/2014/10/the-specificity-graph/)
* [inuitcss](https://github.com/inuitcss/inuitcss) - OOCSS framework dựa trên ITCSS  và thể hiện một số khái niệm và khả
năng nâng cao
* [Quy ước đặt tên cho BEMIT](http://www.jamesturneronline.net/blog/bemit-naming-convention.html)
Bạn cũng có thể kiểm tra [Chisel](https://github.com/xfiveco/generator-chisel/), bộ sinh Yeoman cho front-end và dự án WordPress,
những thức hỗ trợ ITCSS
##Kinh nghiệm
Ở đây là một vài ý kiển cơ bạn dựa trên kinh nghiệm của tôi qua các dự án ITCSS
###Nghĩ ít hơn trong việc đặt tên hay vị trí mẫu
Các quy định tự nhiên của ITCSS, đặc biệt khi kết hợp với [Quy ước đặt tên cho BEMIT](http://www.jamesturneronline.net/blog/bemit-naming-convention.html) 
cho phép bạn tập trung hơn vào việc giải quyết những thách thức của font-end hơn là nghĩ tên hay vị trí mẫu. Đây là những
gì mà Xfive.co tìm thấy:  
```
@import "settings.colors";
@import "settings.global";

@import "tools.mixins";

@import "normalize-scss/normalize.scss";
@import "generic.reset";
@import "generic.box-sizing";
@import "generic.shared";

@import "elements.headings";
@import "elements.hr";
@import "elements.forms";
@import "elements.links";
@import "elements.lists";
@import "elements.page";
@import "elements.quotes";
@import "elements.tables";

@import "objects.animations";
@import "objects.drawer";
@import "objects.list-bare";
@import "objects.media";
@import "objects.layout";
@import "objects.overlays";

@import "components.404";
@import "components.about";
@import "components.archive";
@import "components.avatars";
@import "components.blog-post";
@import "components.buttons";
@import "components.callout";
@import "components.clients";
@import "components.comments";
@import "components.contact";
@import "components.cta";
@import "components.faq";
@import "components.features";
@import "components.footer";
@import "components.forms";
@import "components.header";
@import "components.headings";
@import "components.hero";
@import "components.jobs";
@import "components.legal-nav";
@import "components.main-cta";
@import "components.main-nav";
@import "components.newsletter";
@import "components.page-title";
@import "components.pagination";
@import "components.post-teaser";
@import "components.process";
@import "components.quote-banner";
@import "components.offices";
@import "components.sec-nav";
@import "components.services";
@import "components.share-buttons";
@import "components.social-media";
@import "components.team";
@import "components.testimonials";
@import "components.topbar";
@import "components.reasons";
@import "components.wordpress";
@import "components.work-list";
@import "components.work-detail";

@import "vendor.prism";

@import "trumps.clearfix";
@import "trumps.utilities";

@import "healthcheck";
```   
Chú ý: Chúng tôi sử dụng [tách rời thư mục cho từng layer](https://github.com/xfiveco/generator-chisel/tree/master/generators/app/templates/styles/itcss)
và tự động tải các định dạng mới tại [Chisel](https://github.com/xfiveco/generator-chisel/)
###Dùng lại đối tượng để phát triển xa
Đối tượng của ITCSS là những ứng viên hoàn hảo cho việc xây dựng thư viện về những thành phần tái sử dụng được cho phép
phát triển font-end nhanh. Phần UI bao gồm những đối tượng chung và những thành phần cụ thể của dự án. Ví dụ như unnuitcss
như một ITCSS framework cơ bản chứa một nhánh của đối tượng, nhưng chỉ một đối tượng mẫu.
###Hoạt hình
Tôi nhắc bạn nên định nghĩa chung, toàn cầu như các đối tượng, ví dụ:  *@keyframes o-fade-in* trong tệp *_objects.animations.scss*  
Những hoạt hình cấu tạo đặc biệt nên được định nghĩa trong các file có cấu tạo tương ứng, ví dụ *@keyframes c-hero-scale*
trong * _components.hero.scss*
### Tính mềm dẻo
ITCSS khá mềm dẻo trong quan hệ của công việc của bạn với công cụ. Một trong những nhà phát triển của chúng tôi đã bày tỏ
sự quan tâm về việc ITCSS đã có bao nhiêu bản mẫu. Tuy nhiên, thực tế thì nó phụ thuộc vào bạn - ITCSS không quy định rằng
bạn cần tất cả bao nhiêu layer  hiện tại(chỉ gọi những cái họ cần nếu nó là hiện tại).  
Do vậy, trong một cài đặt tối thiểu, bạn có thể có những thành phần với thiết kế mặc định của trình duyêt. Tất nhiên, nó
không phải quá thiết thực - một vài cài đặt, cài lại và/hoặc hay chuẩn hóa CSS được hầu hết mọi người sử dụng vì những lý
do tích cực
###Critical CSS
ITCSS đóng vai trò tốt với critical CSS nhờ những số liệu khóa của tam giác ngược. Những mô hình thành phần cơ bản cho 
phép bạn tách riêng từng phần UI thành các thành phần logic, do đó bạn có thể chọn các thành phần CSS bằng tay (chi tiết
hơn ở bài tiếp theo)
###Kích thước tệp và sao chép mẫu
Nếu có bất kì mối quan ngại nào với kiến trúc như là ITCSS hay bất cứ thành phần cơ bản nào như kiến trúc CSS, nó có thể
là kết quả kích thước của tệp. Cách đóng gói thành phần và cho phép tránh xung đột CSS và ghi đè lên nhưng nó cũng có nghĩa
rằng việc xảy ra lặp mẫu cũng hay xảy ra.  
ITCSS không thể cạnh tranh với những [chức năng CSS](https://blog.colepeters.com/building-and-shipping-functional-css/).
Mặt khác, nếu bạn tìm thấy sự lặp lại trong thành phần, bạn nên cân nhắc chuyển chúng sang các đối tượng.
### Phần kết luận
Bạn sẽ không mắc sai lầm với ITCSS được. Nó là kết quả của kinh nghiệm và rất nhiều năm làm việc của Harry Roberts, một 
trong những tác giả CSS nổi tiếng nhất trên thế giới. Nếu bạn muốn đào sâu vào mã nguồn 1 chút, bạn sẽ thấy rằng đây là 
một kiến trúc đơn giản nhưng mô cùng mạnh mẽ, cho phép bạn tạo ra những dự án nhỏ lẫn to với CSS rất dễ mở rộng và bảo trì.  
Tuy nhiên, đừng quên để mắt đến những cái khác như [CSS modules](https://github.com/css-modules/css-modules) trong lúc rảnh rỗi.