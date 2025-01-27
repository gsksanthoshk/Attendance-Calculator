
<html>
<head>
    <title>Attendance Calculator</title>
    <style>
        h2{
            margin-top: 15px;
        }
        body {
            font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
            background-color:aquamarine;
            margin:0;
            padding:0; 
        }
        input{
            width: 14%;
            padding: 5px;
            margin: 0px 0;
            border: 0.5px solid #ccc;
        }
        button {
            background-color: #007bff;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 3px;
            cursor:pointer;
            margin-top: 10px;
        }
        button:hover {
            background-color: #0056b3;
        }
        #p{
            border-radius: 2px;
            margin: 2px;
        }
        #t{
            border-radius: 2px;
            margin: 2px;
        }
    </style>
<body>
    <h2 align="Center">75% Attendance Calculator</h2><hr>
    <p align ="Center">
    <label for="pr">Percentage Requirement: </label>
    <select id="pr">
        <option value="0"> </option>
        <option value="65">65%</option>
        <option value="75">75%</option>
        <option value="80">80%</option>
    </select><br>
    <label for="p">Present:</label>
    <input type ="number" id="p"><br>
    <label for="t">Total :  </label>
    <input type ="number" id="t"><br>
    <button onclick="calculateAttendance()">Calculate</button>
    <p id="result"></p>
    </p>
<script>
     function calculateAttendance() 
    {
    const total = Number(document.getElementById("t").value);
    const attended = Number(document.getElementById("p").value);
    const required = Number(document.getElementById("pr").value);
    if (total <= 0 || attended < 0 || required <= 0 || required > 100) {
        document.getElementById("result").innerText = "Enter valid numbers.";
        return;
    }
    const currentPercent = (attended / total) * 100;
    if (currentPercent >= required) {
        document.getElementById("result").innerText = `Your attendance is ${currentPercent.toFixed(2)}%. You meet the requirement of ${required}%.`;
    } 
    else 
    {
        const needed = Math.ceil((required / 100) * total) - attended;
        document.getElementById("result").innerText = `Your attendance is ${currentPercent.toFixed(2)}%. Attend ${needed} more classes to reach ${required}%.`;
    }
}
</script>

</body>
</head>
</html>
