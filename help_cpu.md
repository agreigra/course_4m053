+++
title = "6. Temps CPU"

date = 2018-09-09T00:00:00
# lastmod = 2018-09-09T00:00:00

draft = false  # Is this a draft? true/false
toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.

math = true
weight = 50
diagram = false
#markup = "mmark"

edit_page = {repo_url = "https://github.com/Bertbk/course_4m053", repo_branch = "master", submodule_dir="content/course/4m053/"}

[git]
  icon = "github"
  repo = "https://github.com/Bertbk/course_4m053"
  submodule_dir = "content/course/4m053/"

# Add menu entry to sidebar.
[menu.4m053]
  parent = "II. Aides & Bonnes Pratiques"
  name = "6. Temps CPU"
  weight = 50

+++


Une quantité d'intérêt pour comparer les performances des méthodes est le *temps CPU* en secondes. Nous suggérons d'utiliser la fonction `clock()` de la bibliothèque standard `ctime`. Cette fonction renvoit un temps CPU (en "clock" de type `clock_t`), il suffit donc de l'appeler juste avant et juste après l'action à mesurer, et d'effectuer la différence des deux. Voici un exemple de code minimaliste permettant d'obtenir le temps CPU mis pour effectuer une action. La variable  `CLOCKS_PER_SEC` est déjà codée en dure et permet de calculer le temps en seconde.

```cpp
# include <ctime> 
int main (){
clock_t start, end ;
start = clock();
/* Entrez ici les opérations à mesurer ... */
end = clock();
double temps_en_secondes = static_cast<double>(end - start) / CLOCKS_PER_SEC ;
```

{{% alert warning %}}
Si votre temps est inférieur à la milliseconde, vous risquez de mesurer du bruit. Vous pouvez, au choix :

- [Mieux] Augmenter la taille du problème
- [Moins bien] Effectuer N fois la même opération et diviser ensuite le temps par N
{{% /alert %}}