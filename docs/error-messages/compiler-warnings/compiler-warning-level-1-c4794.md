---
title: Avertissement du compilateur (niveau 1) C4794
ms.date: 11/04/2016
f1_keywords:
- C4794
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
ms.openlocfilehash: 7d669280c0dc6a730a22480e602dac8cc6153449
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052379"
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