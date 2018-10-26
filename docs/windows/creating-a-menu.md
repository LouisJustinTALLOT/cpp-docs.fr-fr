---
title: Création d’un Menu (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.menu
dev_langs:
- C++
helpviewer_keywords:
- mnemonics [C++], associating menu items
- menus [C++], associating commands with mnemonic keys
- menus [C++], creating
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 91098a0a225519f9b657d9424872e99be0e86354
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065536"
---
# <a name="creating-a-menu-c"></a>Création d’un Menu (C++)

> [!NOTE]
> Le **des ressources, fenêtre** n’est pas disponible dans les éditions Express.

### <a name="to-create-a-standard-menu"></a>Pour créer un menu standard

1. Dans le menu **Affichage** , cliquez sur **Affichage des ressources** , puis cliquez avec le bouton droit sur l’en-tête **Menu** et choisissez **Ajouter une ressource**. Choisissez **Menu**.

2. Sélectionnez la zone **Nouvel élément** (le rectangle qui contient « Tapez ici ») dans la barre de menus.

   ![Zone de nouvel élément dans l’éditeur de menus](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   Zone Nouvel élément

3. Tapez un nom pour votre nouveau menu, par exemple, « Fichier ».

   Le texte que vous tapez s’affiche dans l’ **Éditeur de menus** et dans la zone **Légende** de la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window). Vous pouvez modifier les propriétés du nouveau menu dans les deux emplacements.

   Une fois que vous avez donné un nom à votre nouveau menu dans la barre de menus, la zone Nouvel élément se déplace vers la droite (pour vous permettre d’ajouter un autre menu) et une autre zone Nouvel élément s’ouvre sous votre premier menu pour que vous puissiez y ajouter des commandes de menu.

   ![Zone nouvel élément développée](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   Zone Nouvel élément avec déplacement du focus quand vous avez tapé le nom du menu

   > [!NOTE]
   > Pour créer un seul élément de menu sur la barre de menus, définissez le **contextuelle** propriété **False**.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de menus](../windows/menu-editor.md)