---
title: Identifications de ressources (Symboles) (CMD)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.identifiers
helpviewer_keywords:
- symbols [C++], resource identifiers
- symbols [C++], creating
- resource symbols
- symbols [C++], editing
- resource editors [C++], resource symbols
ms.assetid: 8fccc09a-0237-4a65-b9c4-57d60c59e324
ms.openlocfilehash: c6b3cf7d3edfc870164645632bb07bf49c792a48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359887"
---
# <a name="resource-identifiers-symbols-c"></a>Identifications de ressources (Symboles) (CMD)

Un symbole est un identifiant de ressource (ID) qui se compose de deux parties, un nom de symbole (chaîne de texte) cartographié à une valeur de symbole (integer), par exemple :

```cpp
IDC_EDITNAME = 5100
```

Les noms de symboles sont souvent appelés « identificateurs ».

Les symboles permettent de faire référence aux ressources et aux objets d’interface utilisateur d’une manière descriptive, à la fois dans votre code source et quand vous travaillez avec eux dans les éditeurs de ressources. Vous pouvez afficher et manipuler les symboles dans un emplacement pratique par le biais de la boîte de dialogue [Symboles des ressources](../windows/viewing-resource-symbols.md).

Le nombre de ressources et de symboles de votre application augmente à mesure qu’elle augmente en taille et en complexité. Le suivi d’un grand nombre de symboles éparpillés dans plusieurs fichiers peut être difficile. La boîte de dialogue **De symboles de ressources** simplifie la gestion des symboles en offrant un outil central à travers lequel vous pouvez :

- [Créer des symboles](../windows/creating-new-symbols.md)

- [Gérer les symboles](../windows/changing-a-symbol-or-symbol-name-id.md)

- [Afficher des ID de symboles prédéfinis](../windows/predefined-symbol-ids.md)

Lorsque vous créez une ressource ou un objet de ressource, les [éditeurs de ressources](../windows/resource-editors.md) fournissent un nom par défaut pour la ressource, par exemple `IDC_RADIO1`, et lui affectent une valeur. La définition de nom-plus-valeur `Resource.h` est stockée dans le fichier.

> [!NOTE]
> Lorsque vous copiez des ressources ou des objets de ressources d’un fichier .rc vers un autre, Visual C++ peut modifier la valeur du symbole de la ressource transférée, ou le nom et la valeur du symbole, pour éviter les conflits avec les noms de symboles ou les valeurs dans le fichier existant.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Rédacteurs en ressources](../windows/resource-editors.md)<br/>
