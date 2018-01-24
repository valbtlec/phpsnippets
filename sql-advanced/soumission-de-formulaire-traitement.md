 * méthode : 
1- vérif si formulaire soumis
2-initialise le tableau d'erreur
3- vérifie si toutes les données sont remplies (création d'un fn générique qui prend en parametre la clé POST, la valeur de ce post, la table )
4 extrait les valeurs de post
5- réalise les différents tests et alimente le tableau d'erreur si des données sont mal remplies
	5.1 test longueur pseudo
	5.2 test mail valide 
	5.3 test si pseudo existe déja -> renvoi 0  ou 1 c'est à dire false ou true si true -> existe déja
	5.4 test pwd correspondent
	...
6- si aucune erreur (tableau d'erreur count =0), on traite

```php
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
```

les 2 fonctions :


```php
// vérif champs non vides=> param =tableau
if(!function_exists('not_empty'))
{
	function not_empty($fields=[])
	{
		if(count($fields !=0))
		{
			foreach ($fields as $field) 
			{
				if(empty($_POST[$field]) || trim($_POST[$field])=="")
				{
						return false;
				}	
			}
			return true;
		}
	}

}




//verification de l'unicité d'une valeur

if(!function_exists('is_already_in_use'))
{
	function is_already_in_use($field,$value,$table)
	{
		// on utilise la connection qui est crée dans le fichier database qui lui est inclue dans register.php
		global $db;

		$req=$db->prepare("SELECT id FROM $table WHERE $field = ?");
		$req->execute([$value]);

		$count=$req->rowCount();

		$req->closeCursor();

		//0 si n'exite pas 1 si exsite
		return $count;

	}	
}
```


