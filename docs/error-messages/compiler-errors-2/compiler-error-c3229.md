---
description: 'En savoir plus sur : erreur du compilateur C3229'
title: Erreur du compilateur C3229
ms.date: 11/04/2016
f1_keywords:
- C3229
helpviewer_keywords:
- C3229
ms.assetid: f2d90923-aa8b-444f-ab10-1f37dbb864e1
ms.openlocfilehash: 17d50d0bcc60357e024505499e002589525c5cba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304114"
---
# <a name="compiler-error-c3229"></a>Erreur du compilateur C3229

'type' : les indirections sur un paramètre de type générique ne sont pas autorisées

Vous ne pouvez pas utiliser de paramètres génériques avec `*`, `^`ou `&`.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’erreur C3229.

```cpp
// C3229.cpp
// compile with: /clr /c
generic <class T>
ref class C {
   T^ t;   // C3229
};

// OK
generic <class T>
ref class D {
   T u;
};
```

L’exemple suivant génère l’erreur C3229.

```cpp
// C3229_b.cpp
// compile with: /clr /c
generic <class T>   // OK
ref class Utils {
   static void sort(T elems[], size_t size);   // C3229
   static void sort2(T elems, size_t size);   // OK
};
```
