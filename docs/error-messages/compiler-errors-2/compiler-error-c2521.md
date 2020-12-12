---
description: 'En savoir plus sur : erreur du compilateur C2521'
title: Erreur du compilateur C2521
ms.date: 11/04/2016
f1_keywords:
- C2521
helpviewer_keywords:
- C2521
ms.assetid: 6042821b-e345-4a54-a7e9-a2c9019ea016
ms.openlocfilehash: a85ae6db2bd2f41ecbdd3aef385068cd2515e2bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177729"
---
# <a name="compiler-error-c2521"></a>Erreur du compilateur C2521

la fonction ne prend aucun argument

Vous avez tenté d’utiliser des arguments avec un destructeur ou un finaliseur.

Pour plus d’informations, consultez [destructeurs et finaliseurs](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2521.

```cpp
// C2521.cpp
// compile with: /clr
ref class R {
protected:
   !R() {}

public:
   void CleanUp() {
      this->!R(4);   // C2521
      this->!R();   // OK
   }
};

int main() {
   R^ r = gcnew R();
   r->CleanUp();
}
```
