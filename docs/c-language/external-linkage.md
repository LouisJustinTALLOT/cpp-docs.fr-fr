---
title: Liaison externe
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
ms.openlocfilehash: d8a7655b7504aa8458bda8db24ff3f919b5b09c1
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509920"
---
# <a name="external-linkage"></a>Liaison externe

Si la première déclaration au niveau de la portée du fichier pour un identificateur n’utilise pas le **`static`** spécificateur de classe de stockage, l’objet a une liaison externe.

Si la déclaration d’un identificateur pour une fonction n’a pas de *Storage-Class-specifier*, sa liaison est déterminée exactement comme si elle était déclarée avec *Storage-Class-specifier* **`extern`** . Si la déclaration d'un identificateur pour un objet a une portée de fichier et aucun *storage-class-specifier*, sa liaison est externe.

Le nom d'un identificateur avec liaison externe désigne la même fonction ou le même objet de données que toute autre déclaration du même nom avec liaison externe. Les deux déclarations peuvent se trouver dans la même unité de traduction ou dans des unités différentes. Si l'objet ou la fonction a également une durée de vie globale, il ou elle est partagé(e) par le programme entier.

## <a name="see-also"></a>Voir aussi

[Utilisation d’extern pour spécifier la liaison](../cpp/extern-cpp.md)
