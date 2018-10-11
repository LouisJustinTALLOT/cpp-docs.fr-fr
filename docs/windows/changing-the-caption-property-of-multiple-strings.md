---
title: Modification de la propriété Caption de plusieurs ressources de type chaîne (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- String editor [C++], changing properties of multiple strings
- string tables [C++], changing caption of multiple strings
ms.assetid: 82ac4389-fd9c-4794-a18f-c6bf5b253bd7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fe08462c95750f483cdec5650fccb1c199505ee1
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082395"
---
# <a name="changing-the-caption-property-of-multiple-string-resources-c"></a>Modification de la propriété Caption de plusieurs ressources de type chaîne (C++)

La procédure suivante vous montre comment modifier la propriété caption de plusieurs chaînes.

### <a name="to-change-the-caption-property-of-multiple-strings"></a>Pour modifier la propriété caption de plusieurs chaînes

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Sélectionnez les chaînes que vous souhaitez modifier en maintenant enfoncée la **Ctrl** enfoncée quand vous cliquez sur chacun d’eux.

3. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), tapez une nouvelle valeur pour la propriété que vous souhaitez modifier.

4. Appuyez sur **Entrée**.

Pour plus d’informations sur l’ajout de ressources aux projets managés (ceux qui ciblent le common language runtime), consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [procédure pas à pas : localisation de Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de chaînes](../windows/string-editor.md)  