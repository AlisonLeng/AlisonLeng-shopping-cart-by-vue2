<template>
  <footer>
    <div class="footer-container">
      <div class="footer-logo">
        <img src="../assets/img/footer-logo.png" alt="" />
      </div>

      <div class="customer-service">
        <h2>客戶服務</h2>
        <ul>
          <li><a href="#">運送說明</a></li>
          <li><a href="#">退換貨相關</a></li>
          <li><a href="#">付款資訊</a></li>
          <li><a href="#">FAQ</a></li>
        </ul>
      </div>
      <div class="about-us">
        <h2>關於我們</h2>
        <ul>
          <li><a href="#">品牌故事</a></li>
          <li><a href="#">媒體聯繫</a></li>
          <li><a href="#">Press kit</a></li>
        </ul>
      </div>
      <div class="information">
        <h2>資訊</h2>
        <ul>
          <li><a href="#">隱私權政策</a></li>
          <li><a href="#">Cookie</a></li>
          <li><a href="#">GDPR</a></li>
        </ul>
      </div>
      <div class="follow-us">
        <h2>追蹤我們</h2>
        <ul>
          <li>+886 02123-45678</li>
          <li><img src="../assets/img/social-media-icon.png" alt="" /></li>
        </ul>
      </div>
    </div>
  </footer>
</template>

<style lang="scss" scoped>
@import "../assets/scss/main.scss";
footer {
  grid-column: 1/13;
  grid-row: 3/4;
  width: 100%;
  margin: 0 auto;
  background: #f6f7f8;

  .footer-container {
    width: 90%;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    padding-top: 100px;
    .footer-logo > img {
      width: 175px;
      height: 31px;
      margin-top: 40px;
    }

    li {
      margin-top: 10px;
      color: $label_color;
      a {
        color: $label_color;
      }
    }

    .follow-us > ul > li > img {
      width: 104px;
      height: 24px;
    }
  }
}
</style>
