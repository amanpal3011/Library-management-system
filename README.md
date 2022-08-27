# Library-management-system
<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<meta http-equiv="X-UA-Compatible" content="IE=edge">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Registration Form</title>
	<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>

	
	<style>
		body {
			background-image: url(book1.jpg);
			background-size: cover;
		}

		fieldset {
			border: 2px solid transparent;
			border-color: black;
			box-sizing: border-box;
			padding: 20px;
			border-radius: 10px;
			width: fit-content;
			background-color: rgba(240, 248, 255, 0.301);
		}

		legend {
			background-color: rgba(240, 248, 255, 0.315);
			padding-inline: 10px;
			border-radius: 10px;
			border-top: 2px solid transparent;
			border-color: black;
		}

		div {
			color: red;
			font-weight: bold;
			margin-left: 20px;
			font-size: small;
		}

		textarea,
		input {
			font-family: Verdana, Geneva, Tahoma, sans-serif;
		}

		#da {
			margin-left: 60px;
		}
	</style>
	<script>
		$(document).ready(function () {
			$("button").click(function () {
				alert("Do you want to submit the form !!");
			});
			$("#R_form").on({
				"click": function () {
					$(this).css("background", "grey");
				},
				"mouseover": function () {
					$(this).css("background", "white");
				},
				"mouseout": function () {
					$(this).css("background", "light blue");
				}
			})
		});
	</script>
	<script>

		function ValidateForm() {
			let returnValue = 1;
			let fname = document.getElementById('fname').value;
			let lname = document.getElementById('lname').value;
			let uname = document.getElementById('uname').value;
			let age = document.getElementById('age').value;
			let gen = document.getElementById('gen').value;
			let email = document.getElementById('email').value;
			let amail = document.getElementById('amail').value;
			let phone = document.getElementById('phone').value;
			let btn_used = document.getElementById('radio');
			let code = document.getElementById('code').value;
			let occ = document.getElementById('occ');
			let name_reg = /^[A-Za-z]+[$*@*]+[0-9]+/;
			let email_reg = /^[A-Za-z0-9]+[_]*[A-Za-z0-9]+@gmail.com$/;
			let phone_reg = /^[0-9]{10}$/
			if (uname == "") {
				alert("user name not found");
				document.R_form.uname.focus();
				returnValue = 0; return false;
			}
			if (uname.length < 8) {
				alert("user name Length is too short");
				document.R_form.uname.focus();
				returnValue = 0; return false;
			}
			if (name_reg.test(uname) == false) {
				alert("user name Format mismatch");
				document.R_form.uname.focus();
				returnValue = 0; return false;
			}
			if (age < 14 || age > 60) {
				alert("user between 14-60 registration only");
				document.R_form.age.focus();
				returnValue = 0; return false;
			}
			if (email_reg.test(email) == false) {
				alert("invalid Email ");
				document.R_form.email.focus();
				returnValue = 0; return false;
			}
			if (amail == email) {
				alert("alternate Email can not be same ");
				document.R_form.email.focus();
				returnValue = 0; return false;
			}
			if (phone_reg.test(phone) == false) {
				alert("invalid Phone Number ");
				document.R_form.phone.focus();
				returnValue = 0; return false;
			}
			if (code != code1) {
				alert("Human Validation Failure");
			}
			if (btn_used[1].checked) {
				alert("*Accept Terms and Conditions");
				returnValue = 0; return false;
			}
			if (returnValue == 1) {
				open('login.html', '_blank');
				return true;
			}
			else
				return false;
		}
	</script>
</head>

<body>
	<center>
		<fieldset>
			<legend>
				<h1>Registration Form</h1>
			</legend>
			<form id="R_form" name="R_form" method="post" onsubmit="ValidateForm()" action="register1.php">
				<table>
					<tr>
						<td>First Name <div id="red" style="display: inline-block;"> * </div>
						</td>
						<td><input name="fname" id="fname" type="text" value="" required></td>
						<td>
							<div id="fname_error"></div>
						</td>
					</tr>
					<tr>
						<td>Last Name<div id="red" style="display: inline-block;"> * </div>
						</td>
						<td><input name="lname" id="lname" type="text" value="" required></td>
						<td>
							<div id="lname_error"></div>
						</td>
					</tr>
					<tr>
						<td>User_Name<div id="red" style="display: inline-block;"> * </div>
						</td>
						<td><input name="uname" id="uname" type="text" value="" required></td>
						<td>
							<div id="lname_error"></div>
						</td>
					</tr>
					<tr>
						<td>Age <div id="red" style="display: inline-block;"> * </div>
						</td>
						<td><input name="age" id="age" type="number" value="" required></td>
						<td>
							<div id="age_error"></div>
						</td>
					</tr>
					<tr>
						<td>Gender<div id="red" style="display: inline-block;"> * </div>
						</td>
						<td><select name="gen" id="gen" required>
								<option value="male">Male</option>
								<option value="female">Female</option>
								<option value="other">other</option>
							</select></td>
						<td>
							<div id="gen_error"></div>
						</td>
					</tr>
					<tr>
						<td>Email ID<div id="red" style="display: inline-block;"> * </div>
						</td>
						<td><input name="email" id="email" type="email" value="" required></td>
						<td>
							<div id="email_error"></div>
						</td>
					</tr>
					<tr>
						<td>Alternate Mail ID<div id="red" style="display: inline-block;"> * </div>
						</td>
						<td><input name="amail" id="amail" type="email" value="" required></td>
						<td>
							<div id="amail_error"></div>
						</td>
					</tr>
					<tr>
						<td>Address<div id="red" style="display: inline-block;"> * </div>
						</td>
						<td><textarea type="text" name="faddress" rows="3" cols="20" required></textarea></td>
					</tr>
					<tr>
						<td>Phone<div id="red" style="display: inline-block;"> * </div>
						</td>
						<td><input name="phone" id="phone" type="text" value="" required></td>
						<td>
							<div id="phone_error"></div>
						</td>
					</tr>
					<tr>
						<td>Occupation<div id="red" style="display: inline-block;"> * </div>
						</td>
						<td><input type="text" name="occupation" value="" id="occ" required></td>
					</tr>

					<td>Enter Code Displayed below<div id="red" style="display: inline-block;"> * </div>
					</td>
					<td><input type="text" value="" required></td>
					</tr>
					<tr>
						<td colspan="2">
							<center>
								<fieldset style="border-color: red; text-align: center;">
									<p id="p"></p>
								</fieldset>
							</center>
						</td>
					</tr>
				</table>
				<br>
				<input type="radio" id="tnc" name="radio" required>
				<label for="tnc">I Agree Terms & Conditions</label>
				<input type="radio" id="da" name="radio">
				<label for="da">I Disgree</label>
				<br>
				<div id="tnc_error"></div>
				<br>
				<button type="submit" value="submit">SUBMIT</button>
			</form>
		</fieldset>
	</center>
</body>
</html>
<script>
	var code1 = Math.random();
	code1 = code1 * 10000;
	code1 = parseInt(code1);
	document.getElementById("p").innerHTML = code1;
</script>
