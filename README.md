<!DOCTYPE html>
<html>
<head>
    <title>Countdown Timer</title>
</head>
<body>
    <div id="countdown"></div>

    <script>
        // Function to convert Western digits to Kurdish digits
        function westernToKurdishDigits(number) {
            const kurdishDigits = ['٠', '١', '٢', '٣', '٤', '٥', '٦', '٧', '٨', '٩'];
            return number.toString().replace(/\d/g, (d) => kurdishDigits[d]);
        }

        // Function to add leading zero if number is less than 10
        function addLeadingZero(number) {
            return number < 10 ? '0' + number : number;
        }

        // Set the date and time of the countdown (replace this with your desired end date)
        const countdownDate = new Date('2023-12-31T23:59:59').getTime();

        // Update the countdown every second
        const countdown = setInterval(function() {
            // Get the current date and time
            const now = new Date().getTime();

            // Calculate the time remaining
            const timeRemaining = countdownDate - now;

            // Calculate days, hours, minutes, and seconds
            const days = Math.floor(timeRemaining / (1000 * 60 * 60 * 24));
            const hours = Math.floor((timeRemaining % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((timeRemaining % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((timeRemaining % (1000 * 60)) / 1000);

            // Convert numbers to Kurdish digits with leading zeros
            const kurdishDays = westernToKurdishDigits(days);
            const kurdishHours = westernToKurdishDigits(addLeadingZero(hours));
            const kurdishMinutes = westernToKurdishDigits(addLeadingZero(minutes));
            const kurdishSeconds = westernToKurdishDigits(addLeadingZero(seconds));

            // Display the countdown in the "countdown" element using Kurdish digits with leading zeros
            document.getElementById('countdown').innerHTML = `
                <h1>کۆنترۆلی ژمارە شمێلەکان</h1>
                <p>${kurdishDays} ڕۆژ ${kurdishHours} کاتژمێر ${kurdishMinutes} خولەک ${kurdishSeconds} چرکە</p>
            `;

            // If the countdown is over, display a message
            if (timeRemaining < 0) {
                clearInterval(countdown);
                document.getElementById('countdown').innerHTML = `
                    <h1>کۆنترۆلی ژمارە شمێلەکان</h1>
                    <p>کۆنترۆل کردن کۆتاییە!</p>
                `;
            }
        }, 1000); // Update every second (1000 milliseconds)
    </script>
</body>
</html>
