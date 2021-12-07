In this project, let's build a **Fruits Counter** by applying the concepts we have learned till now.

### Refer to the image below:

<br/>
<div style="text-align: center;">
    <img src="https://assets.ccbp.in/frontend/content/react-js/fruits-counter-output.gif" alt="fruits-counter" style="max-width:70%;box-shadow:0 2.8px 2.2px rgba(0, 0, 0, 0.12)">
</div>
<br/>

### Design Files

<details>
<summary>Click to view</summary>

- [Extra Small (Size < 576px) and Small (Size >= 576px)](https://assets.ccbp.in/frontend/content/react-js/fruits-counter-sm-output.png)
- [Medium (Size >= 768px), Large (Size >= 992px) and Extra Large (Size >= 1200px)](https://assets.ccbp.in/frontend/content/react-js/fruits-counter-lg-output.png)

</details>

### Set Up Instructions

<details>
<summary>Click to view</summary>

- Download dependencies by running `npm install`
- Start up the app using `npm start`
</details>

### Completion Instructions

<details>
<summary>Functionality to be added</summary>
<br/>

The app must have the following functionalities

- Initially, the count of the eaten mangoes and bananas should be 0
- When **Eat Mango** is clicked the count of the mangoes eaten should be incremented by 1
- When **Eat Banana** is clicked the count of the bananas eaten should be incremented by 1

</details>

<details>
<summary>Implementation Files</summary>
<br/>

Use these files to complete the implementation:

- `src/components/FruitsCounter/index.js`
- `src/components/FruitsCounter/index.css`
</details>

### Quick Tips

<details>
<summary>Click to view</summary>
<br>

- **State updates are merged**. It means that when you update only one key-value pair in the `state` object, it will not affect the other key-value pairs in the state object.

  For example let's say your state is as followed:

  ```
  state = { key1 : value1, key2 : value2 }
  ```

  If you use this.setState such as :

  ```
  this.setState(prevState => ({key1: prevState + valueN}))
  ```

  Your new state will be :

  ```
  state = { key1 : value3, key2 : value2 }
  ```

- You can use the below cursor CSS property for buttons to set the type of mouse cursor, to show when the mouse pointer is over an element,

  ```
    cursor: pointer;
  ```

  <br/>
   <img src="https://assets.ccbp.in/frontend/content/react-js/cursor-pointer-img.png" alt="cursor pointer" style="width:100px" />

- You can use the below outline CSS property for buttons and input elements to remove the highlighting when the elements are clicked,

  ```
    outline: none;
  ```

</details>

### Resources

<details>
<summary>Image URLs</summary>

- [https://assets.ccbp.in/frontend/react-js/mango-img.png](https://assets.ccbp.in/frontend/react-js/mango-img.png) alt should be **mango**
- [https://assets.ccbp.in/frontend/react-js/banana-img.png](https://assets.ccbp.in/frontend/react-js/banana-img.png) alt should be **banana**

</details>

<details>
<summary>Colors</summary>

<br/>

<div style="background-color: #ffd569 ; width: 150px; padding: 10px; color: black">Hex: #ffd569</div>
<div style="background-color: #ffffff ; width: 150px; padding: 10px; color: black">Hex: #ffffff</div>
<div style="background-color: #000000 ; width: 150px; padding: 10px; color: white">Hex: #000000</div>
<div style="background-color: #007bff ; width: 150px; padding: 10px; color: white">Hex: #007bff</div>

</details>

<details>
<summary>Font-families</summary>

- Roboto

</details>

> ### _Things to Keep in Mind_
>
> - All components you implement should go in the `src/components` directory.
> - Don't change the component folder names as those are the files being imported into the tests.
> - **Do not remove the pre-filled code**
> - Want to quickly review some of the concepts you’ve been learning? Take a look at the Cheat Sheets.
# Fruits-Counter-react.JS

    
    /////index.css ////////////////////////////////////////
    .fruits-counter-container {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #ffd569;
  height: 100vh;
}

.fruits-counter {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #ffffff;
  border-radius: 16px;
  width: 90%;
  padding: 24px;
  max-width: 1110px;
}

@media screen and (min-width: 768px) {
  .fruits-counter {
    width: 80%;
    padding-top: 96px;
    padding-left: 64px;
    padding-right: 64px;
    padding-bottom: 96px;
  }
}

.count-text {
  text-align: center;
  color: #000000;
  font-family: 'Roboto';
  font-size: 20px;
  font-weight: 700;
}

@media screen and (min-width: 768px) {
  .count-text {
    font-size: 48px;
  }
}

.count {
  color: #ffd569;
}

.counters-control-container {
  display: flex;
  flex-direction: column;
}

@media screen and (min-width: 768px) {
  .counters-control-container {
    flex-direction: row;
  }
}

.counter-control {
  display: flex;
  flex-direction: column;
  margin-top: 32px;
  margin-left: 16px;
  margin-right: 16px;
}

@media screen and (min-width: 768px) {
  .counter-control {
    margin-top: 96px;
    margin-left: 48px;
    margin-right: 48px;
  }
}

.fruit-image {
  width: 200px;
  height: 175px;
}

@media screen and (min-width: 992px) {
  .fruit-image {
    width: 296px;
    height: 275px;
  }
}

.button-container {
  text-align: center;
  margin-top: 24px;
}

@media screen and (min-width: 768px) {
  .button-container {
    margin-top: 48px;
  }
}

.button {
  color: #ffffff;
  background-color: #007bff;
  font-size: 12px;
  font-family: 'Roboto';
  border: none;
  border-radius: 4px;
  padding-left: 16px;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-right: 16px;
  outline: none;
  cursor: pointer;
}

@media screen and (min-width: 768px) {
  .button {
    font-size: 16px;
  }
}

    
    
    ///////index.js/////////////////////////////////////////
    import {Component} from 'react'

import './index.css'

class FruitsCounter extends Component {
  state = {
    mangoesCount: 0,
    bananasCount: 0,
  }

  onClickEatBanana = () => {
    this.setState(prevState => ({bananasCount: prevState.bananasCount + 1}))
  }

  onClickEatMango = () => {
    this.setState(prevState => ({mangoesCount: prevState.mangoesCount + 1}))
  }

  render() {
    const {mangoesCount, bananasCount} = this.state

    return (
      <div className="fruits-counter-container">
        <div className="fruits-counter">
          <h1 className="count-text">
            Bob ate <span className="count">{mangoesCount}</span> mangoes
            <span className="count"> {bananasCount}</span> bananas
          </h1>
          <div className="counters-control-container">
            <div className="counter-control">
              <img
                src="https://assets.ccbp.in/frontend/react-js/mango-img.png"
                alt="mango"
                className="fruit-image"
              />
              <div className="button-container">
                <button
                  type="button"
                  className="button"
                  onClick={this.onClickEatMango}
                >
                  Eat Mango
                </button>
              </div>
            </div>
            <div className="counter-control">
              <img
                src="https://assets.ccbp.in/frontend/react-js/banana-img.png"
                alt="banana"
                className="fruit-image"
              />
              <div className="button-container">
                <button
                  type="button"
                  className="button"
                  onClick={this.onClickEatBanana}
                >
                  Eat Banana
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    )
  }
}

export default FruitsCounter

    
