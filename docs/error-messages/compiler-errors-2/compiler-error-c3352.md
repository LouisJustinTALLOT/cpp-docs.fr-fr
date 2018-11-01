---
title: Erreur du compilateur C3352
ms.date: 11/04/2016
f1_keywords:
- C3352
helpviewer_keywords:
- C3352
ms.assetid: f233bed7-474e-425f-aad2-7801578169d4
ms.openlocfilehash: c45ce5e2e72c6a987a0053cb4b1bbb151c149faf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496537"
---
# <a name="compiler-error-c3352"></a>Erreur du compilateur C3352

'fonction' : la fonction spécifiée ne correspond pas au type de délégué 'type'

Les listes de paramètres pour `function` et le délégué ne correspondent pas.

Pour plus d’informations, consultez [delegate (Extensions du composant C++)](../../windows/delegate-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C3352 :

```
// C3352.cpp
// compile with: /clr
delegate int D( int, int );
ref class C {
public:
   int mf( int ) {
      return 1;
   }

   // Uncomment the following line to resolve.
   // int mf(int, int) { return 1; }
};

int main() {
   C^ pC = gcnew C;
   System::Delegate^ pD = gcnew D( pC, &C::mf );   // C3352
}
```
