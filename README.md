window.onload = function() {

  const minutesDisplay = document.getElementById('minutes');
  const secondsDisplay = document.getElementById('seconds');
  const intervalInput = document.getElementById('interval');
  const startButton = document.getElementById('start');
  const pauseButton = document.getElementById('pause');
  const resetButton = document.getElementById('reset');


  let intervalId;
  let remainingTime;
  let intervalDuration = 1000;


  function startCountdown() {
    intervalDuration = intervalInput.value * 1000;
    intervalId = setInterval(updateCountdown, intervalDuration);
    startButton.disabled = true;
    pauseButton.disabled = false;
  }


  function pauseCountdown() {
    clearInterval(intervalId);
    startButton.disabled = false;
    pauseButton.disabled = true;
  }


  function resetCountdown() {
    clearInterval(intervalId);
    remainingTime = undefined;
    minutesDisplay.innerText = '00';
    secondsDisplay.innerText = '00';
    startButton.disabled = false;
    pauseButton.disabled = true;
  }


  function updateCountdown() {
    // Initialize remaining time on first update
    if (remainingTime === undefined) {
      remainingTime = intervalDuration;
    } else {
      remainingTime -= intervalDuration;
    }

 
    const minutes = Math.floor(remainingTime / 60000);
    const seconds = Math.floor((remainingTime % 60000) / 1000);

    // Display minutes and seconds with leading zeros
    minutesDisplay.innerText = padNumberWithLeadingZeros(minutes, 2);
    secondsDisplay.innerText = padNumberWithLeadingZeros(seconds, 2);


    if (remainingTime <= 0) {
      resetCountdown();
      alert('Countdown finished!');
    }
  }


  function padNumberWithLeadingZeros(number, length) {
    let result = number.toString();
    while (result.length < length) {
      result = '0' + result;
    }
    return result;
  }


  startButton.addEventListener('click', startCountdown);
  pauseButton.addEventListener('click', pauseCountdown);
  resetButton.addEventListener('click', resetCountdown);
};
