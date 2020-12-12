---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1312'
title: Erreur des outils Éditeur de liens LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: d861b6976f9b065e3a693e916164879a3311d3db
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193628"
---
# <a name="linker-tools-error-lnk1312"></a>Erreur des outils Éditeur de liens LNK1312

fichier non valide ou endommagé : impossible d’importer l’assembly

Lors de la génération d’un assembly, un fichier autre qu’un module ou un assembly compilé avec **/CLR** a été passé à l’option de l’éditeur de liens **/ASSEMBLYMODULE** .  Si vous avez passé un fichier objet à **/ASSEMBLYMODULE**, il vous suffit de passer l’objet directement à l’éditeur de liens, plutôt qu’à **/ASSEMBLYMODULE**.

## <a name="examples"></a>Exemples

L’exemple suivant a créé le fichier. obj.

```cpp
// LNK1312.cpp
// compile with: /clr /LD
public ref class A {
public:
   int i;
};
```

L’exemple suivant génère l’LNK1312.

```cpp
// LNK1312_b.cpp
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj
// LNK1312 error expected
public ref class M {};
```
