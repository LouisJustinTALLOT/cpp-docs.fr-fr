---
title: spawnlpe
ms.date: 12/16/2019
api_name:
- spawnlpe
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
- spawnlpe
helpviewer_keywords:
- spawnlpe function
ms.assetid: 379143a7-f3d0-41de-83cc-2b4321146390
ms.openlocfilehash: e0dd321c26e02989898016c1ea707f6b6de886ff
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300727"
---
# <a name="spawnlpe"></a>spawnlpe

Le nom de fonction spécifique à Microsoft `spawnlpe` est un alias déconseillé pour la fonction [_spawnlpe](spawnlpe-wspawnlpe.md) . Par défaut, il génère un [Avertissement du compilateur (niveau 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Le nom est déconseillé, car il ne suit pas les règles C standard pour les noms spécifiques à l’implémentation. Toutefois, la fonction est toujours prise en charge.

Nous vous recommandons d’utiliser [_spawnlpe](spawnlpe-wspawnlpe.md) à la place. Vous pouvez continuer à utiliser ce nom de fonction et désactiver l’avertissement. Pour plus d’informations, consultez [Désactiver les](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) noms de [fonction](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)d’avertissement et POSIX.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).
