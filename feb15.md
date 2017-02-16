# LJ Code 201 - Day 8 (Feb 15)

Today, I:

- Successfully debugged by Staff Table, basically alone. Here was the problem: I was using a nested for loop to pull the values and length of random customers array, iterate through it to create a value for staff, write the math problem to find that value for staff, and then iterate through it again to actually push the value to the DOM.
    - I had a few issues:
        * I was using a return statement inside my second for loop (the inner-most one). The return was killing my loop after iterating through only the zero index.
        * I didn't really need to be using two for loops; everything I needed to do could be done inside one for loop within my generateStaffTable() function.
    - I ultimately solved the problem, which felt amazing.
- Learned about event listeners and forms. Event handlers are much more simple to use with the DOM than, say, a table would be. I can use eventListeners for mouse, keyboard, forms, etc.
- Learned that event listeners require an event handler, which is essentially their method/function to run after being triggered. The event listener is really only listening; it needs the handler to execute.
- Successfully built my form, and generated a new store within my event handler function.
- Made my code more DRY (with Jon's help) by creating one array for all of my store values, pushing any new stores created into that array (in the event handler) and creating a function that populated all stores from the array.
- Tried my hand at creating the 'Total' row, but I can't figure out the calculations. Pasted what I have so far below.
    * Still pretty frustrated by this, but I feel I might be able to figure it out. The real concern this brings up is that I still clearly don't understand nested for loops.

Reflections on today: I felt a lot better today than I did yesterday or Monday. The course is definitely starting to make sense, I'm starting to feel more comfortable debugging and running my code and thinking about my problems in a logical way. 

Aaron said that we didn't have to do the learning journal anymore, but I honestly find this 10 mins of reflecting on the day and writing about what I learned and how I processed it to be very helpful. Plus, I had a really good day today, and I want to brag. :P

----------------
// Sales: generate footer row
function renderFooter() {
  // pull from 'table' in DOM, creater tfooter, append tfooter
  var storeTable = document.getElementById('table-sales');
  var tableFooter = document.createElement('tfooter');
  storeTable.appendChild(tableFooter);

  // append table row to footer
  var tableRow = document.createElement('tr');
  tableFooter.appendChild(tableRow);

  // add "Totals" box to table
  var totalTh = document.createElement('th');
  totalTh.textContent = 'Hourly Totals';
  tableRow.appendChild(totalTh);

    // for loop iterating through each value of todayResults for all stores and summing them
    // math that sums values for table column
  var totalAllStores = 0;
  var hourTotal;
  var hourTd;
  var dailyTotalTd;
  
  for (var i = 0; i < storeHours.length; i++) {
    hourTotal = 0;

    for (var j = 0; j < allStores.length; j++) {
      hourTotal += allStores[j].todayResults[i];
      console.log(hourTotal);
    }
    totalCookiesPerHour.push(hourTotal);
    console.log(totalCookiesPerHour);
    // create td element and append to tableRow
    hourTd = document.createElement('td');
    hourTd.textContent = hourTotal;
    tableRow.appendChild(hourTd);

    totalAllStores += hourTotal;
  }
  
  dailyTotalTd = document.createElement('td');
  dailyTotalTd.textContent = totalAllStores;
  tableRow.appendChild(dailyTotalTd);
};