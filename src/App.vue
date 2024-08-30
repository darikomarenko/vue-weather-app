<script>

</script>

<template>
  <div className="wrapper">
    <h1>Weather App</h1>
    <p>Check on weather in my city</p>
    <input type="text" placeholder="Enter city">
    <button>Check weather</button>
  </div>
</template>

<style scoped>
.wrapper {
  width: 900px;
  height: 500px;
  border-radius: 50px;
  background: #94bbe9;
  padding: 20px;
  text-align: center;
  color: black;
}

.wrapper h1 {
  margin-top: 50px;
}

.wrapper p {
  margin-top: 20px;
}

.wrapper input {
  margin: 10px;
  background: white;
  color: #6e2d7d;
  font-size: 14px;
  border: 2px solid #6e2d7d;
  border-radius: 10px;
  padding: 10px 15px;
  outline: none;
}

.wrapper input:focus {
  border: 2px solid #6e2d7d;
}

.wrapper button {
  background: #6e2d7d;
  color: white;
  border-radius: 10px;
  border: 2px solid #6e2d7d;
  padding: 10px 15px;
  cursor: pointer;
  transition: transform 500ms ease;
}

.wrapper button:hover {
  background: white;
  color: #6e2d7d;
}
</style>
