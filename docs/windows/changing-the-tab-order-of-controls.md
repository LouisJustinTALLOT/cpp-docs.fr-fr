---
title: Modification de l’ordre de tabulation des contrôles | Microsoft Docs
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
- tab controls [C++], tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls [C++], tab order
ms.assetid: e2cee764-4367-42d7-9563-65a68f76f5ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 822e0c5ac0232ac30e4db63b3605fda0126959de
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434594"
---
# <a name="changing-the-tab-order-of-controls"></a>Modification de l'ordre de tabulation des contrôles

L’ordre de tabulation est l’ordre dans lequel le **onglet** touche déplace le focus d’entrée d’un contrôle à l’autre dans une boîte de dialogue. Généralement, l’ordre de tabulation se déroule de gauche à droite et de haut en bas dans une boîte de dialogue. Chaque contrôle possède une **Tabstop** propriété qui détermine si un contrôle reçoit le focus d’entrée.

### <a name="to-set-input-focus-for-a-control"></a>Pour définir le focus d’entrée pour un contrôle

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), sélectionnez **True** ou **False** dans le **Tabstop** propriété.

Même les contrôles qui n’ont pas la **Tabstop** propriété définie sur **True** doivent faire partie de l’ordre de tabulation. Cela peut être important, par exemple, lorsque vous [définir des touches d’accès rapide (mnémoniques)](../windows/defining-mnemonics-access-keys.md) pour les contrôles qui n’ont pas de légende. Texte statique qui contient une clé d’accès pour un contrôle lié doit précéder immédiatement le contrôle concerné dans l’ordre de tabulation.

> [!NOTE]
> Si votre boîte de dialogue contient des contrôles qui se chevauchent, la modification de l’ordre de tabulation peut changer la façon des que contrôles sont affichés. Contrôles fournis plus loin dans l’ordre de tabulation sont toujours affichés au-dessus des contrôles superposés qui les précèdent dans l’ordre de tabulation.

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>Pour afficher l’ordre de tabulation actuel pour tous les contrôles dans une boîte de dialogue

1. Sur le **Format** menu, cliquez sur **l’ordre de tabulation**.

\- ou -

- Appuyez sur **Ctrl**+**D**.

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>Pour modifier l’ordre de tabulation pour tous les contrôles dans une boîte de dialogue

1. Sur le **Format** menu, cliquez sur **l’ordre de tabulation**.

   Un nombre dans le coin supérieur gauche de chaque contrôle affiche sa place dans l’ordre de tabulation en cours.

2. Définir l’ordre de tabulation en cliquant sur chaque contrôle dans l’ordre que vous souhaitez que le **onglet** clé à suivre.

3. Appuyez sur **entrée** pour quitter **l’ordre de tabulation** mode.

   > [!TIP]
   > Une fois que vous entrez **l’ordre de tabulation** mode, vous pouvez appuyer sur **ÉCHAP** ou **entrée** pour désactiver la possibilité de modifier l’ordre de tabulation.

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>Pour modifier l’ordre de tabulation pour deux ou plusieurs contrôles

1. À partir de la **Format** menu, choisissez **l’ordre de tabulation**.

2. Spécifier où commence la modification dans l’ordre. Pour ce faire, maintenez la **Ctrl** clé et cliquez sur le contrôle avant celle où vous souhaitez modifier l’ordre.

   Par exemple, si vous souhaitez modifier l’ordre des contrôles `7` via `9`, maintenez la touche **Ctrl**, puis sélectionnez le contrôle `6` première.

   > [!NOTE]
   > Pour affecter à un contrôle spécifique numéro `1` (tout d’abord dans l’ordre de tabulation), double-cliquez sur le contrôle.

3. Mise en production la **Ctrl** de clé, puis cliquez sur les contrôles dans l’ordre que vous souhaitez que le **onglet** à partir de ce point.

4. Appuyez sur **entrée** pour quitter **l’ordre de tabulation** mode.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Organisation des contrôles dans les boîtes de dialogue](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles](../mfc/controls-mfc.md)