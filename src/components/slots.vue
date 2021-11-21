<template >
  <div>
      <div class="cart">
          <header>
              <slot name="header"></slot>
          </header>
          <content>
              <slot name="content"></slot>
          </content>
          <footer>
              <slot name="footer"></slot>
          </footer>

      </div>
  </div>
</template>

<script>

export default {


}
</script>

<style>

.cart {
    width: 326px;
    height: 496px;
    border: 2px solid;
    background-color: rgb(160, 129, 160);
    padding: 15px 10px;
    display: flex;
    flex-flow: column;
    justify-content: space-evenly;
    margin: 10px;
    border-radius: 10px;
    box-shadow: 5px 7px 21px 2px rgb(31, 30, 30);
}
footer{
    display: flex;
    flex-flow: column;
    align-items: center;
    justify-content: space-evenly;
}
</style>