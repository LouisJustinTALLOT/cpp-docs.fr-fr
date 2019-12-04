---
title: Erreur du compilateur C3893
ms.date: 11/04/2016
f1_keywords:
- C3893
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
ms.openlocfilehash: 20c17eaa6555b5511ecbc930eacdb2ec92475b23
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749501"
---
# <a name="compiler-error-c3893"></a>Erreur du compilateur C3893

'var' : l’utilisation de l-value des données membres initonly n’est autorisée que dans un constructeur d’instance de la classe’type_name'

L’adresse des membres de données [initonly](../../dotnet/initonly-cpp-cli.md) statiques ne peut être utilisée que dans un constructeur statique.

Les membres de données initonly de l’instance (non statiques) ne peuvent avoir qu’une adresse prise dans des constructeurs d’instance (non statiques).

L’exemple suivant génère l’C3893 :

```cpp
// C3893.cpp
// compile with: /clr
ref struct Y1 {
   Y1() : data_var(0) {
      int% i = data_var;   // OK
   }
   initonly int data_var;
};

int main(){
   Y1^ y= gcnew Y1;
   int% i = y->data_var;   // C3893
}
```
