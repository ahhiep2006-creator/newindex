<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Thư viện ảnh tương tác</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        h1 {
            color: #333;
            text-align: center;
        }
        
        .gallery {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            margin-top: 30px;
        }
        
        .gallery-item {
            border: 2px solid #ddd;
            border-radius: 8px;
            padding: 10px;
            text-align: center;
            transition: all 0.3s ease;
        }
        
        .gallery-item img {
            max-width: 100%;
            height: 200px;
            object-fit: cover;
            border-radius: 4px;
        }
        
        .gallery-item:hover {
            border-color: #007bff;
            transform: scale(1.05);
        }
        
        .gallery-item:focus {
            outline: 3px solid #ff6b6b;
            border-color: #ff6b6b;
        }
        
        .caption {
            margin-top: 10px;
            font-weight: bold;
            color: #555;
        }
    </style>
</head>
<body>
    <header>
        <h1>Thư viện ảnh tương tác</h1>
        <h2>Khám phá bộ sưu tập hình ảnh đẹp</h2>
    </header>

    <main>
        <div class="gallery" id="imageGallery">
        
        </div>
    </main>

    <script>
    
        const images = [
            {
                src: "https://via.placeholder.com/300x200/4CAF50/white?text=Cảnh+thiên+nhiên",
                alt: "Phong cảnh thiên nhiên với cây xanh và núi non",
                caption: "Thiên nhiên tươi đẹp"
            },
            {
                src: "https://via.placeholder.com/300x200/2196F3/white?text=Thành+phố+hiện+đại",
                alt: "Thành phố hiện đại với các tòa nhà cao tầng",
                caption: "Đô thị hiện đại"
            },
            {
                src: "https://via.placeholder.com/300x200/FF9800/white?text=Bãi+biển",
                alt: "Bãi biển với cát trắng và nước trong xanh",
                caption: "Bãi biển tuyệt đẹp"
            },
            {
                src: "https://via.placeholder.com/300x200/9C27B0/white?text=Rừng+cây",
                alt: "Rừng cây xanh mát với ánh nắng xuyên qua tán lá",
                caption: "Rừng nguyên sinh"
            },
            {
                src: "https://via.placeholder.com/300x200/F44336/white?text=Hoàng+hôn",
                alt: "Hoàng hôn với bầu trời đầy màu sắc rực rỡ",
                caption: "Hoàng hôn lãng mạn"
            },
            {
                src: "https://via.placeholder.com/300x200/607D8B/white?text=Núi+non",
                alt: "Dãy núi hùng vĩ phủ đầy tuyết trắng",
                caption: "Núi non hùng vĩ"
            }
        ];

        
        function initGallery() {
            console.log("Trang đã tải xong - khởi tạo gallery");
            
            const gallery = document.getElementById('imageGallery');
            
            
            for (let i = 0; i < images.length; i++) {
                const imageData = images[i];
                
                
                const galleryItem = document.createElement('div');
                galleryItem.className = 'gallery-item';
                galleryItem.tabIndex = 0; 
                
            
                const img = document.createElement('img');
                img.src = imageData.src;
                img.alt = imageData.alt;
                
            
                const caption = document.createElement('div');
                caption.className = 'caption';
                caption.textContent = imageData.caption;
                
                
                galleryItem.appendChild(img);
                galleryItem.appendChild(caption);
                
                
                addEventListeners(galleryItem, i);
                
            
                gallery.appendChild(galleryItem);
            }
            
            console.log("Gallery đã được khởi tạo với " + images.length + " hình ảnh");
        }

        
        function addEventListeners(element, index) {
            
            element.addEventListener('mouseover', function() {
                console.log(`Mouse over hình ảnh ${index + 1}`);
                this.style.transform = 'scale(1.05)';
                this.style.borderColor = '#007bff';
            });
            
            element.addEventListener('mouseleave', function() {
                console.log(`Mouse leave hình ảnh ${index + 1}`);
                this.style.transform = 'scale(1)';
                this.style.borderColor = '#ddd';
            });
            
            
            element.addEventListener('focus', function() {
                console.log(`Focus vào hình ảnh ${index + 1}`);
                this.style.outline = '3px solid #ff6b6b';
                this.style.borderColor = '#ff6b6b';
            });
            
            element.addEventListener('blur', function() {
                console.log(`Blur khỏi hình ảnh ${index + 1}`);
                this.style.outline = 'none';
                this.style.borderColor = '#ddd';
            });
            
            
            element.addEventListener('click', function() {
                console.log(`Click vào hình ảnh ${index + 1}`);
                alert(`Bạn đã chọn: ${images[index].caption}`);
            });
        }

        
        function addTabFocusAttributes() {
            const galleryItems = document.querySelectorAll('.gallery-item');
            galleryItems.forEach((item, index) => {
                item.setAttribute('tabindex', '0');
                console.log(`Đã thêm tabindex cho hình ảnh ${index + 1}`);
            });
        }

        
        window.addEventListener('load', function() {
            console.log("Sự kiện onload được kích hoạt");
            initGallery();
            addTabFocusAttributes();
        });

        
        function testKeyboardFunctionality() {
            console.log("Kiểm tra tính năng bàn phím:");
            console.log("- Sử dụng Tab để di chuyển giữa các hình ảnh");
            console.log("- Sử dụng Enter/Space để chọn hình ảnh");
            console.log("- Sử dụng phím mũi tên để điều hướng (nếu được triển khai)");
        }

        testKeyboardFunctionality();
    </script>
</body>
</html>
