---
title: Erreur mathématique M6108 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6108
dev_langs:
- C++
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1624a89b472733b4adb5563c8ba52e0b03dcaa2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048615"
---
# <a name="math-error-m6108"></a>Erreur mathématique M6108

racine carrée

L’opérande dans une opération de la racine carrée était négatif.

Programme se termine par le code de sortie 136.

> [!NOTE]
>  Le `sqrt` fonction dans la bibliothèque Runtime C et la fonction intrinsèque FORTRAN **SQRT** ne génèrent pas cette erreur. Le C `sqrt` fonction vérifie l’argument avant d’effectuer l’opération et retourne une valeur d’erreur si l’opérande est négatif. Le FORTRAN **SQRT** fonction génère l’erreur de domaine [M6201](../../error-messages/tool-errors/math-error-m6201.md) au lieu de cette erreur.