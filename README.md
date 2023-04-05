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
  if (remainingTime === undefined) {
    remainingTime = intervalDuration;
  } else {
    remainingTime -= intervalDuration;
  }
  
  const minutes = Math.floor(remainingTime / 60000);
  const seconds = Math.floor((remainingTime % 60000) / 1000);
  
  minutesDisplay.innerText = padTime(minutes);
  secondsDisplay.innerText = padTime(seconds);
  
  if (remainingTime <= 0) {
    resetCountdown();
    alert('Countdown finished!');
  }
}

function padTime(time) {
  return time < 10 ? `0${time
