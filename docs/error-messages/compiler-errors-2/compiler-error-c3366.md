---
title: Erreur du compilateur C3366
ms.date: 11/04/2016
f1_keywords:
- C3366
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
ms.openlocfilehash: 4d1cd510cda9957ced1d9dd5fd8fea267f39220d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507768"
---
# <a name="compiler-error-c3366"></a>Erreur du compilateur C3366

'variable' : données membres static des gérés ou WinRTtypes doivent être définies dans la définition de classe

Vous avez tenté de référencer un membre statique d'une interface ou d'une classe WinRT ou .NET à l'extérieur de la définition de cette classe ou interface.

Le compilateur doit connaître la définition complète de la classe (pour émettre les métadonnées après une passe) et exige l'initialisation des membres de données statiques dans la classe.

Par exemple, l'exemple suivant génère l'erreur C3366 et montre comment la corriger :

```
// C3366.cpp
// compile with: /clr /c
ref class X {
   public:
   static int i;   // initialize i here to avoid C3366
};

int X::i = 5;      // C3366
```
