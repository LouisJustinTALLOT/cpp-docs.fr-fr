---
description: 'En savoir plus sur : bibliothèques statiques (C++/CX)'
title: Bibliothèques statiques (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 0e8a0100e2822719e4105ed4e9b1029a4ff488da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341930"
---
# <a name="static-libraries-ccx"></a>Bibliothèques statiques (C++/CX)

Une bibliothèque statique qui est utilisée dans une application plateforme Windows universelle (UWP) peut contenir du code C++ standard ISO, y compris des types STL, ainsi que des appels à des API Win32 qui ne sont pas exclues de la plateforme d’application Windows Runtime. Une bibliothèque statique consomme Windows Runtime composants et peut créer des Windows Runtime composants avec certaines restrictions.

## <a name="creating-static-libraries"></a>Création de bibliothèques statiques

Les instructions de création d’un nouveau projet varient en fonction de la version de Visual Studio que vous avez installée. Pour consulter la documentation de votre version par défaut de Visual Studio, utilisez le contrôle sélecteur de **version** . Elle se trouve en haut de la table des matières sur cette page.

::: moniker range="msvc-160"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>Pour créer une bibliothèque statique UWP dans Visual Studio 2019

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

1. En haut de la boîte de dialogue, définissez  **Language** sur **C++**, **Set Platform** to **Windows** et Set **Project type** sur **UWP**.

1. Dans la liste filtrée des types de projets, choisissez **bibliothèque statique (Universal Windows-C++/CX)** , puis choisissez **suivant**. Dans la page suivante, donnez un nom au projet et spécifiez l’emplacement du projet si vous le souhaitez.

1. Choisissez le bouton **Créer** pour créer le projet.

::: moniker-end

::: moniker range="<=msvc-150"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>Pour créer une bibliothèque statique UWP dans Visual Studio 2017 ou Visual Studio 2015

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**. Sous **Visual C++**  >  bibliothèque **Windows universelle** **, choisissez bibliothèque statique (Windows universel)**.

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **Propriétés**. Dans la boîte de dialogue **Propriétés** , dans la page **Propriétés de configuration**  >  **C/C++** , affectez à **utiliser l’extension Windows Runtime** la valeur **Oui (/ZW)**.

::: moniker-end

Quand vous compilez une nouvelle bibliothèque statique, si vous appelez une API Win32 qui est exclue pour les applications UWP, le compilateur déclenche l’erreur C3861, « identificateur introuvable ». Pour rechercher une autre méthode prise en charge pour le Windows Runtime, consultez [alternatives aux API Windows dans les applications UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Si vous ajoutez un projet de bibliothèque statique C++ à une solution d’application UWP, vous devrez peut-être mettre à jour les paramètres de propriété du projet de bibliothèque de sorte que la propriété de prise en charge UWP soit définie sur **Oui**. Sans ce paramètre, le code est généré et crée des liens, mais une erreur se produit lorsque vous tentez de vérifier l’application pour la Microsoft Store. La bibliothèque statique doit être compilée avec les mêmes paramètres de compilateur que ceux du projet qui la consomme.

Si vous consommez une bibliothèque statique qui crée des classes `ref` publiques, des classes d'interface publiques ou des classes de valeur publiques, l'éditeur de liens déclenche l'avertissement suivant :

> **Avertissement LNK4264 :** archivage du fichier objet compilé avec/ZW dans une bibliothèque statique ; Notez que lors de la création de Windows Runtime types, il n’est pas recommandé d’établir une liaison avec une bibliothèque statique qui contient des métadonnées Windows Runtime.

Vous pouvez ignorer sans risque l’avertissement uniquement si la bibliothèque statique ne produit pas Windows Runtime composants qui sont consommés en dehors de la bibliothèque elle-même. Si la bibliothèque ne consomme pas un composant qu'elle définit, l'éditeur de liens peut optimiser l'implémentation même si les métadonnées publiques contiennent les informations de type. En d'autres termes, les composants publics d'une bibliothèque statique sont compilés mais ne sont pas activés au moment de l'exécution. C’est la raison pour laquelle tout Windows Runtime composant destiné à être consommé par d’autres composants ou applications doit être implémenté dans une bibliothèque de liens dynamiques (DLL).

## <a name="see-also"></a>Voir aussi

[Thread et marshaling](../cppcx/threading-and-marshaling-c-cx.md)
