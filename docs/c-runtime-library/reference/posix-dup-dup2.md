---
title: dup, dup2
ms.date: 12/16/2019
api_name:
- dup2
- dup
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
- dup
- dup2
helpviewer_keywords:
- dup function
- dup2 function
ms.assetid: c7572170-47ff-4e0d-b9c3-10f0ab0ba40a
ms.openlocfilehash: ea6fe475b4a5e3cce5e9d05d89bd351361c2a4de
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301208"
---
# <a name="dup-dup2"></a>dup, dup2

Les noms des fonctions POSIX implémentées par Microsoft `dup` et `dup2` sont des alias déconseillés pour les fonctions [_dup](dup-dup2.md) et [_dup2](dup-dup2.md) . Par défaut, ils génèrent un [Avertissement du compilateur (niveau 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Les noms sont déconseillés, car ils ne suivent pas les règles C standard pour les noms spécifiques à l’implémentation. Toutefois, les fonctions sont toujours prises en charge.

Nous vous recommandons d’utiliser à la place [_dup](dup-dup2.md) et [_dup2](dup-dup2.md) . Ou encore, vous pouvez continuer à utiliser ces noms de fonctions et désactiver l’avertissement. Pour plus d’informations, consultez [Désactiver les](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) noms de [fonction](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)d’avertissement et POSIX.
