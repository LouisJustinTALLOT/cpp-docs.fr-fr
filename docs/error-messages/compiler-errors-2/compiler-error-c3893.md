---
title: Erreur du compilateur C3893 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3893
dev_langs:
- C++
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 857d13de61f03bf0784d8cd10ad092d16f7acdaa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087036"
---
# <a name="compiler-error-c3893"></a>Erreur du compilateur C3893

'var' : utilisation comme l-value des données membres initonly n’est autorisée uniquement dans un constructeur d’instance de classe 'nom_type'

Statique [initonly](../../dotnet/initonly-cpp-cli.md) membres de données peuvent avoir uniquement leur adresse effectuée dans un constructeur statique.

Instance (non statique) les données membres initonly n’admet qu’adresse est acceptée dans les constructeurs d’instance (non statique).

L’exemple suivant génère l’erreur C3893 :

```
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