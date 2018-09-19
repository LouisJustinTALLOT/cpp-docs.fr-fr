---
title: Erreur du compilateur C3116 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3116
dev_langs:
- C++
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1104b731fa565991615eb88cc34fa946e2bfb505
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077843"
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