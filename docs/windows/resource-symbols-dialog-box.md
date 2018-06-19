---
title: Ressource de boîte de dialogue symboles | Documents Microsoft
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
ms.openlocfilehash: 486d4c6c89a43c9d91c655911fa7fee8a31ebd32
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880190"
---
# <a name="resource-symbols-dialog-box"></a>Symboles des ressources (boîte de dialogue)
Le **symboles des ressources** boîte de dialogue vous permet d’ajouter de nouveaux symboles des ressources, de changer les symboles affichés, ou passez à l’emplacement dans le code source où un symbole est en cours d’utilisation.  
  
 **Name**  
 Affiche le nom du symbole. Pour plus d’informations, consultez [restrictions relatives au nom de symbole](../windows/symbol-name-restrictions.md).  
  
 **Valeur**  
 Affiche la valeur numérique du symbole. Pour plus d’informations, consultez [Restrictions de valeur de symbole](../windows/symbol-value-restrictions.md).  
  
 **En cours d’utilisation**  
 En cas de sélection, indique que le symbole est utilisé par une ou plusieurs ressources. La ou les ressources sont répertoriées dans la zone Utilisé par.  
  
 **Afficher les symboles en lecture seule**  
 En cas de sélection, affiche les ressources en lecture seule. Par défaut, la boîte de dialogue Symboles des ressources affiche uniquement les ressources modifiables dans votre fichier de script de ressources. Toutefois, quand cette option est sélectionnée, les ressources modifiables s'affichent en gras et les ressources en lecture seule s'affichent en texte brut.  
  
 **Utilisé par**  
 Affiche la ou les ressources à l'aide du symbole sélectionné dans la liste des symboles. Pour passer à l’éditeur pour une ressource donnée, sélectionnez la ressource dans le **utilisé par** , puis cliquez sur **afficher l’utilisation**. Pour plus d’informations, consultez [ouverture de l’éditeur de ressources pour un symbole donné](../windows/opening-the-resource-editor-for-a-given-symbol.md).  
  
 **Nouveau**  
 Ouvre la boîte de dialogue Nouveau symbole, qui vous permet de définir le nom et, si nécessaire, une valeur pour un nouvel identificateur de ressource symbolique. Pour plus d’informations, consultez [création de nouveaux symboles](../windows/creating-new-symbols.md).  
  
 **Modification**  
 Ouvre la boîte de dialogue Modifier le symbole, qui vous permet de changer le nom ou la valeur d'un symbole. Si le symbole est destiné à un contrôle ou une ressource en cours d'utilisation, il ne peut être modifié qu'à partir de l'éditeur de ressources correspondant. Pour plus d’informations, consultez [la modification des symboles non assignés](../windows/changing-unassigned-symbols.md).  
  
 **Afficher l’utilisation**  
 Ouvre la ressource qui contient le symbole dans l'éditeur de ressources correspondant. Pour plus d’informations, consultez [ouverture de l’éditeur de ressources pour un symbole donné](../windows/opening-the-resource-editor-for-a-given-symbol.md).  
  

  
## <a name="requirements"></a>Spécifications  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Affichage des symboles des ressources](../windows/viewing-resource-symbols.md)