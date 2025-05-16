<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Navigation Demo</title>
  <style>
    /* Reset & Base Styles */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Arial', sans-serif;
      line-height: 1.6;
      padding: 20px;
      min-height: 100vh;
    }

    /* Navbar */
    .navbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1rem 2rem;
      background: #333;
      color: white;
    }

    .logo {
      color: white;
      font-size: 1.5rem;
      font-weight: bold;
      text-decoration: none;
    }

    .nav-links {
      display: flex;
      gap: 2rem;
      list-style: none;
    }

    .nav-links a {
      color: white;
      text-decoration: none;
      transition: 0.3s;
    }

    .nav-links a:hover {
      color: #4CAF50;
    }

    /* Hamburger Menu (Hidden on Desktop) */
    .hamburger {
      display: none;
      cursor: pointer;
    }

    .hamburger .bar {
      width: 25px;
      height: 3px;
      background: white;
      margin: 5px 0;
      transition: 0.4s;
    }

    /* Mobile Styles */
    @media (max-width: 768px) {
      .hamburger {
        display: block;
      }

      .nav-links {
        position: fixed;
        top: 70px;
        left: -100%;
        width: 100%;
        height: calc(100vh - 70px);
        background: #333;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        gap: 2rem;
        transition: 0.5s;
      }

      .nav-links.active {
        left: 0;
      }

      /* Hamburger to X Animation */
      .hamburger.active .bar:nth-child(1) {
        transform: rotate(-45deg) translate(-5px, 6px);
      }

      .hamburger.active .bar:nth-child(2) {
        opacity: 0;
      }

      .hamburger.active .bar:nth-child(3) {
        transform: rotate(45deg) translate(-5px, -6px);
      }
    }

    /* Demo Content */
    main {
      padding: 2rem;
      text-align: center;
    }
  </style>
</head>
<body>
  <header>
    <nav class="navbar">
      <a href="#" class="logo">NavDemo</a>
      <ul class="nav-links">
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Services</a></li>
        <li><a href="#">Contact</a></li>
      </ul>
      <div class="hamburger">
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
      </div>
    </nav>
  </header>

  <main>
    <h1>Responsive Navigation Demo</h1>
    <p>Resize your browser or open on mobile to see the hamburger menu.</p>
  </main>

  <script>
    // Mobile Menu Toggle
    const hamburger = document.querySelector('.hamburger');
    const navLinks = document.querySelector('.nav-links');

    hamburger.addEventListener('click', () => {
      hamburger.classList.toggle('active');
      navLinks.classList.toggle('active');
    });

    // Close menu when clicking a link (optional)
    document.querySelectorAll('.nav-links a').forEach(link => {
      link.addEventListener('click', () => {
        hamburger.classList.remove('active');
        navLinks.classList.remove('active');
      });
    });
  </script>
</body>
</html>
