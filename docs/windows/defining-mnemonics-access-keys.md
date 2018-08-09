---
title: Définition des mnémoniques (touches d’accès) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls, mnemonics
- access keys [C++], checking
- mnemonics, checking for duplicate
- mnemonics
- mnemonics, dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 960dcd17a1ff581db540aecfd536e9d2f2e98539
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645095"
---
# <a name="defining-mnemonics-access-keys"></a>Définition des mnémoniques (Touches d'accès rapide)
En règle générale, les utilisateurs du clavier déplacent le focus d’entrée d’un contrôle à l’autre dans une boîte de dialogue avec le **onglet** et **flèche** clés. Toutefois, vous pouvez définir une clé d’accès (un nom mnémonique ou facile à mémoriser) qui permet aux utilisateurs de choisir un contrôle en appuyant sur une clé unique.  
  
### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Pour définir une clé d’accès pour un contrôle avec une légende visible (boutons de commande, cases à cocher et des boutons radio)  
  
1.  Sélectionnez le contrôle dans la boîte de dialogue.  
  
2.  Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), dans le **légende** propriété, tapez un nouveau nom pour le contrôle en tapant une esperluette (`&`) devant la lettre que vous souhaitez comme touche d’accès pour ce contrôle. Par exemple, `&Radio1`.  
  
3.  Appuyez sur **Entrée**.  
  
     Un trait de soulignement apparaît dans la légende pour indiquer la clé d’accès, par exemple, **R**adio1.  
  
### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Pour définir une clé d’accès pour un contrôle sans légende visible  
  
1.  Créez une légende pour le contrôle à l’aide un **texte statique** dans contrôler le [boîte à outils](/visualstudio/ide/reference/toolbox).  
  
2.  Dans la légende de texte statique, tapez une esperluette (`&`) devant la lettre que vous souhaitez comme touche d’accès.  
  
3.  Assurez-vous que le contrôle de texte statique précède immédiatement le contrôle qu’il identifie dans l’ordre de tabulation.  
  
 Toutes les clés d’accès au sein d’une boîte de dialogue doivent être uniques.  
  
### <a name="to-check-for-duplicate-access-keys"></a>Pour vérifier les clés d’accès en double  
  
1.  Sur le **Format** menu, cliquez sur **vérifier les mnémoniques**.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)   
 [Contrôles](../mfc/controls-mfc.md)