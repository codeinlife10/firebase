1. Firebase là gì ? `Cơ sở dữ liệu hoạt động trên cloud được cung cấp bởi google`
    # Cơ sở dữ liệu NoSQL  * -> Not only SQL 
    # Cơ sở dữ liệu SQL -> Structure query language
    # Phiên bản cấp cao hơn của local ? `Chính xác` 
        -> local hay session không thể lưu lượng dữ liệu lớn
        -> local hay session không đảm bảo an toàn từ các cuộc tấn công 
Ví dụ : Mongodb - NoSQL , mySQL-SQLserver -> SQL
# Link đọc thêm: https://viblo.asia/p/nhung-diem-khac-biet-giua-sql-va-nosql-gGJ59b4rKX2


2. Các chức năng của firebase ? 
# Link đọc thêm: https://viblo.asia/p/firebase-la-gi-giai-thich-nhung-chuc-nang-co-ban-cua-firebase-bWrZn0jQ5xw

3. Những kiến thức chủ yếu sử dụng: `Màu xanh là những tham số cần truyền cho hàm`
    🧠 Cấu hình firebase
    🧠 Firebase Authentication: https://firebase.google.com/docs/auth/web/start

        1. `getAuth()` -> Trỏ tới authentication firebase của mình
        2. Đăng kí: createUserWithEmailAndPassword( `getAuth()`, `email` , `password` ).then(`Lưu thông tin tài khoản,chuyển hướng...`).catch(`Xử lí lỗi`)
        3. Đăng nhập: signInWithEmailAndPassword( `getAuth()`, `email` , `password` ).then(`Lưu thông tin tài khoản,chuyển hướng...`).catch(`Xử lí lỗi`)
        4. Đăng xuất: signOut( `getAuth()` )

    🧠 Cloud Firestore: https://firebase.google.com/docs/firestore/quickstart

    # Tìm hiểu về cấu trúc cơ sở dữ liệu trong firebase
    ## Một collection chứa nhiều document, document có thể chứa các kiểu dữ liệu như mảng, object, string,... thậm chí chứa 1 subcollection 
        collections ->  documents -> Thông tin chi tiết mỗi document
    Ví dụ: collection `user` -> document `user1` (thường là auto id) -> thông tin chi tiết `{name,age,address}` 
        1. getFireStore() -> Trỏ tới cloud firestore firebase của mình
        💥💥💥 Để tương tác với dữ liệu ta cần biết dữ liệu nằm ở đâu ( Luôn thực hiện đầu tiên trước khi dùng `getDoc` -> gán vào 1 biến cho dễ dùng)
            1.1. collection( `getFirestore()` , `Tên collection` )
            1.2. doc( `getFirestore()` , `Tên collection` , `Tên document` )
        2. Đọc dữ liệu
           2.1. getDoc( `doc` ) -> Lấy doc có vị trí đã lấy ở trên
           2.2. getDocs( `collection` ) -> Lấy toàn bộ doc của 1 collection
        3. Thêm dữ liệu
            3.1. setDoc( `doc`, `Dữ liệu truyền vào` ) -> Thêm mới hoặc ghi đè tùy thuộc vào tham số `Tên document` 
                + Nếu tên document tồn tại thì ghi đè
                + Nếu không truyền vào `Tên document` thì firebase sẽ tự tạo id ngẫu nhiên
        4. Xóa dữ liệu
            4.1. deleteDoc( `doc` ) 
            4.2. Delete collection thì không khuyến khích 👩‍⚖️bị tấn công thì toang :)) 

    🧠 Firebase Storage: https://firebase.google.com/docs/storage/web/start
        1. getStorage() -> Trỏ tới cloud storage của mình thôi 👼🧔
        2. Rõ ràng ta cũng cần biết nơi lưu vào nhỉ !! Đi tìm nó nào :)
            2.1. ref( `getStorage()` , `Tên folder muốn lưu/Tên file sẽ lưu` )
    # Ví dụ 1: ref(getStorage(), 'dogs/chihuahua.png') -> Nó sẽ tạo 1 folder trên storage có tên như kia lun nha :)
    # Ví dụ 2: Trên thực tế tên file sẽ tạo trùng tên file người dùng upload ref(getStorage(), 'dogs/' + fileName) -> fileName lấy được nhé :))



# CDN: https://firebase.google.com/docs/web/learn-more?authuser=0#available-libraries
# API: https://firebase.google.com/docs/reference/js
# Hàng ngon: https://www.youtube.com/watch?v=9zdvmgGsww0&list=PL4cUxeGkcC9jERUGvbudErNCeSZHWUVlb
