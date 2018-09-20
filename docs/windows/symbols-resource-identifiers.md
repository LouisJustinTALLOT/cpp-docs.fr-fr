---
title: 'Symboles : Identificateurs de ressources (C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.identifiers
dev_langs:
- C++
helpviewer_keywords:
- symbols [C++], resource identifiers
- symbols [C++], creating
- resource symbols
- symbols [C++], editing
- resource editors [C++], resource symbols
ms.assetid: 8fccc09a-0237-4a65-b9c4-57d60c59e324
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c3bbcc774115311cd4ed0f302e4d9812ecfc6505
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422251"
---
# <a name="symbols-resource-identifiers-c"></a>Symboles : Identificateurs de ressources (C++)

Un symbole est un identificateur de ressource (ID) composé de deux parties : une chaîne de texte (nom du symbole) mappée à une valeur entière (valeur du symbole). Exemple :

```
IDC_EDITNAME = 5100
```

Les noms de symboles sont souvent appelés « identificateurs ».

Les symboles permettent de faire référence aux ressources et aux objets d’interface utilisateur d’une manière descriptive, à la fois dans votre code source et quand vous travaillez avec eux dans les éditeurs de ressources. Vous pouvez afficher et manipuler les symboles dans un emplacement pratique par le biais de la boîte de dialogue [Symboles des ressources](../windows/viewing-resource-symbols.md).

Lorsque vous créez une ressource ou un objet de ressource, les [éditeurs de ressources](../windows/resource-editors.md) fournissent un nom par défaut pour la ressource, par exemple `IDC_RADIO1`, et lui affectent une valeur. La définition nom-plus-valeur est stockée dans le fichier Resource.h.

> [!NOTE]
> Lorsque vous copiez des ressources ou des objets de ressources d’un fichier .rc vers un autre, Visual C++ peut modifier la valeur du symbole de la ressource transférée, ou le nom et la valeur du symbole, pour éviter les conflits avec les noms de symboles ou les valeurs dans le fichier existant.

Le nombre de ressources et de symboles de votre application augmente à mesure qu’elle augmente en taille et en complexité. Le suivi d’un grand nombre de symboles éparpillés dans plusieurs fichiers peut être difficile. La boîte de dialogue [Symboles des ressources](../windows/resource-symbols-dialog-box.md) simplifie la gestion des symboles en offrant un outil centralisé qui vous permet d’effectuer les tâches suivantes :

- [Afficher les symboles des ressources](../windows/viewing-resource-symbols.md)

- [Créer des symboles](../windows/creating-new-symbols.md)

- [Modifier des symboles non assignés](../windows/changing-unassigned-symbols.md)

- [Supprimer des symboles non assignés](../windows/deleting-unassigned-symbols.md)

- [Ouvrir l’Éditeur de ressources pour un symbole donné](../windows/opening-the-resource-editor-for-a-given-symbol.md)

- [Modifier un symbole ou un nom de symbole (ID)](../windows/changing-a-symbol-or-symbol-name-id.md)

- [Modifier la valeur numérique d’un symbole](../windows/changing-a-symbol-s-numeric-value.md)

- [Modifier les noms des fichiers d’en-têtes de symboles](../windows/changing-the-names-of-symbol-header-files.md)

- [Inclure des symboles partagés (en lecture seule) ou calculés](../windows/including-shared-read-only-or-calculated-symbols.md)

- [Afficher des ID de symboles prédéfinis](../windows/predefined-symbol-ids.md)

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Guide pratique pour rechercher des symboles dans les ressources](../windows/how-to-search-for-symbols-in-resources.md)<br/>
[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)