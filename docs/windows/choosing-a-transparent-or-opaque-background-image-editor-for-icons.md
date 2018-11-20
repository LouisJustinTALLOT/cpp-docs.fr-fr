---
title: Choix d'un arrière-plan transparent ou opaque (Éditeur d'images pour les icônes)
ms.date: 11/19/2018
helpviewer_keywords:
- opaque backgrounds [C++]
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- images [C++], transparency
- images [C++], opaque background
ms.assetid: 61b743d9-c86b-405d-9a81-0806431b4363
ms.openlocfilehash: ceea31b998d5c4dca52657db570ace664f7e373f
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175429"
---
# <a name="choosing-a-transparent-or-opaque-background-image-editor-for-icons"></a>Choix d'un arrière-plan transparent ou opaque (Éditeur d'images pour les icônes)

Lorsque vous déplacez ou copiez une sélection d’une image, les pixels de la sélection qui correspondent à la couleur d’arrière-plan actuelle sont, par défaut, transparent ; ils ne masquent pas les pixels dans l’emplacement cible.

Vous pouvez passer d’un arrière-plan transparent (la valeur par défaut) à un arrière-plan opaque et inversement. Lorsque vous utilisez un outil de sélection, le **arrière-plan Transparent** et **arrière-plan Opaque** options s’affichent dans le **Option** sélecteur sur le **Éditeur d’images** barre d’outils (comme indiqué ci-dessous).

![Options d’arrière-plan &#45; opaque ou transparent](../windows/media/vcimageeditoropaqtranspback.gif "options d’arrière-plan &#45; opaque ou transparent")<br/>
**Options transparentes et opaques** sur la **barre d’outils Éditeur d’images**

### <a name="to-switch-between-a-transparent-and-opaque-background"></a>Pour basculer entre un arrière-plan transparent et opaque

1. Dans le **Éditeur d’images** barre d’outils, cliquez sur le **Option** sélecteur, puis cliquez sur l’arrière-plan approprié :

   - `Opaque Background (O)`: Image existante est masqué par toutes les parties de la sélection.

   - `Transparent Background (T)`: Illustration existant par le biais de la sélection des parties qui correspondent à la couleur d’arrière-plan actuelle.

   \- ou -

1. Sur le **Image** menu, cochez ou décochez **dessin Opaque**.

Vous pouvez modifier la couleur d’arrière-plan alors qu’une sélection est déjà en vigueur pour modifier les parties de l’image sont transparents.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Utilisation des couleurs](../windows/working-with-color-image-editor-for-icons.md)