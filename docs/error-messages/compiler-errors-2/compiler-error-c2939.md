---
description: 'En savoir plus sur : erreur du compilateur C2939'
title: Erreur du compilateur C2939
ms.date: 11/04/2016
f1_keywords:
- C2939
helpviewer_keywords:
- C2939
ms.assetid: 455b050b-f2dc-4b5b-bd6a-e1f81d3d1644
ms.openlocfilehash: 465d2d9535a1c8f393e21b4ef48707f8e5fab89b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323023"
---
# <a name="compiler-error-c2939"></a>Erreur du compilateur C2939

'classe' : type-class-id redéfini comme variable locale de données

Vous ne pouvez pas utiliser une classe générique ou de modèle comme variable locale de données.

Cette erreur peut être provoquée par une mise en correspondance incorrecte des accolades.

L’exemple suivant génère l’erreur C2939 :

```cpp
// C2939.cpp
template<class T>
struct TC { };
int main() {
   int TC<int>;   // C2939
   int TC;   // OK
}
```

L’erreur C2939 peut également se produire lors de l’utilisation de génériques :

```cpp
// C2939b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };

int main() {
   int GC<int>;   // C2939
   int GC;   // OK
}
```
