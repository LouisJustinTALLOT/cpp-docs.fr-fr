---
title: Recherche une ressource de type chaîne (C++) | Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- vc.editors.string
helpviewer_keywords:
- strings [C++], searching
- strings [C++]
ms.assetid: c2497173-f356-4f77-97d6-f0ac41782510
ms.openlocfilehash: 0e6d8ac8027028377e903a9e0a3c89238a9862a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585922"
---
# <a name="finding-a-string-resource-c"></a>Recherche une ressource de type chaîne (C++)

Vous pouvez rechercher une ou plusieurs chaînes dans la table de chaînes et utiliser [expressions régulières](/visualstudio/ide/using-regular-expressions-in-visual-studio) avec la **rechercher dans les fichiers** commande (**modifier** menu) pour rechercher toutes les instances de chaînes qui correspondent à un modèle.

### <a name="to-find-a-string-in-the-string-table"></a>Pour rechercher une chaîne dans la table de chaînes

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Sur le **modifier** menu, cliquez sur **rechercher et remplacer**, puis choisissez **trouver**.

3. Dans le **rechercher** zone, sélectionnez une chaîne de recherche précédente à partir de la liste déroulante ou tapez l’identificateur de texte ou de ressource de légende de la chaîne à rechercher.

4. Sélectionnez un de la **trouver** options.

5. Cliquez sur **Rechercher suivant**.

   > [!TIP]
   > Pour utiliser des expressions régulières lors de la recherche de fichiers, utilisez le **rechercher dans les fichiers** commande. Tapez une expression régulière pour correspondre à un modèle, ou cliquez sur le bouton à droite de la **rechercher** à cocher pour afficher une liste des expressions régulières de recherche. Lorsque vous sélectionnez une expression à partir de cette liste, elle se substitue le texte de recherche dans les **rechercher** boîte. Si vous utilisez des expressions régulières, n’oubliez pas le **utiliser : Expressions régulières** case à cocher est activée.

Pour plus d’informations sur l’ajout de ressources aux projets managés (ceux qui ciblent le common language runtime), consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [procédure pas à pas : localisation de Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de chaînes](../windows/string-editor.md)