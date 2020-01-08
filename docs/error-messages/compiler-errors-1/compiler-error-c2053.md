---
title: Erreur du compilateur C2053
ms.date: 11/04/2016
f1_keywords:
- C2053
helpviewer_keywords:
- C2053
ms.assetid: 13324c85-13a8-4996-bd42-a31bfe7ff80f
ms.openlocfilehash: a74e8104ec55e465875846b48186b9abdcb0f2f0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302066"
---
# <a name="compiler-error-c2053"></a>Erreur du compilateur C2053

'identificateur' : incompatibilité de chaîne étendue

La chaîne étendue est assignée à un type incompatible.

L’exemple suivant génère l’C2053 :

```c
// C2053.c
int main() {
   char array[] = L"Rika";   // C2053
}
```
