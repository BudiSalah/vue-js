<template>
  <div>
    <header>
      <nav class="navbar navbar-light navbar-expand-xl">
        <div class="container container--relative container--navbar-px">
          <router-link class="navbar-brand nav__brand" to="/">
            <img
              src="./assets/logo.png"
              class="d-inline-block align-top"
              alt=""
              loading="lazy"
            />
          </router-link>

          <ul id="toggleMenu" class="nav collapse navbar-collapse text-rtl">
            <li class="nav-item nav__item">
              <router-link class="nav-link nav__link" to="/">Home</router-link>
            </li>
            <li class="nav-item nav__item dropdown">
              <router-link
                class="nav-link nav__link dropdown-toggle dropdown-toggle--noicon"
                to="/about"
                data-toggle="dropdown"
                role="button"
                aria-haspopup="true"
                aria-expanded="false"
              >
                About us
              </router-link>
              <div class="dropdown-menu nav__dropdown-menu">
                <router-link class="dropdown-item nav__dropdown-item" to="/"
                  >Our Company</router-link
                >
                <router-link class="dropdown-item nav__dropdown-item" to="/"
                  >Partners & Accreditations</router-link
                >
                <router-link class="dropdown-item nav__dropdown-item" to="/"
                  >Corporate Structure</router-link
                >
              </div>
            </li>
            <li class="nav-item nav__item">
              <router-link class="nav-link nav__link" to="/business"
                >Business Units</router-link
              >
            </li>
            <li class="nav-item nav__item">
              <router-link class="nav-link nav__link" to="/projects"
                >Projects</router-link
              >
            </li>
            <li class="nav-item nav__item">
              <router-link class="nav-link nav__link" to="/partners"
                >Partners</router-link
              >
            </li>
            <li class="nav-item nav__item">
              <router-link class="nav-link nav__link" to="/media-events"
                >Media&Events</router-link
              >
            </li>
            <li class="nav-item nav__item">
              <router-link class="nav-link nav__link" to="/contact"
                >Contacts</router-link
              >
            </li>
            <li class="nav-item nav__item">
              <router-link class="nav-link nav__link" to="/careers"
                >Careers</router-link
              >
            </li>
            <li class="nav-item nav__item">
              <router-link class="nav-link nav__link" to="/search">
                <img src="./assets/icon/icon-search.png" alt="Search Icon" />
              </router-link>
            </li>
            <li class="nav-item nav__item">
              <router-link class="nav-link nav__link lang__btn" to="/">
                <img :src="langIcon" alt="Language Icon" />
              </router-link>
            </li>
          </ul>

          <button
            class="navbar-toggler navbar__mobile-btn navbar__mobile-btn--rtl"
            type="button"
            data-toggle="collapse"
            data-target="#toggleMenu"
            aria-controls="toggleMenu"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <span class="navbar-toggler-icon"></span>
          </button>
        </div>
      </nav>
    </header>

    <main style="min-height: 17.8vh">
      <router-view />
    </main>

    <Footer />
  </div>
</template>

<script>
import "./scss/imports.scss";
import Footer from "./components/Footer";
import { mapActions } from "vuex";

export default {
  name: "App",
  data: function () {
    return {
      langIcon: require("@/assets/icon/icon-lang-ar.png"),
    };
  },
  components: {
    Footer,
  },
  mounted() {
    this.siteLang();
    this.showDropDown();
    this.toggleMobileMenu();
    this.closeMenu();
  },
  methods: {
    ...mapActions(["changeSliderImg"]),
    siteLang: function () {
      let langBtn = document.querySelector(".lang__btn");
      let currentLang = localStorage.getItem("lang");

      function setEn(target) {
        localStorage.setItem("lang", "en");
        document.body.classList.remove("rtl");
        target.langIcon = require("@/assets/icon/icon-lang-ar.png");
      }

      function setAr(target) {
        localStorage.setItem("lang", "ar");
        document.body.classList.add("rtl");
        target.langIcon = require("@/assets/icon/icon-lang-eng.png");
      }

      currentLang == null || currentLang == "en" ? setEn(this) : setAr(this);

      function switchLang(target) {
        currentLang = localStorage.getItem("lang");
        currentLang == "en" ? setAr(target) : setEn(target);
      }

      langBtn.addEventListener("click", (e) => {
        e.preventDefault();
        switchLang(this);
        this.changeSliderImg();
      });
    },
    toggleMenu: function (e) {
      let target = e.target;
      let dropBtn = target.querySelector(".dropdown-toggle");
      let dropMenu = target.querySelector(".dropdown-menu");

      setTimeout(() => {
        if (
          !target.classList.contains("dropdown-menu") ||
          !target.classList.contains("dropdown")
        ) {
          if (e.type == "mouseenter") {
            target.classList.add("show");
            dropMenu.classList.add("show");
            dropBtn.setAttribute("aria-expanded", "true");
          } else {
            target.classList.remove("show");
            dropMenu.classList.remove("show");
            dropBtn.setAttribute("aria-expanded", "false");
          }
        }
      }, 200);
    },
    showDropDown: function () {
      let dropdowns = document.querySelectorAll(".dropdown");

      for (let dropdown of dropdowns) {
        dropdown.addEventListener("mouseenter", this.toggleMenu);
        dropdown.addEventListener("mouseleave", this.toggleMenu);
      }
    },
    toggleMobileMenu: function () {
      let menuBtn = document.querySelector('[data-target="#toggleMenu"]');
      let menu = document.getElementById("toggleMenu");
      menuBtn.addEventListener("click", () => {
        menu.classList.toggle("show");
      });
    },
    closeMenu: function () {
      let mobileMenu = document.getElementById("toggleMenu");
      mobileMenu.addEventListener("click", (e) => {
        e.target.closest(".dropdown") == null || e.target.closest(".nav__dropdown-menu") != null ? e.target.closest("#toggleMenu").classList.remove("show") : "";
      });
    },
  },
  created() {
    this.changeSliderImg();
  },
};
</script>
