<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Welcome Bonus - Join Now</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: linear-gradient(to bottom, #0f2027, #203a43, #2c5364);
      color: white;
      text-align: center;
      padding: 50px 20px;
    }
    h1 {
      font-size: 32px;
      margin-bottom: 20px;
    }
    p {
      font-size: 18px;
    }
    .btn {
      background: #ff5722;
      color: white;
      padding: 15px 30px;
      border: none;
      border-radius: 10px;
      font-size: 18px;
      margin-top: 30px;
      cursor: pointer;
    }
    .btn:hover {
      background: #e64a19;
    }
    .footer {
      margin-top: 60px;
      font-size: 14px;
      color: #ccc;
    }
  </style>
</head>
<body>

  <h1>🎁 Claim Your Welcome Bonus Now!</h1>
  <p>Get started in seconds. Safe, fast, and rewarding!</p>

  <button class="btn" id="redirectBtn">Join Now</button>

  <div class="footer">
    Privacy Policy | Terms & Conditions
  </div>

  <!-- Facebook Pixel Script (dynamic load) -->
  <script>
    function loadFbPixel(pixelId) {
      !function(f,b,e,v,n,t,s) {
        if(f.fbq)return;n=f.fbq=function(){n.callMethod?
        n.callMethod.apply(n,arguments):n.queue.push(arguments)};
        if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
        n.queue=[];t=b.createElement(e);t.async=!0;
        t.src=v;s=b.getElementsByTagName(e)[0];
        s.parentNode.insertBefore(t,s)
      }(window, document,'script',
        'https://connect.facebook.net/en_US/fbevents.js');

      fbq('init', pixelId);
      fbq('track', 'PageView');
      console.log('FB Pixel loaded:', pixelId);
    }

    // Get URL Parameters
    const urlParams = new URLSearchParams(window.location.search);
    const affiliateCode = urlParams.get('affiliateCode');
    const fbPixelId = urlParams.get('fbPixelId');
    const redirectUrl = "https://targetwebsite.com?ref=" + (affiliateCode || 'default');

    // Log tracking info (optional - you can send to Google Sheet later)
    console.log("Tracking Info:", {
      affiliateCode,
      fbPixelId,
      utm_source: urlParams.get('utm_source'),
      utm_campaign: urlParams.get('utm_campaign'),
    });

    // Load Facebook Pixel if ID present
    if (fbPixelId) {
      loadFbPixel(fbPixelId);
    }

    // Redirect on button click
    document.getElementById("redirectBtn").addEventListener("click", function () {
      window.location.href = redirectUrl;
    });

    // Optional: Auto redirect after 5 seconds
    setTimeout(() => {
      window.location.href = redirectUrl;
    }, 5000);
  </script>
</body>
</html>
