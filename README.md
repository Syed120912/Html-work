<?php
// sim-info.php
header('Content-Type: application/json');
$phone = $_GET['phone'] ?? null;

if ($phone) {
    // Connect to the database
    $conn = new mysqli('localhost', 'root', '', 'sim_data');

    // Check connection
    if ($conn->connect_error) {
        echo json_encode(['error' => 'Database connection failed']);
        exit;
    }

    // Query the database
    $query = $conn->prepare("SELECT * FROM sim_info WHERE phone = ?");
    $query->bind_param("s", $phone);
    $query->execute();
    $result = $query->get_result();

    if ($result->num_rows > 0) {
        echo json_encode($result->fetch_assoc());
    } else {
        echo json_encode(['message' => 'No data found']);
    }
    $conn->close();
} else {
    echo json_encode(['error' => 'Phone number is required']);
}
?>
