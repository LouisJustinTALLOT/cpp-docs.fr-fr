---
title: Avertissement du compilateur (niveau 4) C4820
ms.date: 11/04/2016
f1_keywords:
- C4820
helpviewer_keywords:
- C4820
ms.assetid: 17aa29f4-c287-49b8-bc43-8ed82ffed5ea
ms.openlocfilehash: ac97a943e6a8178e930d93a097071b0e3da09773
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989062"
---
# <a name="compiler-warning-level-4-c4820"></a>Avertissement du compilateur (niveau 4) C4820

'octets' octets de remplissage ajoutés après construction 'nom_membre'

Le type et l’ordre des éléments ont fait en sorte que le compilateur ajoute un remplissage à la fin d’un struct. Pour plus d’informations sur le remplissage dans une structure, consultez [Aligner](../../cpp/align-cpp.md) .

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’C4820 :

```cpp
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
