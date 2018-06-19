---
title: Par défaut des événements de contrôle | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog editor, default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls, events
ms.assetid: 75556b23-18f5-4390-97a4-2ecad3309741
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a50b0deeb525481afb1da7221689924c41930bff
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874094"
---
# <a name="default-control-events"></a>Événements de contrôle par défaut
Les noms de contrôle suivants ont des événements par défaut qui l’accompagne :  
  
|Nom du contrôle|Événement par défaut|  
|------------------|-------------------|  
|Animer|**MESSAGE ACN_START**|  
|Case à cocher|**BN_CLICKED**|  
|Zone de liste modifiable|**CBN_SELCHANGE DU**|  
|Personnalisé|**TTN_GETDISPINFO**|  
|Sélecteur de date heure|**DTN_DATETIMECHANGE**|  
|Zone d’édition|**EN_CHANGE**|  
|Zone de groupe|(Non applicable)|  
|Touche d’accès rapide|**NM_OUTOFMEMORY**|  
|Adresse IP|**IPN_FIELDCHANGED**|  
|Liste|**LVN_ITEMCHANGE**|  
|Zone de liste|**LBN_SELCHANGE**|  
|Calendrier mensuel|**MCN_SELCHANGE**|  
|Contrôle d’image|(Non applicable)|  
|Progression|**NM_CUSTOMDRAW**|  
|Bouton de commande|**BN_CLICKED**|  
|Case d’option|**BN_CLICKED**|  
|RichEdit|**EN_CHANGE**|  
|Barre de défilement|**NM_THEMECHANGED**|  
|Curseur|**NM_CUSTOMDRAW**|  
|Faire pivoter|**UDN_DELTAPOS**|  
|Texte statique|(Non applicable)|  
|Onglet|**TCN_SELCHANGE**|  
|Arborescence|**TVN_SELCHANGE**|  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Spécifications  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Définir des Variables membres pour les contrôles de boîte de dialogue](../windows/defining-member-variables-for-dialog-controls.md)   
 [Types de messages associés aux objets d’Interface utilisateur](../mfc/reference/message-types-associated-with-user-interface-objects.md)   
 [Modification d’un gestionnaire de messages](../mfc/reference/editing-a-message-handler.md)   
 [Définition d’un gestionnaire de messages pour un Message réfléchi](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)   
 [Déclaration d’une Variable basée sur votre nouvelle classe de contrôle](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)   
 [Une fonction virtuelle de substitution](../ide/overriding-a-virtual-function-visual-cpp.md)

