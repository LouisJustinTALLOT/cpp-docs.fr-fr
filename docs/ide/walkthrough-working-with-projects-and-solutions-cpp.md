---
title: 'Procédure pas à pas : utilisation de projets et de solutions (C++)'
ms.date: 05/14/2019
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
ms.openlocfilehash: 36c64a74310c72df38021aebd8abb3ee430da3f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375892"
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Procédure pas à pas : utilisation de projets et de solutions (C++)

Voici comment créer un projet C++ dans Visual Studio, ajouter du code, puis générer et exécuter le projet. Le projet dans cette procédure pas à pas est un programme qui assure le suivi du nombre de joueurs qui jouent à différents jeux de cartes.

Dans Visual Studio, le travail est organisé en projets et solutions. Une solution peut comporter plusieurs projets, par exemple une DLL et un fichier exécutable référençant cette DLL. Pour plus d’informations, consultez [Solutions et projets](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="before-you-start"></a>Avant de commencer

Cette procédure pas à pas nécessite Visual Studio 2017 ou ultérieur. Si vous avez besoin d’une copie, suivez ce guide rapide : [Installer la prise en charge de C++ dans Visual Studio](../build/vscpp-step-0-installation.md). Si ce n’est pas déjà fait, effectuez après l’installation les étapes du tutoriel « Hello, World » pour vérifier que les composants C++ ont bien été installés et qu’ils fonctionnent correctement.

Il est recommandé d’avoir des notions de base du langage C++ et de savoir à quoi servent un compilateur, un éditeur de liens et un débogueur. Par ailleurs, le tutoriel part du principe que vous connaissez bien Windows et que vous savez utiliser les menus et les boîtes de dialogue.

## <a name="create-a-project"></a>Création d’un projet

Pour créer un projet, choisissez d'abord un modèle de type de projet. Pour chaque type de projet, Visual Studio définit les paramètres du compilateur et, en fonction du type, génère du code de démarrage que vous pouvez modifier ultérieurement. Les étapes suivantes varient légèrement selon la version de Visual Studio que vous utilisez. Pour voir la documentation de votre version préférée de Visual Studio, utilisez le contrôle du sélecteur **Version.** On le trouve en haut de la table des contenus sur cette page.

::: moniker range="vs-2019"

### <a name="to-create-a-project-in-visual-studio-2019"></a>Pour créer un projet dans Visual Studio 2019

1. Dans le menu principal, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

1. En haut de la boîte de dialogue, définissez **Langage** sur ** C++ **, **Plateforme** sur **Windows** et **Type de projet** sur **Console**.

1. À partir de la liste des types de projets, choisissez **Application console**, puis choisissez **Suivant**. Dans la page suivante, entrez *Game* comme nom de projet.

   Vous pouvez accepter l’emplacement par défaut dans la liste déroulante **Emplacement**, entrer un emplacement différent ou choisir le bouton **Parcourir** pour accéder au répertoire où vous souhaitez enregistrer le projet.

   Quand vous créez un projet, Visual Studio place le projet dans une solution. Par défaut, la solution porte le même nom que le projet. Vous pouvez changer de nom dans la zone **Nom de la solution**, mais pour cet exemple, conservez le nom par défaut.

1. Choisissez le bouton **Créer** pour créer le projet.

   Visual Studio crée votre solution et les fichiers projet, puis ouvre l’éditeur pour le fichier de code source Game.cpp généré.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017"></a>Pour créer un projet dans Visual Studio 2017

1. Sur la barre de menu, choisissez **File** > **New** > **Project**.

1. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **Installés**, puis sélectionnez **Visual C++** s’il n’est pas déjà ouvert.

1. Dans la liste de modèles installés dans le volet central, sélectionnez **Application console Windows**.

1. Donnez un nom au projet dans la zone **Nom**. Pour cet exemple, entrez *Game*.

   Vous pouvez accepter l’emplacement par défaut dans la liste déroulante **Emplacement**, entrer un emplacement différent ou choisir le bouton **Parcourir** pour accéder au répertoire où vous souhaitez enregistrer le projet.

   Quand vous créez un projet, Visual Studio place le projet dans une solution. Par défaut, la solution porte le même nom que le projet. Vous pouvez changer de nom dans la zone **Nom de la solution**, mais pour cet exemple, conservez le nom par défaut.

1. Choisissez le bouton **OK** pour créer le projet.

   Visual Studio crée votre solution et les fichiers projet, puis ouvre l’éditeur pour le fichier de code source Game.cpp généré.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-project-in-visual-studio-2015"></a>Pour créer un projet dans Visual Studio 2015

1. Sur la barre de menu, choisissez **File** > **New** > **Project**.

1. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **Installés**, puis sélectionnez **Visual C++** s’il n’est pas déjà ouvert.

1. Dans la liste des modèles installés dans le volet central, sélectionnez **Application console Win32**.

1. Donnez un nom au projet dans la zone **Nom**. Pour cet exemple, entrez *Game*.

   Vous pouvez accepter l’emplacement par défaut dans la liste déroulante **Emplacement**, entrer un emplacement différent ou choisir le bouton **Parcourir** pour accéder au répertoire où vous souhaitez enregistrer le projet.

   Quand vous créez un projet, Visual Studio place le projet dans une solution. Par défaut, la solution porte le même nom que le projet. Vous pouvez changer de nom dans la zone **Nom de la solution**, mais pour cet exemple, conservez le nom par défaut.

1. Choisissez le bouton **OK** pour créer le projet.

   Visual Studio crée votre solution et les fichiers projet, puis ouvre l’éditeur pour le fichier de code source Game.cpp généré.

::: moniker-end

## <a name="organize-projects-and-files"></a>Organiser les projets et les fichiers

Vous pouvez utiliser **l’Explorateur de solutions** pour organiser et gérer les projets, fichiers et autres ressources dans votre solution.

Cette partie de la procédure pas à pas montre comment ajouter une classe au projet. Quand vous ajoutez la classe, Visual Studio ajoute les fichiers .h et .cpp correspondants. Vous pouvez afficher les résultats dans **l’Explorateur de solutions**.

### <a name="to-add-a-class-to-a-project"></a>Pour ajouter une classe à un projet

1. Si **l’Explorateur de solutions** n’est pas visible dans Visual Studio, dans la barre de menus, choisissez **Affichage** > **Explorateur de solutions**.

1. Dans **l’Explorateur de solutions**, sélectionnez le projet **Game**. Sur la barre de menu, choisissez **Project** > **Add Class**.

1. Dans le dialogue **De classe Add,** entrez *Cardgame* dans la case **Nom de classe.** Ne modifiez pas les noms de fichiers et les paramètres par défaut. Choisissez le bouton **OK**.

   Visual Studio crée des fichiers et les ajoute à votre projet. Ceux-ci sont visibles dans la fenêtre **Explorateur de solutions**. Les fichiers Cardgame.h et Cardgame.cpp sont ouverts dans l’éditeur.

1. Modifiez le fichier Cardgame.h et apportez les changements suivants :

   - Ajoutez deux membres de données privés après l'accolade gauche de la définition de classe.
     <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - Modifiez le constructeur par défaut généré par Visual Studio. Après le spécificateur d’accès `public:`, recherchez la ligne qui ressemble à ceci :

      `Cardgame();`

      Modifiez le constructeur pour qu’il prenne un paramètre de type `int` nommé *players*.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - Après le destructeur par défaut, ajoutez une déclaration inline pour une fonction membre `static int` nommée *GetParticipants* qui n’accepte aucun paramètre et retourne la valeur `totalParticipants`.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   Le fichier Cardgame.h doit ressembler au code ci-dessous après son changement :

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]-->

    ```cpp
    #pragma once
    class Cardgame
    {
        int players;
        static int totalParticipants;
    public:
        Cardgame(int players);
        ~Cardgame();
        static int GetParticipants() { return totalParticipants; }
    };
    ```

   La ligne `#pragma once` indique au compilateur qu’il doit inclure le fichier d’en-tête une seule fois. Pour plus d’informations, consultez [once](../preprocessor/once.md). Pour plus d’informations sur les autres mots clés C++ du fichier d’en-tête ci-dessus, consultez [class](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [static](../cpp/storage-classes-cpp.md) et [public](../cpp/public-cpp.md).

1. Choisissez l’onglet **Cardgame.cpp** en haut du volet de modification pour l’ouvrir et le modifier.

1. Supprimez tout le contenu du fichier et remplacez-le par le code :

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]-->

    ```cpp
    #include "pch.h" // remove this line in Visual Studio 2019
    #include "Cardgame.h"
    #include <iostream>

    using namespace std;

    int Cardgame::totalParticipants = 0;

    Cardgame::Cardgame(int players)
        : players(players)
    {
        totalParticipants += players;
        cout << players << " players have started a new game.  There are now "
             << totalParticipants << " players in total." << endl;
    }

    Cardgame::~Cardgame()
    {
    }
    ```

   > [!NOTE]
   > Vous pouvez utiliser la saisie semi-automatique lorsque vous écrivez du code. Par exemple, si vous entrez ce code au clavier, vous pouvez entrer *pl* ou *tot,* puis appuyez sur **Ctrl**+**Spacebar**. La saisie semi-automatique entre `players` ou `totalParticipants` pour vous.

## <a name="add-test-code-to-your-main-function"></a>Ajouter du code de test à votre fonction principale

Ajoutez du code à votre application qui teste les nouvelles fonctions.

### <a name="to-add-test-code-to-the-project"></a>Pour ajouter du code de test au projet

1. Dans la fenêtre d’éditeur **Game.cpp**, remplacez le code existant par ceci :

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]-->

    ```cpp
    // Game.cpp : Defines the entry point for the console application.
    //

    #include "pch.h" // remove this line in Visual Studio 2019
    #include "Cardgame.h"
    #include <iostream>

    using namespace std;

    void PlayGames()
    {
        Cardgame bridge(4);
        Cardgame blackjack(8);
        Cardgame solitaire(1);
        Cardgame poker(5);
    }

    int main()
    {
        PlayGames();
        return 0;
    }
    ```

   Le code ajoute une fonction de test, `PlayGames`, au code source, et l’appelle dans `main`.

## <a name="build-and-run-your-app-project"></a>Générer et exécuter votre projet d’application

Ensuite, générez le projet et exécutez l’application.

### <a name="to-build-and-run-the-project"></a>Pour générer et exécuter le projet

1. Sur la barre de menu, choisissez **Build** > **Build Solution**.

   La sortie d’une génération s’affiche dans la fenêtre **Sortie**. Si votre génération réussit, la sortie doit ressembler à ceci :

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>pch.cpp
    1>Cardgame.cpp
    1>Game.cpp
    1>Generating Code...
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

   La fenêtre **Sortie** peut afficher différentes étapes, selon la configuration de build, mais si la génération du projet réussit, la dernière ligne doit ressembler à la sortie indiquée.

   Si votre génération a échoué, comparez votre code au code présenté dans les étapes précédentes.

1. Pour exécuter le projet, sur la barre de menu, choisissez **Debug** > **Start Without Debugging**. Une fenêtre de console doit s’afficher, et la sortie doit ressembler à ceci :

    ```Output
    4 players have started a new game.  There are now 4 players in total.
    8 players have started a new game.  There are now 12 players in total.
    1 players have started a new game.  There are now 13 players in total.
    5 players have started a new game.  There are now 18 players in total.
    ```

   Appuyez sur une touche pour faire disparaître la fenêtre de console.

Félicitations, vous venez de générer une solution et un projet d’application. Continuez la procédure pas à pas pour découvrir plus en détail comment générer des projets de code C++ dans Visual Studio.

## <a name="next-steps"></a>Étapes suivantes

**Précédent :** [Utilisation de l’IDE Visual Studio pour le développement de bureau de C](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)<br/>
**Suivant :** [Procédure pas à pas : Construire un projet (CMD)](../ide/walkthrough-building-a-project-cpp.md)

## <a name="see-also"></a>Voir aussi

[Référence linguistique de CMD](../cpp/cpp-language-reference.md)<br/>
[Projets et systèmes de build](../build/projects-and-build-systems-cpp.md)<br/>
