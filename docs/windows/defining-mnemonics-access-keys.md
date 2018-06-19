---
title: Définition des mnémoniques (touches d’accès) | Documents Microsoft
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
ms.openlocfilehash: a60cf597a88fcf7038848be6c9e2d31269f6a906
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873691"
---
# <a name="defining-mnemonics-access-keys"></a>Définition des mnémoniques (Touches d'accès rapide)
Normalement, les utilisateurs du clavier déplacement le focus d’entrée à partir d’un contrôle à l’autre dans une boîte de dialogue avec les touches TAB et flèche. Toutefois, vous pouvez définir une clé d’accès (un nom mnémonique ou facile à retenir) qui permet aux utilisateurs de choisir un contrôle en appuyant sur une clé unique.  
  
### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Pour définir une touche d’accès pour un contrôle avec une légende visible (boutons de commande, cases à cocher et des boutons radio)  
  
1.  Sélectionnez le contrôle dans la boîte de dialogue.  
  
2.  Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), dans le **légende** propriété, tapez un nouveau nom pour le contrôle en tapant une esperluette (**&**) devant la lettre que vous souhaitez définir comme le clé d’accès pour ce contrôle. Par exemple, `&Radio1`.  
  
3.  Appuyez sur **Entrée**.  
  
     Un soulignement s’affiche dans la légende pour indiquer la clé d’accès, par exemple, **R**adio1.  
  
### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Pour définir une touche d’accès pour un contrôle sans légende visible  
  
1.  Rendre une légende pour le contrôle à l’aide un **texte statique** contrôler dans le [boîte à outils](/visualstudio/ide/reference/toolbox).  
  
2.  Dans la légende de texte statique, tapez un « et commercial » (**&**) devant la lettre que vous souhaitez comme touche d’accès rapide.  
  
3.  Assurez-vous que le contrôle de texte statique précède immédiatement le contrôle qu’il identifie dans l’ordre de tabulation.  
  
 Toutes les clés d’accès au sein d’une boîte de dialogue doivent être uniques.  
  
#### <a name="to-check-for-duplicate-access-keys"></a>Pour vérifier les clés d’accès en double  
  
1.  Sur le **Format** menu, cliquez sur **vérifier les mnémoniques**.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Spécifications  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)   
 [Contrôles](../mfc/controls-mfc.md)

