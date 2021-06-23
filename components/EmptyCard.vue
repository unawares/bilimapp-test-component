<template>
  <v-card
    class="empty-card">
    <div class="wrapper">
      <svg width="62" height="62" viewBox="0 0 62 62" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M31.1211 62C14.0941 62 0 48.1481 0 31.1211C0 14.0941 14.0941 0 31.1211 0C48.1481 0 62 14.0941 62 31.1211C62 48.1481 48.1481 62 31.1211 62ZM47.4688 27.4883H34.7539V14.5312C34.7539 12.5284 33.1228 10.8984 31.1211 10.8984C29.1182 10.8984 27.4883 12.5284 27.4883 14.5312V27.4883H14.5312C12.5284 27.4883 10.8984 29.1182 10.8984 31.1211C10.8984 33.124 12.5284 34.7539 14.5312 34.7539H27.4883V47.4688C27.4883 49.4716 29.1182 51.1016 31.1211 51.1016C33.1228 51.1016 34.7539 49.4716 34.7539 47.4688V34.7539H47.4688C49.4704 34.7539 51.1016 33.124 51.1016 31.1211C51.1016 29.1182 49.4704 27.4883 47.4688 27.4883Z" fill="#1864AB"/>
      </svg>
    </div>
  </v-card>
</template>

<style lang="scss" scoped>
.empty-card {
  cursor: pointer;
  padding: 23px 20px 18px;
  box-shadow: 0px 4px 30px rgba(0, 72, 180, 0.15) !important;
  border-radius: 20px !important;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  padding: 85px 0;
  border: 1px solid transparent;

  .wrapper {
    height: 62px;
    width: 62px;
    display: inline-flex;
    justify-content: center;
    align-items: center;

    svg {
      display: none;
    }
  }

  &:hover {
    border: 1px solid #1864AB;
    
    .wrapper svg {
      display: block;
    }
  }

}
</style>
