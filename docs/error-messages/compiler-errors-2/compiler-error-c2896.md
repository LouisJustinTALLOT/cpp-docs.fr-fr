---
description: 'En savoir plus sur : erreur du compilateur C2896'
title: Erreur du compilateur C2896
ms.date: 11/04/2016
f1_keywords:
- C2896
helpviewer_keywords:
- C2896
ms.assetid: b600407b-cb05-42e3-9069-2aa6960f0eaa
ms.openlocfilehash: 096650ab4ced95ace9bbf51680339ba0258eff45
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270899"
---
# <a name="compiler-error-c2896"></a>Erreur du compilateur C2896

'fonction1 ' : impossible d’utiliser le modèle de fonction’fonction2 'en tant qu’argument

Un modèle de fonction ne peut pas être un argument d’un autre modèle de fonction.

L’exemple suivant génère l’C2896 :

```cpp
// C2896.cpp
template<class T1, class T2> void f1(void(*)(T1, T2));
template<class T1, class T2> void f2(T1, T2);

int main() {
   f1(f2);   // C2896
}
```

C2896 peut également se produire quand vous utilisez des génériques :

```cpp
// C2896b.cpp
// compile with: /clr
generic<class T1> void gf1(T1){}
generic<class T1> void gf2(T1){}

int main() {
   gf1(gf2);   // C2896
   gf1(1);   // OK
}
```
