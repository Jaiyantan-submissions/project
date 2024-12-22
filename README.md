# Project Responsive Web Design using Bootstrap
# Date: 7/12/2024
# AIM:
To create a simplified clone of Dribbble (https://dribbble.com/) landing page.

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Insert the necessary CSS and JavaScript files as external in order to use Bootstrap.

## Step 5:
Create a HTML file and include the needed Bootstrap components.

## Step 6:
Publish the website in the LocalHost.

# PROGRAM :

# HOME PAGE:
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Dribbble Clone</title>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
        <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&family=Poppins:wght@300;600&display=swap" rel="stylesheet">
        <style>
            body {
                background: linear-gradient(135deg, #ff7eb3, #ff758c);
                font-family: 'Montserrat', sans-serif;
                color: #333;
            }
            .navbar {
                background: rgba(255, 255, 255, 0.9);
                backdrop-filter: blur(10px);
                box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            }
            .navbar-brand {
                font-weight: bold;
                font-size: 1.5rem;
                color: #ff758c;
            }
            .card {
                border: none;
                border-radius: 20px;
                overflow: hidden;
                background: #fff;
                box-shadow: 0 6px 15px rgba(0, 0, 0, 0.1);
                transition: transform 0.4s, box-shadow 0.4s;
            }
            .card img {
                max-height: 220px;
                object-fit: cover;
                cursor: pointer;
            }
            .card:hover {
                transform: translateY(-10px);
                box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            }
            .gallery-title {
                font-family: 'Poppins', sans-serif;
                font-size: 2.8rem;
                text-align: center;
                color: #fff;
                margin: 40px 0;
            }
            .filter-bar {
                text-align: center;
                margin: 30px 0;
            }
            .filter-bar button {
                background: #fff;
                color: #ff758c;
                border: 2px solid #ff758c;
                border-radius: 20px;
                padding: 10px 20px;
                font-weight: bold;
                margin: 5px;
                transition: background 0.3s, color 0.3s;
            }
            .filter-bar button:hover {
                background: #ff758c;
                color: #fff;
            }
            footer {
                background: #ff758c;
                color: #fff;
                text-align: center;
                padding: 20px;
                font-family: 'Poppins', sans-serif;
            }
            .modal-content {
                border-radius: 10px;
                overflow: hidden;
                max-width: 90%;
                max-height: 90%;
            }
            .modal img {
                width: 100%;
                height: auto;
                border-radius: 10px;
                box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
                transition: transform 0.3s;
            }
            .modal img:hover {
                transform: scale(1.05);
            }
            .contact-section {
                background: #fff;
                padding: 40px;
                border-radius: 10px;
                box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
                margin-top: 50px;
            }
            .contact-section h2 {
                font-family: 'Poppins', sans-serif;
                font-size: 2.5rem;
                margin-bottom: 20px;
                color: #333;
            }
            .contact-section p {
                font-size: 1rem;
                margin-bottom: 20px;
            }
        </style>
    </head>
    <body>
        <!-- Navbar -->
        <nav class="navbar navbar-expand-lg">
            <div class="container">
                <a class="navbar-brand" href="#">Dribbble Clone</a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarNav">
                    <ul class="navbar-nav ms-auto">
                        <li class="nav-item"><a class="nav-link" href="#gallery">Gallery</a></li>
                        <li class="nav-item"><a class="nav-link" href="#about">About</a></li>
                        <li class="nav-item"><a class="nav-link" href="#contact">Contact</a></li>
                    </ul>
                    <div class="ms-3">
                        <a href="login.html" class="btn btn-outline-danger">Login</a>
                        <a href="signup.html" class="btn btn-danger">Sign Up</a>
                    </div>
                </div>
            </div>
        </nav>

        <!-- Gallery Title -->
        <div class="gallery-title">Discover Creative Shots</div>

        <!-- Filter Bar -->
        <div class="filter-bar">
            <button class="btn">All</button>
            <button class="btn">UI Design</button>
            <button class="btn">Graphic Design</button>
            <button class="btn">Illustrations</button>
        </div>

        <!-- Gallery Section -->
        <div class="container">
            <div id="gallery" class="row g-4">
                <!-- Dynamically Generated Cards -->
            </div>
        </div>

        <!-- Lightbox Modal -->
        <div class="modal fade" id="lightboxModal" tabindex="-1" aria-labelledby="lightboxModalLabel" aria-hidden="true">
            <div class="modal-dialog modal-dialog-centered modal-lg">
                <div class="modal-content">
                    <div class="modal-body text-center">
                        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                        <img id="lightboxImage" src="" alt="Zoomed Image">
                    </div>
                    <div class="modal-footer justify-content-between">
                        <button class="btn btn-secondary" id="prevButton" onclick="navigateLightbox(-1)">Previous</button>
                        <button class="btn btn-secondary" id="nextButton" onclick="navigateLightbox(1)">Next</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Pagination -->
        <nav aria-label="Page navigation" class="mt-4">
            <ul class="pagination justify-content-center">
                <li class="page-item"><button class="page-link" id="prevGalleryPage" onclick="changePage(-1)" disabled>Previous</button></li>
                <li class="page-item"><button class="page-link" id="nextGalleryPage" onclick="changePage(1)">Next</button></li>
            </ul>
        </nav>

        <!-- About Section -->
        <div class="container my-5" id="about">
            <div class="p-4 bg-light shadow rounded">
                <h2>About Us</h2>
                <p>We are a creative hub for designers to share their artwork, inspire others, and connect with a global community. Explore, collaborate, and grow with us.</p>
                <p>Our platform offers a seamless way to showcase your talent and receive valuable feedback from industry experts and fellow creatives. Whether you're a budding designer or a seasoned professional, you'll find a supportive environment here.</p>
                <p>Beyond a gallery, we provide opportunities for learning through tutorials, challenges, and collaborations. Join us and be part of a vibrant, inspiring community that celebrates the beauty of design.</p>
            </div>
        </div>

        <!-- Contact Section -->
        <div class="container my-5" id="contact">
            <div class="contact-section">
                <h2>Contact Us</h2>
                <p>Have questions, feedback, or just want to say hello? We'd love to hear from you!</p>
                <form>
                    <div class="mb-3">
                        <label for="name" class="form-label">Name</label>
                        <input type="text" class="form-control" id="name" placeholder="Your Name">
                    </div>
                    <div class="mb-3">
                        <label for="email" class="form-label">Email</label>
                        <input type="email" class="form-control" id="email" placeholder="Your Email">
                    </div>
                    <div class="mb-3">
                        <label for="message" class="form-label">Message</label>
                        <textarea class="form-control" id="message" rows="5" placeholder="Your Message"></textarea>
                    </div>
                    <button type="submit" class="btn btn-danger">Submit</button>
                </form>
            </div>
        </div>

        <!-- Footer -->
        <footer>
            <p>&copy; 2024 Dribbble Clone. Built with creativity and passion.</p>
        </footer>

        <!-- Bootstrap JS -->
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>

        <script>
        const cardsData = [
        { title: "Project 1", designer: "Designer 1", likes: 1200, views: 300, imgSrc: "download.jpeg" },
        { title: "Project 2", designer: "Designer 2", likes: 1400, views: 450, imgSrc: "2.jpeg" },
        { title: "Project 3", designer: "Designer 3", likes: 2000, views: 600, imgSrc: "3.jpeg" },
        { title: "Project 4", designer: "Designer 4", likes: 1200, views: 300, imgSrc: "4.jpeg" },
        { title: "Project 5", designer: "Designer 5", likes: 1400, views: 450, imgSrc: "5.jpeg" },
        { title: "Project 6", designer: "Designer 6", likes: 2000, views: 600, imgSrc: "6.jpeg" },
        { title: "Project 7", designer: "Designer 7", likes: 1200, views: 300, imgSrc: "7.jpeg" },
        { title: "Project 8", designer: "Designer 8", likes: 1400, views: 450, imgSrc: "8.jpeg" },
        { title: "Project 9", designer: "Designer 9", likes: 2000, views: 600, imgSrc: "9.jpeg" },
        { title: "Project 10", designer: "Designer 10", likes: 1200, views: 300, imgSrc: "10.jpeg" },
        { title: "Project 11", designer: "Designer 11", likes: 1400, views: 450, imgSrc: "11.jpeg" },
        { title: "Project 12", designer: "Designer 12", likes: 2000, views: 600, imgSrc: "12.jpeg" },
        { title: "Project 13", designer: "Designer 13", likes: 1200, views: 300, imgSrc: "13.jpeg" },
        { title: "Project 14", designer: "Designer 14", likes: 1400, views: 450, imgSrc: "14.jpeg" },
        { title: "Project 15", designer: "Designer 15", likes: 2000, views: 600, imgSrc: "15.jpeg" },
        { title: "Project 16", designer: "Designer 16", likes: 1200, views: 300, imgSrc: "16.jpeg" },
        { title: "Project 17", designer: "Designer 17", likes: 1400, views: 450, imgSrc: "17.jpeg" },
        { title: "Project 18", designer: "Designer 18", likes: 2000, views: 600, imgSrc: "18.jpeg" },

        // Add more cards with unique images
    ];


            let currentImageIndex = 0;
            const lightboxImages = [];
            let currentPage = 0;
            const pageSize = 9;

            function loadCards() {
                const gallery = document.getElementById('gallery');
                gallery.innerHTML = '';

                const start = currentPage * pageSize;
                const end = start + pageSize;
                const currentCards = cardsData.slice(start, end);

                currentCards.forEach((card, index) => {
                    lightboxImages.push(card.imgSrc);
                    const cardHTML = `
                        <div class="col-md-4">
                            <div class="card">
                                <img src="${card.imgSrc}" alt="${card.title}" onclick="openLightbox(${start + index})">
                                <div class="card-body">
                                    <h5>${card.title}</h5>
                                    <p>by ${card.designer}</p>
                                    <p>❤️ ${card.likes} 👁️ ${card.views}</p>
                                </div>
                            </div>
                        </div>
                    `;
                    gallery.insertAdjacentHTML('beforeend', cardHTML);
                });

                document.getElementById('prevGalleryPage').disabled = currentPage === 0;
                document.getElementById('nextGalleryPage').disabled = end >= cardsData.length;
            }

            function changePage(direction) {
                currentPage += direction;
                loadCards();
            }

            function openLightbox(index) {
                currentImageIndex = index;
                document.getElementById('lightboxImage').src = lightboxImages[currentImageIndex];
                const lightboxModal = new bootstrap.Modal(document.getElementById('lightboxModal'));
                lightboxModal.show();
            }

            function navigateLightbox(step) {
                currentImageIndex = (currentImageIndex + step + lightboxImages.length) % lightboxImages.length;
                document.getElementById('lightboxImage').src = lightboxImages[currentImageIndex];
            }

            document.addEventListener('DOMContentLoaded', loadCards);
        </script>
    </body>
    </html>



# LOGIN PAGE:
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Login Page</title>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
        <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&display=swap" rel="stylesheet">
        <style>
            body {
                margin: 0;
                padding: 0;
                background: radial-gradient(circle, #4b79a1, #283e51);
                min-height: 100vh;
                display: flex;
                justify-content: center;
                align-items: center;
                font-family: 'Poppins', sans-serif;
            }
            .login-card {
                backdrop-filter: blur(10px);
                background: rgba(255, 255, 255, 0.1);
                border-radius: 15px;
                box-shadow: 0 8px 32px rgba(0, 0, 0, 0.37);
                width: 100%;
                max-width: 400px;
                padding: 2rem;
                color: #fff;
            }
            .login-card h2 {
                text-align: center;
                font-size: 1.8rem;
                font-weight: bold;
                margin-bottom: 1.5rem;
            }
            .form-control {
                background: rgba(255, 255, 255, 0.2);
                color: #fff;
                border: 1px solid rgba(255, 255, 255, 0.3);
                border-radius: 8px;
            }
            .form-control:focus {
                box-shadow: none;
                border-color: #6c63ff;
                background: rgba(255, 255, 255, 0.3);
            }
            .btn-primary {
                background: linear-gradient(90deg, #6c63ff, #3a3dff);
                border: none;
                font-weight: bold;
                padding: 0.8rem;
                border-radius: 8px;
            }
            .btn-primary:hover {
                background: linear-gradient(90deg, #3a3dff, #6c63ff);
            }
            .text-center a {
                color: #6c63ff;
                text-decoration: none;
                font-weight: 600;
            }
            .text-center a:hover {
                text-decoration: underline;
            }
        </style>
    </head>
    <body>
        <div class="login-card">
            <h2>Login</h2>
            <form>
                <div class="mb-3">
                    <label for="email" class="form-label">Email Address</label>
                    <input type="email" id="email" class="form-control" placeholder="Enter your email" required>
                </div>
                <div class="mb-3">
                    <label for="password" class="form-label">Password</label>
                    <input type="password" id="password" class="form-control" placeholder="Enter your password" required>
                </div>
                <div class="d-flex justify-content-between align-items-center">
                    <div>
                        <input type="checkbox" id="rememberMe">
                        <label for="rememberMe" class="form-label">Remember me</label>
                    </div>
                    <a href="#" class="text-decoration-none">Forgot Password?</a>
                </div>
                <button type="submit" class="btn btn-primary w-100 mt-4">Login</button>
            </form>
            <div class="text-center mt-3">
                <span>Don't have an account? <a href="signup.html" target="_blank">Sign Up</a></span>
            </div>
        </div>

        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    </body>
    </html>


# SIGN UP PAGE:
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Sign Up Page</title>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
        <link href="https://fonts.googleapis.com/css2?family=Raleway:wght@400;600&family=Roboto+Mono:wght@500&display=swap" rel="stylesheet">
        <style>
            body {
                margin: 0;
                padding: 0;
                background: linear-gradient(135deg, #1e3c72, #2a5298);
                min-height: 100vh;
                display: flex;
                justify-content: center;
                align-items: center;
                font-family: 'Raleway', sans-serif;
            }
            .signup-card {
                backdrop-filter: blur(12px);
                background: rgba(255, 255, 255, 0.15);
                border-radius: 20px;
                box-shadow: 0 8px 30px rgba(0, 0, 0, 0.25);
                width: 100%;
                max-width: 450px;
                padding: 2.5rem;
                color: #fff;
            }
            .signup-card h2 {
                text-align: center;
                font-size: 2rem;
                font-weight: 600;
                margin-bottom: 1.5rem;
            }
            .form-control {
                background: rgba(255, 255, 255, 0.2);
                color: #fff;
                border: 1px solid rgba(255, 255, 255, 0.3);
                border-radius: 8px;
            }
            .form-control:focus {
                box-shadow: none;
                border-color: #56ab2f;
                background: rgba(255, 255, 255, 0.3);
            }
            .btn-success {
                background: linear-gradient(90deg, #56ab2f, #a8e063);
                border: none;
                font-weight: bold;
                padding: 0.8rem;
                border-radius: 8px;
            }
            .btn-success:hover {
                background: linear-gradient(90deg, #a8e063, #56ab2f);
            }
            .text-center a {
                color: #a8e063;
                text-decoration: none;
                font-weight: 600;
            }
            .text-center a:hover {
                text-decoration: underline;
            }
        </style>
    </head>
    <body>
        <div class="signup-card">
            <h2>Create an Account</h2>
            <form>
                <div class="mb-3">
                    <label for="fullName" class="form-label">Full Name</label>
                    <input type="text" id="fullName" class="form-control" placeholder="Enter your full name" required>
                </div>
                <div class="mb-3">
                    <label for="email" class="form-label">Email Address</label>
                    <input type="email" id="email" class="form-control" placeholder="Enter your email" required>
                </div>
                <div class="mb-3">
                    <label for="password" class="form-label">Password</label>
                    <input type="password" id="password" class="form-control" placeholder="Enter your password" required>
                </div>
                <div class="mb-3">
                    <label for="confirmPassword" class="form-label">Confirm Password</label>
                    <input type="password" id="confirmPassword" class="form-control" placeholder="Confirm your password" required>
                </div>
                <button type="submit" class="btn btn-success w-100 mt-4">Sign Up</button>
            </form>
            <div class="text-center mt-3">
                <span>Already have an account? <a href="login.html" target="_blank">Login</a></span>
            </div>
        </div>

        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    </body>
    </html>


# OUTPUT:

# HOME PAGE:
!['Result'](o1.png)

# CONTACT FORM:
!['rsult'](o3.png)
# LOGIN PAGE:
!['Result'](o4.png)

# SIGN UP PAGE:
!['Result'](o5.png)
# RESULT:
The Project for responsive web design using Bootstrap is completed successfully.
