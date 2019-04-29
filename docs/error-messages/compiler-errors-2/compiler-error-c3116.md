---
title: Erreur du compilateur C3116
ms.date: 11/04/2016
f1_keywords:
- C3116
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
ms.openlocfilehash: 3f587bc677d64bda0fb5eea0b7ebc8d5761a2e75
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376066"
---
# <a name="compiler-error-c3116"></a>Erreur du compilateur C3116

'spécificateur de stockage' : classe de stockage non valide pour la méthode d’interface

Vous avez utilisé `typedef`, `register`, ou `static` comme classe de stockage pour une méthode d’interface. Ces classes de stockage ne sont pas autorisées sur les membres d’interface.

L’exemple suivant génère l’erreur C3116 :

```
// C3116.cpp
__interface ImyInterface
{
   static void myFunc();   // C3116
};
```