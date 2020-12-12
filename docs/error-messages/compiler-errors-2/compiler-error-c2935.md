---
description: 'En savoir plus sur : erreur du compilateur C2935'
title: Erreur du compilateur C2935
ms.date: 11/04/2016
f1_keywords:
- C2935
helpviewer_keywords:
- C2935
ms.assetid: e11ef90d-0756-4e43-8a09-4974c6aa72a3
ms.openlocfilehash: 853c1e51444454ffdbd09e8387d47eb9770d7fa7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320303"
---
# <a name="compiler-error-c2935"></a>Erreur du compilateur C2935

'classe' : type-class-id redéfini comme fonction globale

Vous ne pouvez pas utiliser une classe générique ou une classe de modèle comme fonction globale.

Cette erreur peut être provoquée par une mise en correspondance incorrecte des accolades.

L’exemple suivant génère l’erreur C2935 :

```cpp
// C2935.cpp
// compile with: /c
template<class T>
struct TC {};
void TC<int>() {}   // C2935

// OK
struct TC2 {};
void TC2() {}
```

L’erreur C2935 peut également se produire lors de l’utilisation de génériques :

```cpp
// C2935b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC { };
void GC<int>() {}   // C2935
void GC() {}   // OK
```
