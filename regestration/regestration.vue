<template>
  <div class="main">
    <div class="logo">
      <img src="./assets/logo.png" alt="" />
    </div>
    <div class="info">
      <h1>Вход</h1>
      <div>
        <input v-model="login"
          type="text"
          class="login"
          placeholder="Введите логин "
          id="login"
          :name="login"
        />
      </div>
      <div>
        <div class="password_label">
          <div class="password_form">
            <input v-model="password"
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
          <button class="btn" v-on:click="send">Войти</button>
          <div class="linker">
            Ещё нет аккаунта?
            <!-- <router-link class="linker_style" to="../avtoreg"
              >Зарегистрироваться</router-link> -->
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
const ShowOrHide = () => {
  const input = document.getElementById("password-input");
  const image = document.getElementById("password-control");

  if (input != null && image != null) {
    if (input.getAttribute("type") === "password") {
      input.setAttribute("type", "text");
      image.classList.add("view");
    } else {
      input.setAttribute("type", "password");
      image.classList.remove("view");
    }
    return false;
  }
  return false;
};

export default {
  components: {},
  methods: {
    showOrHide: ShowOrHide,
    send() {
      const url = "https://6ff19a43-6d37-41bf-a4e0-bac584742f16.mock.pstmn.io";
      
      axios
        .get(url + "/Autoregestration", {
          params: {
            "login": this.login,
            "password": this.password,
          },
        })
        .then((response) => {
          alert(response.data)
          console.log(response);
        })
        .catch((error) => {
          console.error(error);
        });
    },
//     toggleStyleRegister() {
//         const login :HTMLDivElement = document.querySelector('.login');
//           const register :HTMLDivElement = document.querySelector('.register');
//           login.style.display = 'none';
//           register.style.display = 'flex';
// },
  },
};
</script>
<style>
.main {
  margin: 0 auto;
  width: 500px;
  height: 345px;
  display: flex;
  flex-direction: row;
  background: rgb(128, 235, 102);
}
.info h1 {
  margin-left: 70px;
}

.logo img {
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
    right: 5px;
    top: 17px;
    height: 32px;
    width: 32px;
}
.regist {
  width: 300px;
  margin-top: 10px;
}
@media (max-width: 740px) {
  .main {
    flex-direction: column;
    text-align: center;
    align-items: center;
    height: 405px;
    width: 500px;
    background: rgb(128, 235, 102);
  }
  .password_btn {
    right: 20px;
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
  .btn {
    margin-left: 0;
  }
  .password_btn {
    margin-top: 3px;
  }
}
</style>