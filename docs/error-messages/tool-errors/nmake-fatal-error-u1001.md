---
title: Erreur irrécupérable NMAKE U1001
ms.date: 11/04/2016
f1_keywords:
- U1001
helpviewer_keywords:
- U1001
ms.assetid: 5d7da559-6cbd-44d6-848c-aaf54cae0d1a
ms.openlocfilehash: bfe2edf9c57eda073826a8c161ae0c358f3a6232
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378451"
---
# <a name="nmake-fatal-error-u1001"></a>Erreur irrécupérable NMAKE U1001

Erreur de syntaxe : caractère non conforme 'caractère' dans la macro

Le caractère donné apparaît dans une macro, mais n’est pas une lettre, un nombre ou un trait de soulignement.

Cette erreur peut être provoquée par un signe deux-points manquant dans une expansion macro :

```
syntax error : illegal character '=' in macro
```