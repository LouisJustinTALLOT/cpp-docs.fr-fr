---
title: Erreur du compilateur C2006 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2006
dev_langs:
- C++
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9468be17584a54047563bace2b35f5cb4888b41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031202"
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