---
title: Avertissement du compilateur (niveau 1) C4794
ms.date: 11/04/2016
f1_keywords:
- C4794
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
ms.openlocfilehash: 7f7ea7555937069caf5f83c9bf00f0fa980ef020
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175114"
---
# <a name="compiler-warning-level-1-c4794"></a>Avertissement du compilateur (niveau 1) C4794

segment de variable de thread de stockage local 'variable' modifié de 'section name' en '.tls$'

Vous avez utilisé [#pragma data_seg](../../preprocessor/data-seg.md) pour placer une variable tls dans une section qui ne commence pas par .tls$.

La section .tls$*x* existe dans le fichier objet dans lequel sont définies des variables [__declspec(thread)](../../cpp/thread.md) . Une section .tls dans le fichier EXE ou DLL résulte de ces sections.

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4794 :

```cpp
// C4794.cpp
// compile with: /W1 /c
#pragma data_seg(".someseg")
__declspec(thread) int i;   // C4794

// OK
#pragma data_seg(".tls$9")
__declspec(thread) int j;
```
