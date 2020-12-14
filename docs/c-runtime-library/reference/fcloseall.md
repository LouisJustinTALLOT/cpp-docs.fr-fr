---
description: 'En savoir plus sur : fcloseall'
title: fcloseall
ms.date: 12/16/2019
api_name:
- fcloseall
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
- fcloseall
helpviewer_keywords:
- fcloseall function
ms.assetid: 4f14acde-5bc5-43da-a709-7a3c559df3cf
ms.openlocfilehash: b54bf604adf4bd4d9c30a9c4d3a4c4e37ecbc99f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235864"
---
# <a name="fcloseall"></a>fcloseall

Le nom de fonction spécifique à Microsoft `fcloseall` est un alias déconseillé pour la fonction [_fcloseall](fclose-fcloseall.md) . Par défaut, il génère un [Avertissement du compilateur (niveau 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Le nom est déconseillé, car il ne suit pas les règles C standard pour les noms spécifiques à l’implémentation. Toutefois, la fonction est toujours prise en charge.

Nous vous recommandons d’utiliser [_fcloseall](fclose-fcloseall.md) à la place. Vous pouvez continuer à utiliser ce nom de fonction et désactiver l’avertissement. Pour plus d’informations, consultez [Désactiver les](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) noms de [fonction](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)d’avertissement et POSIX.
