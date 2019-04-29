---
title: include()
ms.date: 10/18/2018
f1_keywords:
- include()
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
ms.openlocfilehash: 1208f14a9f6b3724dd5353df57213baa3910d07f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383735"
---
# <a name="include"></a>include()

**Spécifique à C++**

Désactive l'exclusion automatique.

## <a name="syntax"></a>Syntaxe

```
include("Name1"[,"Name2", ...])
```

### <a name="parameters"></a>Paramètres

*Name1*<br/>
Premier élément à inclure de force.

*Name2*<br/>
Deuxième élément à inclure de force (si nécessaire).

## <a name="remarks"></a>Notes

Les bibliothèques de types peuvent inclure des définitions d'éléments définis dans les en-têtes système ou dans d'autres bibliothèques de types. `#import` tente d'éviter les erreurs de définitions multiples en excluant automatiquement ces éléments. Si les éléments ont été exclus, comme indiqué par [Avertissement du compilateur (niveau 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md), et ils ne doivent pas avoir été, cet attribut peut être utilisé pour désactiver l’exclusion automatique. Cet attribut peut comprendre n’importe quel nombre d’arguments, chacun portant le nom de l’élément bibliothèque-types à inclure.

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)