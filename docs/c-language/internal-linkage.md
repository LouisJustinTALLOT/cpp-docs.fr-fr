---
title: Liaison interne
ms.date: 11/04/2016
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
ms.openlocfilehash: 79601af27f847a3afe7e8bdaefa926cd45459847
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325921"
---
# <a name="internal-linkage"></a>Liaison interne

Si la déclaration d'un identificateur de portée de fichier pour un objet ou une fonction contient le *storage-class-specifier * **static**, l'identificateur a une liaison interne. Sinon, l'identificateur a une liaison externe. Consultez [Classes de stockage](../c-language/c-storage-classes.md) pour plus d'informations sur l'élément non terminal *storage-class-specifier*.

Dans une unité de traduction, chaque instance d'un identificateur avec une liaison interne désigne le même identificateur ou la même fonction. Les identificateurs liés en interne sont spécifiques à une unité de traduction.

## <a name="see-also"></a>Voir aussi

[Utilisation d’extern pour spécifier la liaison](../cpp/using-extern-to-specify-linkage.md)
