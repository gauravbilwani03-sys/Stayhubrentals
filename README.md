# Stayhubrentals
I want to make a site for rental services through which customers can search on google and our site pops up for booking a room or hotel or hostel something like that so help me with it
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>StayHub | Book Budget Hotels & Rooms in Goa, Somnath, Mount Abu</title>
    
    <!-- SEO Meta Tags -->
    <meta name="description" content="Book affordable hotel rooms, homestays, and rental properties in Somnath, Goa, Mount Abu, Mumbai, and Ahmedabad with zero booking fees on StayHub.">
    <meta name="keywords" content="hotel booking Goa, cheap rooms Somnath, Mount Abu resort rental, rooms in Ahmedabad, budget hotels Mumbai, room rentals near temple">
    <meta name="author" content="StayHub Rentals">

    <!-- Open Graph (WhatsApp, Facebook, Social Media Share Cards) -->
    <meta property="og:title" content="Book Budget Rooms & Hotels | StayHub">
    <meta property="og:description" content="Find budget hotels, homestays, and resorts in Goa, Somnath, Mount Abu, Mumbai & Ahmedabad. Best prices guaranteed!">
    <meta property="og:type" content="website">

    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">

    <style>
        .hero-bg {
            background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.6)), url('https://images.unsplash.com/photo-1566073771259-6a8506099945?auto=format&fit=crop&w=1600&q=80');
            background-size: cover;
            background-position: center;
        }
    </style>
</head>
<body class="bg-gray-50 text-gray-800 font-sans flex flex-col min-h-screen">

    <!-- Navigation Header -->
    <header class="bg-white shadow-sm sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4 flex justify-between items-center">
            <div class="flex items-center space-x-2 cursor-pointer" onclick="filterByCity('All')">
                <i class="fa-solid me-2 fa-hotel text-indigo-600 text-2xl"></i>
                <span class="text-2xl font-bold text-gray-900 tracking-tight">Stay<span class="text-indigo-600">Hub</span></span>
            </div>
            
            <nav class="hidden md:flex space-x-8 text-sm font-semibold text-gray-600">
                <a href="#destinations" class="hover:text-indigo-600 transition">Destinations</a>
                <a href="#listings" class="hover:text-indigo-600 transition">Featured Stay Options</a>
                <a href="#host" class="hover:text-indigo-600 transition">List Your Property</a>
                <a href="#guide" class="hover:text-indigo-600 transition">Earn Money</a>
            </nav>

            <div class="flex items-center space-x-3">
                <button onclick="toggleMyBookingsModal()" class="px-4 py-2 border border-indigo-600 text-indigo-600 rounded-lg font-medium hover:bg-indigo-50 transition text-sm">
                    <i class="fa-solid fa-bookmark mr-1"></i> My Bookings
                </button>
            </div>
        </div>
    </header>

    <!-- Hero Search Section -->
    <section class="hero-bg text-white py-20 px-4 text-center relative">
        <div class="max-w-4xl mx-auto">
            <h1 class="text-3xl md:text-5xl font-extrabold mb-4 leading-tight">Find & Book Rental Rooms in Top Tourist Destinations</h1>
            <p class="text-lg md:text-xl opacity-90 mb-8">Affordable hotels, homestays, & guest houses in Somnath, Goa, Mount Abu, Mumbai, & Ahmedabad.</p>

            <!-- Search Box Widget -->
            <div class="bg-white rounded-xl p-4 md:p-6 text-gray-800 shadow-2xl grid grid-cols-1 md:grid-cols-4 gap-4 items-center">
                <div class="text-left">
                    <label class="block text-xs font-semibold text-gray-500 uppercase mb-1">Destination</label>
                    <div class="flex items-center bg-gray-100 rounded-lg px-3 py-2">
                        <i class="fa-solid fa-location-dot text-indigo-600 mr-2"></i>
                        <select id="search-city" class="bg-transparent w-full focus:outline-none font-medium text-gray-700">
                            <option value="All">All Cities</option>
                            <option value="Goa">Goa</option>
                            <option value="Somnath">Somnath</option>
                            <option value="Mount Abu">Mount Abu</option>
                            <option value="Mumbai">Mumbai</option>
                            <option value="Ahmedabad">Ahmedabad</option>
                        </select>
                    </div>
                </div>

                <div class="text-left">
                    <label class="block text-xs font-semibold text-gray-500 uppercase mb-1">Check-in</label>
                    <div class="flex items-center bg-gray-100 rounded-lg px-3 py-2">
                        <i class="fa-solid fa-calendar text-indigo-600 mr-2"></i>
                        <input type="date" id="search-checkin" class="bg-transparent w-full focus:outline-none font-medium text-gray-700">
                    </div>
                </div>

                <div class="text-left">
                    <label class="block text-xs font-semibold text-gray-500 uppercase mb-1">Guests</label>
                    <div class="flex items-center bg-gray-100 rounded-lg px-3 py-2">
                        <i class="fa-solid fa-users text-indigo-600 mr-2"></i>
                        <select id="search-guests" class="bg-transparent w-full focus:outline-none font-medium text-gray-700">
                            <option value="1">1 Guest</option>
                            <option value="2" selected>2 Guests</option>
                            <option value="4">4 Guests / Family</option>
                        </select>
                    </div>
                </div>

                <button onclick="handleSearch()" class="bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-3 px-6 rounded-lg shadow-md hover:shadow-lg transition flex items-center justify-center">
                    <i class="fa-solid fa-magnifying-glass mr-2"></i> Search Stays
                </button>
            </div>
        </div>
    </section>

    <!-- Top Tourist Locations Grid -->
    <section id="destinations" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
        <h2 class="text-2xl md:text-3xl font-bold mb-2">Popular Tourist Destinations</h2>
        <p class="text-gray-600 mb-8">Select a destination to filter top rated rooms and accommodations</p>

        <div class="grid grid-cols-2 md:grid-cols-5 gap-4">
            <div onclick="filterByCity('Goa')" class="cursor-pointer group relative rounded-xl overflow-hidden shadow-md h-40">
                <img src="https://images.unsplash.com/photo-1512343879784-a960bf40e7f2?auto=format&fit=crop&w=600&q=80" alt="Goa" class="w-full h-full object-cover group-hover:scale-110 transition duration-300">
                <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent flex items-end p-4">
                    <span class="text-white font-bold text-lg">Goa</span>
                </div>
            </div>

            <div onclick="filterByCity('Somnath')" class="cursor-pointer group relative rounded-xl overflow-hidden shadow-md h-40">
                <img src="https://images.unsplash.com/photo-1627894483216-2138af692e32?auto=format&fit=crop&w=600&q=80" alt="Somnath" class="w-full h-full object-cover group-hover:scale-110 transition duration-300">
                <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent flex items-end p-4">
                    <span class="text-white font-bold text-lg">Somnath</span>
                </div>
            </div>

            <div onclick="filterByCity('Mount Abu')" class="cursor-pointer group relative rounded-xl overflow-hidden shadow-md h-40">
                <img src="https://images.unsplash.com/photo-1596178065887-1198b6148b2b?auto=format&fit=crop&w=600&q=80" alt="Mount Abu" class="w-full h-full object-cover group-hover:scale-110 transition duration-300">
                <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent flex items-end p-4">
                    <span class="text-white font-bold text-lg">Mount Abu</span>
                </div>
            </div>

            <div onclick="filterByCity('Mumbai')" class="cursor-pointer group relative rounded-xl overflow-hidden shadow-md h-40">
                <img src="https://images.unsplash.com/photo-1570168007204-dfb528c6958f?auto=format&fit=crop&w=600&q=80" alt="Mumbai" class="w-full h-full object-cover group-hover:scale-110 transition duration-300">
                <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent flex items-end p-4">
                    <span class="text-white font-bold text-lg">Mumbai</span>
                </div>
            </div>

            <div onclick="filterByCity('Ahmedabad')" class="cursor-pointer group relative rounded-xl overflow-hidden shadow-md h-40">
                <img src="https://images.unsplash.com/photo-1609946782912-663806313175?auto=format&fit=crop&w=600&q=80" alt="Ahmedabad" class="w-full h-full object-cover group-hover:scale-110 transition duration-300">
                <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent flex items-end p-4">
                    <span class="text-white font-bold text-lg">Ahmedabad</span>
                </div>
            </div>
        </div>
    </section>

    <!-- Room Listings Section -->
    <section id="listings" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 flex-grow">
        <div class="flex justify-between items-center mb-6">
            <div>
                <h2 id="listings-title" class="text-2xl md:text-3xl font-bold">Available Accommodations</h2>
                <p id="listings-subtitle" class="text-gray-600 text-sm">Showing properties for all locations</p>
            </div>
            <button onclick="filterByCity('All')" class="text-indigo-600 text-sm font-semibold hover:underline">Show All</button>
        </div>

        <div id="property-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
            <!-- Dynamic Injection by JavaScript -->
        </div>
    </section>

    <!-- Property Owner / Host Registration CTA -->
    <section id="host" class="bg-indigo-900 text-white py-16 my-12">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
            <div>
                <span class="bg-indigo-700 text-indigo-200 text-xs font-semibold px-3 py-1 rounded-full uppercase">For Property Owners</span>
                <h2 class="text-3xl font-bold mt-3 mb-4">Have a hotel, room, or homestay in tourist cities?</h2>
                <p class="text-indigo-200 mb-6">List your property on StayHub for free and start getting room booking inquiries from travelers across India.</p>
                
                <form id="host-form" onsubmit="handleHostSubmit(event)" class="bg-white text-gray-800 rounded-xl p-6 shadow-lg space-y-4">
                    <h3 class="text-lg font-bold text-gray-900 mb-2">Register Your Property</h3>
                    <input type="text" required id="host-name" placeholder="Your Name / Business Name" class="w-full border border-gray-300 rounded-lg p-2 text-sm focus:outline-none focus:border-indigo-600">
                    <input type="tel" required id="host-phone" placeholder="WhatsApp / Phone Number" class="w-full border border-gray-300 rounded-lg p-2 text-sm focus:outline-none focus:border-indigo-600">
                    <div class="grid grid-cols-2 gap-2">
                        <select id="host-city" class="border border-gray-300 rounded-lg p-2 text-sm focus:outline-none focus:border-indigo-600">
                            <option value="Goa">Goa</option>
                            <option value="Somnath">Somnath</option>
                            <option value="Mount Abu">Mount Abu</option>
                            <option value="Mumbai">Mumbai</option>
                            <option value="Ahmedabad">Ahmedabad</option>
                        </select>
                        <input type="number" required id="host-price" placeholder="Price / night (₹)" class="border border-gray-300 rounded-lg p-2 text-sm focus:outline-none focus:border-indigo-600">
                    </div>
                    <button type="submit" class="w-full bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-2 rounded-lg text-sm transition">Submit Property for Listing</button>
                </form>
            </div>

            <div class="bg-indigo-800 p-8 rounded-2xl border border-indigo-700">
                <h3 class="text-xl font-bold mb-4"><i class="fa-solid fa-chart-line text-yellow-400 mr-2"></i> How You Make Money (Zero Investment Strategy)</h3>
                <ol class="space-y-4 text-sm text-indigo-100 list-decimal list-inside">
                    <li><strong class="text-white">Partner with local hotel owners:</strong> Visit guest houses in Somnath, Mount Abu, or Goa. Ask them for lower direct rates.</li>
                    <li><strong class="text-white">List their rooms on StayHub:</strong> Post clean photos and price quotes with your 10%-15% commission margin included.</li>
                    <li><strong class="text-white">Collect advance payment:</strong> When a user books on your site, contact the hotel and confirm the booking instantly!</li>
                </ol>
            </div>
        </div>
    </section>

    <!-- Booking Modal -->
    <div id="booking-modal" class="fixed inset-0 bg-black/60 backdrop-blur-sm hidden z-50 flex justify-center items-center p-4">
        <div class="bg-white rounded-2xl max-w-md w-full p-6 relative shadow-2xl">
            <button onclick="closeBookingModal()" class="absolute top-4 right-4 text-gray-400 hover:text-gray-600">
                <i class="fa-solid fa-xmark text-xl"></i>
            </button>
            <h3 id="modal-prop-title" class="text-xl font-bold text-gray-900 mb-1">Confirm Booking</h3>
            <p id="modal-prop-city" class="text-sm text-gray-500 mb-4"></p>

            <form onsubmit="confirmBooking(event)" class="space-y-3">
                <div>
                    <label class="block text-xs font-semibold text-gray-600 mb-1">Full Name</label>
                    <input type="text" id="guest-name" required placeholder="John Doe" class="w-full border rounded-lg p-2 text-sm focus:border-indigo-600 focus:outline-none">
                </div>
                <div>
                    <label class="block text-xs font-semibold text-gray-600 mb-1">Phone Number (For WhatsApp Confirmation)</label>
                    <input type="tel" id="guest-phone" required placeholder="+91 9876543210" class="w-full border rounded-lg p-2 text-sm focus:border-indigo-600 focus:outline-none">
                </div>
                <div class="grid grid-cols-2 gap-2">
                    <div>
                        <label class="block text-xs font-semibold text-gray-600 mb-1">Check-in</label>
                        <input type="date" id="guest-checkin" required class="w-full border rounded-lg p-2 text-sm focus:border-indigo-600 focus:outline-none">
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-gray-600 mb-1">Check-out</label>
                        <input type="date" id="guest-checkout" required class="w-full border rounded-lg p-2 text-sm focus:border-indigo-600 focus:outline-none">
                    </div>
                </div>

                <div class="bg-gray-50 p-3 rounded-lg border mt-2">
                    <div class="flex justify-between text-sm font-semibold mb-1">
                        <span>Total Price:</span>
                        <span id="modal-total-price" class="text-indigo-600">₹0</span>
                    </div>
                    <p class="text-xs text-gray-500">Pay at Hotel or via UPI upon arrival.</p>
                </div>

                <button type="submit" class="w-full bg-emerald-600 hover:bg-emerald-700 text-white font-bold py-3 rounded-lg transition mt-4">
                    Confirm Reservation Now
                </button>
            </form>
        </div>
    </div>

    <!-- My Bookings Modal -->
    <div id="my-bookings-modal" class="fixed inset-0 bg-black/60 backdrop-blur-sm hidden z-50 flex justify-center items-center p-4">
        <div class="bg-white rounded-2xl max-w-lg w-full p-6 relative shadow-2xl max-h-[80vh] flex flex-col">
            <button onclick="toggleMyBookingsModal()" class="absolute top-4 right-4 text-gray-400 hover:text-gray-600">
                <i class="fa-solid fa-xmark text-xl"></i>
            </button>
            <h3 class="text-xl font-bold text-gray-900 mb-4"><i class="fa-solid fa-receipt text-indigo-600 mr-2"></i> Your Reserved Bookings</h3>
            
            <div id="bookings-list" class="overflow-y-auto space-y-3 flex-grow pr-2">
                <!-- Injected via Javascript -->
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer class="bg-gray-900 text-gray-400 py-8 text-center text-sm border-t border-gray-800">
        <p>© 2026 StayHub Rentals. Room bookings in Somnath, Goa, Mount Abu, Mumbai & Ahmedabad.</p>
    </footer>

    <!-- JavaScript Application Logic -->
    <script>
        // Sample Property Database
        const properties = [
            { id: 1, title: "Ocean Breeze Resort & Stay", city: "Goa", price: 1800, rating: 4.8, distance: "200m from Calangute Beach", image: "https://images.unsplash.com/photo-1540541338287-41700207dee6?auto=format&fit=crop&w=600&q=80" },
            { id: 2, title: "Somnath Temple View Guest House", city: "Somnath", price: 950, rating: 4.6, distance: "Walking distance to Temple", image: "https://images.unsplash.com/photo-1566073771259-6a8506099945?auto=format&fit=crop&w=600&q=80" },
            { id: 3, title: "Nakki Lake Hilltop Villa", city: "Mount Abu", price: 1400, rating: 4.7, distance: "1.2 km from Nakki Lake", image: "https://images.unsplash.com/photo-1582719478250-c89cae4dc85b?auto=format&fit=crop&w=600&q=80" },
            { id: 4, title: "Marine Drive Luxury Studio", city: "Mumbai", price: 2800, rating: 4.9, distance: "South Mumbai Coastal View", image: "https://images.unsplash.com/photo-1590490360182-c33d57733427?auto=format&fit=crop&w=600&q=80" },
            { id: 5, title: "Heritage Heritage Room Stay", city: "Ahmedabad", price: 1100, rating: 4.5, distance: "Near Sabarmati Riverfront", image: "https://images.unsplash.com/photo-1566665797739-1674de7a421a?auto=format&fit=crop&w=600&q=80" },
            { id: 6, title: "Baga Beach Backpackers Lodge", city: "Goa", price: 800, rating: 4.4, distance: "In Baga Market area", image: "https://images.unsplash.com/photo-1520250497591-112f2f40a3f4?auto=format&fit=crop&w=600&q=80" }
        ];

        let selectedProperty = null;

        // Render Property Cards
        function renderProperties(items) {
            const grid = document.getElementById('property-grid');
            grid.innerHTML = '';

            if (items.length === 0) {
                grid.innerHTML = `<div class="col-span-full text-center py-12 text-gray-500">No rooms found for this location. Try changing your search filters.</div>`;
                return;
            }

            items.forEach(prop => {
                const card = document.createElement('div');
                card.className = "bg-white rounded-xl overflow-hidden shadow-md hover:shadow-xl transition border border-gray-100 flex flex-col";
                card.innerHTML = `
                    <div class="relative h-48">
                        <img src="${prop.image}" alt="${prop.title}" class="w-full h-full object-cover">
                        <span class="absolute top-3 left-3 bg-white/90 backdrop-blur-md text-xs font-bold px-2.5 py-1 rounded-full text-indigo-700 shadow-sm">${prop.city}</span>
                        <span class="absolute top-3 right-3 bg-gray-900/80 text-white text-xs font-semibold px-2 py-1 rounded-md"><i class="fa-solid fa-star text-yellow-400 mr-1"></i>${prop.rating}</span>
                    </div>
                    <div class="p-4 flex-grow flex flex-col justify-between">
                        <div>
                            <h3 class="font-bold text-gray-900 text-lg mb-1">${prop.title}</h3>
                            <p class="text-xs text-gray-500 mb-3"><i class="fa-solid fa-location-dot mr-1 text-gray-400"></i>${prop.distance}</p>
                        </div>
                        <div class="flex items-center justify-between border-t pt-3 mt-2">
                            <div>
                                <span class="text-xl font-bold text-indigo-600">₹${prop.price}</span>
                                <span class="text-xs text-gray-500"> / night</span>
                            </div>
                            <button onclick="openBookingModal(${prop.id})" class="bg-indigo-600 hover:bg-indigo-700 text-white text-sm font-semibold px-4 py-2 rounded-lg transition">Reserve</button>
                        </div>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        // Filter Functionality
        function filterByCity(city) {
            document.getElementById('listings-title').innerText = city === 'All' ? 'Available Accommodations' : `Stays in ${city}`;
            document.getElementById('listings-subtitle').innerText = city === 'All' ? 'Showing properties for all locations' : `Showing properties in ${city}`;
            
            if (city === 'All') {
                renderProperties(properties);
            } else {
                const filtered = properties.filter(p => p.city.toLowerCase() === city.toLowerCase());
                renderProperties(filtered);
            }
        }

        function handleSearch() {
            const city = document.getElementById('search-city').value;
            filterByCity(city);
            document.getElementById('listings').scrollIntoView({ behavior: 'smooth' });
        }

        // Modal Controls
        function openBookingModal(propId) {
            selectedProperty = properties.find(p => p.id === propId);
            document.getElementById('modal-prop-title').innerText = selectedProperty.title;
            document.getElementById('modal-prop-city').innerText = `${selectedProperty.city} • ₹${selectedProperty.price}/night`;
            document.getElementById('modal-total-price').innerText = `₹${selectedProperty.price}`;
            document.getElementById('booking-modal').classList.remove('hidden');
        }

        function closeBookingModal() {
            document.getElementById('booking-modal').classList.add('hidden');
        }

        // Form Submit & LocalStorage
        function confirmBooking(event) {
            event.preventDefault();
            const booking = {
                id: Date.now(),
                title: selectedProperty.title,
                city: selectedProperty.city,
                price: selectedProperty.price,
                name: document.getElementById('guest-name').value,
                phone: document.getElementById('guest-phone').value,
                checkin: document.getElementById('guest-checkin').value
            };

            const existingBookings = JSON.parse(localStorage.getItem('stayhub_bookings') || '[]');
            existingBookings.push(booking);
            localStorage.setItem('stayhub_bookings', JSON.stringify(existingBookings));

            alert('🎉 Reservation Confirmed! We will contact you on WhatsApp shortly.');
            closeBookingModal();
        }

        function toggleMyBookingsModal() {
            const modal = document.getElementById('my-bookings-modal');
            const list = document.getElementById('bookings-list');
            
            if (modal.classList.contains('hidden')) {
                const bookings = JSON.parse(localStorage.getItem('stayhub_bookings') || '[]');
                if (bookings.length === 0) {
                    list.innerHTML = `<p class="text-center text-gray-500 py-6">No active bookings found.</p>`;
                } else {
                    list.innerHTML = bookings.map(b => `
                        <div class="border rounded-lg p-3 bg-gray-50 flex justify-between items-center">
                            <div>
                                <h4 class="font-bold text-sm text-gray-800">${b.title}</h4>
                                <p class="text-xs text-gray-500">Date: ${b.checkin} | Guest: ${b.name}</p>
                                <span class="text-xs font-semibold text-emerald-600">Reserved • ₹${b.price}</span>
                            </div>
                        </div>
                    `).join('');
                }
                modal.classList.remove('hidden');
            } else {
                modal.classList.add('hidden');
            }
        }

        function handleHostSubmit(e) {
            e.preventDefault();
            alert('Thank you! Your property submission was received. We will contact you soon.');
            document.getElementById('host-form').reset();
        }

        // Initial Load
        renderProperties(properties);
    </script>
</body>
</html>
