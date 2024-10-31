Agriculture Portal
Agriculture Portal is a machine learning-based project designed to provide predictions and recommendations for farmers. The system utilizes various algorithms to predict crops, recommend fertilizers, and provide rainfall and yield predictions, enabling farmers to make informed decisions about their crops.

Additionally, the portal supports direct crop sales to customers with a real payment interface using the Stripe API. Other supporting features include a chatbot powered by OpenAI's GPT-3.5-turbo model, weather forecasts for up to four days using the Weather API, and agriculture-related news using the News API.

Features
Crop Prediction: Predict the best crop based on location and season.
Crop Recommendation: Recommend suitable crops based on soil nutrients and environmental conditions.
Fertilizer Recommendation: Suggest the best fertilizers for specific crops and locations.
Rainfall Prediction: Forecast expected rainfall based on historical data.
Yield Prediction: Estimate the yield for specified crops in a given location.
OTP Verification: Secure verification through email.
Agriculture News: Stay updated with the latest news in agriculture.
Chatbot: Interactive chatbot using OpenAI's GPT-3.5-turbo model.
Weather Forecast: Get weather forecasts for up to four days.
Payment Interface: Direct crop sales with a real-time payment interface using Stripe API.
Technologies Used
Python
PHP
Pandas
NumPy
JavaScript
HTML/CSS
Bootstrap 4
Scikit-learn
Prerequisites
Before you start, ensure you have the following API keys:

News API
OpenWeatherMap API
Stripe API
OpenAI API
Gmail SMTP Setup: Set up an app password for Gmail.
Configuration
Open fsend_otp.php and csend_otp.php files and update the username and password.

php
Copy code
function smtp_mailer($to, $subject, $msg) {
    require_once("../smtp/class.phpmailer.php");
    $mail = new PHPMailer(); 
    $mail->IsSMTP(); 
    $mail->SMTPDebug = 0; 
    $mail->SMTPAuth = TRUE; 
    $mail->SMTPSecure = 'ssl'; 
    $mail->Host = "smtp.gmail.com";
    $mail->Port = 465; 
    $mail->IsHTML(true);
    $mail->CharSet = 'UTF-8';
    $mail->Username = "username@gmail.com"; // Change to your email address
    $mail->Password = "password"; // App Password
    $mail->SetFrom("username@gmail.com"); // App Password
    $mail->Subject = $subject;
    $mail->Body = $msg;
    $mail->AddAddress($to);
    return $mail->Send() ? 1 : 0;
}
Installation
Clone the repository to your local machine:

bash
Copy code
git clone https://github.com/vaishnavid0604/agriculture-portal.git
Navigate to the Farmers folder and install the required packages using pip:

bash
Copy code
pip install -r requirements.txt
Update Success URL and Cancel URL in customer/cbuy_crops.php:

php
Copy code
$session = \Stripe\Checkout\Session::create([
    'payment_method_types' => ['card'],
    'line_items' => [[
        'price_data' => [
            'product' => 'prod_NdAYaoDLX3DnMY',
            'unit_amount' => $TotalCartPrice,
            'currency' => 'inr',
        ],
        'quantity' => 1,
    ]],
    'mode' => 'payment',
    'success_url' => 'http://localhost/projects/agri2/customer/cupdatedb.php', // Change File Path
    'cancel_url' => 'http://localhost/projects/agri2/customer/cbuy_crops.php', // Change File Path
]);
Add your API keys to the respective files:

News API Key: fnewsfeed.php
OpenWeatherMap API Key: fweather_forecast.php
Stripe API Key: customer/stripePayment/config.php
OpenAI API Key: index.php and fchatgpt.php
Import the database from the db folder.

Run the Apache web server using XAMPP.

Dataset
The Crop Management System dataset includes the following features:

Crop Prediction Dataset

State_Name
District_Name
Season
Crop
Crop Recommendation Dataset

N
P
K
Temperature
Humidity
pH
Rainfall
Label
Fertilizer Recommendation Dataset

Temperature
Humidity
Soil Moisture
Soil Type
Crop Type
Nitrogen
Phosphorous
Potassium
Fertilizer Name
Rainfall Prediction Dataset

SUBDIVISION
YEAR
JAN - DEC (Monthly Rainfall)
ANNUAL
Jan-Feb
Mar-May
Jun-Sep
Oct-Dec
Yield Prediction Dataset

State_Name
District_Name
Crop_Year
Season
Crop
Area
Production
How to Use
Crop Prediction: Input State_Name, District_Name, and Season to predict the best crop for that location.
Crop Recommendation: Input N, P, K, Temperature, Humidity, pH, and Rainfall to get recommended crops.
Fertilizer Recommendation: Input Temperature, Humidity, Soil Moisture, Soil Type, Crop Type, Nitrogen, Phosphorous, and Potassium to get recommended fertilizers.
Rainfall Prediction: Input Subdivision and Year to predict rainfall.
Yield Prediction: Input State_Name, District_Name, Crop_Year, Season, Crop, Area, and Production to predict yields.
