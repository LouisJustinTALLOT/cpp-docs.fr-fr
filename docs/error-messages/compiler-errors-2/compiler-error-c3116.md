---
description: 'En savoir plus sur : erreur du compilateur C3116'
title: Erreur du compilateur C3116
ms.date: 11/04/2016
f1_keywords:
- C3116
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
ms.openlocfilehash: ea11d851c4348725c48e408ffdd0ed6de4393e6e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115935"
---
# <a name="compiler-error-c3116"></a>Erreur du compilateur C3116

'Storage specifier' : classe de stockage non valide pour la méthode d’interface

Vous avez utilisé **`typedef`** , **`register`** ou **`static`** comme classe de stockage pour une méthode d’interface. Ces classes de stockage ne sont pas autorisées sur les membres d’interface.

L’exemple suivant génère l’C3116 :

```cpp
// C3116.cpp
__interface ImyInterface
{
   static void myFunc();   // C3116
};
```
