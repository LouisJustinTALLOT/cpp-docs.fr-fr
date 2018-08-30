---
title: Modification des propriétés d’une chaîne | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource identifiers, string properties
- string tables, changing strings
- strings [C++], properties
ms.assetid: 0a220434-f444-4405-9a64-d28d6b965687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5897801a0b0350d813f7dddc5d1595e04213e2dd
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221638"
---
# <a name="changing-the-properties-of-a-string"></a>Modification des propriétés d'une chaîne

### <a name="to-change-a-string-or-its-identifier"></a>Pour modifier une chaîne ou son identificateur

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Sélectionnez la chaîne que vous souhaitez modifier, puis double-cliquez sur le **ID**, **valeur**, ou **légende** colonne. Vous pouvez désormais :

   - Sélectionnez un **ID** à partir de la **ID de liste déroulante** liste ou tapez une `ID` directement en place.

   - Tapez un nombre différent dans le **valeur** colonne.

   - Taper des modifications dans le **légende** colonne.

        > [!NOTE]
        >  Vous pouvez également modifier les propriétés d’une chaîne dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

Pour plus d’informations sur l’ajout de ressources aux projets managés (ceux qui ciblent le common language runtime), consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [procédure pas à pas : localisation de Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3\(v=vs.100\)).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de chaînes](../windows/string-editor.md)  