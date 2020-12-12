---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4103'
title: Avertissement du compilateur (niveau 1) C4103
ms.date: 11/04/2016
f1_keywords:
- C4103
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
ms.openlocfilehash: 98a9cfbda60ccc938f2cda7803fcdf7e996def9f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272225"
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
