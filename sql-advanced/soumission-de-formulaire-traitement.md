<?php 

// 1- vérif si formulaire soumis
if(isset($_POST['register']))
{
	//2-initialise le tableau d'erreur
	$errors=[];
	//3- vérifie si toutes les données sont remplies => normalement mais on remplace par une fonction créé dans le fichier functions.php
	///if(!empty($_POST['pseudo']) && !empty($_POST['email']))
	if(not_empty(['pseudo','password','email']))

		{
			//4 extrait les valeurs de post
			extract($_POST);	
			// 5- réalise les différents tests et alimente le tableau d'erreur si des données sont mal remplies
		
			// 5.1 test longueur pseudo
			if(mb_strlen($pseudo) < 4)
			{
				$errors[]="pseudo trop court";
			}

			//5.2 test mail valide 
			if(!filter_var($email,FILTER_VALIDATE_EMAIL))
			{
				$errors[]="mail non valide";

			}
			//5.3 test si pseudo existe déja -> renvoi 0  ou 1 c'est à dire false ou true si true -> existe déja
			if(already_in_use('pseudo', $pseudo, 'user_table'))
			{
				$errors[]="le pseudo existe déja";
			}

			//5.4 test pwd correspodent
			
			//6 si aucune erreur, on traite
			if(count($errors==00))
			{

			}

		}
		else
		{
			$errors[]="merci de remplir tous les champs";
		}

}


 ?>