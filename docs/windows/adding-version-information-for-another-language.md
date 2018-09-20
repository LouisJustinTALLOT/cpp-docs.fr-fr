---
title: Ajout des informations de Version pour une autre langue (C++) | Microsoft Docs
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
- languages, version information
- New Version Info Block
- blocks, adding
- resources [C++], adding version information
- version information, adding for languages
ms.assetid: 17f6273c-e1cc-441a-a3d8-f564341cbf20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97ad11f7982fd5a413c6740fe969c5edc20636a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389380"
---
# <a name="adding-version-information-for-another-language-c"></a>Ajout des informations de Version pour une autre langue (C++)

### <a name="to-add-version-information-for-another-language-new-info-block"></a>Pour ajouter des informations de version pour une autre langue (nouveau bloc d’informations)

1. Ouvrez une ressource d’informations de version en double-cliquant dessus dans [Affichage des ressources](../windows/resource-view-window.md).

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Cliquez avec le bouton droit dans la table d’informations de version et choisissez **Nouveau bloc d’informations sur la version** dans le menu contextuel.

   Cette commande ajoute un bloc d’informations supplémentaire à la ressource d’informations de version actuelle et ouvre ses propriétés correspondantes dans la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window).

3. Dans la fenêtre **Propriétés** , sélectionnez la langue et le jeu de caractères appropriés pour votre nouveau bloc de caractères.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur d’informations sur la version](../windows/version-information-editor.md)<br/>
[Informations de version (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)