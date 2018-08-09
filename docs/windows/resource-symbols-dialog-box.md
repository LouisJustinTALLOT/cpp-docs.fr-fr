---
title: Ressource de boîte de dialogue symboles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resourcesymbols
dev_langs:
- C++
helpviewer_keywords:
- New Symbol dialog box
- Resource Symbols dialog box
- Change Symbol dialog box
ms.assetid: 9706cde3-1f48-4fcd-bedb-2b03b455e3c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2bbd7a6048e47f1f2958a438c79b828f5aca5b66
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020012"
---
# <a name="resource-symbols-dialog-box"></a>Symboles des ressources (boîte de dialogue)
Le **symboles des ressources** boîte de dialogue vous permet d’ajouter de nouveaux symboles des ressources, changer les symboles affichés, ou passez à l’emplacement dans le code source où un symbole est en cours d’utilisation.  
  
 **Name**  
 Affiche le nom du symbole. Pour plus d’informations, consultez [restrictions relatives au nom de symbole](../windows/symbol-name-restrictions.md).  
  
 **Valeur**  
 Affiche la valeur numérique du symbole. Pour plus d’informations, consultez [Restrictions de valeur de symbole](../windows/symbol-value-restrictions.md).  
  
 **En cours d’utilisation**  
 En cas de sélection, indique que le symbole est utilisé par une ou plusieurs ressources. La ou les ressources sont répertoriées dans la zone Utilisé par.  
  
 **Afficher les symboles en lecture seule**  
 En cas de sélection, affiche les ressources en lecture seule. Par défaut, le **symboles des ressources** boîte de dialogue affiche uniquement les ressources modifiables dans votre fichier de script de ressources, mais avec cette option est sélectionnée, les ressources modifiables s’affichent en gras et les ressources en lecture seule s’affichent en texte brut.  
  
 **Utilisé par**  
 Affiche la ou les ressources à l'aide du symbole sélectionné dans la liste des symboles. Pour passer à l’éditeur pour une ressource donnée, sélectionnez la ressource dans le **Used By** , puis cliquez sur **afficher l’utilisation**. Pour plus d’informations, consultez [ouverture de l’éditeur de ressources pour un symbole donné](../windows/opening-the-resource-editor-for-a-given-symbol.md).  
  
 **Nouveau**  
 Ouvre le **nouveau symbole** boîte de dialogue qui vous permet de définir le nom et, si nécessaire, une valeur pour un nouvel identificateur de ressource symbolique. Pour plus d’informations, consultez [création de nouveaux symboles](../windows/creating-new-symbols.md).  
  
 **Modification**  
 Ouvre le **modifier le symbole** boîte de dialogue qui vous permet de modifier le nom ou la valeur d’un symbole. Si le symbole est destiné à un contrôle ou une ressource en cours d'utilisation, il ne peut être modifié qu'à partir de l'éditeur de ressources correspondant. Pour plus d’informations, consultez [modification des symboles non assignés](../windows/changing-unassigned-symbols.md).  
  
 **Afficher l’utilisation**  
 Ouvre la ressource qui contient le symbole dans l'éditeur de ressources correspondant. Pour plus d’informations, consultez [ouverture de l’éditeur de ressources pour un symbole donné](../windows/opening-the-resource-editor-for-a-given-symbol.md).  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Affichage des symboles des ressources](../windows/viewing-resource-symbols.md)