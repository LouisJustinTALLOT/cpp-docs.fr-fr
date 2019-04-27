---
title: Avertissement du compilateur (niveaux 1 et 4) C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: 8050edbd7a653776d046bc7b4155fd43094d9a5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187520"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>Avertissement du compilateur (niveaux 1 et 4) C4949

les pragmas 'managed' et 'unmanaged' sont significatifs uniquement lors de la compilation avec ' / clr [ : option]'

Le compilateur ignore le [gérés](../../preprocessor/managed-unmanaged.md) et non managées pragmas si le code source n’est pas compilé avec [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). Cet avertissement possède un caractère informatif.

L’exemple suivant génère l’erreur C4949 :

```
// C4949.cpp
// compile with: /LD /W1
#pragma managed   // C4949
```

Lorsque **#pragma unmanaged** est utilisé sans **/CLR**, C4949 est un avertissement de niveau 4.

L’exemple suivant génère l’erreur C4949 :

```
// C4949b.cpp
// compile with: /LD /W4
#pragma unmanaged   // C4949
```