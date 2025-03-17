<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Number Tracker Game</title>
</head>
<body>
    <script>
        class NumberTracker {
  constructor() {
    this.validNumbers = new Set([0, "00", 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36]);
    this.colorMap = {
      red: new Set([1, 3, 5, 7, 9, 12, 14, 16, 18, 19, 21, 23, 25, 27, 30, 32, 34, 36]),
      black: new Set([2, 4, 6, 8, 10, 11, 13, 15, 17, 20, 22, 24, 26, 28, 29, 31, 33, 35]),
      green: new Set([0, "00"])
    };
    this.numbers = JSON.parse(localStorage.getItem("numbers")) || Array.from({ length: 36 }, (_, i) => i + 1);
    this.undoStack = [];
    this.checkPassword();
  }

  checkPassword() {
    document.body.innerHTML = "";
    const passwordInput = document.createElement("input");
    passwordInput.type = "password";
    passwordInput.placeholder = "Enter password";
    
    const submitButton = document.createElement("button");
    submitButton.textContent = "Submit";
    submitButton.addEventListener("click", () => {
      if (passwordInput.value === "paul") {
        document.body.innerHTML = "";
        this.createUI();
        this.render();
      } else {
        alert("Incorrect password. Try again.");
      }
    });
    
    document.body.append(passwordInput, submitButton);
  }

  createUI() {
    this.inputField = document.createElement("input");
    this.inputField.type = "text";
    this.inputField.addEventListener("keydown", (e) => this.handleKeydown(e));
    
    this.undoButton = document.createElement("button");
    this.undoButton.textContent = "Undo";
    this.undoButton.addEventListener("click", () => this.undoLastEntry());
    
    this.voiceButton = document.createElement("button");
    this.voiceButton.textContent = "Start Voice Input";
    this.voiceButton.addEventListener("click", () => this.initVoiceRecognition());
    
    this.voiceStatus = document.createElement("p");
    this.voiceStatus.textContent = "Tap 'Start Voice Input' to begin...";
    
    this.message = document.createElement("div");
    this.warning = document.createElement("p");
    this.errorMessage = document.createElement("p");
    this.errorMessage.style.color = "red";
    
    document.body.append(this.inputField, this.undoButton, this.voiceButton, this.voiceStatus, this.message, this.warning, this.errorMessage);
  }

  render() {
    document.body.innerHTML = "";
    this.createUI();
    const container = document.createElement("div");
    container.style.display = "flex";
    container.style.gap = "5px";
    
    this.numbers.forEach((n) => {
      const span = document.createElement("span");
      span.textContent = `| ${n} `;
      span.style.padding = "5px";
      span.style.fontWeight = "bold";
      span.style.fontSize = "18px";
      
      if (this.colorMap.red.has(n)) span.style.color = "red";
      else if (this.colorMap.black.has(n)) span.style.color = "black";
      else if (this.colorMap.green.has(n)) span.style.color = "green";
      
      container.appendChild(span);
    });
    
    document.body.prepend(container);
  }

  handleKeydown(event) {
    if (event.key === "Enter") {
      this.processInput(this.inputField.value.trim());
    }
  }

  processInput(input) {
    let newNumber = input.toLowerCase().trim();
    if (newNumber === "single zero") {
      newNumber = 0;
    } else if (newNumber === "double zero") {
      newNumber = "00";
    } else {
      newNumber = input.replace(/[^0-9]/g, "");
      newNumber = parseInt(newNumber, 10);
    }
    
    if (!this.validNumbers.has(newNumber)) {
      this.errorMessage.textContent = "Invalid entry. Please enter a valid number.";
      this.inputField.value = "";
      return;
    }
    this.errorMessage.textContent = "";
    
    this.undoStack.push([...this.numbers]);
    this.numbers.shift();
    this.numbers.push(newNumber);
    this.inputField.value = "";
    this.checkForTriples();
    this.checkForUpcomingRemoval();
    this.saveProgress();
    this.render();
  }
  
  undoLastEntry() {
    if (this.undoStack.length > 0) {
      this.numbers = this.undoStack.pop();
      this.saveProgress();
      this.render();
    }
  }
  
  checkForTriples() {
    const countMap = {};
    this.message.innerHTML = "";
    for (const num of this.numbers) {
      countMap[num] = (countMap[num] || 0) + 1;
      if (countMap[num] === 3) {
        const msg = document.createElement("p");
        msg.textContent = `Number ${num} appears 3 times!`;
        this.message.appendChild(msg);
      }
    }
  }
  
  checkForUpcomingRemoval() {
    const firstNumber = this.numbers[0];
    if (this.numbers.filter(n => n === firstNumber).length === 3) {
      this.warning.textContent = `Warning: ${firstNumber} is about to be removed, preventing it from appearing 3 times again.`;
    } else {
      this.warning.textContent = "";
    }
  }
  
  saveProgress() {
    localStorage.setItem("numbers", JSON.stringify(this.numbers));
  }
  
  initVoiceRecognition() {
    if (!('webkitSpeechRecognition' in window || 'SpeechRecognition' in window)) {
      this.errorMessage.textContent = "Voice recognition is not supported in this browser.";
      return;
    }
    
    const recognition = new (window.SpeechRecognition || window.webkitSpeechRecognition)();
    recognition.lang = "en-US";
    recognition.continuous = false;
    recognition.interimResults = false;
    
    recognition.onstart = () => {
      this.voiceStatus.textContent = "Listening...";
    };
    
    recognition.onresult = (event) => {
      let spokenText = event.results[0][0].transcript.trim();
      this.inputField.value = spokenText;
      this.processInput(spokenText);
      this.voiceStatus.textContent = "Tap 'Start Voice Input' to begin...";
    };
    
    recognition.onerror = () => {
      this.errorMessage.textContent = "Could not recognize speech. Try again.";
      this.voiceStatus.textContent = "Tap 'Start Voice Input' to begin...";
    };
    
    recognition.start();
  }
}

new NumberTracker();

    </script>
</body>
</html>
