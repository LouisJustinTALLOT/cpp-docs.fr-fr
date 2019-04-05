---
title: no_auto_exclude
ms.date: 11/04/2016
f1_keywords:
- no_auto_exclude
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
ms.openlocfilehash: 06bde7535bd181057750ab9dd4c3999321b4990c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038940"
---
# <a name="noautoexclude"></a>no_auto_exclude
**Section spécifique à C++**

Désactive l'exclusion automatique.

## <a name="syntax"></a>Syntaxe

```
no_auto_exclude
```

## <a name="remarks"></a>Notes

Les bibliothèques de types peuvent inclure des définitions d'éléments définis dans les en-têtes système ou dans d'autres bibliothèques de types. `#import` tente d’éviter les erreurs de définitions multiples en excluant automatiquement ces éléments. Dans ce cas, [Avertissement du compilateur (niveau 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) sera émis pour chaque élément à exclure. Vous pouvez désactiver cette exclusion automatique à l'aide de cet attribut.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[Attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import, directive](../preprocessor/hash-import-directive-cpp.md)