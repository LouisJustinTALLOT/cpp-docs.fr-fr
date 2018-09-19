---
title: Compilateur avertissement (niveau 4) C4820 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4820
dev_langs:
- C++
helpviewer_keywords:
- C4820
ms.assetid: 17aa29f4-c287-49b8-bc43-8ed82ffed5ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c27466912956988a2396b8e3c52fc41ed2caa604
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016337"
---
# <a name="compiler-warning-level-4-c4820"></a>Avertissement du compilateur (niveau 4) C4820

'octets' octets de remplissage ajoutés après construction 'nom_membre'

Le type et l’ordre des éléments due au compilateur d’ajouter une marge intérieure à la fin d’un struct. Consultez [aligner](../../cpp/align-cpp.md) pour plus d’informations sur le remplissage dans un struct.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’erreur C4820 :

```
// C4820.cpp
// compile with: /W4 /c
#pragma warning(default : 4820)

// Delete the following 4 lines to resolve.
__declspec(align(2)) struct MyStruct {
   char a;
   int i;   // C4820
};

// OK
#pragma pack(1)
__declspec(align(1)) struct MyStruct2 {
   char a;
   int i;
};
```