---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4794'
title: Avertissement du compilateur (niveau 1) C4794
ms.date: 11/04/2016
f1_keywords:
- C4794
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
ms.openlocfilehash: bd43a9fb1f7f2433a4e1d337d49c1921211a9e5d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334952"
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
