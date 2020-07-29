---
title: Liaison interne
ms.date: 11/04/2016
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
ms.openlocfilehash: 3709ca815877b98fe5dfe6e5b2eca6b5c627641b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229595"
---
# <a name="internal-linkage"></a>Liaison interne

Si la déclaration d’un identificateur de portée de fichier pour un objet ou une fonction contient le *Storage-Class-specifier* **`static`** , l’identificateur a une liaison interne. Sinon, l'identificateur a une liaison externe. Consultez [Classes de stockage](../c-language/c-storage-classes.md) pour plus d'informations sur l'élément non terminal *storage-class-specifier*.

Dans une unité de traduction, chaque instance d'un identificateur avec une liaison interne désigne le même identificateur ou la même fonction. Les identificateurs liés en interne sont spécifiques à une unité de traduction.

## <a name="see-also"></a>Voir aussi

[Utilisation d’extern pour spécifier la liaison](../cpp/using-extern-to-specify-linkage.md)
