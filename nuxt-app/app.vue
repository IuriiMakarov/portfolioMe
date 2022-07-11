<script>
  export default {
    data: () => {
      return {
        typeValue: '',
        typeStatus: false,
        typeArray: ['Hi, I am Makarov Iurii', 'Привет, я Макаров Юрий', 'Hola, soy Makarov Iurii', 'Merhaba, ben Makarov Iurii'],
        typingSpeed: 100,
        erasingSpeed: 100,
        newTextDelay: 2000,
        typeArrayIndex: 0,
        charIndex: 0
      }
    },

    methods: {
      typeText() {
        if(this.charIndex < this.typeArray[this.typeArrayIndex].length) {
          if(!this.typeStatus)
            this.typeStatus = true;
          this.typeValue += this.typeArray[this.typeArrayIndex].charAt(this.charIndex);
          this.charIndex += 1;
          setTimeout(this.typeText, this.typingSpeed);
        }
        else {
          this.typeStatus = false;
          setTimeout(this.eraseText, this.newTextDelay);
        }
      },
      eraseText() {
        if(this.charIndex > 0) {
          if(!this.typeStatus)
            this.typeStatus = true;
          this.typeValue = this.typeArray[this.typeArrayIndex].substring(0, this.charIndex - 1);
          this.charIndex -= 1;
          setTimeout(this.eraseText, this.erasingSpeed);
        }
        else {
          this.typeStatus = false;
          this.typeArrayIndex += 1;
          if(this.typeArrayIndex >= this.typeArray.length)
            this.typeArrayIndex = 0;
          setTimeout(this.typeText, this.typingSpeed + 1000);
        }
      }
    },
    created() {
      setTimeout(this.typeText, this.newTextDelay + 200);
    }
  }
</script>

  <template>
  <div class="container">
   <section class="information">
    <img src="./src/img/me.png" alt="Photo of me" class="information__photo">
    <h2 class="information__name">Makarov Iurii</h2>
    <h3 class="information__job">Front-End developer</h3>
    <div class="social">
     <a href="https://www.linkedin.com/in/iurii-makarov/" class="social__link social__link_linkedin"></a>
     <a href="https://github.com/" class="social__link  social__link_git"></a>
     <a href="https://vk.com/id183905108" class="social__link social__link_vk"></a>
    </div>
   </section>

   <section class="bio">
    <h1 class="name"><span class="typed-text" >{{ typeValue }}</span><br>Front-End Developer</h1>
    <h2 class="intro">If you want to see my project or learn information about me go to "projects" section</h2>
    <button class="contactMe">CONTACT ME</button>
   </section>

    <nav class="menu">

    </nav>
  </div>
</template>

<style lang="scss">

body {
  background-color: rgb(24,25,26);
  margin: 0;
  font-family: 'Helvetica Neue', sans-serif;
}

.container {
  max-width: 1280px;
  width: 100%;
  display: flex;
}

.information {
  width: 280px;
  background-color: rgb(36,37,38);
  height: 1080px;
  display: flex;
  flex-direction: column;
}

.information__photo {
  max-width: 190px;
  max-height: 190px;
  border-radius: 140px;
  margin: auto;
  margin-top: 30px;
  margin-bottom: 0;
}

.information__name{
  color: white;
  font-size: 30px;
  margin: auto;
  margin-top: 30px;
  margin-bottom: 0;
}

.information__job{
  color: rgb(83, 84, 84);
  font-size: 25px;
  margin: auto;
  margin-top: 10px;
  margin-bottom: 0; 
}

.bio {
  width: 830px;
  background-color: rgb(36,37,38);
  height: 350px;
  margin: auto;
  margin-top: 0;
}

.menu {
  width: 120px;
  background-color: rgb(36,37,38);
  height: 1080px;
}

.name {
  color: white;
  font-size: 48px;
  margin-left: 40px;

  span.typed-text {
    color: #ffb400;
  }
}

.intro {
  color: rgb(83, 84, 84);
  font-size: 16px;
  max-width: 415px;
  margin-left: 40px;
}

.contactMe{
  border-radius: 6px;
  background-color: #ffb400;
  width: 175px;
  height: 50px;
  border: 1px solid #ffb400;
  font-size: 19px;
  font-weight: bold;
  margin-left: 40px;
  margin-top: 25px;
}
.social {
  max-width: 240px;
  height: 50px;
  display: flex;
  justify-content: center;
  margin: auto;
  margin-top: 20px;
}

.social__link {
  width: 35px;
  height: 35px;
  margin-right: 15px;
  margin-left: 15px;
  background-position: center;
  background-repeat: no-repeat;
}

.social__link_linkedin {
  background-image: url(./src/img/linkedin.svg);
}

.social__link_git {
  background-image: url(./src/img/github.svg);
  background-color: #ffb400;
}

.social__link_vk {
  background-image: url(./src/img/vk.svg);
  background-color: #ffb400;
  background-size: contain;
}

</style>
