---
title: Suppression d’un bloc d’informations de Version (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.version
helpviewer_keywords:
- blocks, deleting
- version information, deleting blocks
- resources [C++], deleting version information
ms.assetid: 4e1641eb-d5b2-4183-b273-bc5b51af1537
ms.openlocfilehash: e0bdc719e3ca3a3ffa4493f1d7c578a91733a7f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648303"
---
# <a name="deleting-a-version-information-block-c"></a>Suppression d’un bloc d’informations de Version (C++)

### <a name="to-delete-a-version-information-block"></a>Pour supprimer un bloc d’informations de version

1. Ouvrez la ressource d’informations de version en double-cliquant sur son icône dans l’ [Affichage des ressources](../windows/resource-view-window.md).

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Cliquez sur l’en-tête de bloc que vous souhaitez supprimer, puis choisissez **Supprimer le bloc d’informations sur la version** dans le menu contextuel.

   Cette commande supprime l’en-tête sélectionné et laisse intactes les informations de version restantes. Notez que vous ne pouvez pas annuler cette action.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur d’informations sur la version](../windows/version-information-editor.md)<br/>
[Informations sur la version (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)