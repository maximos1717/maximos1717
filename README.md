package main

import (
	"fmt"
	"net/http"
)

func handler(w http.ResponseWriter, r *http.Request) {
	// Write the HTML response
	html := `
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <title>My Go Web App</title>
	</head>
	<body>
	    <h1>Hello, Gophers!</h1>
	</body>
	</html>
	`
	fmt.Fprint(w, html)
}

func main() {
	// Handle requests to the root path ("/") with the handler function
	http.HandleFunc("/", handler)

	// Start the web server on port 8080
	fmt.Println("Server is running on http://localhost:8080")
	http.ListenAndServe(":8080", nil)
}
