## Repository

Un repository est un composant de votre application qui gère les opérations de persistance (CRUD) sur les entités dans une BDD. En gros c'est la couche qui nous permet de parler  à la BDD sans se soucier des détails.

## Annotation @Repository

Elle sert à marquer une classe comme étant un repository, c'est a dire in endroit où vous allez interagir avec votre BDD.

## Est-ce obligatoire
NON ! Quand on implémente déjà une interface comme ``JpaRepository``, Spring detecte automatiquement notre repository

## @PathVariable vs @RequestBody vs @RequestParam

### @PathVariable
On l'utilise pour extraire une partie variable dans notre chemin d'URL

## @RequestBody
On l'utilise quand on reçoit des données via post.

## @RequestParam
On l'utilise quand on a des paramètres dans l'URL
