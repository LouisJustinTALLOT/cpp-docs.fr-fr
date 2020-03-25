---
title: Avertissement du compilateur (niveau 1) C4103
ms.date: 11/04/2016
f1_keywords:
- C4103
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
ms.openlocfilehash: dfc3a91b2dcb3ed1e8f4f4993edd67219a6bf1d8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163843"
---
# <a name="compiler-warning-level-1-c4103"></a>Avertissement du compilateur (niveau 1) C4103

'NomFichier' : alignement modifié après l’ajout de l’en-tête, peut être dû à un #pragma Pack (POP) manquant

La compression affecte la disposition des classes, et en général, si les modifications sont comportées dans des fichiers d’en-tête, il peut y avoir des problèmes.

Utilisez #pragma [Pack](../../preprocessor/pack.md)(POP) avant de quitter le fichier d’en-tête pour résoudre cet avertissement.

L’exemple suivant génère l’C4103 :

```cpp
// C4103.h
#pragma pack(push, 4)

// defintions and declarations

// uncomment the following line to resolve
// #pragma pack(pop)
```

Puis,

```cpp
// C4103.cpp
// compile with: /LD /W1
#include "c4103.h"   // C4103
```
