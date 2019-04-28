---
title: Avertissement du compilateur (niveau 4) C4820
ms.date: 11/04/2016
f1_keywords:
- C4820
helpviewer_keywords:
- C4820
ms.assetid: 17aa29f4-c287-49b8-bc43-8ed82ffed5ea
ms.openlocfilehash: adf8b365bc39acc1ce729e89260f8385ecb6c048
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280397"
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