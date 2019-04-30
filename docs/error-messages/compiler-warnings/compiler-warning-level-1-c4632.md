---
title: Avertissement du compilateur (niveau 1) C4632
ms.date: 11/04/2016
f1_keywords:
- C4632
helpviewer_keywords:
- C4632
ms.assetid: 9e35d205-cf21-4e34-8bd5-e1e7b0e2cdd3
ms.openlocfilehash: f1870da4f7889d79f5a4eabfcc3a95a21703e9fd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393543"
---
# <a name="compiler-warning-level-1-c4632"></a>Avertissement du compilateur (niveau 1) C4632

Commentaire de document XML : fichier - accès refusé : raison

Le chemin d’accès au fichier .xdc (`file`) n’était pas valide, et aucun fichier .xdc est créé.

L’exemple suivant génère l’erreur C4632 :

```
// C4632.cpp
// compile with: /clr /docv:\\falsedir /LD /W1
// C4632 expected

/// Text for class MyClass.
public ref class MyClass {};
```