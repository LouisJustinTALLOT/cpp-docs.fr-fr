---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4078'
title: Avertissement des outils Éditeur de liens LNK4078
ms.date: 11/04/2016
f1_keywords:
- LNK4078
helpviewer_keywords:
- LNK4078
ms.assetid: 5a16796d-6caf-42d9-8f65-b042843eafb8
ms.openlocfilehash: 3fd22316d0775561c18fc2662c2f2ca843e64977
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210125"
---
# <a name="linker-tools-warning-lnk4078"></a>Avertissement des outils Éditeur de liens LNK4078

plusieurs sections « nom de la section » trouvées avec des attributs différents

Un lien a trouvé deux sections ou plus qui ont le même nom mais des attributs différents.

Cet avertissement peut être provoqué par une bibliothèque d’importation ou un fichier d’exportation qui a été créé par une version antérieure de LINK ou LIB.

Recréez le fichier et recréez la liaison.

## <a name="example"></a>Exemple

LNK4078 peut également être dû à une modification avec rupture : la section nommée par [init_seg](../../preprocessor/init-seg.md) sur x86 était en lecture/écriture, elle est désormais en lecture seule.

L’exemple suivant génère l’LNK4078.

```cpp
// LNK4078.cpp
// compile with: /W1
// LNK4078 expected
#include <stdio.h>
#pragma warning(disable : 4075)
typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors to call
PF pfx[200];   // pointers to destructors.

struct A { A() {} };

int myexit (PF pf) { return 0; }

#pragma section(".mine$a", read, write)
// try the following line instead
// #pragma section(".mine$a", read)
__declspec(allocate(".mine$a")) int ii = 1;

#pragma section(".mine$z", read, write)
// try the following line instead
// #pragma section(".mine$z", read)
__declspec(allocate(".mine$z")) int i = 1;

#pragma data_seg()
#pragma init_seg(".mine$m", myexit)
A bbbb;
A cccc;
int main() {}
```
