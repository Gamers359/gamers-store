<!DOCTYPE html>
<html lang="hi">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>GAmËRs - Official Gaming Store</title>
  
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" />
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@600;800;900&family=Rajdhani:wght@500;600;700&family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet" />

  <style>
    :root {
      --primary: #cce600; 
      --bg-dark: #0a0d16;
      --card-bg: #131826;
      --card-border: #1e263d;
      --text-main: #f8fafc;
      --text-muted: #94a3b8;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Inter', sans-serif; }
    body { background-color: var(--bg-dark); color: var(--text-main); padding-top: 65px; padding-bottom: 75px; }

    .top-bar { position: fixed; top: 0; left: 0; right: 0; height: 60px; background: #0e1320; border-bottom: 1px solid var(--card-border); display: flex; justify-content: space-between; align-items: center; padding: 0 15px; z-index: 100; }
    .brand-logo { font-family: 'Orbitron', sans-serif; font-size: 1.4rem; font-weight: 800; color: var(--text-main); }
    .brand-logo span { color: var(--primary); }
    
    .cart-wrapper { position: relative; cursor: pointer; }
    .cart-wrapper i { color: var(--primary); font-size: 1.3rem; }
    .cart-badge { position: absolute; top: -6px; right: -8px; background: #ef4444; color: white; font-size: 0.65rem; font-weight: bold; width: 16px; height: 16px; border-radius: 50%; display: flex; align-items: center; justify-content: center; }

    .hero-banner { text-align: center; padding: 25px 15px; border-bottom: 1px solid var(--card-border); background: #0c101c; }
    .hero-banner h1 { font-family: 'Rajdhani', sans-serif; font-size: 1.8rem; font-weight: 700; color: #fff; }
    .hero-banner p { color: var(--primary); font-size: 0.85rem; letter-spacing: 1px; }

    .container { max-width: 1000px; margin: 20px auto; padding: 0 15px; }
    .section-title { font-family: 'Rajdhani', sans-serif; font-size: 1.2rem; font-weight: 700; margin-bottom: 15px; color: var(--primary); display: flex; align-items: center; gap: 8px; }

    .product-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 18px; }
    .product-card { background: var(--card-bg); border: 1px solid var(--card-border); border-radius: 12px; padding: 14px; position: relative; display: flex; flex-direction: column; }
    
    .badge-deal { position: absolute; top: 12px; left: 12px; background: linear-gradient(135deg, #ff0055, #d90429); color: #fff; font-family: 'Rajdhani', sans-serif; font-weight: 700; font-size: 0.75rem; padding: 3px 8px; border-radius: 5px; z-index: 5; }
    .badge-digital { background: linear-gradient(135deg, #8b5cf6, #3b82f6); }

    .product-img { width: 100%; height: 190px; object-fit: cover; margin-bottom: 12px; border-radius: 8px; background: #080b12; }
    .item-title { font-size: 1.05rem; font-weight: 600; margin-bottom: 6px; }
    .item-desc { font-size: 0.8rem; color: var(--text-muted); margin-bottom: 10px; line-height: 1.3; flex: 1; }
    
    .price-row { display: flex; align-items: center; gap: 10px; margin-bottom: 12px; }
    .price { color: var(--primary); font-size: 1.4rem; font-weight: 700; font-family: 'Rajdhani', sans-serif; }
    .mrp { text-decoration: line-through; color: var(--text-muted); font-size: 0.85rem; }

    .btn-action { background: transparent; color: var(--primary); border: 1px solid var(--primary); width: 100%; padding: 10px; border-radius: 8px; font-weight: 600; cursor: pointer; text-transform: uppercase; margin-bottom: 6px; font-size: 0.85rem; }
    .btn-action:hover { background: var(--primary); color: #000; }
    .btn-buy { background: var(--primary); color: #000; border: none; }
    .btn-digital { background: linear-gradient(135deg, #f59e0b, #ea580c); color: #fff; border: none; }

    .bottom-nav { position: fixed; bottom: 0; left: 0; right: 0; height: 60px; background: #0e1320; border-top: 1px solid var(--card-border); display: flex; justify-content: space-around; align-items: center; z-index: 100; }
    .nav-item { display: flex; flex-direction: column; align-items: center; gap: 3px; color: var(--text-muted); font-size: 0.7rem; cursor: pointer; text-decoration: none; }
    .nav-item i { font-size: 1.1rem; }
    .nav-item.active { color: var(--primary); }

    .modal-overlay { display: none; position: fixed; inset: 0; background: rgba(0,0,0,0.88); z-index: 2000; justify-content: center; align-items: center; padding: 15px; }
    .modal-box { background: var(--card-bg); border: 1px solid var(--primary); border-radius: 12px; width: 100%; max-width: 420px; padding: 20px; color: var(--text-main); max-height: 90vh; overflow-y: auto; text-align: center; }
    .modal-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px; border-bottom: 1px solid var(--card-border); padding-bottom: 10px; }
    
    input { width: 100%; background: #090c14; border: 1px solid var(--card-border); color: #fff; padding: 10px; border-radius: 8px; margin-bottom: 10px; outline: none; font-size: 0.85rem; }
    input:focus { border-color: var(--primary); }

    .profile-avatar { width: 60px; height: 60px; background: var(--primary); color: #000; font-size: 1.8rem; border-radius: 50%; display: flex; align-items: center; justify-content: center; margin: 0 auto 10px; font-weight: bold; }
    .profile-row { display: flex; justify-content: space-between; padding: 10px 0; border-bottom: 1px solid var(--card-border); font-size: 0.9rem; }
    
    .pack-row { display: flex; justify-content: space-between; align-items: center; background: #090c14; border: 1px solid var(--card-border); padding: 12px; border-radius: 8px; margin-bottom: 8px; cursor: pointer; }
    .pack-row:hover { border-color: var(--primary); }

    .qr-container { background: #fff; padding: 10px; border-radius: 12px; display: inline-block; margin: 10px 0; }
    .qr-container img { width: 210px; height: 210px; object-fit: contain; display: block; }
    .upi-badge { background: #090c14; border: 1px dashed var(--primary); padding: 6px 12px; border-radius: 6px; font-size: 0.85rem; color: var(--primary); margin-bottom: 10px; display: inline-block; }
  </style>
</head>
<body>

  <div class="top-bar">
    <div class="brand-logo">GAm<span>ËRs</span></div>
    <div class="cart-wrapper" id="topCartBtn">
      <i class="fa-solid fa-cart-shopping"></i>
      <span class="cart-badge" id="cartCount">0</span>
    </div>
  </div>

  <div class="hero-banner">
    <h1 id="userGreeting">GAmËRs Official Store</h1>
    <p>Scan & Pay Instant UPI Checkout</p>
  </div>

  <div class="container">
    <div class="section-title"><i class="fa-solid fa-fire"></i> Best Selling Gears</div>
    <div class="product-grid">

      <!-- ITEM 1: Mouse -->
      <div class="product-card">
        <span class="badge-deal">50% OFF</span>
        <img src="https://images.unsplash.com/photo-1615663245857-ac93bb7c39e7?auto=format&fit=crop&w=600&q=80" class="product-img" alt="Mouse">
        <div class="item-title">GEONIX Vigor R7 Gaming Mouse</div>
        <p class="item-desc">1200 DPI Optical Sensor, Breathing RGB Lights, 1.35m PVC Cable.</p>
        <div class="price-row"><span class="price">₹299</span><span class="mrp">₹599</span></div>
        <button class="btn-action btn-add-cart" data-name="GEONIX Vigor R7 Mouse" data-price="299">Add to Cart</button>
        <button class="btn-action btn-buy btn-direct-buy" data-name="GEONIX Vigor R7 Mouse" data-price="299">Buy Now</button>
      </div>

      <!-- ITEM 2: Sleeves -->
      <div class="product-card">
        <span class="badge-deal">87% OFF</span>
        <img src="https://images.unsplash.com/photo-1592840496073-e70ba6566a5e?auto=format&fit=crop&w=600&q=80" class="product-img" alt="Sleeves">
        <div class="item-title">Gaming Finger Sleeves (3 Pairs)</div>
        <p class="item-desc">Sweat-proof carbon fiber sleeves for smooth control in mobile shooting games.</p>
        <div class="price-row"><span class="price">₹129</span><span class="mrp">₹999</span></div>
        <button class="btn-action btn-add-cart" data-name="Gaming Finger Sleeves" data-price="129">Add to Cart</button>
        <button class="btn-action btn-buy btn-direct-buy" data-name="Gaming Finger Sleeves" data-price="129">Buy Now</button>
      </div>

      <!-- ITEM 3: Mousepad -->
      <div class="product-card">
        <span class="badge-deal">45% OFF</span>
        <img src="https://images.unsplash.com/photo-1618384887929-16ec33fab9ef?auto=format&fit=crop&w=600&q=80" class="product-img" alt="Mousepad">
        <div class="item-title">Extended Speed Gaming Mousepad</div>
        <p class="item-desc">Large non-slip rubber base for stable aim, fast flick movements.</p>
        <div class="price-row"><span class="price">₹249</span><span class="mrp">₹499</span></div>
        <button class="btn-action btn-add-cart" data-name="Speed Mousepad" data-price="249">Add to Cart</button>
        <button class="btn-action btn-buy btn-direct-buy" data-name="Speed Mousepad" data-price="249">Buy Now</button>
      </div>

      <!-- ITEM 4: Earphones -->
      <div class="product-card">
        <span class="badge-deal">55% OFF</span>
        <img src="https://images.unsplash.com/photo-1590658268037-6bf12165a8df?auto=format&fit=crop&w=600&q=80" class="product-img" alt="Earphones">
        <div class="item-title">Wired In-Ear Gaming Earphones</div>
        <p class="item-desc">Deep in-game footstep audio clarity with low-latency microphone.</p>
        <div class="price-row"><span class="price">₹399</span><span class="mrp">₹899</span></div>
        <button class="btn-action btn-add-cart" data-name="Gaming Earphones" data-price="399">Add to Cart</button>
        <button class="btn-action btn-buy btn-direct-buy" data-name="Gaming Earphones" data-price="399">Buy Now</button>
      </div>

      <!-- ITEM 5: Triggers -->
      <div class="product-card">
        <span class="badge-deal">60% OFF</span>
        <img src="https://images.unsplash.com/photo-1550745165-9bc0b252726f?auto=format&fit=crop&w=600&q=80" class="product-img" alt="Triggers">
        <div class="item-title">4-Finger Metal Mobile Triggers</div>
        <p class="item-desc">Alloy metal trigger locks for instant firing without touch delay.</p>
        <div class="price-row"><span class="price">₹199</span><span class="mrp">₹499</span></div>
        <button class="btn-action btn-add-cart" data-name="Metal Triggers" data-price="199">Add to Cart</button>
        <button class="btn-action btn-buy btn-direct-buy" data-name="Metal Triggers" data-price="199">Buy Now</button>
      </div>

      <!-- ITEM 6: Cooler -->
      <div class="product-card">
        <span class="badge-deal">40% OFF</span>
        <img src="https://images.unsplash.com/photo-1587202372775-e229f172b9d7?auto=format&fit=crop&w=600&q=80" class="product-img" alt="Cooler">
        <div class="item-title">Clip-on Mobile Cooling Fan</div>
        <p class="item-desc">High RPM cooling fan prevents phone throttling during heavy matches.</p>
        <div class="price-row"><span class="price">₹449</span><span class="mrp">₹799</span></div>
        <button class="btn-action btn-add-cart" data-name="Phone Cooler" data-price="449">Add to Cart</button>
        <button class="btn-action btn-buy btn-direct-buy" data-name="Phone Cooler" data-price="449">Buy Now</button>
      </div>

      <!-- ITEM 7: BGMI UC -->
      <div class="product-card" style="border-color: #f59e0b;">
        <span class="badge-deal badge-digital">DIGITAL</span>
        <img src="https://images.unsplash.com/photo-1542751371-adc38448a05e?auto=format&fit=crop&w=600&q=80" class="product-img" alt="BGMI">
        <div class="item-title">BGMI UC Top-up</div>
        <p class="item-desc">Direct Character ID top-up. Packs from 60 UC to 1800 UC.</p>
        <div class="price-row"><span class="price" style="color: #f59e0b;">Starting ₹30</span></div>
        <button class="btn-action btn-digital" id="btnOpenBgmi">Select UC Pack</button>
      </div>

      <!-- ITEM 8: Free Fire -->
      <div class="product-card" style="border-color: #ef4444;">
        <span class="badge-deal badge-digital">DIGITAL</span>
        <img src="https://images.unsplash.com/photo-1538481199705-c710c4e965fc?auto=format&fit=crop&w=600&q=80" class="product-img" alt="Free Fire">
        <div class="item-title">Free Fire Diamonds (80% OFF)</div>
        <p class="item-desc">Direct Player UID top-up with automatic discount applied.</p>
        <div class="price-row"><span class="price" style="color: #ef4444;">Starting ₹16</span></div>
        <button class="btn-action btn-digital" id="btnOpenFf">Select Diamond Pack</button>
      </div>

    </div>
  </div>

  <div class="bottom-nav">
    <div class="nav-item active"><i class="fa-solid fa-gamepad"></i><span>Store</span></div>
    <div class="nav-item" id="navCartBtn"><i class="fa-solid fa-cart-shopping"></i><span>Cart</span></div>
    <div class="nav-item" id="navProfileBtn"><i class="fa-solid fa-user"></i><span id="navUserLabel">Profile</span></div>
  </div>

  <!-- QR SCANNER / PAYMENT MODAL -->
  <div class="modal-overlay" id="paymentModal">
    <div class="modal-box">
      <div class="modal-header">
        <h3 id="payModalTitle" style="font-size: 1.1rem; color: #fff;">Scan & Pay</h3>
        <i class="fa-solid fa-xmark close-btn" data-target="paymentModal" style="cursor:pointer;"></i>
      </div>
      
      <p style="font-size: 0.85rem; color: var(--text-muted);">Payable Amount:</p>
      <h2 id="payModalAmount" style="color: var(--primary); font-family: 'Rajdhani', sans-serif; font-size: 2rem; margin: 4px 0 6px;">₹0</h2>
      
      <div class="upi-badge">UPI ID: <strong>bgmiitoo@fam</strong></div>
      
      <div class="qr-container">
        <img id="upiQrCodeImg" src="" alt="UPI QR Code" />
      </div>

      <p style="font-size: 0.78rem; color: var(--text-muted); margin-bottom: 12px;">FamPay / GPay / PhonePe / Paytm se scan karein</p>
      
      <a id="directUpiAppBtn" href="#" class="btn-action btn-buy" style="display: block; text-decoration: none; margin-bottom: 14px;">⚡ Pay Directly in UPI App</a>

      <div style="text-align: left; background: #090c14; padding: 12px; border-radius: 8px; border: 1px solid var(--card-border); margin-bottom: 10px;">
        <label style="font-size:0.75rem; color:var(--text-muted);">Aapka Naam</label>
        <input type="text" id="orderCustName" placeholder="Full Name" />
        <label style="font-size:0.75rem; color:var(--text-muted);">Mobile Number</label>
        <input type="tel" id="orderCustPhone" placeholder="Mobile Number" />
        <label style="font-size:0.75rem; color:var(--text-muted);">Address / Delivery Details</label>
        <input type="text" id="orderCustAddr" placeholder="Street, City, Pincode" />
        <label style="font-size:0.75rem; color:var(--text-muted);">12-digit UPI / UTR Transaction ID</label>
        <input type="text" id="utrNumberInp" placeholder="Enter UTR Reference No." />
      </div>

      <button id="submitPayBtn" class="btn-action" style="border-color: #22c55e; color: #22c55e; padding: 12px;">Confirm & Send Order</button>
    </div>
  </div>

  <!-- PROFILE MODAL -->
  <div class="modal-overlay" id="profileModal">
    <div class="modal-box" style="text-align: left;">
      <div class="modal-header">
        <h3>User Profile</h3>
        <i class="fa-solid fa-xmark close-btn" data-target="profileModal" style="cursor:pointer;"></i>
      </div>
      <div style="text-align: center; margin-bottom: 15px;">
        <div class="profile-avatar" id="avatarInitial">G</div>
        <h2 id="dispName">Gamer</h2>
      </div>
      <div class="profile-row"><span>Mobile:</span><strong id="dispPhone">-</strong></div>
      <div class="profile-row"><span>Address:</span><span id="dispAddress" style="text-align:right; max-width:200px;">-</span></div>
      <button class="btn-action" id="btnEditProfile" style="margin-top:20px;">Edit Profile</button>
      <button class="btn-action" id="btnLogoutUser" style="color:#ef4444; border-color:#ef4444;">Logout / Clear</button>
    </div>
  </div>

  <!-- EDIT PROFILE MODAL -->
  <div class="modal-overlay" id="editProfileModal">
    <div class="modal-box" style="text-align: left;">
      <div class="modal-header">
        <h3>Save Details</h3>
        <i class="fa-solid fa-xmark close-btn" data-target="editProfileModal" style="cursor:pointer;"></i>
      </div>
      <label style="font-size:0.8rem; color:var(--text-muted);">Name</label>
      <input type="text" id="profInpName" placeholder="Aapka Naam" />
      <label style="font-size:0.8rem; color:var(--text-muted);">Phone Number</label>
      <input type="tel" id="profInpPhone" placeholder="10-digit Mobile" />
      <label style="font-size:0.8rem; color:var(--text-muted);">Delivery Address</label>
      <input type="text" id="profInpAddress" placeholder="Address, City, Pincode" />
      <button class="btn-action btn-buy" id="btnSaveProfile">Save Details</button>
    </div>
  </div>

  <!-- DIGITAL ITEM MODAL -->
  <div class="modal-overlay" id="digitalModal">
    <div class="modal-box" style="text-align: left;">
      <div class="modal-header">
        <h3 id="digitalModalTitle">Top-up Packs</h3>
        <i class="fa-solid fa-xmark close-btn" data-target="digitalModal" style="cursor:pointer;"></i>
      </div>
      <label style="font-size:0.8rem; color:var(--text-muted);">Game UID</label>
      <input type="text" id="gameUID" placeholder="Enter Character ID" />
      <div id="digitalPacksList"></div>
    </div>
  </div>

  <!-- CART MODAL -->
  <div class="modal-overlay" id="cartModal">
    <div class="modal-box" style="text-align: left;">
      <div class="modal-header">
        <h3>Your Cart</h3>
        <i class="fa-solid fa-xmark close-btn" data-target="cartModal" style="cursor:pointer;"></i>
      </div>
      <div id="cartList" style="margin-bottom:15px; max-height:220px; overflow-y:auto;"></div>
      <div style="display:flex; justify-content:space-between; font-weight:bold; font-size:1.2rem; border-top:1px solid var(--card-border); padding-top:10px; margin-bottom:15px;">
        <span>Total:</span>
        <span style="color:var(--primary);">₹<span id="cartTotalVal">0</span></span>
      </div>
      <button class="btn-action btn-buy" id="btnProceedCartPay">Proceed to Pay</button>
    </div>
  </div>

  <script>
    document.addEventListener("DOMContentLoaded", function () {
      let cart = [];
      const UPI_ID = "bgmiitoo@fam";
      const OWNER_PHONE = "916201143946";
      let pendingOrder = null;

      function getSavedUser() {
        try {
          return JSON.parse(localStorage.getItem('gamer_profile')) || null;
        } catch(e) {
          return null;
        }
      }

      function syncProfileUI() {
        const u = getSavedUser();
        if(u && u.name) {
          document.getElementById('userGreeting').innerText = `Welcome, ${u.name}!`;
          document.getElementById('navUserLabel').innerText = u.name.split(' ')[0];
          document.getElementById('dispName').innerText = u.name;
          document.getElementById('avatarInitial').innerText = u.name.charAt(0).toUpperCase();
          document.getElementById('dispPhone').innerText = u.phone || '-';
          document.getElementById('dispAddress').innerText = u.address || '-';
        } else {
          document.getElementById('userGreeting').innerText = "GAmËRs Official Store";
          document.getElementById('navUserLabel').innerText = "Profile";
        }
      }

      function openModal(id) {
        document.getElementById(id).style.display = 'flex';
      }

      function closeModal(id) {
        document.getElementById(id).style.display = 'none';
      }

      document.querySelectorAll('.close-btn').forEach(btn => {
        btn.addEventListener('click', function() {
          closeModal(this.getAttribute('data-target'));
        });
      });

      document.getElementById('navProfileBtn').addEventListener('click', function() {
        if(getSavedUser()) {
          openModal('profileModal');
        } else {
          openEditProfile();
        }
      });

      function openEditProfile() {
        closeModal('profileModal');
        const u = getSavedUser() || {};
        document.getElementById('profInpName').value = u.name || '';
        document.getElementById('profInpPhone').value = u.phone || '';
        document.getElementById('profInpAddress').value = u.address || '';
        openModal('editProfileModal');
      }

      document.getElementById('btnEditProfile').addEventListener('click', openEditProfile);

      document.getElementById('btnSaveProfile').addEventListener('click', function() {
        const name = document.getElementById('profInpName').value.trim();
        const phone = document.getElementById('profInpPhone').value.trim();
        const address = document.getElementById('profInpAddress').value.trim();
        if(!name || phone.length < 10) return alert("Kripya apna naam aur phone number bharein.");
        localStorage.setItem('gamer_profile', JSON.stringify({ name, phone, address }));
        closeModal('editProfileModal');
        syncProfileUI();
        alert("Profile save ho gaya!");
      });

      document.getElementById('btnLogoutUser').addEventListener('click', function() {
        localStorage.removeItem('gamer_profile');
        closeModal('profileModal');
        syncProfileUI();
      });

      document.querySelectorAll('.btn-add-cart').forEach(btn => {
        btn.addEventListener('click', function() {
          const title = this.getAttribute('data-name');
          const price = parseInt(this.getAttribute('data-price'));
          cart.push({ title, price });
          document.getElementById('cartCount').innerText = cart.length;
          alert(`${title} cart me jud gaya!`);
        });
      });

      function openCartModal() {
        const container = document.getElementById('cartList');
        let total = 0;
        if(cart.length === 0) {
          container.innerHTML = "<p style='color:var(--text-muted); text-align:center;'>Cart khali hai</p>";
        } else {
          container.innerHTML = cart.map((c) => {
            total += c.price;
            return `<div style="display:flex; justify-content:space-between; padding:8px 0; border-bottom:1px solid #1e263d;">
              <span>${c.title}</span><strong>₹${c.price}</strong>
            </div>`;
          }).join('');
        }
        document.getElementById('cartTotalVal').innerText = total;
        openModal('cartModal');
      }

      document.getElementById('topCartBtn').addEventListener('click', openCartModal);
      document.getElementById('navCartBtn').addEventListener('click', openCartModal);

      function initiatePayment(itemName, amount) {
        pendingOrder = { itemName, amount };
        document.getElementById('payModalTitle').innerText = itemName;
        document.getElementById('payModalAmount').innerText = `₹${amount}`;
        
        const u = getSavedUser() || {};
        document.getElementById('orderCustName').value = u.name || '';
        document.getElementById('orderCustPhone').value = u.phone || '';
        document.getElementById('orderCustAddr').value = u.address || '';
        
        const upiUri = `upi://pay?pa=${UPI_ID}&pn=GAmERs&am=${amount}&cu=INR&tn=${encodeURIComponent(itemName)}`;
        document.getElementById('directUpiAppBtn').href = upiUri;

        const dynamicQr = `https://api.qrserver.com/v1/create-qr-code/?size=250x250&data=${encodeURIComponent(upiUri)}`;
        document.getElementById('upiQrCodeImg').src = dynamicQr;

        openModal('paymentModal');
      }

      document.querySelectorAll('.btn-direct-buy').forEach(btn => {
        btn.addEventListener('click', function() {
          const name = this.getAttribute('data-name');
          const price = parseInt(this.getAttribute('data-price'));
          initiatePayment(name, price);
        });
      });

      document.getElementById('btnProceedCartPay').addEventListener('click', function() {
        if(cart.length === 0) return alert("Cart khali hai!");
        const total = parseInt(document.getElementById('cartTotalVal').innerText);
        const items = cart.map(c => c.title).join(", ");
        closeModal('cartModal');
        initiatePayment(items, total);
      });

      document.getElementById('submitPayBtn').addEventListener('click', function() {
        const name = document.getElementById('orderCustName').value.trim();
        const phone = document.getElementById('orderCustPhone').value.trim();
        const address = document.getElementById('orderCustAddr').value.trim();
        const utr = document.getElementById('utrNumberInp').value.trim();

        if(!name || phone.length < 10) return alert("Kripya apna naam aur phone number bharein.");
        if(utr.length < 6) return alert("Kripya payment ke baad UTR Ref number daalein.");

        const msg = `*NEW ORDER RECEIVED*\n\n` +
                    `*Item:* ${pendingOrder.itemName}\n` +
                    `*Amount:* ₹${pendingOrder.amount}\n` +
                    `*Customer:* ${name}\n` +
                    `*Phone:* ${phone}\n` +
                    `*Address:* ${address || 'N/A'}\n` +
                    `*UTR Ref No:* ${utr}\n` +
                    `*Status:* Payment Submitted`;

        const waUrl = `https://wa.me/${OWNER_PHONE}?text=${encodeURIComponent(msg)}`;
        window.open(waUrl, '_blank');

        alert("Order details submit ho gayi hain!");
        document.getElementById('utrNumberInp').value = '';
        closeModal('paymentModal');
        cart = [];
        document.getElementById('cartCount').innerText = 0;
      });

      document.getElementById('btnOpenBgmi').addEventListener('click', function() {
        document.getElementById('digitalModalTitle').innerText = "BGMI UC Packs";
        const inp = document.getElementById('gameUID');
        inp.value = '';
        inp.placeholder = "Enter Character ID (e.g. 512345678)";
        
        document.getElementById('digitalPacksList').innerHTML = `
          <div class="pack-row" data-pack="BGMI 60 UC" data-price="30"><span>60 UC</span><strong>₹30</strong></div>
          <div class="pack-row" data-pack="BGMI 300 UC" data-price="180"><span>300 UC</span><strong>₹180</strong></div>
          <div class="pack-row" data-pack="BGMI 1800 UC" data-price="1200"><span>1800 UC</span><strong>₹1200</strong></div>
        `;
        attachDigitalEvents();
        openModal('digitalModal');
      });

      document.getElementById('btnOpenFf').addEventListener('click', function() {
        document.getElementById('digitalModalTitle').innerText = "Free Fire Diamond Packs";
        const inp = document.getElementById('gameUID');
        inp.value = '';
        inp.placeholder = "Enter Player UID (e.g. 123456789)";
        
        document.getElementById('digitalPacksList').innerHTML = `
          <div class="pack-row" data-pack="FF 100 Diamonds" data-price="16"><span>100 Diamonds</span><strong>₹16</strong></div>
          <div class="pack-row" data-pack="FF 310 Diamonds" data-price="50"><span>310 Diamonds</span><strong>₹50</strong></div>
          <div class="pack-row" data-pack="FF 520 Diamonds" data-price="80"><span>520 Diamonds</span><strong>₹80</strong></div>
          <div class="pack-row" data-pack="FF 1060 Diamonds" data-price="160"><span>1060 Diamonds</span><strong>₹160</strong></div>
          <div class="pack-row" data-pack="FF 2180 Diamonds" data-price="320"><span>2180 Diamonds</span><strong>₹320</strong></div>
        `;
        attachDigitalEvents();
        openModal('digitalModal');
      });

      function attachDigitalEvents() {
        document.querySelectorAll('.pack-row').forEach(row => {
          row.addEventListener('click', function() {
            const uid = document.getElementById('gameUID').value.trim();
            if(uid.length < 5) return alert("Pehle valid Game UID daalein.");
            const packName = this.getAttribute('data-pack');
            const price = parseInt(this.getAttribute('data-price'));
            closeModal('digitalModal');
            initiatePayment(`${packName} (UID: ${uid})`, price);
          });
        });
      }

      syncProfileUI();
    });
  </script>
</body>
</html>
