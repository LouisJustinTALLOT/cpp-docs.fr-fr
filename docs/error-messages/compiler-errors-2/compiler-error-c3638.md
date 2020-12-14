---
description: 'En savoir plus sur : erreur du compilateur C3638'
title: Erreur du compilateur C3638
ms.date: 11/04/2016
f1_keywords:
- C3638
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
ms.openlocfilehash: 1d1cc59cd8065a5b0e661292b717ba885c6febeb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239192"
---
# <a name="compiler-error-c3638"></a>Erreur du compilateur C3638

'operator' : impossible de redéfinir les opérateurs de conversion boxing et unboxing standard

Le compilateur définit un opérateur de conversion pour chaque classe managée afin de prendre en charge la conversion boxing implicite. Cet opérateur ne peut pas être redéfini.

Pour plus d’informations, consultez [conversion boxing implicite](../../extensions/boxing-cpp-component-extensions.md).

L’exemple suivant génère l’C3638 :

```cpp
// C3638.cpp
// compile with: /clr
value struct V {
   V(){}
   static operator V^(V);   // C3638
};

int main() {
   V myV;
   V ^ pmyV = myV;   // operator supports implicit boxing
}
```
