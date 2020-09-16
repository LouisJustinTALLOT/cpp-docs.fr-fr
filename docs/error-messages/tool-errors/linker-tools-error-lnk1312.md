---
title: Erreur des outils Éditeur de liens LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: 69af2bd2c22fdb1188cf0b7119791e451e80f966
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686494"
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
