<template>
  <header id="header" class="fixed-top">
    <div class="container d-flex align-items-center justify-content-between">
      <h1 class="logo"><a href="/books">Bookish</a></h1>
      <!-- Uncomment below if you prefer to use an image logo -->
      <!-- <a href="index.html" class="logo"><img src="assets/img/logo.png" alt="" class="img-fluid"></a>-->

      <nav id="navbar" class="navbar">
        <ul>
          <li><a class="nav-link scrollto active" href="/books">All Books</a></li>
          <li><a class="nav-link scrollto" href="/login">Login</a></li>
          <li><a class="nav-link scrollto" href="/logout">Logout</a></li>
          <li><a class="nav-link scrollto o" href="/signup">Signup</a></li>
          <!-- <li><a class="nav-link scrollto" href="#team">Team</a></li> -->
          <!-- <li><a class="nav-link scrollto" href="#pricing">Pricing</a></li> -->
          <!-- <li class="dropdown">
            <a href="#">
              <span>Drop Down</span>
              <i class="bi bi-chevron-down"></i>
            </a>
            <ul>
              <li><a href="#">Drop Down 1</a></li>
              <li class="dropdown">
                <a href="#">
                  <span>Deep Drop Down</span>
                  <i class="bi bi-chevron-right"></i>
                </a>
                <ul>
                  <li><a href="#">Deep Drop Down 1</a></li>
                  <li><a href="#">Deep Drop Down 2</a></li>
                  <li><a href="#">Deep Drop Down 3</a></li>
                  <li><a href="#">Deep Drop Down 4</a></li>
                  <li><a href="#">Deep Drop Down 5</a></li>
                </ul>
              </li>
              <li><a href="#">Drop Down 2</a></li>
              <li><a href="#">Drop Down 3</a></li>
              <li><a href="#">Drop Down 4</a></li>
            </ul>
          </li> -->
          <!-- <li><a class="nav-link scrollto" href="#contact">Contact</a></li> -->
          <!-- <li><a class="getstarted scrollto" href="#about">Get Started</a></li> -->
        </ul>
        <i class="bi bi-list mobile-nav-toggle"></i>
      </nav>
      <!-- .navbar -->
    </div>
  </header>
  <!-- End Header -->
  <!-- <router-link to="/">Home</router-link>
  |
  <router-link to="/books">Books</router-link>
  | -->
  <!-- <router-link to="/books-show">See a Book</router-link> -->
  <!-- | -->
  <!-- <router-link to="/signup">Signup</router-link>
  |
  <router-link to="/login">Login</router-link>
  |
  <router-link to="logout">Logout</router-link> -->
  <router-view />
  <footer id="footer">
    <div class="footer-top">
      <div class="container">
        <div class="row">
          <div class="col-lg-3 col-md-6 footer-contact">
            <h3>OnePage</h3>
            <p>
              A108 Adam Street
              <br />
              New York, NY 535022
              <br />
              United States
              <br />
              <br />
              <strong>Phone:</strong>
              +1 5589 55488 55
              <br />
              <strong>Email:</strong>
              info@example.com
              <br />
            </p>
          </div>

          <div class="col-lg-2 col-md-6 footer-links">
            <h4>Useful Links</h4>
            <ul>
              <li>
                <i class="bx bx-chevron-right"></i>
                <a href="#">Home</a>
              </li>
              <li>
                <i class="bx bx-chevron-right"></i>
                <a href="#">About us</a>
              </li>
              <li>
                <i class="bx bx-chevron-right"></i>
                <a href="#">Services</a>
              </li>
              <li>
                <i class="bx bx-chevron-right"></i>
                <a href="#">Terms of service</a>
              </li>
              <li>
                <i class="bx bx-chevron-right"></i>
                <a href="#">Privacy policy</a>
              </li>
            </ul>
          </div>

          <div class="col-lg-3 col-md-6 footer-links">
            <h4>Our Services</h4>
            <ul>
              <li>
                <i class="bx bx-chevron-right"></i>
                <a href="#">Web Design</a>
              </li>
              <li>
                <i class="bx bx-chevron-right"></i>
                <a href="#">Web Development</a>
              </li>
              <li>
                <i class="bx bx-chevron-right"></i>
                <a href="#">Product Management</a>
              </li>
              <li>
                <i class="bx bx-chevron-right"></i>
                <a href="#">Marketing</a>
              </li>
              <li>
                <i class="bx bx-chevron-right"></i>
                <a href="#">Graphic Design</a>
              </li>
            </ul>
          </div>

          <div class="col-lg-4 col-md-6 footer-newsletter">
            <h4>Join Our Newsletter</h4>
            <p>Tamen quem nulla quae legam multos aute sint culpa legam noster magna</p>
            <form action="" method="post">
              <input type="email" name="email" />
              <input type="submit" value="Subscribe" />
            </form>
          </div>
        </div>
      </div>
    </div>

    <div class="container d-md-flex py-4">
      <div class="me-md-auto text-center text-md-start">
        <div class="copyright">
          &copy; Copyright
          <strong><span>OnePage</span></strong>
          . All Rights Reserved
        </div>
        <div class="credits">
          <!-- All the links in the footer should remain intact. -->
          <!-- You can delete the links only if you purchased the pro version. -->
          <!-- Licensing information: https://bootstrapmade.com/license/ -->
          <!-- Purchase the pro version with working PHP/AJAX contact form: https://bootstrapmade.com/onepage-multipurpose-bootstrap-template/ -->
          Designed by
          <a href="https://bootstrapmade.com/">BootstrapMade</a>
        </div>
      </div>
      <div class="social-links text-center text-md-right pt-3 pt-md-0">
        <a href="#" class="twitter"><i class="bx bxl-twitter"></i></a>
        <a href="#" class="facebook"><i class="bx bxl-facebook"></i></a>
        <a href="#" class="instagram"><i class="bx bxl-instagram"></i></a>
        <a href="#" class="google-plus"><i class="bx bxl-skype"></i></a>
        <a href="#" class="linkedin"><i class="bx bxl-linkedin"></i></a>
      </div>
    </div>
  </footer>
</template>

<style></style>
