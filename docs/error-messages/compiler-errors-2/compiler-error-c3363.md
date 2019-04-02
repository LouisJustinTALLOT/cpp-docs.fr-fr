---
title: Erreur du compilateur C3363
ms.date: 11/04/2016
f1_keywords:
- C3363
helpviewer_keywords:
- C3363
ms.assetid: 41aa922f-608e-4f7a-ba66-451fc1161935
ms.openlocfilehash: eca598233dbe4cae4730e952b45945653ec8ffaa
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775502"
---
# <a name="compiler-error-c3363"></a>Erreur du compilateur C3363

'type' : 'typeid' applicable seulement à un type

L’opérateur [typeid](../../extensions/typeid-cpp-component-extensions.md) a été utilisé incorrectement.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3363.

```
// C3363.cpp
// compile with: /clr
int main() {
   System::typeid;   // C3363
}
```