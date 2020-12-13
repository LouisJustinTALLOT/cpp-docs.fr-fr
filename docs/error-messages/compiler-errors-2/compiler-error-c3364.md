---
description: 'En savoir plus sur : erreur du compilateur C3364'
title: Erreur du compilateur C3364
ms.date: 11/04/2016
f1_keywords:
- C3364
helpviewer_keywords:
- C3364
ms.assetid: 98654741-60fe-4472-a6af-e580f8c0a6e1
ms.openlocfilehash: e500b984489de1dfc2cd68d91ac5cb457d3887f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150850"
---
# <a name="compiler-error-c3364"></a>Erreur du compilateur C3364

'Delegate' : constructeur délégué : l’argument doit être un pointeur vers une fonction membre d’une classe managée ou d’une fonction globale

Le deuxième paramètre du constructeur du délégué prend l’adresse d’une fonction membre ou l’adresse d’une fonction membre statique d’une classe quelconque. Les deux sont traités comme des adresses simples.

L’exemple suivant génère l’C3364 :

```cpp
// C3364_2.cpp
// compile with: /clr

delegate int D( int, int );

ref class C {
public:
   int mf( int, int ) {
      return 1;
   }
};

int main() {
   C^ pC = gcnew C;
   System::Delegate^ pD = gcnew D( pC,pC->mf( 1, 2 ) ); // C3364

   // try the following line instead
   // System::Delegate^ pD = gcnew D(pC, &C::mf);
}
```
