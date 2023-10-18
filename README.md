//Lester S.

<?php
require_once('DB_config.php');

if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $Account_Name = $_POST['Account_Name'];
    $Balance = floatval($_POST['Balance']);
    $Account_Type = $_POST['Account_Type'];
    $Password = $_POST['Password'];

    if ($Balance < 0) {
        echo "Balance cannot be negative.";
    } else {
        $sql = "INSERT INTO Bank_Account (Account_Name, Balance, Account_Type, Password) VALUES (?, ?, ?, ?)";
        $stmt = $conn->prepare($sql);
        $stmt->bind_param("sdss", $Account_Name, $Balance, $Account_Type, $Password);

        if ($stmt->execute()) {
            echo "Account registered successfully!";
        } else {
            echo "Error registering the account: " . $stmt->error;
        }
        $stmt->close();
    }
}
?>
<!DOCTYPE html>
<html>
<head>
    <title>Bank Account Registration</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>Bank Account Registration</h1>
    <form class="form" method="post" action="Registration.php">
        <label for="Account_ID">Account ID:</label>
        <input type="text" name="Account_Name" required><br>

        <label for="Account Name">Account Name:</label>
        <input type="text" name="Account_Name" required><br>
        

        <label for="Balance">Initial Balance:</label>
        <input type="number" name="Balance" step="0.01" required><br>


        <label for="Password">Password:</label>
        <input type="password" name="Password" required><br>

        <input type="submit" value="Submit">
    </form>
</body>
</html>
// John Edcel R.
<style>
/* Apply styles to the body of the page */
body {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
  margin: 0;
  padding: 0;
  text-align: center;
}

/* Style the registration form */
.form {
  max-width: 400px;
  margin: 0 auto;
  background-color: #fff;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

/* Style the heading */
h1 {
  color: #333;
}

/* Style form labels */
label {
  display: block;
  margin-top: 10px;
  color: #555;
  font-weight: bold;
}

/* Style form input fields */
input[type="text"],
input[type="number"],
input[type="password"] {
  width: 100%;
  padding: 10px;
  margin-top: 5px;
  margin-bottom: 15px;
  border: 1px solid #ccc;
  border-radius: 3px;
}

/* Style the submit button */
input[type="submit"] {
  background-color: #007BFF;
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 3px;
  cursor: pointer;
}

input[type="submit"]:hover {
  background-color: #0056b3;
}

/* Style form validation messages */
input:invalid {
  border: 1px solid #ff6347;
}

/* Customize other styles as needed */
</style># db_bank
