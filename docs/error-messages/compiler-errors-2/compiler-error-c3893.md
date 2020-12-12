---
description: 'En savoir plus sur : erreur du compilateur C3893'
title: Erreur du compilateur C3893
ms.date: 11/04/2016
f1_keywords:
- C3893
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
ms.openlocfilehash: 975e2e356bc4b98a25a80e8ae4cc152c3b9b3207
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119916"
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
