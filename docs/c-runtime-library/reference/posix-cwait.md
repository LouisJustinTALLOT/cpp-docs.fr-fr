---
description: 'En savoir plus sur : cwait'
title: cwait
ms.date: 12/16/2019
api_name:
- cwait
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
- cwait
helpviewer_keywords:
- cwait function
ms.assetid: 1ad1ab19-02e5-4155-94ca-f02c2d5a90a6
ms.openlocfilehash: 974a0bb474376cb54baca513d9f53a686aae5f0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304543"
---
# <a name="cwait"></a>cwait

Le nom de fonction spécifique à Microsoft `cwait` est un alias déconseillé pour la fonction [_cwait](cwait.md) . Par défaut, il génère un [Avertissement du compilateur (niveau 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Le nom est déconseillé, car il ne suit pas les règles C standard pour les noms spécifiques à l’implémentation. Toutefois, la fonction est toujours prise en charge.

Nous vous recommandons d’utiliser [_cwait](cwait.md) à la place. Vous pouvez continuer à utiliser ce nom de fonction et désactiver l’avertissement. Pour plus d’informations, consultez [Désactiver les](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) noms de [fonction](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)d’avertissement et POSIX.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).
