---
title: Avertissement des outils Éditeur de liens LNK4254
ms.date: 11/04/2016
f1_keywords:
- LNK4254
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
ms.openlocfilehash: 8431bd2d89fd5df5cf076ad006ab04006f552c4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988062"
---
# <a name="linker-tools-warning-lnk4254"></a>Avertissement des outils Éditeur de liens LNK4254

section 'section1' (offset) merged into 'section2' (offset) with different attributes

The contents of one section were merged into another, but the attributes of the two sections are different. Your program may give unexpected results. For example, data you wanted to be read only may now be in a writable section.

To resolve LNK4254, modify or remove the merge request.

When targeting x86 machines and Windows CE targets (ARM, MIPS, SH4, and Thumb) with Visual C++, the .CRT section is read-only. If your code depends on previous behavior (.CRT sections are read/write), you could see unexpected behavior.

Pour plus d'informations, consultez

- [/MERGE (Combiner des sections)](../../build/reference/merge-combine-sections.md)

- [commentaire (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Exemple

The following sample generates LNK4254.

```cpp
// LNK4254.cpp
// compile with: /W1 /link /WX
// LNK4254 expected
#pragma comment(linker, "/merge:.data=.text")
int main() {}
```
