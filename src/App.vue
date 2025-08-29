<script setup>
import IdCard from './components/IdCard.vue'
import Random from './components/Random.vue'
import BoxColor from './components/BoxColor.vue'
import CreditCard from './components/CreditCard.vue'
import Rating from './components/Rating.vue'
import DriverCard from './components/DriverCard.vue'
import LikeButton from './components/LikeButton.vue'
import ClickablePicture from './components/ClickablePicture.vue'
import Dice from './components/Dice.vue'
import Carousel from './components/Carousel.vue'
import NumbersTable from './components/NumbersTable.vue'
import FaceBook from './components/FaceBook.vue'
import SignupPage from './components/SignupPage.vue'
import RGBColorPicker from './components/RGBColorPicker.vue'
</script>

<template>
  <div class="app">
    <h1>Vue Components Showcase</h1>
    
    <section>
      <h2>IdCard Component</h2>
      <IdCard
        first-name="John"
        last-name="Doe"
        gender="male"
        :height="180"
        :birth="new Date('1990-05-15')"
        picture="/maxence.png"
      />
    </section>

    <section>
      <h2>Random Component</h2>
      <Random :min="1" :max="6" />
      <Random :min="1" :max="100" />
    </section>

    <section>
      <h2>BoxColor Component</h2>
      <BoxColor :r="255" :g="0" :b="0" />
      <BoxColor :r="128" :g="255" :b="0" />
    </section>

    <section>
      <h2>CreditCard Component</h2>
      <CreditCard
        type="Visa"
        number="0123456789018845"
        :expiration-month="3"
        :expiration-year="2021"
        bank="BNP"
        owner="Maxence Bouret"
        bg-color="#11aa99"
        color="white"
      />
      <CreditCard
        type="Master Card"
        number="0123456789010995"
        :expiration-month="3"
        :expiration-year="2021"
        bank="N26"
        owner="Maxence Bouret"
        bg-color="#eeeeee"
        color="#222222"
      />
    </section>

    <section>
      <h2>Rating Component</h2>
      <Rating :rate="0" />
      <Rating :rate="1.49" />
      <Rating :rate="1.5" />
      <Rating :rate="3" />
      <Rating :rate="4" />
      <Rating :rate="5" />
    </section>

    <section>
      <h2>DriverCard Component</h2>
      <DriverCard
        name="Travis Kalanick"
        :rating="4.2"
        img="https://si.wsj.net/public/resources/images/BN-TY647_37gql_OR_20170621052140.jpg?width=620&height=428"
        :car="{ model: 'Toyota Corolla Altis', licensePlate: 'CO42DE' }"
      />
      <DriverCard
        name="Dara Khosrowshahi"
        :rating="4.9"
        img="https://ubernewsroomapi.10upcdn.com/wp-content/uploads/2017/09/Dara_ELT_Newsroom_1000px.jpg"
        :car="{ model: 'Audi A3', licensePlate: 'BE33ER' }"
      />
    </section>

    <section>
      <h2>LikeButton Component</h2>
      <LikeButton />
    </section>

    <section>
      <h2>ClickablePicture Component</h2>
      <ClickablePicture img="/maxence.png" img-clicked="/maxence-glasses.png" />
    </section>

    <section>
      <h2>Dice Component</h2>
      <Dice />
    </section>

    <section>
      <h2>Carousel Component</h2>
      <Carousel
        :images="[
          'https://randomuser.me/api/portraits/women/1.jpg',
          'https://randomuser.me/api/portraits/men/1.jpg',
          'https://randomuser.me/api/portraits/women/2.jpg',
          'https://randomuser.me/api/portraits/men/2.jpg'
        ]"
      />
    </section>

    <section>
      <h2>NumbersTable Component</h2>
      <NumbersTable :limit="12" />
    </section>

    <section>
      <h2>FaceBook Component</h2>
      <FaceBook />
    </section>

    <section>
      <h2>SignupPage Component</h2>
      <SignupPage />
    </section>

    <section>
      <h2>RGBColorPicker Component</h2>
      <RGBColorPicker />
    </section>
  </div>
</template>

<style scoped>
.app {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

section {
  margin-bottom: 40px;
  padding: 20px;
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  background-color: #f9f9f9;
}

h1 {
  text-align: center;
  color: #333;
  margin-bottom: 30px;
}

h2 {
  color: #555;
  border-bottom: 2px solid #007bff;
  padding-bottom: 10px;
  margin-bottom: 20px;
}
</style>
