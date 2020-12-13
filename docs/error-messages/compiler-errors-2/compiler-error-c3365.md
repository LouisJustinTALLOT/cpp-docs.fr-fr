---
description: 'En savoir plus sur : erreur du compilateur C3365'
title: Erreur du compilateur C3365
ms.date: 11/04/2016
f1_keywords:
- C3365
helpviewer_keywords:
- C3365
ms.assetid: 875ec3a4-522c-4e3d-9b67-48808b857f6d
ms.openlocfilehash: e25c0b4c53b9a811c863a96baf9555d0bde0bfc7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335017"
---
# <a name="compiler-error-c3365"></a>Erreur du compilateur C3365

opérateur 'operator' : opérandes différents de type 'type1' et 'type2'

Une tentative de composition de délégués avec des types différents a été effectuée.  Pour plus d’informations sur les délégués, consultez Guide pratique [pour définir et utiliser des délégués (C++/CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3365 :

```cpp
// C3365.cpp
// compile with: /clr
delegate void D1();
delegate void D2(int);

ref class R {
public:
   void f(){}
   void g(int){}
};

int main() {
   D1^ d1 = gcnew D1(gcnew R, &R::f);
   D2^ d2 = gcnew D2(gcnew R, &R::g);
   D1^ d3 = gcnew D1(gcnew R, &R::f);

   d1 += d2;   // C3365
   d1 += d3;   // OK
   d1();
}
```
