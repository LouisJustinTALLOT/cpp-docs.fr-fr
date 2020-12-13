---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4820'
title: Avertissement du compilateur (niveau 4) C4820
ms.date: 11/04/2016
f1_keywords:
- C4820
helpviewer_keywords:
- C4820
ms.assetid: 17aa29f4-c287-49b8-bc43-8ed82ffed5ea
ms.openlocfilehash: 778bf605d6ee1441e9efd68380c64d231df03b69
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330476"
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
