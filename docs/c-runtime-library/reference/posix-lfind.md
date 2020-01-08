---
title: lfind
ms.date: 12/16/2019
api_name:
- lfind
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
- lfind
helpviewer_keywords:
- lfind function
ms.assetid: 2528e787-94b6-4740-8a8d-6efc276d1f42
ms.openlocfilehash: 7a1ac69bbebfea45345c7dae17b18f02b84228cd
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300909"
---
# <a name="lfind"></a>lfind

Le nom de fonction POSIX implémenté par Microsoft `lfind` est un alias déconseillé pour la fonction [_lfind](lfind.md) . Par défaut, il génère un [Avertissement du compilateur (niveau 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Le nom est déconseillé, car il ne suit pas les règles C standard pour les noms spécifiques à l’implémentation. Toutefois, la fonction est toujours prise en charge.

Nous vous recommandons d’utiliser à la place [_lfind](lfind.md) ou la fonction [_lfind_s](lfind-s.md) à la sécurité améliorée. Vous pouvez continuer à utiliser ce nom de fonction et désactiver l’avertissement. Pour plus d’informations, consultez [Désactiver les](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) noms de [fonction](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)d’avertissement et POSIX.
