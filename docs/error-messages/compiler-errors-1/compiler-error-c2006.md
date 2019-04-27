---
title: Erreur du compilateur C2006
ms.date: 11/04/2016
f1_keywords:
- C2006
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
ms.openlocfilehash: c23f17483925f25468214165fb459db577e576fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209001"
---
# <a name="compiler-error-c2006"></a>Erreur du compilateur C2006

'directive directive' attendu d’un nom de fichier, trouvé : 'token'

Directives telles que [#include](../../preprocessor/hash-include-directive-c-cpp.md) ou [#import](../../preprocessor/hash-import-directive-cpp.md) nécessitent un nom de fichier. Pour résoudre l’erreur, assurez-vous que *jeton* est un nom de fichier valide. En outre, placez le nom de fichier entre guillemets doubles ou crochets pointus.

L’exemple suivant génère l’erreur C2006 :

```
// C2006.cpp
#include stdio.h   // C2006
```

Solution possible :

```
// C2006b.cpp
// compile with: /c
#include <stdio.h>
```