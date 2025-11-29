<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Restoran Rahmath Bistro - Menu Online</title>
    <!-- Load Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Custom font import for a professional look */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&family=Playfair+Display:ital,wght@0,400..900;1,400..900&display=swap');
        
        :root {
            --primary-color: #004D40; /* Dark Green */
            --secondary-color: #F8F4E3; /* Light Cream/Parchment - Background */
            --text-color: #333333;
            --accent-color: #FFEB3B; /* Bright Yellow for contrast */
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--secondary-color);
            color: var(--text-color);
        }

        .menu-title {
            font-family: 'Playfair Display', serif;
            color: var(--primary-color);
        }
        
        /* Utility classes for easy color reference */
        .bg-primary { background-color: var(--primary-color); }
        .text-primary { color: var(--primary-color); }
        .border-primary { border-color: var(--primary-color); }
        .text-accent { color: var(--accent-color); }

        /* Custom scrollbar for aesthetics */
        body::-webkit-scrollbar {
            width: 8px;
        }
        body::-webkit-scrollbar-thumb {
            background-color: var(--primary-color);
            border-radius: 4px;
        }
        body::-webkit-scrollbar-track {
            background-color: var(--secondary-color);
        }
        
        /* Active tab styling */
        .tab-button.active {
            background-color: var(--primary-color);
            color: var(--accent-color);
            font-weight: bold;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        /* Image styling */
        .food-item-image {
            width: 80px; /* Small image size for dishes */
            height: 80px;
            object-fit: cover;
            border-radius: 8px; 
            margin-right: 15px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1); 
            transition: opacity 0.3s ease-in-out;
        }
        .drink-item-image {
            width: 48px; /* Extra small image size for drinks */
            height: 48px;
        }

        /* Loading state opacity */
        .loading-image {
            opacity: 0.5;
            animation: pulse 1.5s infinite;
        }
        @keyframes pulse {
            0%, 100% { opacity: 0.5; }
            50% { opacity: 1; }
        }

        /* Adjust layout for image placement */
        .food-item-card {
            display: flex; 
            align-items: center; 
        }

        .food-item-details {
            flex-grow: 1; 
        }
    </style>
</head>
<body class="min-h-screen">

    <!-- Header Section with Logo Integration -->
    <header class="bg-primary shadow-lg sticky top-0 z-10">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4 flex justify-between items-center">
            
            <!-- Logo and Restaurant Name Group -->
            <div class="flex items-center space-x-3">
                <!-- Pastikan fail LOGO.jpg berada di folder yang sama -->
                <img src="LOGO.jpg" 
                     alt="Restoran Rahmath Bistro Logo" 
                     class="h-12 w-12 sm:h-16 sm:w-16 rounded-full border-2 border-accent shadow-md object-contain p-1 bg-white"
                     onerror="this.onerror=null; this.src='https://placehold.co/48x48/004D40/FFEB3B?text=LOGO';"> 
                <h1 class="text-3xl sm:text-4xl font-extrabold menu-title text-accent tracking-wider">
                    Restoran Rahmath Bistro
                </h1>
            </div>

            <p class="text-sm sm:text-base text-accent font-semibold hidden md:block">
                Makanan lazat, disajikan dengan penuh perhatian.
            </p>
        </div>
    </header>

    <!-- Main Content: Menu Sections -->
    <main class="max-w-7xl mx-auto p-4 sm:p-6 lg:p-8">
        
        <h2 class="text-center text-4xl sm:text-5xl font-bold mb-8 text-primary menu-title">Menu Kami</h2>
        
        <!-- Tab Navigation -->
        <nav class="sticky top-[73px] bg-secondary pt-4 pb-4 z-10 overflow-x-auto shadow-md rounded-lg mb-8">
            <div class="flex space-x-2 sm:space-x-4 px-2 sm:px-0">
                <!-- Tab Buttons -->
                <button data-tab="nasi-lemak" class="tab-button active flex-shrink-0 px-4 py-2 text-sm sm:text-base rounded-lg transition duration-200 text-primary bg-white shadow-md hover:bg-gray-100">Nasi Lemak</button>
                <button data-tab="roti" class="tab-button flex-shrink-0 px-4 py-2 text-sm sm:text-base rounded-lg transition duration-200 text-primary bg-white shadow-md hover:bg-gray-100">Roti</button>
                <button data-tab="nasi-goreng" class="tab-button flex-shrink-0 px-4 py-2 text-sm sm:text-base rounded-lg transition duration-200 text-primary bg-white shadow-md hover:bg-gray-100">Nasi Goreng</button>
                <button data-tab="naan" class="tab-button flex-shrink-0 px-4 py-2 text-sm sm:text-base rounded-lg transition duration-200 text-primary bg-white shadow-md hover:bg-gray-100">Naan</button>
                <button data-tab="thai" class="tab-button flex-shrink-0 px-4 py-2 text-sm sm:text-base rounded-lg transition duration-200 text-primary bg-white shadow-md hover:bg-gray-100">Thai</button>
                <button data-tab="western" class="tab-button flex-shrink-0 px-4 py-2 text-sm sm:text-base rounded-lg transition duration-200 text-primary bg-white shadow-md hover:bg-gray-100">Western</button>
                <button data-tab="rojak" class="tab-button flex-shrink-0 px-4 py-2 text-sm sm:text-base rounded-lg transition duration-200 text-primary bg-white shadow-md hover:bg-gray-100">Rojak</button>
                <button data-tab="minuman" class="tab-button flex-shrink-0 px-4 py-2 text-sm sm:text-base rounded-lg transition duration-200 text-primary bg-white shadow-md hover:bg-gray-100">Minuman</button>
            </div>
        </nav>

        <!-- Menu Content Sections (Tab Panes) -->
        <div id="menu-content">
            
            <!-- Nasi Lemak Section (Ditetapkan sebagai aktif secara lalai) -->
            <section id="nasi-lemak" class="tab-content mb-16">
                <h3 class="text-3xl font-extrabold mb-6 pb-2 border-b-2 border-primary text-primary menu-title">Nasi Lemak</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <div class="bg-white p-6 rounded-lg shadow-xl hover:shadow-2xl transition duration-300 food-item-card">
                        <img src="https://placehold.co/80x80/cccccc/000000?text=..." 
                             alt="Nasi Lemak Ayam Goreng Berempah with Sambal" 
                             class="food-item-image loading-image"
                             data-prompt="Nasi Lemak with spicy deep-fried chicken, perfect close-up food photography, dark background, rich color, 8k, cinematic lighting, food photography award winner style"
                        > 
                        <div class="food-item-details">
                            <div class="flex justify-between items-start mb-2">
                                <h4 class="text-xl font-bold">Nasi Lemak Ayam Goreng Berempah</h4>
                                <span class="text-xl font-bold text-primary">RM 14.50</span>
                            </div>
                            <p class="text-gray-600">Nasi wangi yang dimasak dengan santan, disajikan dengan ayam goreng rempah, sambal, ikan bilis, kacang, dan telur rebus.</p>
                        </div>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-xl hover:shadow-2xl transition duration-300 food-item-card">
                        <img src="https://placehold.co/80x80/cccccc/000000?text=..." 
                             alt="Classic Nasi Lemak with boiled egg, peanuts, anchovies, and sambal" 
                             class="food-item-image loading-image"
                             data-prompt="Classic Nasi Lemak with boiled egg, fried anchovies, peanuts, and a spoonful of red sambal chili paste, overhead view, restaurant lighting"
                        >
                        <div class="food-item-details">
                            <div class="flex justify-between items-start mb-2">
                                <h4 class="text-xl font-bold">Nasi Lemak Biasa (Telur)</h4>
                                <span class="text-xl font-bold text-primary">RM 8.00</span>
                            </div>
                            <p class="text-gray-600">Versi klasik dengan sambal pedas, ikan bilis rangup, kacang goreng, dan telur rebus separuh masak.</p>
                        </div>
                    </div>
                </div>
            </section>
            
            <!-- Roti Section -->
            <section id="roti" class="tab-content mb-16 hidden">
                <h3 class="text-3xl font-extrabold mb-6 pb-2 border-b-2 border-primary text-primary menu-title">Roti</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <div class="bg-white p-6 rounded-lg shadow-xl hover:shadow-2xl transition duration-300 food-item-card">
                        <img src="https://placehold.co/80x80/cccccc/000000?text=..." 
                             alt="Roti Canai with mutton curry gravy" 
                             class="food-item-image loading-image"
                             data-prompt="Flaky Roti Canai bread dipped in rich, dark mutton curry (kari kambing), close-up shot, authentic Malaysian food"
                        >
                        <div class="food-item-details">
                            <div class="flex justify-between items-start mb-2">
                                <h4 class="text-xl font-bold">Roti Canai Kuah Kari Kambing</h4>
                                <span class="text-xl font-bold text-primary">RM 10.00</span>
                            </div>
                            <p class="text-gray-600">Roti canai lembut dan rangup, disajikan dengan kuah kari kambing yang kaya rasa.</p>
                        </div>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-xl hover:shadow-2xl transition duration-300 food-item-card">
                        <img src="https://placehold.co/80x80/cccccc/000000?text=..." 
                             alt="Roti Telur Bawang" 
                             class="food-item-image loading-image"
                             data-prompt="Malaysian Roti Telur Bawang, flatbread with egg and onions cooked inside, served folded on a plate, warm lighting"
                        >
                        <div class="food-item-details">
                            <div class="flex justify-between items-start mb-2">
                                <h4 class="text-xl font-bold">Roti Telur Bawang</h4>
                                <span class="text-xl font-bold text-primary">RM 5.50</span>
                            </div>
                            <p class="text-gray-600">Roti yang dilemparkan dengan telur dan hirisan bawang, hidangan sarapan yang sempurna.</p>
                        </div>
                    </div>
                </div>
            </section>
            
            <!-- Nasi Goreng Section -->
            <section id="nasi-goreng" class="tab-content mb-16 hidden">
                <h3 class="text-3xl font-extrabold mb-6 pb-2 border-b-2 border-primary text-primary menu-title">Nasi Goreng</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <div class="bg-white p-6 rounded-lg shadow-xl hover:shadow-2xl transition duration-300 food-item-card">
                        <img src="https://placehold.co/80x80/cccccc/000000?text=..." 
                             alt="Spicy Nasi Goreng Kampung" 
                             class="food-item-image loading-image"
                             data-prompt="Nasi Goreng Kampung, spicy fried rice with fried anchovies and kangkung, topped with a perfect sunny-side-up egg, high angle, Malaysian cuisine"
                        >
                        <div class="food-item-details">
                            <div class="flex justify-between items-start mb-2">
                                <h4 class="text-xl font-bold">Nasi Goreng Kampung</h4>
                                <span class="text-xl font-bold text-primary">RM 13.00</span>
                            </div>
                            <p class="text-gray-600">Nasi goreng pedas dengan ikan bilis, kangkung, dan telur mata kerbau.</p>
                        </div>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-xl hover:shadow-2xl transition duration-300 food-item-card">
                        <img src="https://placehold.co/80x80/cccccc/000000?text=..." 
                             alt="Nasi Goreng Cina" 
                             class="food-item-image loading-image"
                             data-prompt="Chinese style Nasi Goreng, lighter fried rice with prawns, chicken, and mixed vegetables, served on white porcelain, soft studio lighting"
                        >
                        <div class="food-item-details">
                            <div class="flex justify-between items-start mb-2">
                                <h4 class="text-xl font-bold">Nasi Goreng Cina</h4>
                                <span class="text-xl font-bold text-primary">RM 12.00</span>
                            </div>
                            <p class="text-gray-600">Nasi goreng gaya Cina yang lebih ringan, dengan udang, ayam, dan sayur-sayuran.</p>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Naan Section -->
            <section id="naan" class="tab-content mb-16 hidden">
                <h3 class="text-3xl font-extrabold mb-6 pb-2 border-b-2 border-primary text-primary menu-title">Naan</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <div class="bg-white p-6 rounded-lg shadow-xl hover:shadow-2xl transition duration-300 food-item-card">
                        <img src="https://placehold.co/80x80/cccccc/000000?text=..." 
                             alt="Naan Cheese melting mozzarella inside" 
                             class="food-item-image loading-image"
                             data-prompt="Indian Cheese Naan bread, torn open to show melted mozzarella cheese, fresh from the tandoor oven, cinematic food shot"
                        >
                        <div class="food-item-details">
                            <div class="flex justify-between items-start mb-2">
                                <h4 class="text-lg font-bold">Naan Cheese</h4>
                                <span class="text-lg font-bold text-primary">RM 8.50</span>
                            </div>
                            <p class="text-gray-600 text-sm">Roti naan lembut dengan inti keju mozzarella cair yang melimpah.</p>
                        </div>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-xl hover:shadow-2xl transition duration-300 food-item-card">
                        <img src="https://placehold.co/80x80/cccccc/000000?text=..." 
                             alt="Naan Garlic with butter and coriander" 
                             class="food-item-image loading-image"
                             data-prompt="Garlic Naan, soft bread topped with melted garlic butter and fresh cilantro, close-up, warm colors"
                        >
                        <div class="food-item-details">
                            <div class="flex justify-between items-start mb-2">
                                <h4 class="text-lg font-bold">Naan Garlic</h4>
                                <span class="text-lg font-bold text-primary">RM 6.00</span>
                            </div>
                            <p class="text-gray-600 text-sm">Naan yang disapu dengan mentega bawang putih dan daun ketumbar segar.</p>
                        </div>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-xl hover:shadow-2xl transition duration-300 food-item-card">
                        <img src="https://placehold.co/80x80/cccccc/000000?text=..." 
                             alt="Plain Naan bread" 
                             class="food-item-image loading-image"
                             data-prompt="Plain Naan bread, slightly charred, perfect for dipping in curry, side angle view, rustic table setting"
                        >
                        <div class="food-item-details">
                            <div class="flex justify-between items-start mb-2">
                                <h4 class="text-lg font-bold">Naan Biasa</h4>
                                <span class="text-lg font-bold text-primary">RM 4.00</span>
                            </div>
                            <p class="text-gray-600 text-sm">Naan bakar tradisional, sesuai untuk dicicah dengan kari.</p>
                        </div>
                    </div>
                </div>
            </section>
            
            <!-- Thai Section -->
            <section id="thai" class="tab-content mb-16 hidden">
                <h3 class="text-3xl font-extrabold mb-6 pb-2 border-b-2 border-primary text-primary menu-title">Thai</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <div class="bg-white p-6 rounded-lg shadow-xl hover:shadow-2xl transition duration-300 food-item-card">
                        <img src="https://placehold.co/80x80/cccccc/000000?text=..." 
                             alt="Tom Yum Goong Spicy Seafood Soup" 
                             class="food-item-image loading-image"
                             data-prompt="Tom Yum Goong, spicy and sour Thai soup with prawns, lemongrass, and mushrooms, served in a traditional metal pot, rich steam, bright colors"
                        >
                        <div class="food-item-details">
                            <div class="flex justify-between items-start mb-2">
                                <h4 class="text-xl font-bold">Tom Yum Goong (Seafood)</h4>
                                <span class="text-xl font-bold text-primary">RM 18.00</span>
                            </div>
                            <p class="text-gray-600">Sup pedas masam dengan udang, serai, daun limau purut, dan cendawan.</p>
                        </div>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-xl hover:shadow-2xl transition duration-300 food-item-card">
                        <img src="https://placehold.co/80x80/cccccc/000000?text=..." 
                             alt="Pad Kra Pao spicy basil chicken" 
                             class="food-item-image loading-image"
                             data-prompt="Thai Pad Kra Pao, spicy minced chicken and holy basil stir-fry, served over rice with a fried egg on top, authentic Thai street food style"
                        >
                        <div class="food-item-details">
                            <div class="flex justify-between items-start mb-2">
                                <h4 class="text-xl font-bold">Pad Kra Pao (Ayam Basil Pedas)</h4>
                                <span class="text-xl font-bold text-primary">RM 15.50</span>
                            </div>
                            <p class="text-gray-600">Tumisan ayam cincang dengan daun basil pedas, bawang, dan cili, disajikan dengan nasi.</p>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Western Section -->
            <section id="western" class="tab-content mb-16 hidden">
                <h3 class="text-3xl font-extrabold mb-6 pb-2 border-b-2 border-primary text-primary menu-title">Western</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <div class="bg-white p-6 rounded-lg shadow-xl hover:shadow-2xl transition duration-300 food-item-card">
                        <img src="https://placehold.co/80x80/cccccc/000000?text=..." 
                             alt="Grilled Lamb Chop with mashed potato and black pepper sauce" 
                             class="food-item-image loading-image"
                             data-prompt="Restaurant-style Grilled Lamb Chop, coated in black pepper sauce, served with creamy mashed potato and mixed steamed vegetables, fine dining presentation"
                        >
                        <div class="food-item-details">
                            <div class="flex justify-between items-start mb-2">
                                <h4 class="text-xl font-bold">Grilled Lamb Chop</h4>
                                <span class="text-xl font-bold text-primary">RM 38.00</span>
                            </div>
                            <p class="text-gray-600">Cincang kambing bakar dengan sos lada hitam, kentang putar berkrim, dan sayur-sayuran.</p>
                        </div>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-xl hover:shadow-2xl transition duration-300 food-item-card">
                        <img src="https://placehold.co/80x80/cccccc/000000?text=..." 
                             alt="Spaghetti Carbonara with smoked chicken" 
                             class="food-item-image loading-image"
                             data-prompt="Creamy Spaghetti Carbonara with smoked chicken pieces and fresh parsley, twirled on a white fork, Italian style, bright and inviting lighting"
                        >
                        <div class="food-item-details">
                            <div class="flex justify-between items-start mb-2">
                                <h4 class="text-xl font-bold">Spaghetti Carbonara Klasik</h4>
                                <span class="text-xl font-bold text-primary">RM 24.00</span>
                            </div>
                            <p class="text-gray-600">Spaghetti dengan sos krim telur, keju parmesan, dan potongan daging ayam salai.</p>
                        </div>
                    </div>
                </div>
            </section>
            
            <!-- Rojak Section -->
            <section id="rojak" class="tab-content mb-16 hidden">
                <h3 class="text-3xl font-extrabold mb-6 pb-2 border-b-2 border-primary text-primary menu-title">Rojak</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <div class="bg-white p-6 rounded-lg shadow-xl hover:shadow-2xl transition duration-300 food-item-card">
                        <img src="https://placehold.co/80x80/cccccc/000000?text=..." 
                             alt="Rojak Buah fresh fruit salad with thick prawn paste sauce" 
                             class="food-item-image loading-image"
                             data-prompt="Rojak Buah, a mix of fresh tropical fruits like pineapple, mango, and jicama, tossed in a thick, dark, sweet and spicy prawn paste sauce, close-up, vibrant food photography"
                        >
                        <div class="food-item-details">
                            <div class="flex justify-between items-start mb-2">
                                <h4 class="text-xl font-bold">Rojak Buah</h4>
                                <span class="text-xl font-bold text-primary">RM 9.50</span>
                            </div>
                            <p class="text-gray-600">Campuran buah-buahan segar (jambu, nanas, mangga) dengan kuah rojak udang manis pedas.</p>
                        </div>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-xl hover:shadow-2xl transition duration-300 food-item-card">
                        <img src="https://placehold.co/80x80/cccccc/000000?text=..." 
                             alt="Pasembur Indian Rojak" 
                             class="food-item-image loading-image"
                             data-prompt="Pasembur or Indian Rojak, a Penang-style salad with shredded vegetables, fried items, and thick sweet peanut sauce, high contrast lighting"
                        >
                        <div class="food-item-details">
                            <div class="flex justify-between items-start mb-2">
                                <h4 class="text-xl font-bold">Pasembur (Rojak Mamak)</h4>
                                <span class="text-xl font-bold text-primary">RM 11.00</span>
                            </div>
                            <p class="text-gray-600">Sayur-sayuran, tauhu goreng, kentang, dan cucur, disajikan dengan kuah kacang manis yang tebal.</p>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Minuman Section -->
            <section id="minuman" class="tab-content mb-16 hidden">
                <h3 class="text-3xl font-extrabold mb-6 pb-2 border-b-2 border-primary text-primary menu-title">Minuman</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <!-- Column 1 (Hot/Local) -->
                    <div>
                        <h4 class="text-xl font-semibold mb-3 text-primary">Minuman Panas & Lokal</h4>
                        <ul class="space-y-2">
                            <li class="flex justify-between border-b border-gray-300 py-1 food-item-card">
                                <img src="https://placehold.co/48x48/cccccc/000000?text=..." 
                                     alt="Teh Tarik Hot" 
                                     class="food-item-image drink-item-image loading-image"
                                     data-prompt="Hot Teh Tarik in a glass mug, with foam on top, Malaysian drink, soft focus background"
                                >
                                <div class="food-item-details flex justify-between items-center">
                                    <span>Teh Tarik Panas</span><span class="font-medium text-primary">RM 3.50</span>
                                </div>
                            </li>
                            <li class="flex justify-between border-b border-gray-300 py-1 food-item-card">
                                <img src="https://placehold.co/48x48/cccccc/000000?text=..." 
                                     alt="Kopi O Hot" 
                                     class="food-item-image drink-item-image loading-image"
                                     data-prompt="Hot Kopi 'O' (black coffee with sugar) in a traditional porcelain cup, Malaysian Kopi"
                                >
                                <div class="food-item-details flex justify-between items-center">
                                    <span>Kopi 'O' Panas</span><span class="font-medium text-primary">RM 3.00</span>
                                </div>
                            </li>
                            <li class="flex justify-between border-b border-gray-300 py-1 food-item-card">
                                <img src="https://placehold.co/48x48/cccccc/000000?text=..." 
                                     alt="Milo Hot" 
                                     class="food-item-image drink-item-image loading-image"
                                     data-prompt="Hot Milo drink with Milo powder sprinkled on top, comforting drink"
                                >
                                <div class="food-item-details flex justify-between items-center">
                                    <span>Milo Panas</span><span class="font-medium text-primary">RM 4.50</span>
                                </div>
                            </li>
                        </ul>
                    </div>
                    <!-- Column 2 (Cold/Iced) -->
                    <div>
                        <h4 class="text-xl font-semibold mb-3 text-primary">Minuman Sejuk & Ais</h4>
                        <ul class="space-y-2">
                            <li class="flex justify-between border-b border-gray-300 py-1 food-item-card">
                                <img src="https://placehold.co/48x48/cccccc/000000?text=..." 
                                     alt="Teh O Ice Limau" 
                                     class="food-item-image drink-item-image loading-image"
                                     data-prompt="Iced Lemon Tea (Teh O Ais Limau) in a tall glass, condensation, refreshing, studio lighting"
                                >
                                <div class="food-item-details flex justify-between items-center">
                                    <span>Teh 'O' Ais Limau</span><span class="font-medium text-primary">RM 4.00</span>
                                </div>
                            </li>
                            <li class="flex justify-between border-b border-gray-300 py-1 food-item-card">
                                <img src="https://placehold.co/48x48/cccccc/000000?text=..." 
                                     alt="Iced Milo Dinosaur" 
                                     class="food-item-image drink-item-image loading-image"
                                     data-prompt="Iced Milo Dinosaur, a popular cold malt drink topped with extra undissolved Milo powder, tall glass, vibrant food photography"
                                >
                                <div class="food-item-details flex justify-between items-center">
                                    <span>Milo Ais</span><span class="font-medium text-primary">RM 5.00</span>
                                </div>
                            </li>
                            <li class="flex justify-between border-b border-gray-300 py-1 food-item-card">
                                <img src="https://placehold.co/48x48/cccccc/000000?text=..." 
                                     alt="Air Sirap Bandung Iced" 
                                     class="food-item-image drink-item-image loading-image"
                                     data-prompt="Air Sirap Bandung, a pink condensed milk drink with rose syrup, served iced, sweet and refreshing"
                                >
                                <div class="food-item-details flex justify-between items-center">
                                    <span>Air Sirap Bandung</span><span class="font-medium text-primary">RM 4.50</span>
                                </div>
                            </li>
                        </ul>
                    </div>
                </div>
            </section>

             <!-- Allergy and Disclaimer Notice -->
            <div class="mt-16 p-6 bg-yellow-100 border-l-4 border-yellow-500 rounded-lg shadow-inner">
                <p class="text-sm text-gray-700">
                    <span class="font-bold text-primary">Notis Alahan:</span> Sila maklumkan kepada staf kami tentang sebarang alahan sebelum membuat pesanan. Harga tertakluk kepada perubahan.
                </p>
            </div>

        </div>

    </main>

    <!-- Footer Section -->
    <footer class="bg-primary mt-12">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 text-center">
            <p class="text-lg font-semibold menu-title mb-2 text-accent">Restoran Rahmath Bistro</p>
            <p class="text-sm text-yellow-300">&copy; 2024. Hak Cipta Terpelihara. | <a href="#" class="underline hover:opacity-80">Lawati Laman Web Kami</a></p>
            <p class="text-xs mt-2 text-yellow-300">123 Culinary Way, Flavor Town, CA 90210 | (555) 555-GRIL</p>
        </div>
    </footer>

    <script>
        // --- Image Generation and API Logic ---
        const IMAGE_MODEL = "imagen-4.0-generate-001";
        const API_KEY = ""; 

        /**
         * Generic function for fetching with exponential backoff.
         */
        async function fetchWithExponentialBackoff(url, options, maxRetries = 5) {
            for (let attempt = 0; attempt < maxRetries; attempt++) {
                try {
                    const response = await fetch(url, options);
                    if (response.status !== 429 && response.ok) {
                        return response;
                    }
                    if (response.status === 429 || !response.ok) {
                        if (attempt === maxRetries - 1) throw new Error(`API failed after ${maxRetries} attempts with status: ${response.status}`);
                        const delay = Math.pow(2, attempt) * 1000 + Math.random() * 1000;
                        await new Promise(resolve => setTimeout(resolve, delay));
                        continue;
                    }
                    return response;
                } catch (error) {
                    if (attempt === maxRetries - 1) throw error;
                    const delay = Math.pow(2, attempt) * 1000 + Math.random() * 1000;
                    await new Promise(resolve => setTimeout(resolve, delay));
                }
            }
            throw new Error("Exceeded maximum retries.");
        }

        /**
         * Generates an image using the Imagen API and updates the given <img> element.
         * @param {HTMLElement} imgElement - The <img> element to update.
         */
        async function generateAndSetImage(imgElement) {
            const prompt = imgElement.getAttribute('data-prompt');
            if (!prompt) return;

            // Pastikan API Key wujud sebelum membuat panggilan
            if (API_KEY === "") {
                 console.warn("API Key is missing. Skipping image generation.");
                 // Fallback: Replace placeholder color with a food-safe color and add a label
                 imgElement.src = imgElement.src.replace('cccccc/000000', 'FFC107/333333').replace('...', 'N/A');
                 imgElement.classList.remove('loading-image');
                 return;
            }


            imgElement.classList.add('loading-image');

            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/${IMAGE_MODEL}:predict?key=${API_KEY}`;
            
            const payload = { 
                instances: [{ 
                    prompt: prompt 
                }], 
                parameters: { 
                    sampleCount: 1,
                    aspectRatio: "1:1" 
                } 
            };

            try {
                const response = await fetchWithExponentialBackoff(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });

                const result = await response.json();
                
                if (result.predictions && result.predictions.length > 0 && result.predictions[0].bytesBase64Encoded) {
                    const base64Data = result.predictions[0].bytesBase64Encoded;
                    imgElement.src = `data:image/png;base64,${base64Data}`;
                    imgElement.classList.remove('loading-image');
                } else {
                    console.error("Image generation failed. Response:", result);
                    imgElement.classList.remove('loading-image');
                    imgElement.src = 'https://placehold.co/80x80/CC0000/FFFFFF?text=FAIL';
                }
            } catch (error) {
                console.error("Error generating image:", error);
                imgElement.classList.remove('loading-image');
                imgElement.src = 'https://placehold.co/80x80/CC0000/FFFFFF?text=ERROR';
            }
        }

        // --- Tab and Initialization Logic ---

        function switchTab(targetTabId) {
            const tabContents = document.querySelectorAll('.tab-content');
            const tabButtons = document.querySelectorAll('.tab-button');

            // 1. Sembunyikan semua kandungan tab
            tabContents.forEach(content => {
                content.classList.add('hidden');
            });

            // 2. Buang status 'active' dari semua butang
            tabButtons.forEach(button => {
                button.classList.remove('active');
            });

            // 3. Paparkan kandungan tab yang disasarkan
            const targetContent = document.getElementById(targetTabId);
            if (targetContent) {
                targetContent.classList.remove('hidden');
            } else {
                console.error(`Content section with ID '${targetTabId}' not found.`);
                return;
            }

            // 4. Aktifkan butang tab
            const targetButton = document.querySelector(`.tab-button[data-tab="${targetTabId}"]`);
            if (targetButton) {
                targetButton.classList.add('active');
            }
        }

        document.addEventListener('DOMContentLoaded', () => {
            const tabButtons = document.querySelectorAll('.tab-button');
            const menuImages = document.querySelectorAll('.food-item-image');

            // 1. Initialize Tabs
            tabButtons.forEach(button => {
                button.addEventListener('click', function() {
                    const targetTabId = this.getAttribute('data-tab');
                    if (targetTabId) {
                        switchTab(targetTabId);
                    }
                });
            });

            // STARTUP FIX: Pastikan tab butang yang betul diserlahkan dan kandungan dipaparkan
            const initialTab = document.querySelector('.tab-button.active');
            if (initialTab) {
                // Gunakan tab yang mempunyai kelas 'active' di HTML (Nasi Lemak)
                switchTab(initialTab.getAttribute('data-tab'));
            } else if (tabButtons.length > 0) {
                // Jika tiada yang aktif (sepatutnya tidak berlaku dengan kod ini), tetapkan yang pertama
                tabButtons[0].classList.add('active');
                switchTab(tabButtons[0].getAttribute('data-tab'));
            }

            // 2. Generate Images for all menu items
            menuImages.forEach(img => {
                generateAndSetImage(img);
            });
        });
    </script>
    
</body>
</html>
