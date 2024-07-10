let totalResponses = 0;
 
 function respondToVacancies() {
  // Find all response buttons and click on them
  let buttons = document.querySelectorAll('[data-qa="vacancy-serp__vacancy_response"]');
  buttons.forEach(button => {
  button.click();
  totalResponses++;
  });
 
  // Check if we reached the limit of 300 responses
  if (totalResponses >= 300) {
  console.log("Reached 200 responses. Stopping...");
  return;
  }
 
  // Find the next page button and click on it
  let nextPageButton = document.querySelector('[data-qa="pager-next"]');
  if (nextPageButton) {
  nextPageButton.click();
  
  // Use a timeout to wait for the next page to load and then continue the process
  setTimeout(respondToVacancies, 3000); // Wait 3 seconds for the next page to load
  } else {
  console.log("No more pages to navigate. Stopping...");
  }
 }
 
 // Start the process
 respondToVacancies();
