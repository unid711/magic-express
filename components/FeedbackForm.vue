<template>
  <div class="feedback-form">
    <form
      netlify
      netlify-honeypot
      name="feedback"
      method="POST"
      action="/success"
    >
      <p class="hidden">
        <label>
          Don’t fill this out if you’re human: <input name="bot-field" />
        </label>
      </p>
      <input type="hidden" name="form-name" value="feedback" />
      <label for="white-count">White</label>
      <input id="white-count" type="number" name="white-count" />
      <label for="blue-count">Blue</label>
      <input id="blue-count" type="number" name="blue-count" defaulValue="0" />      
      <label for="black-count">Black</label>
      <input id="black-count" type="number" name="black-count" />      
      <label for="green-count">Green</label>
      <input id="green-count" type="number" name="green-count" />      
      <label for="red-count">Red</label>
      <input id="red-count" type="number" name="red-count" />
      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<style scoped>
.feedback-form {
  margin: 40px 40px;
  min-width: 250px;
  width: 45%;
}
input,
textarea,
button {
  font-size: inherit;
  margin: 15px 0;
  padding: 12px 20px;
  width: 100%;
}

button {
  background-color: teal;
  border: 1px solid black;
  color: white;
  width: 50%;
}

.hidden {
  clip: rect(0 0 0 0);
  clip-path: inset(50%);
  height: 1px;
  overflow: hidden;
  position: absolute;
  white-space: nowrap;
  width: 1px;
}
</style>
