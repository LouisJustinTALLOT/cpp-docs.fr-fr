---
title: Bibliothèques statiques (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 188ba06518bf6cdd154b7d6bd61216ed1e4ffad3
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877240"
---
# <a name="static-libraries-ccx"></a>Bibliothèques statiques (C++/CX)

Une bibliothèque statique qui est utilisée dans une application de plateforme universelle Windows (UWP) peut contenir du code à la norme ISO C++, y compris les types STL, ainsi que les appels aux API Win32 qui ne sont pas exclus de la plateforme d’application Windows Runtime. Une bibliothèque statique consomme des composants Windows Runtime et peut créer des composants Windows Runtime avec certaines restrictions.

## <a name="creating-static-libraries"></a>Création de bibliothèques statiques


Instructions pour la création d’un nouveau projet varient en fonction de la version de Visual Studio que vous avez installée. Assurez-vous que vous avez le sélecteur de version dans le coin supérieur gauche défini sur la version correcte.

::: moniker range="vs-2019"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>Pour créer une bibliothèque statique UWP dans Visual Studio 2019

1. Dans la barre de menus, choisissez **fichier** > **New** > **projet** pour ouvrir le **créer un nouveau projet** boîte de dialogue.

1. En haut de la boîte de dialogue, définissez **langage** à **C++**, affectez la valeur **plateforme** à **Windows**et définissez **detypedeprojet** à **UWP**. 

1. Dans la liste filtrée des types de projets, choisissez **bibliothèque statique (Universal Windows - C++/CX)** puis choisissez **suivant**. Dans la page suivante, donnez un nom au projet et spécifier l’emplacement du projet si vous le souhaitez.

1. Choisissez le **créer** bouton pour créer le projet.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>Pour créer une bibliothèque statique UWP dans Visual Studio 2017 ou Visual Studio 2015

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**. Sous **Visual C++** > **Windows universel** choisissez **bibliothèque statique (Windows universel)**.

1. Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**. Dans le **propriétés** boîte de dialogue le **propriétés de Configuration** > **C/C++** , définissez **consommer l’Extension de Runtime Windows** à **Oui (/ZW)**.

::: moniker-end

Lorsque vous compilez une nouvelle bibliothèque statique, si vous effectuez un appel à une API Win32 qui est exclue pour les applications UWP, le compilateur déclenche l’erreur C3861 « Identificateur introuvable ». Pour rechercher une méthode alternative qui est pris en charge pour l’exécution de Windows, consultez [Alternatives aux API Windows dans les applications UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Si vous ajoutez un projet de bibliothèque statique C++ à une solution d’application UWP, vous devrez peut-être mettre à jour les paramètres de propriété du projet de bibliothèque afin que la propriété de la prise en charge UWP est définie sur **Oui**. Sans ce paramètre, le code est généré et des liens, mais une erreur se produit lorsque vous essayez de vérifier l’application pour le Microsoft Store. La bibliothèque statique doit être compilée avec les mêmes paramètres de compilateur que ceux du projet qui la consomme.

Si vous consommez une bibliothèque statique qui crée des classes `ref` publiques, des classes d'interface publiques ou des classes de valeur publiques, l'éditeur de liens déclenche l'avertissement suivant :

> **avertissement LNK4264 :** archivage du fichier objet compilé avec /ZW dans une bibliothèque statique ; Notez que lors de la création des types Windows Runtime qu’il est déconseillé d’effectuer une liaison avec une bibliothèque statique qui contient des métadonnées Windows Runtime.

Vous pouvez ignorer l’avertissement uniquement si la bibliothèque statique ne produit pas de composants Windows Runtime qui sont consommés en dehors de la bibliothèque elle-même. Si la bibliothèque ne consomme pas un composant qu'elle définit, l'éditeur de liens peut optimiser l'implémentation même si les métadonnées publiques contiennent les informations de type. En d'autres termes, les composants publics d'une bibliothèque statique sont compilés mais ne sont pas activés au moment de l'exécution. Pour cette raison, n’importe quel composant Windows Runtime qui est destinée à la consommation par d’autres composants ou les applications doit être implémentée dans une bibliothèque de liens dynamiques (DLL).

## <a name="see-also"></a>Voir aussi

[Thread et marshaling](../cppcx/threading-and-marshaling-c-cx.md)
