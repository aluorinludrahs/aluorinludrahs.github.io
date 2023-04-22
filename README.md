<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Accounting Software</title>
</head>
<body>
  <h1>Accounting Software</h1>
  <h2>Journal Entry</h2>
  <form action="journal_entry.php" method="post">
    <div>
      <label for="date">Date</label>
      <input type="date" name="date" id="date">
    </div>
    <div>
      <label for="narration">Narration</label>
      <textarea name="narration" id="narration" rows="3" cols="50"></textarea>
    </div>
    <div>
      <label for="debit">Debit</label>
      <input type="text" name="debit" id="debit">
    </div>
    <div>
      <label for="credit">Credit</label>
      <input type="text" name="credit" id="credit">
    </div>
    <div>
      <input type="submit" value="Submit">
    </div>
  </form>
  <h2>Ledger</h2>
  <table>
    <thead>
      <tr>
        <th>Account Name</th>
        <th>Debit</th>
        <th>Credit</th>
        <th>Balance</th>
      </tr>
    </thead>
    <tbody>
    </tbody>
  </table>
  <h2>Trial Balance</h2>
  <table>
    <thead>
      <tr>
        <th>Account Name</th>
        <th>Debit</th>
        <th>Credit</th>
      </tr>
    </thead>
    <tbody>
    </tbody>
  </table>
  <h2>Profit and Loss Account</h2>
  <table>
    <thead>
      <tr>
        <th>Account Name</th>
        <th>Debit</th>
        <th>Credit</th>
      </tr>
    </thead>
    <tbody>
    </tbody>
  </table>
  <h2>Trading Account</h2>
  <table>
    <thead>
      <tr>
        <th>Account Name</th>
        <th>Debit</th>
        <th>Credit</th>
      </tr>
    </thead>
    <tbody>
    </tbody>
  </table>
  <h2>Balance Sheet</h2>
  <table>
    <thead>
      <tr>
        <th>Account Name</th>
        <th>Debit</th>
        <th>Credit</th>
      </tr>
    </thead>
    <tbody>
    </tbody>
  </table>
  <h2>Cash Flow Statement</h2>
  <table>
    <thead>
      <tr>
        <th>Account Name</th>
        <th>Debit</th>
        <th>Credit</th>
      </tr>
    </thead>
    <tbody>
    </tbody>
  </table>
</body>
</html>
