---
description: 'En savoir plus sur : J0, J1, Jn'
title: j0, j1, jn
ms.date: 12/16/2019
api_name:
- jn
- j0
- j1
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- jn
- j1
- j0
helpviewer_keywords:
- jn function
- j1 function
- j0 function
ms.assetid: ec8a9512-aacb-423c-a845-fc8927e6e21d
ms.openlocfilehash: 3faff60b89448f296db9a5c64c716e68a5b442a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326974"
---
# <a name="j0-j1-jn"></a>j0, j1, jn

Les noms des fonctions POSIX implémentées `j0` par Microsoft, `j1` et `jn` sont des alias déconseillés pour les fonctions [_j0, _j1 et _jn](bessel-functions-j0-j1-jn-y0-y1-yn.md) . Par défaut, ils génèrent un [Avertissement du compilateur (niveau 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Les noms sont déconseillés, car ils ne suivent pas les règles C standard pour les noms spécifiques à l’implémentation. Toutefois, les fonctions sont toujours prises en charge.

Nous vous recommandons d’utiliser à la place [_j0, _j1 et _jn](bessel-functions-j0-j1-jn-y0-y1-yn.md) . Ou encore, vous pouvez continuer à utiliser ces noms de fonctions et désactiver l’avertissement. Pour plus d’informations, consultez [Désactiver les](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) noms de [fonction](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)d’avertissement et POSIX.
