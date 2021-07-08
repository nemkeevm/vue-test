<template>
  <div id="nav">
    <div class="nav_user">
      <div class="nav_user__logo">
        <img src="https://picsum.photos/200" alt="logo">
      </div>
      <div class="nav_user__info">
        <div class="nav_user__name">Ирина</div>
        <div class="nav_user__email">test@email.com</div>
      </div>
    </div>
    <router-link to="/">
    <svg version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
        viewBox="0 0 512 512" style="enable-background:new 0 0 512 512;" xml:space="preserve">
        <g>
          <g>
            <path d="M503.401,228.884l-43.253-39.411V58.79c0-8.315-6.741-15.057-15.057-15.057H340.976c-8.315,0-15.057,6.741-15.057,15.057
              v8.374l-52.236-47.597c-10.083-9.189-25.288-9.188-35.367-0.001L8.598,228.885c-8.076,7.36-10.745,18.7-6.799,28.889
              c3.947,10.189,13.557,16.772,24.484,16.772h36.689v209.721c0,8.315,6.741,15.057,15.057,15.057h125.913
              c8.315,0,15.057-6.741,15.057-15.057V356.931H293v127.337c0,8.315,6.741,15.057,15.057,15.057h125.908
              c8.315,0,15.057-6.741,15.056-15.057V274.547h36.697c10.926,0,20.537-6.584,24.484-16.772
              C514.147,247.585,511.479,236.245,503.401,228.884z M433.965,244.433c-8.315,0-15.057,6.741-15.057,15.057v209.721h-95.793
              V341.874c0-8.315-6.742-15.057-15.057-15.057H203.942c-8.315,0-15.057,6.741-15.057,15.057v127.337h-95.8V259.49
              c0-8.315-6.741-15.057-15.057-15.057H36.245l219.756-200.24l74.836,68.191c4.408,4.016,10.771,5.051,16.224,2.644
              c5.454-2.41,8.973-7.812,8.973-13.774V73.847h74.002v122.276c0,4.237,1.784,8.276,4.916,11.13l40.803,37.18H433.965z"/>
          </g>
        </g>
      </svg>
      Все новости
    </router-link>
    <router-link to="/create">
    <svg id="Capa_1" enable-background="new 0 0 512 512" height="512" viewBox="0 0 512 512" width="512" xmlns="http://www.w3.org/2000/svg"><path d="m437.02 74.98c-48.352-48.351-112.64-74.98-181.02-74.98s-132.668 26.629-181.02 74.98c-48.351 48.352-74.98 112.64-74.98 181.02s26.629 132.668 74.981 181.02c3.585 3.585 8.533 4.965 13.176 4.161.007.001.01.008.019.007l121.199-21.227c3.038-.532 5.838-1.987 8.019-4.168l194.918-194.919c5.858-5.858 5.858-15.355 0-21.213l-99.986-99.986c-5.857-5.858-15.355-5.858-21.213 0l-194.919 194.919c-2.182 2.181-3.637 4.982-4.169 8.02l-15.814 90.361c-29.97-39.169-46.211-86.821-46.211-136.975 0-124.617 101.383-226 226-226s226 101.383 226 226-101.383 226-226 226c-8.284 0-15 6.716-15 15s6.716 15 15 15c68.38 0 132.668-26.629 181.02-74.98 48.351-48.352 74.98-112.64 74.98-181.02s-26.629-132.668-74.98-181.02zm-320.419 261.234 59.176 59.175-71.73 12.563zm90.185 47.759-28.773-28.773 173.705-173.705 28.773 28.773zm94.933-252.478 28.787 28.787-173.706 173.705-28.786-28.787z"/></svg>
    Добавить запись</router-link>
  </div>
  <div class="content">
    <router-view/>
  </div>
</template>

<style lang="less">
@font-face {
    font-family: "OpenSans"; 
    src: url("./assets/fonts/OpenSans-Regular.ttf") format("truetype"); 
    font-style: normal; 
    font-weight: normal; 
}
@font-face {
    font-family: "OpenSans"; 
    src: url("./assets/fonts/OpenSans-Bold.ttf") format("truetype"); 
    font-style: normal; 
    font-weight: bold; 
}
body {
  margin: 0;
  padding: 0;
}
#app {
  font-family: OpenSans, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

#nav {
  position: fixed;
  left: 0;
  top: 0;
  width: 230px;
  height: 100vh;

  a {
    display: flex;
    align-items: center;
    padding: 10px;
    border-top: 1px solid rgb(122, 111, 111);
    font-weight: bold;
    color: #2c3e50;
    text-decoration: none;
    svg {
      width: 25px;
      height: 25px;
      margin-right: 15px;
    }

    &.router-link-exact-active {
      color: #3179e6;
      svg {
        fill: #3179e6;
      }
    }
  }
}

.nav_user {
  display: flex;
  align-items: center;
  &__logo{
    margin: 10px;
    
    img {
      width: 50px;
      height: 50px;
      border-radius: 50%;
    }
  }
}

.nav_icon {
  width: 40px;
  height: 40px;
}

.content {
  background: #c5d8eb;
  min-height: calc(100% - 230px);
  margin-left: 230px;
  padding: 20px;
}


</style>
