---
title: strupr, wcsupr
ms.date: 12/16/2019
api_name:
- strupr
- wcsupr
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
- strupr
- wcsupr
helpviewer_keywords:
- strupr function
- wcsupr function
ms.assetid: 17dfe1cd-3b09-4702-9f89-2207f44953e6
ms.openlocfilehash: ce51eb4f7eeb80766e19cfdb4a39a3a7dd50d85a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300454"
---
# <a name="strupr-wcsupr"></a>strupr, wcsupr

Les noms de fonctions spécifiques à Microsoft `strupr` et `wcsupr` sont des alias déconseillés pour les fonctions [_strupr et _wcsupr](strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md) . Par défaut, ils génèrent un [Avertissement du compilateur (niveau 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Les noms sont déconseillés, car ils ne suivent pas les règles C standard pour les noms spécifiques à l’implémentation. Toutefois, les fonctions sont toujours prises en charge.

Nous vous recommandons d’utiliser à la place [_strupr et _wcsupr](strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md) ou les fonctions [_strupr_s et _wcsupr_s](strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md) à la sécurité améliorées. Ou encore, vous pouvez continuer à utiliser ces noms de fonctions et désactiver l’avertissement. Pour plus d’informations, consultez [Désactiver les](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) noms de [fonction](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)d’avertissement et POSIX.
