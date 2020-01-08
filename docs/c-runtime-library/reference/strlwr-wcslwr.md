---
title: strlwr, wcslwr
ms.date: 12/16/2019
api_name:
- strlwr
- wcslwr
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
- wcslwr
- strlwr
helpviewer_keywords:
- strlwr function
- wcslwr function
ms.assetid: b9274824-4365-4674-b656-823c89653656
ms.openlocfilehash: ff730d6bea6619c50fefb407a7a69c50e1a06af0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301078"
---
# <a name="strlwr-wcslwr"></a>strlwr, wcslwr

Les noms de fonctions spécifiques à Microsoft `strlwr` et `wcslwr` sont des alias déconseillés pour les fonctions [_strlwr et _wcslwr](strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md) . Par défaut, ils génèrent un [Avertissement du compilateur (niveau 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Les noms sont déconseillés, car ils ne suivent pas les règles C standard pour les noms spécifiques à l’implémentation. Toutefois, les fonctions sont toujours prises en charge.

Nous vous recommandons d’utiliser à la place [_strlwr ou _wcslwr](strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md) ou les fonctions [_strlwr_s et _wcslwr_s](strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md) sécurisées. Ou encore, vous pouvez continuer à utiliser ces noms de fonctions et désactiver l’avertissement. Pour plus d’informations, consultez [Désactiver les](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) noms de [fonction](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)d’avertissement et POSIX.
