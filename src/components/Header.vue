<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <router-link to="/" class="navbar-brand">Stock Trader</router-link>
    <div class="collapse navbar-collapse">
      <ul class="nav navbar-nav">
        <router-link to="/portfolio" activeClass="active" tag="li" class="nav-item"><a class="nav-link">Portfolio</a></router-link>
        <router-link to="/stocks" activeClass="active" tag="li" class="nav-item"><a class="nav-link">Stocks</a></router-link>
      </ul>
      <ul class="navbar-nav ml-auto">
        <li class="nav-item"><a href="#" class="nav-link">End Day</a></li>
        <li class="nav-item dropdown">
          <a
            href="#"
            class="nav-link dropdown-toggle"
            data-toggle="dropdown"
            role="button" aria-haspopup="true"
            aria-expanded="false">
            Save &amp; Load <span class="caret"></span>
          </a>
          <ul class="dropdown-menu">
            <li><a href="#">Save Data</a></li>
            <li><a href="#">Load Data</a></li>
          </ul>
        </li>
      </ul>
    </div>
  </nav>
</template>