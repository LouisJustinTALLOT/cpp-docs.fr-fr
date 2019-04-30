---
title: Erreur du compilateur C3364
ms.date: 11/04/2016
f1_keywords:
- C3364
helpviewer_keywords:
- C3364
ms.assetid: 98654741-60fe-4472-a6af-e580f8c0a6e1
ms.openlocfilehash: e99ab3919edcfb883701c08c52cd7aad60cd4591
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400355"
---
# <a name="compiler-error-c3364"></a>Erreur du compilateur C3364

'délégué' : constructeur délégué : l’argument doit être le pointeur vers la fonction membre de classe managée ou une fonction globale

Le deuxième paramètre de constructeur du délégué prend l’adresse d’une fonction membre ou l’adresse d’une fonction membre statique de n’importe quelle classe. Les deux sont traités en tant qu’adresses simples.

L’exemple suivant génère l’erreur C3364 :

```
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
