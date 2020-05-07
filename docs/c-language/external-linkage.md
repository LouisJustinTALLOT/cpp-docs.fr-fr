---
title: Liaison externe
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
ms.openlocfilehash: 35b0fda1f501755640123f5181454a5c36b7e986
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233735"
---
# <a name="external-linkage"></a>Liaison externe

Si la première déclaration au niveau de la portée du fichier d'un identificateur n'utilise pas le spécificateur de classe de stockage **static**, l'objet a une liaison externe.

Si la déclaration d'un identificateur pour une fonction ne comporte aucun *storage-class-specifier*, sa liaison est déterminée exactement comme s'il était déclaré avec le *storage-class-specifier* `extern`. Si la déclaration d'un identificateur pour un objet a une portée de fichier et aucun *storage-class-specifier*, sa liaison est externe.

Le nom d'un identificateur avec liaison externe désigne la même fonction ou le même objet de données que toute autre déclaration du même nom avec liaison externe. Les deux déclarations peuvent se trouver dans la même unité de traduction ou dans des unités différentes. Si l'objet ou la fonction a également une durée de vie globale, il ou elle est partagé(e) par le programme entier.

## <a name="see-also"></a>Voir aussi

[Utilisation d’extern pour spécifier la liaison](../cpp/using-extern-to-specify-linkage.md)
