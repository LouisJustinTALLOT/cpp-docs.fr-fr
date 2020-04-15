---
title: Bibliothèques statiques (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 3c4bfd28b805903a2e596ef6d648ff31b0b8261c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358108"
---
# <a name="static-libraries-ccx"></a>Bibliothèques statiques (C++/CX)

Une bibliothèque statique utilisée dans une application Universal Windows Platform (UWP) peut contenir du code CMD standard ISO, y compris les types de TSL, ainsi que des appels vers des API Win32 qui ne sont pas exclues de la plate-forme d’application Windows Runtime. Une bibliothèque statique consomme des composants Windows Runtime et peut créer des composants Windows Runtime avec certaines restrictions.

## <a name="creating-static-libraries"></a>Création de bibliothèques statiques

Les instructions pour créer un nouveau projet varient selon la version de Visual Studio que vous avez installée. Pour voir la documentation de votre version préférée de Visual Studio, utilisez le contrôle du sélecteur **Version.** On le trouve en haut de la table des contenus sur cette page.

::: moniker range="vs-2019"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>Créer une bibliothèque statique UWP dans Visual Studio 2019

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

1. En haut du dialogue, définissez **la langue** à **C ,** définissez la **plate-forme** vers **Windows,** et définissez **le type de projet** à **UWP**.

1. Parmi la liste filtrée des types de projets, choisissez **Static Library (Universal Windows - C/CX)** puis choisissez **Next**. Dans la page suivante, donnez un nom au projet et spécifiez l’emplacement du projet si désiré.

1. Choisissez le bouton **Créer** pour créer le projet.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>Créer une bibliothèque statique UWP dans Visual Studio 2017 ou Visual Studio 2015

1. Sur la barre de menu, choisissez **File** > **New** > **Project**. Sous **Visual CMD** > **Windows Universal** choisir Static Library **(Universal Windows)**.

1. Dans **Solution Explorer**, ouvrez le menu raccourci pour le projet, puis choisissez **Propriétés**. Dans la boîte de dialogue **Properties,** sur la page **Configuration Properties** > **C/C,** **définissez l’extension de Windows Runtime** à **Yes (/ZW).**

::: moniker-end

Lorsque vous compilez une nouvelle bibliothèque statique, si vous faites un appel à une API Win32 qui est exclue pour les applications UWP, le compilateur soulèvera l’erreur C3861, "Identifier non trouvé." Pour rechercher une méthode alternative qui est pris en charge pour le Windows Runtime, voir [Alternatives aux API Windows dans les applications UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Si vous ajoutez un projet de bibliothèque statique C à une solution d’application UWP, vous devrez peut-être mettre à jour les paramètres de propriété du projet de bibliothèque afin que la propriété de support UWP soit définie à **Oui**. Sans ce paramètre, le code se construit et les liens, mais une erreur se produit lorsque vous tentez de vérifier l’application pour le Microsoft Store. La bibliothèque statique doit être compilée avec les mêmes paramètres de compilateur que ceux du projet qui la consomme.

Si vous consommez une bibliothèque statique qui crée des classes `ref` publiques, des classes d'interface publiques ou des classes de valeur publiques, l'éditeur de liens déclenche l'avertissement suivant :

> **avertissement LNK4264:** dossier d’objets d’archivage compilé avec /ZW dans une bibliothèque statique; notez que lors de la rédaction de types Windows Runtime, il n’est pas recommandé de lier avec une bibliothèque statique qui contient des métadonnées Windows Runtime.

Vous ne pouvez ignorer l’avertissement en toute sécurité que si la bibliothèque statique ne produit pas de composants Windows Runtime qui sont consommés à l’extérieur de la bibliothèque elle-même. Si la bibliothèque ne consomme pas un composant qu'elle définit, l'éditeur de liens peut optimiser l'implémentation même si les métadonnées publiques contiennent les informations de type. En d'autres termes, les composants publics d'une bibliothèque statique sont compilés mais ne sont pas activés au moment de l'exécution. Pour cette raison, tout composant Windows Runtime destiné à la consommation par d’autres composants ou applications doit être implémenté dans une bibliothèque à liaison dynamique (DLL).

## <a name="see-also"></a>Voir aussi

[Thread et marshaling](../cppcx/threading-and-marshaling-c-cx.md)
