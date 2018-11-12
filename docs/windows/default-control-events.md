---
title: Événements de contrôle par défaut
ms.date: 11/04/2016
helpviewer_keywords:
- Dialog Editor [C++], default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls [C++], events
ms.assetid: 75556b23-18f5-4390-97a4-2ecad3309741
ms.openlocfilehash: 8cd0102be240bc98cf7900653b8fbb714e2a99a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520404"
---
# <a name="default-control-events"></a>Événements de contrôle par défaut

Les noms de contrôle suivants ont des événements par défaut qui accompagne cet article :

|Nom du contrôle|Événement par défaut|
|------------------|-------------------|
|Animer|MESSAGE ACN_START|
|Case à cocher|BN_CLICKED|
|Zone de liste modifiable|CBN_SELCHANGE DU|
|Personnalisé|TTN_GETDISPINFO|
|Sélecteur d’heure date|DTN_DATETIMECHANGE|
|Zone d’édition|EN_CHANGE|
|Zone de groupe|(Non applicable)|
|Touche d’accès rapide|NM_OUTOFMEMORY|
|Adresse IP|IPN_FIELDCHANGED|
|Liste|LVN_ITEMCHANGE|
|Zone de liste|LBN_SELCHANGE|
|Calendrier mensuel|MCN_SELCHANGE|
|Contrôle d’image|(Non applicable)|
|Progression|NM_CUSTOMDRAW|
|Bouton de commande|BN_CLICKED|
|Case d’option|BN_CLICKED|
|Édition enrichie|EN_CHANGE|
|Barre de défilement|NM_THEMECHANGED|
|Curseur|NM_CUSTOMDRAW|
|Toupie (spin)|UDN_DELTAPOS|
|Texte statique|(Non applicable)|
|Onglet|TCN_SELCHANGE|
|Arborescence|TVN_SELCHANGE|

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Définition de variables membres pour les contrôles de boîte de dialogue](../windows/defining-member-variables-for-dialog-controls.md)<br/>
[Types de messages associés aux objets interface utilisateur](../mfc/reference/message-types-associated-with-user-interface-objects.md)<br/>
[Modification d’un gestionnaire de messages](../mfc/reference/editing-a-message-handler.md)<br/>
[Définition d’un gestionnaire de messages pour un message réfléchi](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)<br/>
[Déclaration d’une variable basée sur votre nouvelle classe de contrôle](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)<br/>
[Substitution d’une fonction virtuelle](../ide/overriding-a-virtual-function-visual-cpp.md)