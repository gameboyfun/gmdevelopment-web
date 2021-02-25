<template>
    <b-navbar toggleable="lg" type="dark">
      <b-navbar-brand href="/">
        <img width="300" height="50" :src="require('~/assets/logo/Untitled_Artwork.png')">
      </b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav >
        <!-- Right aligned nav items -->
        <!-- <div id="div"> -->
            <b-navbar-nav id="collapse">
                <div class="inside-div">
                    <b-nav-item to="/home" class="d-flex align-items-center">
                        Home
                    </b-nav-item>
                </div>
                <div class="inside-div">
                    <b-nav-item-dropdown text="Service" right>
                        <b-dropdown-item to="/digitalmarketing">Digital Marketing</b-dropdown-item>
                        <b-dropdown-item to="/development">Development</b-dropdown-item>
                    </b-nav-item-dropdown>
                </div>
                <div class="inside-div">
                    <b-nav-item to="/article" class="d-flex align-items-center">
                        Article
                    </b-nav-item>
                </div>
                <b-button pill variant="outline-light" class="py-1 d-flex align-items-center" href="tel:+66850839976">
                    <fa :icon="['fas', 'phone']" /> 085-083-9976
                </b-button>
                <b-button id="facebook" pill variant="outline-light" href="https://www.facebook.com/gameboyfun.blackfamily/" target="_blank">
                    <fa :icon="['fab', 'facebook']" id="logofacebook" />
                </b-button>
            </b-navbar-nav>
        <!-- </div> -->
      </b-collapse>
    </b-navbar>
</template>