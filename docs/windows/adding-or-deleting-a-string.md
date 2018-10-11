---
title: Ajout ou suppression d’une ressource de type chaîne (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.string
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], adding to string tables
- string tables [C++], deleting strings
- strings [C++], deleting in string tables
- string tables [C++], adding strings
ms.assetid: 077077b4-0f4b-4633-92d6-60b321164cab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1e26af845071e5765b30320a86f8d048d2eb12e6
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083760"
---
# <a name="adding-or-deleting-a-string-resource-c"></a>Ajout ou suppression d’une ressource de type chaîne (C++)

Vous pouvez insérer rapidement de nouvelles entrées dans la table de chaîne à l’aide de la **chaîne** éditeur. Nouvelles chaînes sont placés à la fin de la table et sont fonction de l’identificateur de disponible suivant. Vous pouvez ensuite modifier le **ID**, **valeur**, ou **légende** propriétés dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) en fonction des besoins.

Le **chaîne** éditeur permet de s’assurer, vous n’utilisez pas un ID qui est déjà en cours d’utilisation. Si vous sélectionnez un ID déjà en cours d’utilisation, le **chaîne** éditeur sera vous avertir, puis attribuez un ID unique générique, par exemple `IDS_STRING58113`.

### <a name="to-add-a-string-table-entry"></a>Pour ajouter une entrée de table de chaînes

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Avec le bouton droit dans la table de chaînes et choisissez **nouvelle chaîne** dans le menu contextuel.

3. Dans le **chaîne** éditeur, sélectionnez une **ID** à partir de la liste déroulante d’ID ou le type ID directement sur place.

4. Modifier le **valeur**, si nécessaire.

5. Tapez une entrée pour le **légende**.

   > [!NOTE]
   > Chaînes null ne sont pas autorisés dans les tables de chaînes de Windows. Si vous créez une entrée dans la table de chaînes est une chaîne null, vous recevrez un message vous invitant à « Veuillez entrer une chaîne pour cette entrée de table ».

### <a name="to-delete-a-string-table-entry"></a>Pour supprimer une entrée de table de chaînes

1. Sélectionnez l'entrée à supprimer.

2. Sur le **modifier** menu, cliquez sur **supprimer**.

\- ou -

- Avec le bouton droit de la chaîne que vous souhaitez supprimer, puis sélectionnez **supprimer** dans le menu contextuel.

\- ou -

- Appuyez sur la **supprimer** clé.

Pour plus d’informations sur l’ajout de ressources aux projets managés (ceux qui ciblent le common language runtime), consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [procédure pas à pas : localisation de Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de chaînes](../windows/string-editor.md)  