---
title: Modification d’une chaîne dans une ressource d’informations de Version | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- version information resources
- resources [Visual Studio], editing version information
ms.assetid: d3a7d4e4-7d31-47c2-902c-f50b8404ba4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2ec71759deabfa1b5ff7337befa85bdd9c492ae9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607499"
---
# <a name="editing-a-string-in-a-version-information-resource"></a>Modification d'une chaîne dans une ressource d'informations sur la version

### <a name="to-edit-a-string-in-a-version-information-resource"></a>Pour modifier une chaîne dans une ressource d’informations sur la version

1. Cliquez sur l’élément pour le sélectionner, puis recliquez dessus pour commencer à le modifier. Apportez les modifications directement dans le **informations de Version** table ou dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Les modifications que vous apportez apparaîtront aux deux emplacements.

   > [!NOTE] 
   > Lors de la modification la `FILEFLAGS` clé dans le **informations de Version** éditeur, vous remarquerez que vous ne pouvez pas définir le **déboguer**, **Private Build**, ou **spécial Build** propriétés (dans le **propriétés** fenêtre) pour les fichiers .rc :

   - Le **informations de Version** éditeur attribue le **déboguer** propriété avec une `#ifdef` dans le script de ressources, selon le `_DEBUG` indicateur de build.

   - Si le `Private Build` clé a un **valeur** définie le **informations de Version** correspondant de la table **Private Build** propriété (dans le **propriétés**  fenêtre) pour le `FILEFLAGS` clé sera **True**. Si la **Valeur** est vide, la propriété est **False**. De même, le **Special Build** clé (dans le **informations de Version** table) est liée à la **Special Build** propriété pour le `FILEFLAGS` clé.

Vous pouvez trier la séquence d’informations du bloc de chaîne en cliquant sur l’en-tête de colonne Clé ou Valeur. Ces en-têtes réorganisent automatiquement les informations dans la séquence sélectionnée.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur d’informations sur la version](../windows/version-information-editor.md)  
[Informations de version (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)