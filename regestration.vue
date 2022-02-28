<template>
  <div class="main">
    <div class="logo">
        <img src="./assets/logo.png" alt="">
    </div>
    <div class="info">
      <h1>Авторизация</h1>
      <div>
        <input type="text"
          class="login"
          placeholder="Введите логин "
          :name="login"
        />
      </div>
      <div>
      <div class="password_label">
        <div class="password_form">
          <input
            type="password"
            class="password_form"
            id="password-input"
            placeholder="Введите пароль"
            :name="password"
          />
          <div class="password_btn">
            <img
              v-on:click="showOrHide"
              id="password-control"
              src="./assets/eye.png"
              alt=""
            />
          </div>
        </div>
        </div>
        <div>
          <button class="btn">Войти</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const ShowOrHide = () => {
  const input = document.getElementById('password-input');
  const image = document.getElementById('password-control');

  if (input != null && image != null) {
    if (input.getAttribute('type') === 'password') {
      input.setAttribute('type', 'text');
      image.classList.add('view');
    } else {
      input.setAttribute('type', 'password');
      image.classList.remove('view');
    }
    return false;
  }
  return false;
};

export default {
  components: {},
  methods: {
    showOrHide: ShowOrHide,
  },
};
</script>
<style>
.main {
  margin: 0 auto;
  width: 500px;
  display: flex;
  flex-direction: row;
  background: rgb(183, 235, 183);
}

.logo img{
  margin-top: 30px;
  height: 200px;
  width: 200px;
}

.password_form {
  margin-top: 5%;
  height: 40px;
  font-size: 16px;
}

.btn {
  margin-top: 30px;
  margin-left: 60px;
  width: 80px;
  height: 40px;
  font-size: 16px;
  cursor: pointer;
}
.login {
  height: 40px;
  font-size: 16px;
}
.password_label {
  position: relative;
}
.password_btn {
  position: absolute;
  right: 8px;
  top: 18px;
  height: 32px;
  width: 32px;
}
@media(max-width: 740px){
  .main {
    flex-direction: column;
    text-align: center;
    align-items: center;
  }
  .login {
  height: 40px;
  font-size: 26px;
  width: 300px;
}
  .password_form {
  margin-top: 5%;
  height: 40px;
  font-size: 26px;
  width: 300px;
}
  .logo img {
    margin-top: 10px;
    height: 100px;
    width: 100px;
  }
  .btn{
    margin-left: 0;
  }
  .password_btn{
    margin-top: 3px;
  }
}
</style>