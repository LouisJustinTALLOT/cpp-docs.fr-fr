---
description: 'En savoir plus sur : erreur du compilateur C2010'
title: Erreur du compilateur C2010
ms.date: 11/04/2016
f1_keywords:
- C2010
helpviewer_keywords:
- C2010
ms.assetid: 5795ed1d-e206-410b-b7b4-528d125c67b4
ms.openlocfilehash: 8a96c30103d46c23f3b678a2fa84abf34445dd11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221031"
---
# <a name="compiler-error-c2010"></a>Erreur du compilateur C2010

'caractère' : inattendu dans la liste de paramètres formels d’une macro

Le caractère est utilisé de manière incorrecte dans la liste de paramètres formels d’une définition de macro. Supprimez le caractère pour résoudre l’erreur.

L’exemple suivant génère l’C2010 :

```cpp
// C2010.cpp
// compile with: /c
#define mymacro(a|) (2*a)   // C2010
#define mymacro(a) (2*a)   // OK
```
