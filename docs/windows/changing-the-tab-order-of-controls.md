---
title: Modification de l’ordre de tabulation des contrôles | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], tab order
- focus, tab order
- tab controls, tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls, tab order
ms.assetid: e2cee764-4367-42d7-9563-65a68f76f5ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33e6e9624e7e927860a184361d45f855f3a1e4f6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861543"
---
# <a name="changing-the-tab-order-of-controls"></a>Modification de l'ordre de tabulation des contrôles
L’ordre de tabulation est l’ordre dans lequel la touche TAB déplace le focus d’entrée d’un contrôle à l’autre dans une boîte de dialogue. Généralement, l’ordre de tabulation se déroule de gauche à droite et de haut en bas de la boîte de dialogue. Chaque contrôle possède un **Tabstop** propriété qui détermine si un contrôle reçoit le focus d’entrée.  
  
### <a name="to-set-input-focus-for-a-control"></a>Pour définir le focus d’entrée pour un contrôle  
  
1.  Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), sélectionnez **True** ou **False** dans les **Tabstop** propriété.  
  
 Même les contrôles qui n’ont pas la propriété Tabstop a la valeur True doivent faire partie de l’ordre de tabulation. Cela peut être important, par exemple, lorsque vous [définir des touches d’accès rapide (mnémoniques)](../windows/defining-mnemonics-access-keys.md) pour les contrôles qui n’ont pas de légende. Texte statique qui contient une clé d’accès pour un contrôle lié doit précéder immédiatement le contrôle associé dans l’ordre de tabulation.  
  
> [!NOTE]
>  Si votre boîte de dialogue contient des contrôles qui se chevauchent, la modification de l’ordre de tabulation peut changer la façon des que contrôles sont affichés. Contrôles fournis plus loin dans l’ordre de tabulation sont toujours affichés au-dessus des contrôles superposés qui les précèdent dans l’ordre de tabulation.  
  
#### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>Pour afficher l’ordre de tabulation actuel pour tous les contrôles dans une boîte de dialogue  
  
1.  Sur le **Format** menu, cliquez sur **l’ordre de tabulation**.  
  
 \- ou -  
  
-   Appuyez sur CTRL + D.  
  
#### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>Pour modifier l’ordre de tabulation pour tous les contrôles dans une boîte de dialogue  
  
1.  Sur le **Format** menu, cliquez sur **l’ordre de tabulation**.  
  
     Un nombre dans le coin supérieur gauche de chaque contrôle affiche sa place dans l’ordre de tabulation actuel.  
  
2.  Définir l’ordre de tabulation en cliquant sur chaque contrôle dans l’ordre que vous souhaitez que la touche TAB à suivre.  
  
3.  Appuyez sur **entrée** pour quitter **l’ordre de tabulation** mode.  
  
    > [!TIP]
    >  Une fois que vous entrez le mode de l’ordre de tabulation, vous pouvez appuyer sur ÉCHAP ou entrée pour désactiver la possibilité de modifier l’ordre de tabulation.  
  
#### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>Pour modifier l’ordre de tabulation pour deux ou plusieurs contrôles  
  
1.  À partir de la **Format** menu, choisissez **l’ordre de tabulation**.  
  
2.  Spécifier l’emplacement où commence la modification dans l’ordre. Pour ce faire, maintenez la **CTRL** clé et cliquez sur le contrôle avant celle où vous souhaitez modifier l’ordre.  
  
     Par exemple, si vous souhaitez modifier l’ordre des contrôles 7 à 9, maintenez la touche CTRL, puis sélectionnez d’abord le contrôle 6.  
  
    > [!NOTE]
    >  Pour définir un contrôle spécifique dans le numéro 1 (premier dans l’ordre de tabulation), double-cliquez sur le contrôle.  
  
3.  Relâchez la touche CTRL, puis cliquez sur les contrôles dans l’ordre de la touche TAB à partir de ce point.  
  
4.  Appuyez sur **entrée** pour quitter **l’ordre de tabulation** mode.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Spécifications  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Organisation des contrôles dans les boîtes de dialogue](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)   
 [Contrôles](../mfc/controls-mfc.md)

