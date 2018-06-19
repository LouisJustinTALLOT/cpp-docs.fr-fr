---
title: La modification d’un symbole&#39;valeur numérique s | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing.value
dev_langs:
- C++
helpviewer_keywords:
- numeric values
- symbols, numeric values
- numeric values, changing symbols
ms.assetid: 468e903b-9c07-4251-ae09-3b6cb754cc2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8beacf5195e108d98a0004fe79c2a66cb2b3b610
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860383"
---
# <a name="changing-a-symbol39s-numeric-value"></a>La modification d’un symbole&#39;valeur numérique s
Pour les symboles associés à une seule ressource, vous pouvez utiliser la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour modifier la valeur du symbole. Vous pouvez utiliser la [boîte de dialogue Symboles des ressources](../windows/resource-symbols-dialog-box.md) pour modifier la valeur des symboles pas actuellement assignés à une ressource. Pour plus d’informations, consultez [la modification des symboles non assignés](../windows/changing-unassigned-symbols.md).  
  
### <a name="to-change-a-symbol-value-assigned-to-a-single-resource-or-object"></a>Pour modifier une valeur de symbole assignée à une ressource ou un objet unique  
  
1.  Dans [affichage des ressources](../windows/resource-view-window.md), sélectionnez la ressource.  
  
    > [!NOTE]
    >  Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Dans le **propriétés** fenêtre, tapez le nom du symbole suivi d’un signe égal et d’un entier dans la **ID** zone, par exemple :  
  
    ```  
    IDC_EDITNAME=5100  
    ```  
  
 La nouvelle valeur est stockée dans le fichier d'en-tête de symbole la prochaine fois que vous enregistrez le projet. Seul le nom du symbole reste visible dans la zone ID. Le signe égal et la valeur ne sont pas affichés après leur validation.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour obtenir des informations sur l’ajout de fichiers de ressources aux projets managés, l’accès aux ressources, l’affichage de ressources statiques et l’assignation de chaînes de ressources à des propriétés, consultez [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 Spécifications  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Restrictions de valeur de symbole](../windows/symbol-value-restrictions.md)   
 [ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)