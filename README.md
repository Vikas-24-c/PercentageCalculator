# PercentageCalculator
//index.html
<!DOCTYPE html>
<html>

<head>
    <title>student calculate</title>
    <!-- link for font  -->
    <link href=
"https://fonts.googleapis.com/css?family=Righteous&display=swap" 
          rel="stylesheet" />
    <link rel="stylesheet" href="style.css" />
</head>

<body>
    <!-- main html  -->
    <div class="container">
        <h1>Student grade calculator</h1>
        <div class="screen-body-item">
            <div class="app">
                <div class="form-group">
                    <!-- option for taking the input -->
                    <input type="text" 
                           class="form-control" 
                           placeholder="CHEMISTRY" 
                           id="chemistry" />
                </div>
                <div class="form-group">
                    <input type="text" 
                           class="form-control" 
                           placeholder="HINDI" id="hindi" />
                </div>
                <div class="form-group">
                    <input type="text" 
                           class="form-control" 
                           placeholder="MATHS" id="maths" />
                </div>
                <div class="form-group">
                    <input type="text" 
                           class="form-control" 
                           placeholder="PHYSICS" id="phy" />
                </div>
                <div>
                    <input type="button" 
                           value="show Percentage" 
                           class="form-button" 
                           onclick="calculate()" />
                </div>
            </div>
        </div>
        <!-- for showing the result-->
        <div class="form-group showdata">
            <p id="showdata"></p>
        </div>
    </div>
    <!--adding external javascript file-->
    <script src="script.js"></script>
</body>

</html>

//style.css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    background: #006600;
    font-size: 12px;
}

.container {
    flex: 0 1 700px;
    margin: auto;
    padding: 10px;
}

.screen-body-item {
    flex: 1;
    padding: 50px;
}

input {
    margin: 10px 10px 10px;
}

.showdata {
    color: black;
    font-size: 1.2rem;
    padding-top: 10px;
    padding-bottom: 10px;
}

//script.js
// Function for calculating grades
const calculate = () => {

    // Getting input from user into height variable.
    let chemistry = document.querySelector("#chemistry").value;
    let hindi = document.querySelector("#hindi").value;
    let maths = document.querySelector("#maths").value;
    let phy = document.querySelector("#phy").value;
    let grades = "";

    // Input is string so typecasting is necessary. */
    let totalgrades =
        parseFloat(chemistry) +
        parseFloat(hindi) +
        parseFloat(maths) +
        parseFloat(phy);

    // Checking the condition for the providing the 
    // grade to student based on percentage
    let percentage = (totalgrades / 400) * 100;
    if (percentage <= 100 && percentage >= 80) {
        grades = "A";
    } else if (percentage <= 79 && percentage >= 60) {
        grades = "B";
    } else if (percentage <= 59 && percentage >= 40) {
        grades = "C";
    } else {
        grades = "F";
    }
    // Checking the values are empty if empty than
    // show please fill them
    if (chemistry == "" || hindi == ""
        || maths == "" || phy == "") {
        document.querySelector("#showdata").innerHTML
            = "Please enter all the fields";
    } else {

        // Checking the condition for the fail and pass
        if (percentage >= 39.5) {
            document.querySelector(
                "#showdata"
            ).innerHTML =
                ` Out of 400 your total is  ${totalgrades} 
          and percentage is ${percentage}%. <br> 
          Your grade is ${grades}. You are Pass. `;
        } else {
            document.querySelector(
                "#showdata"
            ).innerHTML =
                ` Out of 400 your total is  ${totalgrades} 
          and percentage is ${percentage}%. <br> 
          Your grade is ${grades}. You are Fail. `;
        }
    }
};
