---
description: 'En savoir plus sur : erreur du compilateur C2921'
title: Erreur du compilateur C2921
ms.date: 11/04/2016
f1_keywords:
- C2921
helpviewer_keywords:
- C2921
ms.assetid: 323642a0-bfc4-4942-9f41-c3adf5c54296
ms.openlocfilehash: 95c47b1446973db77e4567dce0d4af8adf321672
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270301"
---
# <a name="compiler-error-c2921"></a>Erreur du compilateur C2921

redéfinition : 'classe' : classe modèle ou générique en cours de redéclaration comme 'type'

Une classe générique ou de modèle possède plusieurs déclarations qui ne sont pas équivalentes. Pour corriger cette erreur, utilisez des noms différents pour des types différents ou supprimez la redéfinition du nom de type.

L'exemple suivant génère l'erreur C2921 :

```cpp
// C2921.cpp
// compile with: /c
template <class T> struct TC2 {};
typedef int TC2;   // C2921
// try the following line instead
// typedef struct TC2<int> x;   // OK - declare a template instance
```

L'erreur C2921 peut également se produire lors de l'utilisation de génériques.

```cpp
// C2921b.cpp
// compile with: /clr /c
generic <class T> ref struct GC2 {};
typedef int GC2;   // C2921
// try the following line instead
// typedef ref struct GC2<int> x;
```
