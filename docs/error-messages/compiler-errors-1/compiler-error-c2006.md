---
description: 'En savoir plus sur : erreur du compilateur C2006'
title: Erreur du compilateur C2006
ms.date: 11/04/2016
f1_keywords:
- C2006
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
ms.openlocfilehash: 5747f5417db60bd3c1f7bc1420c257552a9b42c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298511"
---
# <a name="compiler-error-c2006"></a>Erreur du compilateur C2006

'directive’attendait un nom de fichier, 'Token’trouvé

Les directives telles que [#include](../../preprocessor/hash-include-directive-c-cpp.md) ou [#import](../../preprocessor/hash-import-directive-cpp.md) requièrent un nom de fichier. Pour résoudre cette erreur, assurez-vous que le *jeton* est un nom de fichier valide. Placez également le nom de fichier entre guillemets doubles ou chevrons.

L’exemple suivant génère l’C2006 :

```cpp
// C2006.cpp
#include stdio.h   // C2006
```

Solution possible :

```cpp
// C2006b.cpp
// compile with: /c
#include <stdio.h>
```
