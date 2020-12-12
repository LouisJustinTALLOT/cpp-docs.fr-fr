---
description: 'En savoir plus sur : erreur du compilateur C2937'
title: Erreur du compilateur C2937
ms.date: 11/04/2016
f1_keywords:
- C2937
helpviewer_keywords:
- C2937
ms.assetid: 95671ca3-79f7-4b56-a5f2-a92296da1629
ms.openlocfilehash: af73e4564293fdcd5b69cc2f1890cb3e5364c618
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323049"
---
# <a name="compiler-error-c2937"></a>Erreur du compilateur C2937

'class' : type-class-id redéfini comme typedef global

Vous ne pouvez pas utiliser une classe générique ou de modèle comme global **`typedef`** .

L’exemple suivant génère l’erreur C2937 :

```cpp
// C2937.cpp
// compile with: /c
template<class T>
struct TC { };
typedef int TC<int>;   // C2937
typedef TC<int> c;   // OK
```

L’erreur C2937 peut également se produire lors de l’utilisation de génériques :

```cpp
// C2937b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };
typedef int GC<int>;   // C2937
typedef GC<int> xx;   // OK
```
