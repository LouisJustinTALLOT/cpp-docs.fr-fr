---
title: Erreur du compilateur C2921 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2921
dev_langs:
- C++
helpviewer_keywords:
- C2921
ms.assetid: 323642a0-bfc4-4942-9f41-c3adf5c54296
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afc445bd9d30e97d669cf02b53d98553e9658e47
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100940"
---
# <a name="compiler-error-c2921"></a>Erreur du compilateur C2921

redéfinition : 'classe' : classe modèle ou générique en cours de redéclaration comme 'type'

Une classe générique ou de modèle possède plusieurs déclarations qui ne sont pas équivalentes. Pour corriger cette erreur, utilisez des noms différents pour des types différents ou supprimez la redéfinition du nom de type.

L'exemple suivant génère l'erreur C2921 :

```
// C2921.cpp
// compile with: /c
template <class T> struct TC2 {};
typedef int TC2;   // C2921
// try the following line instead
// typedef struct TC2<int> x;   // OK - declare a template instance
```

L'erreur C2921 peut également se produire lors de l'utilisation de génériques.

```
// C2921b.cpp
// compile with: /clr /c
generic <class T> ref struct GC2 {};
typedef int GC2;   // C2921
// try the following line instead
// typedef ref struct GC2<int> x;
```