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
ms.openlocfilehash: 3aada3dac208fcf08a9b0e61ef822c3ab13b7b44
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605764"
---
# <a name="how-to-search-for-symbols-in-resources"></a>Comment : rechercher des symboles dans les ressources

### <a name="to-find-symbols-in-resources"></a>Pour rechercher des symboles dans les ressources

1. À partir de la **modifier** menu, choisissez **rechercher un symbole**.

2. Dans le [boîte de dialogue Rechercher un symbole](http://msdn.microsoft.com/63e93d9c-784f-418d-a76a-723da5ff5d96), dans le **rechercher** zone, sélectionnez une chaîne de recherche précédente à partir de la liste déroulante ou tapez la touche accélérateur à rechercher (par exemple, ID_ACCEL1).

   > [!TIP]
   > À utiliser [expressions régulières](/visualstudio/ide/using-regular-expressions-in-visual-studio) pour votre recherche, vous devez utiliser le [rechercher dans les fichiers, commande](/visualstudio/ide/reference/find-command) à partir de la **modifier** menu au lieu du **rechercher un symbole**commande. Pour activer les expressions régulières, vous devez disposer le **utilisation : les Expressions régulières** case cochée dans la [boîte de dialogue Rechercher](http://msdn.microsoft.com/dad03582-4931-4893-83ba-84b37f5b1600). Vous pouvez ensuite cliquer sur le bouton de flèche droite à droite de la **rechercher** à cocher pour afficher une liste des expressions régulières de recherche. Lorsque vous sélectionnez une expression à partir de cette liste, elle se substitue le texte de recherche dans les **rechercher** boîte.

3. Sélectionnez un de la **trouver** options.

4. Cliquez sur **Rechercher suivant**.

   > [!NOTE]
   > Vous ne pouvez pas rechercher de symboles dans les ressources de type chaîne, accélérateur ou binaire.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour obtenir des informations sur l’ajout de fichiers de ressources aux projets managés, l’accès aux ressources, l’affichage de ressources statiques et l’assignation de chaînes de ressources à des propriétés, consultez [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Symboles : identificateurs de ressources](../windows/symbols-resource-identifiers.md)  
[Fichiers de ressources](../windows/resource-files-visual-studio.md)  
[Éditeurs de ressources](../windows/resource-editors.md)