<template>
  <div class="footer-container">
    <v-card outlined class="icon-card">
      <v-card-text style="padding: 10px">
        <v-row dense>
          <!-- Icon -->
          <v-col cols="auto">
            <v-icon size="50" class="v-my-icon" />
          </v-col>

          <!-- Title and Description -->
          <v-col>
            <div class="title" style="margin-top: 5px; font-weight: bold">
              产品名称
            </div>
            <div class="description" style="font-weight: bold">
              产品宣传标语/口号
            </div>
          </v-col>

          <!-- Button -->
          <v-col cols="auto">
            <v-btn rounded class="v-my-btn" height="30">保存到桌面</v-btn>
          </v-col>
        </v-row>
      </v-card-text>
    </v-card>
    <div class="footer-text">建议使用Chrome/Alook/edge/夸克/uc等浏览器</div>
  </div>
</template>
<script></script>
<style>
.footer-container {
  background-color: #262626;
  padding: 15px;
}
.v-my-icon {
  background-color: lightgray;
  border-radius: 7px;
}
.v-my-btn {
  margin-top: 10px;
  color: white !important ;
  background-color: #00d2be;
  font-size: 12px;
  box-shadow: none;
}
.icon-card {
  border-radius: 10px;
}
.title {
  font-size: 17px;
  font-weight: 600;
}
.description {
  font-size: 10px;
  font-weight: 600;
}
.footer-text {
  margin-top: 10px;
  text-align: center;
  font-size: 12px;
  color: white;
}
</style>
