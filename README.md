window.onload = function() {
  // Get DOM elements
  const minutesDisplay = document.getElementById('minutes');
  const secondsDisplay = document.getElementById('seconds');
  const intervalInput = document.getElementById('interval');
  const startButton = document.getElementById('start');
  const pauseButton = document.getElementById('pause');
  const resetButton = document.getElementById('reset');

  // Declare variables
  let intervalId;
  let remainingTime;
  let intervalDuration = 1000;

  // Start the countdown
  function startCountdown() {
    intervalDuration = intervalInput.value * 1000;
    intervalId = setInterval(updateCountdown, intervalDuration);
    startButton.disabled = true;
    pauseButton.disabled = false;
  }

  // Pause the countdown
  function pauseCountdown() {
    clearInterval(intervalId);
    startButton.disabled = false;
    pauseButton.disabled = true;
  }

  // Reset the countdown
  function resetCountdown() {
    clearInterval(intervalId);
    remainingTime = undefined;
    minutesDisplay.innerText = '00';
    secondsDisplay.innerText = '00';
    startButton.disabled = false;
    pauseButton.disabled = true;
  }

  // Update the countdown timer
  function updateCountdown() {
    // Initialize remaining time on first update
    if (remainingTime === undefined) {
      remainingTime = intervalDuration;
    } else {
      remainingTime -= intervalDuration;
    }

    // Calculate minutes and seconds
    const minutes = Math.floor(remainingTime / 60000);
    const seconds = Math.floor((remainingTime % 60000) / 1000);

    // Display minutes and seconds with leading zeros
    minutesDisplay.innerText = padNumberWithLeadingZeros(minutes, 2);
    secondsDisplay.innerText = padNumberWithLeadingZeros(seconds, 2);

    // Reset the countdown and display an alert when it reaches zero
    if (remainingTime <= 0) {
      resetCountdown();
      alert('Countdown finished!');
    }
  }

  // Pad a number with leading zeros to a specific length
  function padNumberWithLeadingZeros(number, length) {
    let result = number.toString();
    while (result.length < length) {
      result = '0' + result;
    }
    return result;
  }

  // Add event listeners to buttons
  startButton.addEventListener('click', startCountdown);
  pauseButton.addEventListener('click', pauseCountdown);
  resetButton.addEventListener('click', resetCountdown);
};
