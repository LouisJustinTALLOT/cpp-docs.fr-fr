---
description: 'En savoir plus sur : erreur mathématique mathématique M6108'
title: Erreur mathématique M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: 1a0acf13bd166e499334cb13de33093c2c804f5f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143882"
---
# <a name="math-error-m6108"></a>Erreur mathématique M6108

racine carrée

L’opérande dans une opération de racine carrée était négatif.

Le programme se termine avec le code de sortie 136.

> [!NOTE]
> La `sqrt` fonction dans la bibliothèque Runtime C et la fonction intrinsèque Fortran **sqrt** ne génèrent pas cette erreur. La `sqrt` fonction C vérifie l’argument avant d’effectuer l’opération et retourne une valeur d’erreur si l’opérande est négatif. La fonction de FORTRAN **sqrt** génère l’erreur de domaine [mathématique M6201](../../error-messages/tool-errors/math-error-m6201.md) au lieu de cette erreur.
