---
title: Erreur du compilateur C3214
ms.date: 11/04/2016
f1_keywords:
- C3214
helpviewer_keywords:
- C3214
ms.assetid: 49ee4a9a-2549-4adb-9d3a-38e154303c2e
ms.openlocfilehash: e4f271ec4abdc05b5cf148e40a752b4d62cc884c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182546"
---
# <a name="compiler-error-c3214"></a>Erreur du compilateur C3214

'type' : argument de type non valide pour le paramètre générique 'paramètre' du générique 'type_générique', ne satisfait pas la contrainte 'contrainte'

Le type a été spécifié pour une instanciation d’une classe générique qui ne satisfait pas à la contrainte de la classe générique.

L’exemple suivant génère l’erreur C3214 :

```
// C3214.cpp
// compile with: /clr
interface struct A {};

generic <class T>
where T : A
ref class C {};

ref class X : public A {};

int main() {
   C<int>^ c = new C<int>;   // C3214
   C<X ^> ^ c2 = new C<X^>;   // OK
}
```