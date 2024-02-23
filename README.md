package main

import (
	"fmt"
	"time"
)

const (
	expectedUsername = "nabil"
	expectedPassword = "maxi"
)

func authenticate(username, password string) bool {
	return username == expectedUsername && password == expectedPassword
}

func main() {
	// Demander à l'utilisateur de saisir le nom d'utilisateur
	fmt.Print("Entrez le nom d'utilisateur : ")
	var username string
	fmt.Scanln(&username)

	// Demander à l'utilisateur de saisir le mot de passe
	fmt.Print("Entrez le mot de passe : ")
	var password string
	fmt.Scanln(&password)

	// Vérifier l'authentification
	if authenticate(username, password) {
		fmt.Println("Authentification réussie!")
	} else {
		fmt.Println("Nom d'utilisateur ou mot de passe incorrect.")
		// Facultatif : vous pouvez quitter le programme ici si l'authentification échoue.
		// os.Exit(1)
	}

	fmt.Println("Appuyez sur Enter pour démarrer le chronomètre.")
	fmt.Scanln()

	startTime := time.Now()

	fmt.Println("Chronomètre démarré. Comptage de 1 à 100.")
	countTo100()

	endTime := time.Now()

	duration := endTime.Sub(startTime)
	fmt.Printf("Le chronomètre a fonctionné pendant : %s\n", duration)
}

// countTo100 effectue un comptage de 1 à 100.
func countTo100() {
	for i := 1; i <= 100; i++ {
		fmt.Println(i)
		time.Sleep(time.Second) // Attendez une seconde entre chaque nombre.
	}
}
