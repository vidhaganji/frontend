---
layout: base
title: journal
permalink: /journal/
--- 

<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Daily Journal</title>
   <link rel="stylesheet" href="style.css">
</head>
<body>
   <div class="container">
       <h1>Daily Journal</h1>
       <div id="word-of-the-day"></div>
       <textarea id="journal-entry" placeholder="Write about today's word..."></textarea>
       <button id="save-entry">Save Entry</button>
   </div>

   <script>
   const words = ['serendipity', 'ephemeral', 'quixotic', 'resilience', 'effervescent'];

function getRandomWord() {
   return words[Math.floor(Math.random() * words.length)];
}

function displayWordOfTheDay() {
   const wordElement = document.getElementById('word-of-the-day');
   const randomWord = getRandomWord();
   wordElement.textContent = `Word of the Day: ${randomWord}`;
}

function saveEntry() {
   const entry = document.getElementById('journal-entry').value;
   if (entry.trim() !== '') {
       localStorage.setItem('journalEntry', entry); // Save entry to local storage
       alert('Entry saved successfully!');
       document.getElementById('journal-entry').value = ''; // Clear the textarea after saving
       window.location.href = 'reflect.md'; // Redirect to the reflect page
   } else {
       alert('Please write something before saving!');
   }
}

// Display a new word of the day when the page loads
window.onload = function() {
   displayWordOfTheDay();
}

document.getElementById('save-entry').addEventListener('click', saveEntry);
   </script>
</body>
</html>
