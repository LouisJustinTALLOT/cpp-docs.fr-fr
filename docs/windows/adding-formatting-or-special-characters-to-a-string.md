---
title: Ajoutez des caractères spéciaux ou de mise en forme à une ressource de chaîne (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: c40f394a-8b2c-4896-ab30-6922863ddbb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 73dd54920e23850235b770d2999e87e69a45c618
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071925"
---
# <a name="adding-formatting-or-special-characters-to-a-string-resource-c"></a>Ajoutez des caractères spéciaux ou de mise en forme à une ressource de chaîne (C++)

### <a name="to-add-formatting-or-special-characters-to-a-string"></a>Pour ajouter des caractères spéciaux ou de mise en forme à une chaîne

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Sélectionnez la chaîne que vous souhaitez modifier.

3. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), ajouter du texte dans des séquences d’échappement standard figurant ci-dessous le **légende** zone, puis appuyez sur **entrée**.

   |Pour résoudre ce|Ce type|
   |-----------------|---------------|
   |Nouvelle ligne|\n|
   |Retour chariot|\r|
   |Onglet|\t|
   |Barre oblique inverse (\\)|\\\|
   |Caractère ASCII|\ddd (notation octale)|
   |alerte (clochette)|\a|

> [!NOTE]
> Le **chaîne** éditeur ne prend pas en charge l’ensemble complet d’échappement des caractères d’ASCII. Vous ne pouvez utiliser que ceux répertoriés ci-dessus.

Pour plus d’informations sur l’ajout de ressources aux projets managés (ceux qui ciblent le common language runtime), consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [procédure pas à pas : localisation de Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de chaînes](../windows/string-editor.md)