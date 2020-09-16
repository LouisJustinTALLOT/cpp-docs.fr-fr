---
title: Collaborer avec Live Share pour C++ dans Visual Studio
description: Utiliser Live Share pour C++ dans Visual Studio pour collaborer et partager du code en temps réel.
ms.date: 05/24/2019
ms.openlocfilehash: 60830ad6c6b98f644e1c3ddb2e78fbf7397ae919
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684519"
---
# <a name="collaborate-using-live-share-for-c"></a>Collaborer en utilisant Live Share pour C++

Dans Visual Studio 2019 et Visual Studio Code, vous pouvez utiliser **Live Share** pour collaborer sur des projets C++ en temps réel. Avec **Live Share**, une autre personne peut modifier et déboguer votre code sans avoir à installer votre projet ou une de ses dépendances. Chacun voit les modifications de l’autre à mesure qu’elles sont effectuées, et chaque modification est étiquetée du nom de la personne qui l’a apportée.

![Modification de la Live Share&#43;&#43; C](../ide/media/live-share-edit-cpp.png "Modification des Live Share en C++")

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

![C&#43;&#43; le débogage Live Share](../ide/media/live-share-debug-cpp.png "Débogage Live Share en C++")

## <a name="start-and-end-a-live-share-session"></a>Démarrer et terminer une session Live Share

Pour démarrer une session de Live share dans Visual Studio, cliquez sur le bouton partager dans le coin supérieur droit, ou accédez à **fichier**  >  **Démarrer la session de collaboration**. Cela génère un lien que vous pouvez partager avec vos collaborateurs.

![Une petite capture d’écran du bouton Live Share.](../ide/media/live-share-button-cpp.png "Bouton Live Share")

Pour mettre fin à une session, sélectionnez **Terminer la session de collaboration** dans la liste déroulante **Partage**.

![Capture d’écran de la liste déroulante partage avec l’option terminer la session de collaboration en surbrillance.](../ide/media/live-share-end-session-cpp.png "Bouton Live Share")

## <a name="for-more-information"></a>Informations supplémentaires

Pour plus d’informations sur **Live Share** dans Visual Studio, consultez [Qu’est-ce que Visual Studio Live Share ?](/visualstudio/liveshare/). Pour plus d’informations sur Live Share dans Visual Studio Code, consultez [Live Share](https://marketplace.visualstudio.com/items?itemName=ms-vsliveshare.vsliveshare).

## <a name="see-also"></a>Voir aussi

[Modifier et refactoriser du code (C++)](writing-and-refactoring-code-cpp.md)</br>
[Naviguer dans votre base de code C++ dans Visual Studio](navigate-code-cpp.md)</br>
[Lire et comprendre du code C++](read-and-understand-code-cpp.md)</br>
