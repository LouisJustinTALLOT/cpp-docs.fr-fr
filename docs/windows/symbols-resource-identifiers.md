---
description: 'En savoir plus sur : identificateurs de ressource (symboles) (C++)'
title: Identificateurs de ressource (symboles) (C++)
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
ms.openlocfilehash: 1299bb366ba380972d0027dc7285f6ac14dffe37
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247083"
---
# <a name="resource-identifiers-symbols-c"></a>Identificateurs de ressource (symboles) (C++)

Un symbole est un identificateur de ressource (ID) composé de deux parties, un nom de symbole (chaîne de texte) mappé à une valeur de symbole (entier), par exemple :

```cpp
IDC_EDITNAME = 5100
```

Les noms de symboles sont souvent appelés « identificateurs ».

Les symboles permettent de faire référence aux ressources et aux objets d’interface utilisateur d’une manière descriptive, à la fois dans votre code source et quand vous travaillez avec eux dans les éditeurs de ressources. Vous pouvez afficher et manipuler les symboles dans un emplacement pratique par le biais de la boîte de dialogue [Symboles des ressources](./creating-new-symbols.md).

Le nombre de ressources et de symboles de votre application augmente à mesure qu’elle augmente en taille et en complexité. Le suivi d’un grand nombre de symboles éparpillés dans plusieurs fichiers peut être difficile. La boîte de dialogue **symboles des ressources** simplifie la gestion des symboles en offrant un outil central permettant d’effectuer les opérations suivantes :

- [Créer des symboles](../windows/creating-new-symbols.md)

- [Gérer les symboles](../windows/changing-a-symbol-or-symbol-name-id.md)

- [Afficher des ID de symboles prédéfinis](../windows/predefined-symbol-ids.md)

Lorsque vous créez une ressource ou un objet de ressource, les [éditeurs de ressources](../windows/resource-editors.md) fournissent un nom par défaut pour la ressource, par exemple `IDC_RADIO1`, et lui affectent une valeur. La définition nom-plus-valeur est stockée dans le `Resource.h` fichier.

> [!NOTE]
> Lorsque vous copiez des ressources ou des objets de ressources d’un fichier .rc vers un autre, Visual C++ peut modifier la valeur du symbole de la ressource transférée, ou le nom et la valeur du symbole, pour éviter les conflits avec les noms de symboles ou les valeurs dans le fichier existant.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Éditeurs de ressources](../windows/resource-editors.md)<br/>
