---
title: 'Comment : rechercher des symboles dans les ressources | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols, finding
- resources [Visual Studio], searching for symbols
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5cefedc4b1517b242eef62192e8d03a60097700c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683170"
---
# <a name="how-to-search-for-symbols-in-resources"></a>Comment : rechercher des symboles dans les ressources

### <a name="to-find-symbols-in-resources"></a>Pour rechercher des symboles dans les ressources

1. À partir de la **modifier** menu, choisissez **rechercher un symbole**.

2. Dans le [boîte de dialogue Rechercher un symbole](/visualstudio/ide/go-to), dans le **rechercher** zone, sélectionnez une chaîne de recherche précédente à partir de la liste déroulante ou tapez la touche accélérateur à rechercher (par exemple, ID_ACCEL1).

   > [!TIP]
   > À utiliser [expressions régulières](/visualstudio/ide/using-regular-expressions-in-visual-studio) pour votre recherche, vous devez utiliser le [rechercher dans les fichiers, commande](/visualstudio/ide/reference/find-command) à partir de la **modifier** menu au lieu du **rechercher un symbole**commande. Pour activer les expressions régulières, vous devez disposer le **utilisation : les Expressions régulières** case cochée dans la [boîte de dialogue Rechercher](/visualstudio/ide/finding-and-replacing-text). Vous pouvez ensuite cliquer sur le bouton de flèche droite à droite de la **rechercher** à cocher pour afficher une liste des expressions régulières de recherche. Lorsque vous sélectionnez une expression à partir de cette liste, elle se substitue le texte de recherche dans les **rechercher** boîte.

3. Sélectionnez un de la **trouver** options.

4. Cliquez sur **Rechercher suivant**.

   > [!NOTE]
   > Vous ne pouvez pas rechercher de symboles dans les ressources de type chaîne, accélérateur ou binaire.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, les chaînes affichage de ressources statiques et l’assignation de ressources aux propriétés.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Symboles : identificateurs de ressources](../windows/symbols-resource-identifiers.md)  
[Fichiers de ressources](../windows/resource-files-visual-studio.md)  
[Éditeurs de ressources](../windows/resource-editors.md)