---
title: Erreur mathématique M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: 68e6ae823613d87eb01c443b564b46746259cd7b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173723"
---
# <a name="math-error-m6108"></a>Erreur mathématique M6108

racine carrée

L’opérande dans une opération de racine carrée était négatif.

Le programme se termine avec le code de sortie 136.

> [!NOTE]
>  La fonction `sqrt` dans la bibliothèque Runtime C et la fonction intrinsèque FORTRAN **sqrt** ne génèrent pas cette erreur. La fonction C `sqrt` vérifie l’argument avant d’effectuer l’opération et retourne une valeur d’erreur si l’opérande est négatif. La fonction de FORTRAN **sqrt** génère l’erreur de domaine [mathématique M6201](../../error-messages/tool-errors/math-error-m6201.md) au lieu de cette erreur.
