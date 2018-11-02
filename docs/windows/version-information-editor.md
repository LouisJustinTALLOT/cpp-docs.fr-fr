---
title: Éditeur d’informations (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.version.F1
helpviewer_keywords:
- Version Information editor [C++], about Version Information editor
- editors, Version Information
- resource editors [C++], Version Information editor
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
ms.openlocfilehash: 817092af316fbc39b696e1ed19e1c67f9a799bd7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667491"
---
# <a name="version-information-editor-c"></a>Éditeur d’informations (C++)

Les informations sur la version sont composées de l’identification de l’entreprise et du produit, d’un numéro de version du produit, et de la notification de copyright et de marque déposée. Avec le **informations de Version** éditeur, vous créez et conserver ces données, qui sont stockées dans la ressource d’informations de version. La ressource d’informations sur la version n’est pas obligatoire pour une application, mais elle est utile pour recueillir des informations qui identifient l’application. Les informations sur la version sont également utilisées par les API d’installation.

Une ressource d’informations sur la version a un bloc supérieur et un ou plusieurs blocs inférieurs : un bloc d’informations fixes unique en haut et un ou plusieurs blocs d’informations sur la version en bas (pour les autres langues et/ou jeux de caractères). Le bloc supérieur contient des zones numériques modifiables et des listes déroulantes sélectionnables. Les blocs inférieurs contiennent uniquement des zones de texte modifiables.

> [!NOTE]
> La norme Windows consiste à n’avoir qu’une seule ressource de version, nommée VS_VERSION_INFO.

Le **informations de Version** éditeur vous permet :

- [Modifier une chaîne dans une ressource d’informations sur la version](../windows/editing-a-string-in-a-version-information-resource.md)

- [Ajouter des informations sur la version pour une autre langue (nouveau bloc d’informations sur la version)](../windows/adding-version-information-for-another-language.md)

- [Supprimer un bloc d’informations sur la version](../windows/deleting-a-version-information-block.md)

- [Accéder aux informations sur la version à partir de votre programme](../windows/accessing-version-information-from-within-your-program.md)

   > [!NOTE]
   > Lors de l’utilisation du **informations de Version** éditeur, dans de nombreux cas, vous pouvez avec le bouton droit pour afficher un menu contextuel de commandes spécifiques à la ressource. Par exemple, si vous cliquez en pointant sur une entrée d’en-tête de bloc, le menu contextuel affiche les **nouveau bloc d’informations sur** et **supprimer bloc d’informations sur** commandes.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Menus et autres ressources](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)