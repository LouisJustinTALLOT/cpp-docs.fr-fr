---
title: Erreur du compilateur C2430 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2430
dev_langs:
- C++
helpviewer_keywords:
- C2430
ms.assetid: 07c20f76-63e1-4d22-b2a9-98b0d45c5cac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 102e7082a3fc1cfd96db5c38832e3ebb91ee742c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054452"
---
# <a name="compiler-error-c2430"></a>Erreur du compilateur C2430

plus d’un registre d’index dans 'identificateur'

Plus d’un Registre est mis à l’échelle. Le compilateur prend en charge l’indexation à l’échelle, mais vous pouvez uniquement mettre à l’échelle un Registre.

## <a name="example"></a>Exemple

L’exemple suivant génère C2430.

```
// C2430.cpp
// processor: x86
int main() {
   _asm mov eax, [ebx*2+ecx*4] // C2430
}
```