---
title: Avertissement des outils Éditeur de liens LNK4078
ms.date: 11/04/2016
f1_keywords:
- LNK4078
helpviewer_keywords:
- LNK4078
ms.assetid: 5a16796d-6caf-42d9-8f65-b042843eafb8
ms.openlocfilehash: d20eb0523ffebe9229d05b6316772259661f6020
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614147"
---
# <a name="linker-tools-warning-lnk4078"></a>Avertissement des outils Éditeur de liens LNK4078

plusieurs sections 'section name' trouvées avec différents attributs

LIEN a détecté deux ou plusieurs sections qui ont le même nomment mais des attributs.

Cet avertissement peut être dû à un fichier de bibliothèque ou les exportations d’importation qui a été créé par une version précédente de LINK ou LIB.

Recréez le fichier et les relier.

## <a name="example"></a>Exemple

Erreur LNK4078 peut également être provoquée par une modification avec rupture : la section nommée par [init_seg](../../preprocessor/init-seg.md) sur x86 était en lecture/écriture, il est désormais en lecture seule.

L’exemple suivant génère l’erreur LNK4078.

```
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