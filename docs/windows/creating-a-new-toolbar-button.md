---
title: Création d’un nouveau bouton de barre d’outils | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.toolbar
dev_langs:
- C++
helpviewer_keywords:
- Toolbar editor, creating buttons
- toolbar buttons (in Toolbar editor), button image
- toolbar buttons (in Toolbar editor), creating
- toolbar buttons (in Toolbar editor)
ms.assetid: 46c120fe-4f2a-4887-a08f-bd1fea04b3f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 737c517a2c92d07a6d5110b0bcc08f0d9a290f5e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603170"
---
# <a name="creating-a-new-toolbar-button"></a>Création d'un nouveau bouton de barre d'outils

### <a name="to-create-a-new-toolbar-button"></a>Pour créer un nouveau bouton de barre d’outils

1. Dans [affichage des ressources](../windows/resource-view-window.md) développez le dossier de ressources (par exemple, Project1.rc).

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Développez le **barre d’outils** dossier et sélectionnez une barre d’outils à modifier.

3. Affecter un ID au bouton vide à l’extrémité droite de la barre d’outils. Vous pouvez le faire en modifiant le **ID** propriété dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Par exemple, vous souhaiterez donner à un bouton de barre d’outils le même ID qu’une option de menu. Dans ce cas, utilisez la zone de liste déroulante pour sélectionner le **ID** de l’option de menu.

   - ou -

   Sélectionnez le bouton vide à l’extrémité droite de la barre d’outils (dans le **affichage de la barre d’outils** volet) et commencez à dessiner. Un ID de commande du bouton par défaut est attribué (ID_BUTTON\<n >).

Vous pouvez également copier et coller une image sur une barre d’outils en tant que nouveau bouton.

### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Pour ajouter une image à une barre d’outils en tant que bouton

1. Dans [affichage des ressources](../windows/resource-view-window.md), ouvrez la barre d’outils en double-cliquant dessus.

2. Ensuite, ouvrez l’image que vous souhaitez ajouter à votre barre d’outils.

   > [!NOTE]
   > Si vous ouvrez l’image dans Visual Studio, il s’ouvre dans le **Image** éditeur. Vous pouvez également ouvrir l’image dans d’autres programmes graphiques.

3. À partir de la **modifier** menu, choisissez **copie**.

4. Basculez vers votre barre d’outils en cliquant sur son onglet en haut de la fenêtre source.

5. À partir de la **modifier** menu, choisissez **coller**.

   L’image s’affiche dans votre barre d’outils en tant que nouveau bouton.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

MFC ou ATL

## <a name="see-also"></a>Voir aussi

[propriétés d’un bouton de barre d’outils](../windows/toolbar-button-properties.md)  
[Création, déplacement et modification de boutons de barre d’outils](../windows/creating-moving-and-editing-toolbar-buttons.md)  
[Éditeur de barres d’outils](../windows/toolbar-editor.md)