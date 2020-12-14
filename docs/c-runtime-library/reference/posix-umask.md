---
description: 'En savoir plus sur : umask'
title: umask
ms.date: 12/16/2019
api_name:
- umask
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
- umask
helpviewer_keywords:
- umask function
ms.assetid: d2f697fc-08d5-4b70-9dd5-df3f5bb8b754
ms.openlocfilehash: 619152cd6d07d5bda5bcaf3fa353289fbd04cfc8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97252855"
---
# <a name="umask"></a>umask

Le nom de fonction POSIX implémenté `umask` par Microsoft est un alias déconseillé pour la fonction [_umask](umask.md) . Par défaut, il génère un [Avertissement du compilateur (niveau 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Le nom est déconseillé, car il ne suit pas les règles C standard pour les noms spécifiques à l’implémentation. Toutefois, la fonction est toujours prise en charge.

Nous vous recommandons d’utiliser à la place [_umask](umask.md) ou la fonction [_umask_s](umask-s.md) à la sécurité améliorée. Vous pouvez continuer à utiliser ce nom de fonction et désactiver l’avertissement. Pour plus d’informations, consultez [Désactiver les](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) noms de [fonction](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)d’avertissement et POSIX.
