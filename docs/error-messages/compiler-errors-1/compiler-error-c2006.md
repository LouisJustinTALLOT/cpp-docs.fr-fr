---
title: Erreur du compilateur C2006
ms.date: 11/04/2016
f1_keywords:
- C2006
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
ms.openlocfilehash: 64f81929916cd3a4adf38a302ea34d46d9a5c070
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756550"
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
