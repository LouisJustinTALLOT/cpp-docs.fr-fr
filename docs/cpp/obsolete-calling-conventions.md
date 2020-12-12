---
description: 'En savoir plus sur : conventions d’appel obsolètes'
title: Conventions d'appel obsolètes
ms.date: 11/04/2016
f1_keywords:
- __fortran
- __pascal
- __syscall
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
ms.openlocfilehash: 0dfbb34215ba79b54d01ce12fe4d543dbe1d6859
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146040"
---
# <a name="obsolete-calling-conventions"></a>Conventions d'appel obsolètes

**Spécifique à Microsoft**

Les conventions d’appel **__pascal**, **__fortran** et **__syscall** ne sont plus prises en charge. Vous pouvez émuler leurs fonctionnalités en utilisant l’une des conventions d’appel prises en charge et les options appropriées de l’Éditeur de liens.

\<windows.h> prend désormais en charge la macro WINAPI, qui se traduit par la Convention d’appel appropriée pour la cible. Utilisez WINAPI dans lequel vous avez précédemment utilisé PASCAL ou **__far \_ _pascal**.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Passage des arguments et conventions de dénomination](../cpp/argument-passing-and-naming-conventions.md)
