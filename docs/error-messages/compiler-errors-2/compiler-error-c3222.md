---
title: Erreur du compilateur C3222
ms.date: 11/04/2016
f1_keywords:
- C3222
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
ms.openlocfilehash: 9f2c245e98609c8da8f5f89902d5c51bbf9d2b4f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364010"
---
# <a name="compiler-error-c3222"></a>Erreur du compilateur C3222

'paramètre' : impossible de déclarer des arguments par défaut pour des fonctions membres d'un type managé ou WinRT ou des fonctions génériques

Il n’est pas autorisé de déclarer un paramètre de méthode avec un argument par défaut. Une forme surchargée de la méthode est une façon de contourner ce problème. Autrement dit, définissez une méthode portant le même nom sans paramètres, puis initialisez la variable dans le corps de la méthode.

L'exemple suivant génère l'erreur C3222 :

```
// C3222_2.cpp
// compile with: /clr
public ref class G {
   void f( int n = 0 );   // C3222
};
```
