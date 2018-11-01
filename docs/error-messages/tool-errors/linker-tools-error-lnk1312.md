---
title: Erreur des outils Éditeur de liens LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: 49fa7e7963d6bb561e1602b58fe1f26c5f3d54bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436229"
---
# <a name="linker-tools-error-lnk1312"></a>Erreur des outils Éditeur de liens LNK1312

fichier non valide ou endommagé : Impossible d’importer l’assembly

Lors de la création d’un assembly, un fichier autre qu’un module ou un assembly compilé avec **/CLR** a été passé à la **/ASSEMBLYMODULE** option de l’éditeur de liens.  Si vous avez passé un fichier objet à **/ASSEMBLYMODULE**, simplement passer l’objet directement à l’éditeur de liens, plutôt qu’à **/ASSEMBLYMODULE**.

## <a name="example"></a>Exemple

L’exemple suivant créé le fichier .obj.

```
// LNK1312.cpp
// compile with: /clr /LD
public ref class A {
public:
   int i;
};
```

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur LNK1312.

```
// LNK1312_b.cpp
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj
// LNK1312 error expected
public ref class M {};
```