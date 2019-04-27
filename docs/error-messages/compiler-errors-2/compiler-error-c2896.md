---
title: Erreur du compilateur C2896
ms.date: 11/04/2016
f1_keywords:
- C2896
helpviewer_keywords:
- C2896
ms.assetid: b600407b-cb05-42e3-9069-2aa6960f0eaa
ms.openlocfilehash: 1e30dc17e7c143af52c5a8b56be7f1efa7632ee2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227408"
---
# <a name="compiler-error-c2896"></a>Erreur du compilateur C2896

'fonction1' : Impossible d’utiliser le modèle de fonction 'fonction2' comme argument

Un modèle de fonction ne peut pas être un argument à un autre modèle de fonction.

L’exemple suivant génère l’erreur C2896 :

```
// C2896.cpp
template<class T1, class T2> void f1(void(*)(T1, T2));
template<class T1, class T2> void f2(T1, T2);

int main() {
   f1(f2);   // C2896
}
```

C2896 peut également se produire lors de l’utilisation de génériques :

```
// C2896b.cpp
// compile with: /clr
generic<class T1> void gf1(T1){}
generic<class T1> void gf2(T1){}

int main() {
   gf1(gf2);   // C2896
   gf1(1);   // OK
}
```