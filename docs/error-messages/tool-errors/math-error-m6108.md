---
title: Erreur mathématique M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: c6bd403437ee5e55eaf4add288995d0e4aa76c3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361970"
---
# <a name="math-error-m6108"></a>Erreur mathématique M6108

racine carrée

L’opérande dans une opération de racine carrée était négative.

Le programme se termine par le code de sortie 136.

> [!NOTE]
> La `sqrt` fonction dans la bibliothèque C run-time et la fonction intrinsèque FORTRAN **SQRT** ne génèrent pas cette erreur. La `sqrt` fonction C vérifie l’argument avant d’effectuer l’opération et renvoie une valeur d’erreur si l’opérande est négative. La fonction FORTRAN **SQRT** génère l’erreur [DOMAIN M6201](../../error-messages/tool-errors/math-error-m6201.md) au lieu de cette erreur.
