
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Milk Production Management System</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">
    <style>
        /* Global Styles */
        body {
            font-family: 'Poppins', sans-serif;
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            background-color: #f4f4f9;
            color: #333;
        }

        /* Navbar */
        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 2rem;
            background-color: #0078d7;
            color: white;
        }

        .navbar h1 {
            margin: 0;
            font-size: 1.5rem;
        }

        .navbar ul {
            list-style: none;
            margin: 0;
            padding: 0;
            display: flex;
        }

        .navbar ul li {
            margin-left: 1.5rem;
        }

        .navbar ul li a {
            color: white;
            text-decoration: none;
            font-weight: bold;
        }

        .navbar ul li a:hover {
            text-decoration: underline;
        }

        /* Section Styles */
        main {
            padding: 2rem;
        }

        section {
            margin-bottom: 2rem;
        }

        h2 {
            font-size: 1.75rem;
            color: #0078d7;
            margin-bottom: 1rem;
        }

        /* Card Styles */
        .card {
            background-color: white;
            padding: 1rem;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            margin-bottom: 1rem;
        }

        .card h3 {
            margin: 0 0 0.5rem;
            font-size: 1.25rem;
        }

        .card p {
            margin: 0;
            font-size: 1rem;
            font-weight: bold;
        }

        /* Table Styles */
        table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 1rem;
            background-color: white;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        table thead th {
            background-color: #0078d7;
            color: white;
            padding: 0.75rem;
            text-align: left;
        }

        table tbody td {
            padding: 0.75rem;
            border-bottom: 1px solid #ddd;
        }

        /* Form Styles */
        form {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            background-color: white;
            padding: 1rem;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            margin-bottom: 1rem;
        }

        form input {
            flex: 1 1 calc(50% - 1rem);
            padding: 0.5rem;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        form button {
            padding: 0.5rem 1rem;
            background-color: #0078d7;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        form button:hover {
            background-color: #005bb5;
        }

        /* Search Bar */
        #search-bar {
            margin: 1rem 0;
            display: flex;
            justify-content: center;
        }

        #search-bar input {
            width: 80%;
            padding: 0.5rem;
            font-size: 1rem;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        #search-bar button {
            padding: 0.5rem 1rem;
            background: #0078d7;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin-left: 0.5rem;
        }

        #search-bar button:hover {
            background-color: #005bb5;
        }

        /* Summary Section */
        #summary-section {
            margin: 2rem 0;
            background: #fff8e5;
            padding: 1.5rem;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        #summary-section h3 {
            color: #ff8c00;
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 1rem;
            background-color: #0078d7;
            color: white;
        }
    </style>
</head>
<body>
    <header>
        <nav class="navbar">
            <h1>Milk Management System</h1>
            <ul>
                <li><a href="#dashboard">Dashboard</a></li>
                <li><a href="#person">Person</a></li>
                <li><a href="#manager">Manager</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <!-- Dashboard Section -->
        <section id="dashboard">
            <h2>Dashboard</h2>
            <div class="card">
                <h3>Total Milk Available</h3>
                <p id="total-milk">0 Liters</p>
            </div>
            <div class="card">
                <h3>Daily Collection</h3>
                <p id="daily-collection">0 Liters</p>
            </div>
        </section>

        <!-- Summary Section -->
        <section id="summary-section">
            <h3>Monthly Summary</h3>
            <p>Total Milk Collected: <span id="total-monthly-milk">0 Liters</span></p>
            <p>Highest Contributor: <span id="highest-contributor">N/A</span></p>
            <p>Average Daily Collection: <span id="average-daily">0 Liters</span></p>
        </section>

        <!-- Person Section -->
        <section id="person">
            <h2>Person Details</h2>
            <div id="search-bar">
                <input type="text" id="search-input" placeholder="Search Contributor by Name...">
                <button onclick="searchContributor()">Search</button>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Name</th>
                        <th>Date</th>
                        <th>Milk Contributed (Liters)</th>
                        <th>Payment (Rs)</th>
                    </tr>
                </thead>
                <tbody id="person-table">
                    <!-- Data will be populated dynamically -->
                </tbody>
            </table>
        </section>

        <!-- Manager Section -->
        <section id="manager">
            <h2>Manager Controls</h2>
            <form id="add-milk-form">
                <input type="text" id="person-name" placeholder="Person Name" required>
                <input type="number" id="milk-quantity" placeholder="Milk Quantity (Liters)" min="0.1" step="0.1" required>
                <button type="submit">Add Milk</button>
            </form>
            <button onclick="exportToCSV()">Export Data as CSV</button>
        </section>
    </main>

    <footer>
        <p>&copy; 2024 Milk Production Management System</p>
    </footer>

    <script>
        // Dynamic Variables
        let totalMilkAmount = 0;
        let contributors = [];
        const ratePerLiter = 50;

        // Add Milk Form
        document.getElementById('add-milk-form').addEventListener('submit', (e) => {
            e.preventDefault();
            const name = document.getElementById('person-name').value;
            const quantity = parseFloat(document.getElementById('milk-quantity').value);

            // Update Milk Amount
            totalMilkAmount += quantity;

            const existingContributor = contributors.find(c => c.name === name);
            if (existingContributor) {
                existingContributor.total += quantity;
            } else {
                contributors.push({ name, total: quantity });
            }

            updateDashboard(quantity);
            updatePersonTable();
            updateSummary();
            e.target.reset();
        });

        // Update Dashboard
        function updateDashboard(quantity) {
            document.getElementById('total-milk').textContent = `${totalMilkAmount} Liters`;
            document.getElementById('daily-collection').textContent = `${quantity} Liters`;
        }

        // Update Person Table
        function updatePersonTable() {
            const table = document.getElementById('person-table');
            table.innerHTML = '';
            contributors.forEach(({ name, total }) => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${name}</td>
                    <td>${new Date().toLocaleDateString()}</td>
                    <td>${total} Liters</td>
                    <td>${(total * ratePerLiter).toFixed(2)} Rs</td>
                `;
                table.appendChild(row);
            });
        }

        // Update Summary
        function updateSummary() {
            const highestContributor = contributors.reduce((max, c) => (c.total > max.total ? c : max), { total: 0 });
            const averageDaily = (totalMilkAmount / new Date().getDate()).toFixed(2);
            document.getElementById('total-monthly-milk').textContent = `${totalMilkAmount} Liters`;
            document.getElementById('highest-contributor').textContent = highestContributor.name || 'N/A';
            document.getElementById('average-daily').textContent = `${averageDaily} Liters`;
        }

        // Search Contributors
        function searchContributor() {
            const query = document.getElementById('search-input').value.toLowerCase();
            const filtered = contributors.filter(c => c.name.toLowerCase().includes(query));
            const table = document.getElementById('person-table');
            table.innerHTML = '';
            filtered.forEach(({ name, total }) => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${name}</td>
                    <td>${new Date().toLocaleDateString()}</td>
                    <td>${total} Liters</td>
                    <td>${(total * ratePerLiter).toFixed(2)} Rs</td>
                `;
                table.appendChild(row);
            });
        }

        // Export Data to CSV
        function exportToCSV() {
            let csvContent = 'data:text/csv;charset=utf-8,Name,Date,Milk Contributed (Liters),Payment (Rs)\n';
            contributors.forEach(({ name, total }) => {
                csvContent += `${name},${new Date().toLocaleDateString()},${total},${(total * ratePerLiter).toFixed(2)}\n`;
            });
            const encodedUri = encodeURI(csvContent);
            const link = document.createElement('a');
            link.setAttribute('href', encodedUri);
            link.setAttribute('download', 'milk_data.csv');
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        }
    </script>
</body>
</html>
