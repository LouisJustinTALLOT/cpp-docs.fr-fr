---
title: Recherche d’une chaîne | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.string
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], searching
- strings [C++]
ms.assetid: c2497173-f356-4f77-97d6-f0ac41782510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 67d3d4ba38563b4716a87d4b57a4753fe1b49e9c
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652092"
---
# <a name="finding-a-string"></a>Recherche d'une chaîne
Vous pouvez rechercher une ou plusieurs chaînes dans la table de chaînes et utiliser [expressions régulières](/visualstudio/ide/using-regular-expressions-in-visual-studio) avec la **rechercher dans les fichiers** commande (**modifier** menu) pour rechercher toutes les instances de chaînes qui correspondent à un modèle.  
  
### <a name="to-find-a-string-in-the-string-table"></a>Pour rechercher une chaîne dans la table de chaînes  
  
1.  Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Sur le **modifier** menu, cliquez sur **rechercher et remplacer**, puis choisissez **trouver**.  
  
3.  Dans le **rechercher** zone, sélectionnez une chaîne de recherche précédente à partir de la liste déroulante ou tapez l’identificateur de texte ou de ressource de légende de la chaîne à rechercher.  
  
4.  Sélectionnez un de la **trouver** options.  
  
5.  Cliquez sur **Rechercher suivant**.  
  
    > [!TIP]
    >  Pour utiliser des expressions régulières lors de la recherche de fichiers, utilisez le **rechercher dans les fichiers** commande. Tapez une expression régulière pour correspondre à un modèle, ou cliquez sur le bouton à droite de la **rechercher** à cocher pour afficher une liste des expressions régulières de recherche. Lorsque vous sélectionnez une expression à partir de cette liste, elle se substitue le texte de recherche dans les **rechercher** boîte. Si vous utilisez des expressions régulières, n’oubliez pas le **utiliser : Expressions régulières** case à cocher est activée.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés (ceux qui ciblent le common language runtime), consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [procédure pas à pas : localisation de Windows Forms](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5) et [Procédure pas à pas : utilisation des ressources pour la localisation avec ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de chaînes](../windows/string-editor.md)   