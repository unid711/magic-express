<script stuff>
  export default{
    data () {
      return {
        whiteCount: "",
        blueCount: "",
        blackCount: "",
        greenCount: "",
        redCount: "",
        otherCount: "",  
        resultString: "",
        totalString: ""
      }
    },
    methods: {
      handleSubmit(event) {
        const nonLandTotalCount = Number(this.whiteCount) + Number(this.blueCount) + Number(this.blackCount) + Number(this.greenCount) + Number(this.redCount) + Number(this.otherCount);
        const ratio = 23 / 40;
        const totalCount = Math.round(nonLandTotalCount / ratio);
        const totalLandCount = totalCount - nonLandTotalCount;

        const whitePercent = this.whiteCount / (nonLandTotalCount - this.otherCount);
        const plainsCount = Math.round(totalLandCount * whitePercent); 

        const bluePercent = this.blueCount / (nonLandTotalCount - this.otherCount);
        const islandsCount = Math.round(totalLandCount * bluePercent);

        const blackPercent = this.blackCount / (nonLandTotalCount - this.otherCount);
        const swampsCount = Math.round(totalLandCount * blackPercent);

        const greenPercent = this.greenCount / (nonLandTotalCount - this.otherCount);
        const forestsCount = Math.round(totalLandCount * greenPercent);

        const redPercent = this.redCount / (nonLandTotalCount - this.otherCount);
        const mountainsCount = Math.round(totalLandCount * redPercent);
        
        const resultStrings = [];
        if(plainsCount > 0){
          resultStrings.push(plainsCount + " plains");
        }
        if(islandsCount > 0){
          resultStrings.push(islandsCount + " islands");
        }
        if(swampsCount > 0){
          resultStrings.push(swampsCount + " swamps");
        }
        if(forestsCount > 0){
          resultStrings.push(forestsCount + " forests");
        }
        if(mountainsCount > 0){
          resultStrings.push(mountainsCount + " mountains");
        }
        this.resultString = "You should have " + resultStrings.join(", ");
        this.totalString = "Total deck size: " + totalCount + " (" + nonLandTotalCount + " non land / " + totalLandCount + " land)";

        this.totalCount = totalCount;
        this.totalLandCount = totalLandCount;
        this.totalNonLandCount = nonLandTotalCount;

        event.preventDefault();
      }
    } 
  }
</script>

<template>
  <div class="feedback-form">
    <p>Enter how many non-land cards of each color:</p>
    <form>
      <p class="hidden">
        <label>
          Don’t fill this out if you’re human: <input name="bot-field" />
        </label>
      </p>
      <input type="hidden" name="form-name" value="feedback" />
      <div class="input-group">
        <label for="white-count">White</label>
        <input id="white-count" v-model="whiteCount" type="number" name="white-count" />
      </div>
      <div class="input-group">
        <label for="blue-count">Blue</label>
        <input id="blue-count" v-model="blueCount" type="number" name="blue-count" />      
      </div>
      <div class="input-group">
        <label for="black-count">Black</label>
        <input id="black-count" v-model="blackCount" type="number" name="black-count" />      
      </div>
      <div class="input-group">
        <label for="green-count">Green</label>
        <input id="green-count" v-model="greenCount" type="number" name="green-count" />      
      </div>
      <div class="input-group">
        <label for="red-count">Red</label>
        <input id="red-count" v-model="redCount" type="number" name="red-count" />   
      </div>
      <div class="input-group">
        <label for="other-count">Other</label>
        <input id="other-count" v-model="otherCount" type="number" name="other-count" />
      </div>
      <button type="submit" @click="handleSubmit">Calculate</button>
    </form>
    <div>{{resultString}}</div>
    <div>{{totalString}}</div>
  </div>
</template>

<style scoped>
.feedback-form {
  margin: 40px 40px;
  margin-top: 0;
  min-width: 250px;
}

label {
  display:inline-block;
  min-width: 50px;
}

input,
textarea {
  font-size: inherit;
  margin: 15px 0;
  padding: 12px 20px;
  width: 100%;
  max-width: 150px;
}

button {
  font-size: inherit;
  background-color: teal;
  border: 1px solid black;
  color: white;
  margin: 15px 0;
  padding: 12px 20px;
  width: 100%;
  max-width: 150px;
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
