---
title: Collaborer avec Live Share pour C++ dans Visual Studio
description: Utiliser Live Share pour C++ dans Visual Studio pour collaborer et partager du code en temps réel.
ms.date: 05/24/2019
ms.openlocfilehash: e6e983c6acb56dffd12756d8bbaccef32dd57f38
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077796"
---
# <a name="collaborate-using-live-share-for-c"></a>Collaborer en utilisant Live Share pour C++

Dans Visual Studio 2019 et Visual Studio Code, vous pouvez utiliser **Live Share** pour collaborer sur des projets C++ en temps réel. Avec **Live Share**, une autre personne peut modifier et déboguer votre code sans avoir à installer votre projet ou une de ses dépendances. Chacun voit les modifications de l’autre à mesure qu’elles sont effectuées, et chaque modification est étiquetée du nom de la personne qui l’a apportée.

![Modification&#43; &#43; de la Live share C](../ide/media/live-share-edit-cpp.png "Live Share la modification dansC++")

## <a name="live-share-host-and-guests"></a>Hôte et invités Live Share

Dans une session Live Share, il existe un hôte et un ou plusieurs invités. L’hôte et les invités peuvent utiliser Visual Studio ou Visual Studio Code. Un hôte utilisant Visual Studio 2019 sur Windows peut partager avec un invité utilisant Visual Studio Code sur Linux.

L’hôte fournit aux invités tout ce dont ils ont besoin pour être productifs. Il n’est pas nécessaire que les invités aient le code source, le compilateur, les dépendances externes ni même les mêmes composants installés.

L’hôte et les invités peuvent utiliser les fonctionnalités IntelliSense suivantes :

- Liste des membres
- Aide sur les paramètres
- Infos express
- Débogage/points d’arrêt
- Rechercher toutes les références
- Atteindre la définition
- Recherche de symbole (Ctrl+T)
- Mise en surbrillance des références
- Diagnostics/Erreurs/Tildes

![C&#43; &#43; Live share le débogage](../ide/media/live-share-debug-cpp.png "Live Share le débogage dansC++")

## <a name="start-and-end-a-live-share-session"></a>Démarrer et terminer une session Live Share

Pour démarrer une session Live Share dans Visual Studio, cliquez sur le bouton Partager dans l’angle supérieur droit, ou accédez à **Fichier** > **Démarrer la session de collaboration**. Cela génère un lien que vous pouvez partager avec vos collaborateurs.

![Bouton&#43; &#43; de Live share C](../ide/media/live-share-button-cpp.png "Bouton Live Share")

Pour mettre fin à une session, sélectionnez **Terminer la session de collaboration** dans la liste déroulante **Partage**.

![Bouton&#43; &#43; de Live share C](../ide/media/live-share-end-session-cpp.png "Bouton Live Share")

## <a name="for-more-information"></a>Informations supplémentaires

Pour plus d’informations sur **Live Share** dans Visual Studio, consultez [Qu’est-ce que Visual Studio Live Share ?](/visualstudio/liveshare/). Pour plus d’informations sur Live Share dans Visual Studio Code, consultez [Live Share](https://marketplace.visualstudio.com/items?itemName=ms-vsliveshare.vsliveshare).

## <a name="see-also"></a>Voir aussi

[Modifier et refactoriser du code (C++)](writing-and-refactoring-code-cpp.md)</br>
[Naviguer dans votre base de code C++ dans Visual Studio](navigate-code-cpp.md)</br>
[Lire et comprendre du code C++](read-and-understand-code-cpp.md)</br>