---
title: Créer un projet d’application console C++
description: Créer une application console Hello World dans Visual C++
ms.custom: mvc
ms.date: 03/25/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 1b2fe7b95ec27a559de73673412cb2d28507b656
ms.sourcegitcommit: 6e4dd21759caaed262a7255735cf8d6e8fb9f4d7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58476875"
---
# <a name="create-a-c-console-app-project"></a>Créer un projet d’application console C++

Habituellement, le programmeur C++ commence par créer une application « Hello, world ! » qu’il exécute sur la ligne de commande. C’est ce que nous allons faire ici, à l’aide de Visual Studio.

## <a name="prerequisites"></a>Prérequis

- Vous devez installer puis exécuter Visual Studio ainsi que la charge de travail Développement Desktop en C++ sur votre ordinateur. Pour les installer, consultez [Installer la prise en charge C++ dans Visual Studio 2017](../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Créer un projet d’application

Visual Studio organise le code des applications dans des *projets*, et vos projets dans des *solutions*. Un projet contient l’ensemble des options, des configurations et des règles utilisées pour créer une application. Il gère également le lien entre tous les fichiers d’un projet et les éventuels fichiers externes. Pour créer votre application, commencez par créer un projet et une solution.

1. Dans la barre des menus de Visual Studio, choisissez **Fichier** > **Nouveau** > **Projet**. La fenêtre **Nouveau projet** s’ouvre.

2. Dans la barre latérale gauche, vérifiez que **Visual C++** est sélectionné. Au centre, choisissez **Application console Windows**.

3. Dans la zone d’édition **Nom** située en bas, nommez le nouveau projet *CalculatorTutorial*, puis choisissez **OK**.

   ![Boîte de dialogue Nouveau projet](./media/calculator-new-project-dialog.png "Boîte de dialogue Nouveau projet")

   Une application console Windows C++ vide est créée. Les applications console utilisent une fenêtre de console Windows pour afficher la sortie et accepter les entrées utilisateur. Dans Visual Studio, une fenêtre d’éditeur s’ouvre et affiche le code généré :

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>

    int main()
    {
        std::cout << "Hello World!\n"; 
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu

    // Tips for Getting Started: 
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

## <a name="verify-that-your-new-app-builds-and-runs"></a>Vérifier que la génération et l’exécution de la nouvelle application se déroulent normalement

Le modèle d’une nouvelle application console Windows crée une simple application « Hello World » en C++. À ce stade, vous pouvez voir que Visual Studio génère et exécute les applications que vous créez directement dans l’IDE.

1. Pour générer le projet, choisissez **Générer la solution** dans le menu **Générer**. La fenêtre **Sortie** affiche les résultats de la génération.

   ![Générer le projet](./media/calculator-initial-build-output.png "Générer le projet")

1. Pour exécuter le projet, dans la barre de menus, choisissez **Déboguer**, **Démarrer sans débogage**.

   ![Démarrer le projet](./media/calculator-hello-world-console.png "Démarrer le projet")

   Une fenêtre de console s’ouvre, puis exécute votre application. Lorsque vous démarrez une application console dans Visual Studio, celui-ci exécute votre code, puis affiche le message « Appuyez sur une touche pour continuer . » afin de vous permettre de voir la sortie. Félicitations ! Vous venez de créer votre première application console « Hello, world ! » dans Visual Studio.

1. Appuyez sur une touche pour fermer la fenêtre de console et revenir à Visual Studio.

Vous disposez maintenant des outils nécessaires pour générer et exécuter votre application après chaque modification, dans le but de vérifier que le code fonctionne toujours comme prévu. Nous vous montrerons plus tard comment la déboguer si ce n’est pas le cas.

## <a name="edit-the-code"></a>Modifier le code

Maintenant, nous allons transformer le code de ce modèle en application de calculatrice.

1. Dans le fichier *CalculatorTutorial.cpp*, modifiez le code selon l’exemple suivant :

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>

    using namespace std;

    int main()
    {
        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
            << endl;
        return 0;
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu
    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

   > Explication du code :
   >
   > - Les instructions `#include` vous permettent de référencer le code situé dans d’autres fichiers. Parfois, vous pouvez voir un nom de fichier entouré de crochets pointus (**\<\>**) et parfois, entouré de guillemets doubles (**" "**). En règle générale, les crochets pointus sont utilisés lors du référencement de la bibliothèque C++ standard. Les guillemets doubles sont utilisés pour les autres fichiers.
   > - La ligne `#include "pch.h"` (ou `#include "stdafx.h"` dans les versions antérieures de Visual Studio) référence ce qu’on appelle un « en-tête précompilé ». Ce type d’en-tête est généralement utilisé par les programmeurs professionnels pour améliorer les temps de compilation. Toutefois, leur utilisation sort du cadre de ce tutoriel.
   > - La ligne `using namespace std;` indique au compilateur qu’il doit s’attendre à ce que des éléments de la bibliothèque C++ standard soient utilisés dans ce fichier. Sans cette ligne, chaque mot clé de la bibliothèque devrait être précédé d’un `std::`, pour indiquer sa portée. Par exemple, sans cette ligne, chaque référence à `cout` devrait être écrite ainsi : `std::cout`. L’instruction `using` est ajoutée pour rendre le code plus clair.
   > - Le mot clé `cout` est utilisé pour afficher la sortie standard en C++. L’opérateur **\<\<** indique au compilateur d’envoyer tout ce qui est à sa droite vers la sortie standard.
   > - Le mot clé **endl** est similaire à la touche Entrée. Il indique la fin de la ligne et déplace le curseur à la ligne suivante. Il est préférable de placer un `\n` à l’intérieur de la chaîne (entre "") pour faire de même, car `endl` vide toujours la mémoire tampon et peut nuire aux performances du programme. Toutefois, comme il s’agit d’une toute petite application, `endl` est utilisé pour une meilleure lisibilité.
   > - Toutes les instructions C++ doivent se terminer par des points-virgules et toutes les applications C++ doivent contenir une fonction `main()`. Cette fonction est exécutée par le programme au démarrage. Pour pouvoir être utilisé, tout le code doit être accessible à partir de `main()`.

1. Pour enregistrer le fichier, tapez **Ctrl + S**, ou choisissez l’icône **Enregistrer** en haut de l’IDE, représentée par une disquette dans la barre d’outils, sous la barre de menus.

1. Pour exécuter l’application, appuyez sur **Ctrl + F5** ou accédez au menu **Déboguer**, puis choisissez **Démarrer sans débogage**. Si une fenêtre contextuelle **Ce projet est obsolète** s’affiche, vous pouvez sélectionner **Ne plus afficher cette boîte de dialogue**, puis choisir **Oui** pour générer votre application. Vous devriez voir apparaître une fenêtre de console affichant le texte spécifié dans le code.

   ![Générer et démarrer votre application](./media/calculator-first-launch.gif "Générer et démarrer votre application")

1. Lorsque vous avez terminé, fermez la fenêtre de console.

## <a name="add-code-to-do-some-math"></a>Ajouter du code pour effectuer des calculs

Il est temps d’ajouter une logique mathématique.

### <a name="to-add-a-calculator-class"></a>Pour ajouter une classe Calculator

1. Dans le menu **Projet**, choisissez **Ajouter une classe**. Dans la zone d’édition **Nom de la classe**, entrez *Calculator*. Cliquez sur **OK**. Deux nouveaux fichiers sont ajoutés à votre projet. Pour enregistrer simultanément tous vos fichiers modifiés, appuyez sur **Ctrl + Maj + S**. Il s’agit du raccourci clavier pour **Fichier** > **Enregistrer tout**. La barre d’outils comprend également un bouton **Enregistrer tout**, représenté par deux disquettes, qui se trouve à côté du bouton **Enregistrer**. En général, il est recommandé de cliquer régulièrement sur **Enregistrer tout** pour ne rater aucun fichier lorsque vous enregistrez.

   ![Créer la classe Calculator](./media/calculator-create-class.gif "Créer la classe Calculator")

   Une classe est comme le blueprint d’un objet chargé d’une action. Ici, nous allons définir le fonctionnement d’une calculatrice. L’Assistant **Ajouter une classe** que vous avez utilisé précédemment créé des fichiers .cpp et .h qui portent le même nom que la classe. Vous pouvez voir la liste complète de vos fichiers projet dans la fenêtre **Explorateur de solutions** qui s’affiche sur le côté de l’IDE. Si la fenêtre ne s’affiche pas, vous pouvez l’ouvrir à partir de la barre de menus. Choisissez **Affichage** > **Explorateur de solutions**.

   ![Explorateur de solutions](./media/calculator-solution-explorer.png "Explorateur de solutions")

   Trois onglets doivent être ouverts dans l’éditeur : *CalculatorTutorial.cpp*, *Calculator.h* et *Calculator.cpp*. Si vous fermez accidentellement l’un d’eux, vous pouvez le rouvrir en double-cliquant dessus dans la fenêtre **Explorateur de solutions**.

1. Dans **Calculator.h**, supprimez les lignes `Calculator();` et `~Calculator();` qui ont été générées, puisque vous n’en avez pas besoin ici. Ensuite, ajoutez la ligne de code suivante pour que le fichier ressemble à ceci :

    ```cpp
    #pragma once
    class Calculator
    {
    public:
        double Calculate(double x, char oper, double y);
    };
    ```

   > Explication du code :
   >
   > - La ligne que vous avez ajoutée déclare une nouvelle fonction appelée `Calculate`, que nous allons utiliser pour effectuer des opérations arithmétiques (additions, soustractions, multiplications et divisions).
   > - Le code C++ est organisé en fichiers d’*en-tête* (.h) et en fichiers *sources* (.cpp). D’autres extensions de fichier sont prises en charge par différents compilateurs, mais il s’agit là des principales extensions à connaître. Les fonctions et les variables sont normalement *déclarées* (c’est-à-dire qu’un nom et un type leur sont attribués) dans les fichiers d’en-tête, et sont *implémentées* (ou définies) dans les fichiers sources. Pour accéder au code défini dans un autre fichier, vous pouvez utiliser `#include "filename.h"`, où « filename.h » correspond au nom du fichier qui déclare les variables ou les fonctions que vous souhaitez utiliser.
   > - Les deux lignes que vous avez supprimées déclaraient un *constructeur* et un *destructeur* pour la classe. Pour une classe simple comme celle-ci, le compilateur les crée pour vous. Toutefois, leur utilisation dépasse le cadre de ce tutoriel.
   > - Il est conseillé d’organiser votre code dans différents fichiers en fonction de son utilité. Vous pourrez ainsi le retrouver plus facilement quand vous en aurez besoin. Ici, nous définissons la classe `Calculator` séparément du fichier qui contient la fonction `main()`, mais nous prévoyons de référencer la classe `Calculator` dans `main()`.

1. Vous verrez une ligne verte ondulée s’afficher sous `Calculate`. Cela se produit parce que nous n’avons pas défini la fonction `Calculate` dans le fichier .cpp. Placez le curseur sur le mot, cliquez sur l’icône représentant une ampoule, puis choisissez **Créer la définition de 'Calculate' dans Calculator.cpp**. Une fenêtre contextuelle s’affiche pour vous montrer comment le code a été modifié dans l’autre fichier. Le code a été ajouté à *Calculator.cpp*.

   ![Créer la définition de Calculate](./media/calculator-create-definition.gif "Créer la définition de Calculate")

   Pour l’instant, il retourne seulement 0.0. Nous allons changer cela. Appuyez sur **Échap** pour fermer la fenêtre contextuelle.

1. Basculez vers le fichier *Calculator.cpp* dans la fenêtre d’éditeur. Supprimez les sections `Calculator()` et `~Calculator()` (comme vous l’avez fait dans le fichier .h), puis ajoutez le code suivant à `Calculate()` :

    ```cpp
    #include "pch.h"
    #include "Calculator.h"

    double Calculator::Calculate(double x, char oper, double y)
    {
        switch(oper)
        {
            case '+':
                return x + y;
            case '-':
                return x - y;
            case '*':
                return x * y;
            case '/':
                return x / y;
            default:
                return 0.0;
        }
    }
    ```

   > Explication du code :
   >
   > - La fonction `Calculate` consomme un nombre, un opérateur et un deuxième nombre, puis exécute l’opération demandée sur les nombres.
   > - L’instruction switch vérifie quel opérateur a été fourni et exécute uniquement le cas correspondant à cette opération. Le cas default: peut servir de solution de secours si l’utilisateur tape un opérateur qui n’est pas accepté, pour éviter que le programme ne s’arrête. En règle générale, il est préférable de gérer les entrées d’utilisateur non valides de façon plus élégante, mais cela n’entre pas dans le cadre de ce tutoriel.
   > - Le mot clé `double` désigne un type de nombre qui prend en charge les décimales. De cette façon, la calculatrice peut gérer à la fois les calculs de décimales et les calculs d’entiers. La fonction `Calculate` doit toujours retourner un tel nombre en raison du `double` situé au tout début du code (qui indique le type de retour de la fonction). C’est pour cette raison que 0.0 est retourné, même dans le cas par défaut.
   > - Le fichier .h déclare la fonction *prototype*, qui indique à l’avance au compilateur de quels paramètres il a besoin, et à quel type de retour il doit s’attendre. Le fichier .cpp comprend tous les détails d’implémentation de la fonction.

Si vous générez et exécutez le code à ce stade, il continuera d’afficher « Hello World » dans la console. Maintenant, vous allez modifier la fonction `main` pour effectuer des calculs.

### <a name="to-call-the-calculator-class-member-functions"></a>Pour appeler les fonctions membres de la classe Calculator

1. Maintenant, nous allons mettre à jour la fonction `main` dans *CalculatorTutorial.cpp* :

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
             << endl;

        Calculator c;
        while (true)
        {
            cin >> x >> oper >> y;
            result = c.Calculate(x, oper, y);
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

   > Explication du code :
   >
   > - Dans la mesure où les programmes C++ commencent toujours à la fonction `main()`, nous devons appeler notre autre code. Une instruction `#include` est donc nécessaire.
   > - Certaines variables initiales (`x`, `y`, `oper` et `result`) sont déclarées pour stocker respectivement le premier nombre, le deuxième nombre, l’opérateur et le résultat final. Il est toujours bon de leur donner des valeurs initiales pour éviter un comportement non défini, ce que nous allons faire ici.
   > - La ligne `Calculator c;` déclare un objet nommé « c » comme une instance de la classe `Calculator`. La classe n’est qu’un blueprint du fonctionnement de la calculatrice. C’est l’objet calculatrice qui effectue les calculs.
   > - L’instruction `while (true)` est une boucle. Le code à l’intérieur de la boucle continue de s’exécuter indéfiniment tant que la condition à l’intérieur de `()` contient la valeur true. Dans la mesure où la condition est simplement listée comme `true`, elle reste toujours vraie. La boucle s’exécute donc indéfiniment. Pour fermer le programme, l’utilisateur doit fermer manuellement la fenêtre de console. Sinon, le programme continuera d’attendre une nouvelle entrée.
   > - Le mot clé `cin` est utilisé pour accepter l’entrée de l’utilisateur. Ce flux d’entrée est suffisamment intelligent pour traiter une ligne de texte entrée dans la fenêtre de console et pour la placer à l’intérieur de chacune des variables listées (dans l’ordre), en supposant que l’entrée utilisateur corresponde à la spécification nécessaire. Vous pouvez modifier cette ligne pour accepter différents types d’entrées (par exemple, plus de deux nombres), cependant la fonction `Calculate()` devra également être mise à jour pour gérer cette situation.
   > - L’expression `c.Calculate(x, oper, y);` appelle la fonction `Calculate` définie précédemment, et fournit les valeurs d’entrée que vous avez tapées. La fonction retourne ensuite un nombre qui est stocké dans `result`.
   > - Enfin, `result` est affiché dans la console pour que l’utilisateur puisse voir le résultat du calcul.

### <a name="build-and-test-the-code-again"></a>Générer et tester à nouveau le contrôle

Il est maintenant temps de retester le programme pour vous assurer que tout fonctionne correctement.

1. Appuyez sur **Ctrl+F5** pour regénérer et démarrer l’application.

1. Entrez `5 + 5`, puis appuyez sur **Entrée**. Vérifiez que le résultat est bien 10.

   ![Résultat de 5 + 5](./media/calculator-five-plus-five.png "Résultat de 5 + 5")

## <a name="debug-the-app"></a>Déboguer l’application

Étant donné que l’utilisateur est libre de taper ce qu’il veut dans la fenêtre de console, vérifions que la calculatrice peut gérer les entrées comme prévu. Au lieu d’exécuter le programme, nous allons le déboguer pour voir ce qu’il fait en détail, étape par étape.

### <a name="to-run-the-app-in-the-debugger"></a>Pour exécuter l’application dans le débogueur

1. Définissez un point d’arrêt sur la ligne `result = c.Calculate(x, oper, y);`, juste après que l’utilisateur a été invité à taper une entrée. Pour définir le point d’arrêt, cliquez en regard de la ligne sur la barre grise verticale située sur le bord gauche de la fenêtre de l’éditeur. Un point rouge apparaît.

   ![Définir un point d’arrêt](./media/calculator-set-breakpoint.gif "Définir un point d’arrêt")

   Désormais, lorsque nous déboguerons le programme, son exécution s’arrêtera toujours au niveau de cette ligne. Nous savons déjà que le programme fonctionne pour les cas simples. Et comme nous ne souhaitons pas suspendre l’exécution à chaque fois, nous allons donc rendre le point d’arrêt conditionnel.

1. Cliquez avec le bouton droit sur le point rouge qui représente le point d’arrêt, puis choisissez **Conditions**. Dans la zone d’édition de la condition, entrez `(y == 0) && (oper == '/')`. Choisissez le bouton **Fermer** lorsque vous avez terminé. La condition est automatiquement enregistrée.

   ![Définir un point d’arrêt conditionnel](./media/calculator-conditional-breakpoint.gif "Définir un point d’arrêt conditionnel")

   Maintenant, nous allons interrompre l’exécution au point d’arrêt si une division par 0 est tentée.

1. Pour déboguer le programme, appuyez sur **F5** ou choisissez le bouton **Débogueur Windows local** (le bouton de la barre d’outils qui est représenté par une flèche verte). Dans votre application de console, si vous entrez quelque chose comme « 5-0 », le programme se comporte normalement et continue de s’exécuter. Toutefois, si vous tapez « 10 / 0 », il s’arrête au point d’arrêt. Vous pouvez même placer n’importe quel nombre d’espaces entre l’opérateur et les nombres. `cin` est suffisamment intelligent pour analyser l’entrée.

   ![Interrompre l’exécution au point d’arrêt conditionnel](./media/calculator-debug-conditional.gif "Interrompre l’exécution au point d’arrêt conditionnel")

### <a name="useful-windows-in-the-debugger"></a>Fenêtres utiles du débogueur

Lorsque vous déboguez votre code, vous pouvez remarquer que de nouvelles fenêtres s’affichent. Ces fenêtres peuvent vous aider lors du débogage. Intéressons-nous à la fenêtre **Automatique**. La fenêtre **Automatique** montre les valeurs actuelles des variables qui sont utilisées au moins trois lignes avant la ligne actuelle.

   ![Fenêtre Automatique](./media/calculator-autos.png "Fenêtre Automatique")

Pour afficher toutes les variables de cette fonction, basculez vers la fenêtre **Variables locales**. Vous pouvez réellement modifier les valeurs de ces variables pendant le débogage, pour voir l’impact de modifications sur le programme. Ici, nous n’y toucherons pas.

   ![Fenêtre Variables locales](./media/calculator-locals.png "Fenêtre Variables locales")

Vous pouvez également pointer sur les variables directement dans le code pour afficher leur valeur au moment où leur exécution est suspendue. Cliquez sur la fenêtre d’éditeur pour la mettre en mode focus.

   ![Passer la souris sur les variables pour voir leur valeur](./media/calculator-hover-tooltip.gif "Passer la souris sur les variables pour voir leur valeur")

### <a name="to-continue-debugging"></a>Pour continuer le débogage

1. La ligne jaune sur la gauche montre le point d’exécution actuel. La ligne actuelle appelle `Calculate`. Par conséquent, appuyez sur **F11** pour **effectuer un pas à pas détaillé** de la fonction. Vous allez vous retrouver dans le corps de la fonction `Calculate`. Soyez prudent avec l’utilisation du **pas à pas détaillé** car une utilisation trop fréquente peut vous faire perdre beaucoup de temps. Le pas à pas exécute l’intégralité du code de la ligne sur laquelle vous vous trouvez, y compris les fonctions de la bibliothèque standard.

1. Maintenant que le point d’exécution se trouve au début de la fonction `Calculate`, appuyez sur **F10** pour passer à la ligne suivante dans l’exécution du programme. **F10** correspond également à **Pas à pas principal**. Vous pouvez utiliser le **pas à pas principal** pour passer d’une ligne à l’autre, sans entrer dans les détails de ce qui se produit dans chaque partie de la ligne. En général, il est préférable d’utiliser le **pas à pas principal** plutôt que le **pas à pas détaillé**, sauf si vous souhaitez analyser davantage le code qui est appelé à partir d’un autre emplacement (comme vous l’avez fait pour atteindre le corps de `Calculate`).

1. Continuez à utiliser **F10** pour effectuer un **pas à pas principal** sur chaque ligne, jusqu’à ce que vous retourniez à la fonction `main()` de l’autre fichier et que vous vous arrêtiez à la ligne `cout`.

   ![Pas à pas sortant sur Calculate et vérification du résultat](./media/calculator-undefined-zero.gif "Pas à pas sortant sur Calculate et vérification du résultat")

1. Il semble que le programme agisse comme attendu : il accepte le premier nombre et le divise par le deuxième. Sur la ligne `cout`, pointez sur la variable `result` ou regardez `result` dans la fenêtre **Automatique**. Vous verrez que sa valeur est « inf ». Cette valeur est incorrecte et nous allons donc la corriger. La ligne `cout` ne fait que générer la valeur qui est stockée dans `result`. Ainsi, lorsque vous avancez d’une ligne à l’aide de **F10**, la fenêtre de console affiche :

   ![Résultat de la division par zéro](./media/calculator-divide-by-zero-fail.png "Résultat de la division par zéro")

   Ce résultat se produit parce que la division par zéro n’est pas définie, donc le programme n’a pas de réponse numérique à l’opération demandée.

### <a name="to-fix-the-divide-by-zero-error"></a>Pour corriger l’erreur de division par zéro

Nous allons traiter le problème de la division par zéro d’une façon plus appropriée, pour permettre à l’utilisateur de mieux le comprendre.

1. Apportez les modifications suivantes dans *CalculatorTutorial.cpp* (vous pouvez laisser le programme s’exécuter pendant que vous le modifiez, grâce à une fonctionnalité du débogueur appelée **Modifier et Continuer**) :

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b" << endl;

        Calculator c;
        while (true)
        {
            cin  >> x  >> oper  >> y;
            if (oper == '/' && y == 0)
            {
                cout << "Division by 0 exception" << endl;
                continue;
            }
            else
            {
                result = c.Calculate(x, oper, y);
            }
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

1. À présent, appuyez une fois sur **F5**. L’exécution du programme continue jusqu’à ce qu’il doive s’interrompre pour demander une entrée utilisateur. Entrez à nouveau `10 / 0`. Maintenant, un message plus utile s’affiche. L’utilisateur est invité à taper une entrée supplémentaire, et le programme continue de s’exécuter normalement.

   ![Résultat final après modifications](./media/calculator-final-verification.gif "Résultat final après modifications")

   > ![Remarque] Lorsque vous modifiez du code en mode débogage, il y a un risque que le code devienne obsolète. Cela se produit lorsque le débogueur exécute le code qu’il n’a pas encore mis à jour. Lorsque cela se produit, le débogueur affiche une boîte de dialogue pour vous en informer. Parfois, vous devrez appuyer sur **F5** pour actualiser le code exécuté. Si vous apportez une modification à l’intérieur d’une fonction alors que le point d’exécution se trouve à l’intérieur de cette fonction, vous devrez effectuer un pas à pas sortant sur la fonction, puis y retourner pour obtenir le code mis à jour. Si cela ne fonctionne pas pour une raison quelconque et si vous voyez un message d’erreur, vous pouvez arrêter le débogage en cliquant sur le carré rouge dans la barre d’outils située sous les menus en haut de l’IDE. Ensuite, vous pouvez redémarrer le débogage en appuyant sur **F5** ou en choisissant la flèche verte située à côté du bouton Arrêter dans la barre d’outils.

   > Comprendre les raccourcis d’exécution et de débogage
   >
   > - **F5** (qui correspond à **Déboguer** > **Démarrer le débogage**) démarre une session de débogage si aucune n’est déjà active, puis exécute le programme jusqu’à ce qu’un point d’arrêt soit atteint ou qu’une entrée utilisateur soit nécessaire. Si aucune entrée utilisateur n’est nécessaire et qu’aucun point d’arrêt ne peut être atteint, l’exécution du programme prend fin et la fenêtre de console se ferme. Si vous devez exécuter un programme du type « Hello World », utilisez **Ctrl + F5** ou définissez un point d’arrêt avant d’appuyer sur **F5** pour maintenir la fenêtre ouverte.
   > - **CTRL + F5** (qui correspond à **Déboguer** > **Démarrer sans débogage**) exécute l’application sans passer en mode débogage. Ce processus est légèrement plus rapide que le débogage, et la fenêtre de console reste ouverte lorsque l’exécution du programme est terminée.
   > - **F10** (qui correspond au **pas à pas principal**) permet d’itérer le code, ligne par ligne, ainsi que de visualiser la façon dont le code est exécuté et quelles sont les valeurs des variables à chaque étape de l’exécution.
   > - **F11** (qui correspond au **pas à pas détaillé**) fonctionne de façon similaire au **pas à pas principal**, sauf qu’il parcourt toutes les fonctions appelées sur la ligne de l’exécution. Par exemple, si la ligne en cours d’exécution appelle une fonction, le fait d’appuyer sur **F11** déplace le pointeur dans le corps de la fonction, afin que vous puissiez suivre le code de la fonction en cours d’exécution avant de revenir à la ligne où vous avez démarré. Le fait d’appuyer sur **F10** effectue un pas à pas principal sur l’appel de fonction et passe à la ligne suivante. L’appel de fonction se produit toujours, mais le programme ne s’interrompt pas pour vous montrer ce qu’il fait.

### <a name="close-the-app"></a>Fermer l’application

1. Fermez la fenêtre de console de l’application de calculatrice si celle-ci est toujours en cours d’exécution.

1. Dans Visual Studio, appuyez sur **Ctrl**+**S** pour enregistrer votre application.

## <a name="the-finished-app"></a>L’application terminée

Félicitations ! Vous venez de terminer le code de l’application de calculatrice, après l’avoir généré et débogué dans Visual Studio.

![Application de console Calculatrice](./media/calculator-app.gif "Application de console Calculatrice")

## <a name="next-steps"></a>Étapes suivantes

[En savoir plus sur Visual Studio pour C++](https://blogs.msdn.microsoft.com/vcblog/2017/04/21/getting-started-with-visual-studio-for-c-and-cpp-development/)
