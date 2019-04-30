---
title: Erreur mathématique M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: d60e9b6284c79828fda1f7af542fcf197f189ad0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393270"
---
# <a name="math-error-m6108"></a>Erreur mathématique M6108

racine carrée

L’opérande dans une opération de la racine carrée était négatif.

Programme se termine par le code de sortie 136.

> [!NOTE]
>  Le `sqrt` fonction dans la bibliothèque Runtime C et la fonction intrinsèque FORTRAN **SQRT** ne génèrent pas cette erreur. Le C `sqrt` fonction vérifie l’argument avant d’effectuer l’opération et retourne une valeur d’erreur si l’opérande est négatif. Le FORTRAN **SQRT** fonction génère l’erreur de domaine [M6201](../../error-messages/tool-errors/math-error-m6201.md) au lieu de cette erreur.