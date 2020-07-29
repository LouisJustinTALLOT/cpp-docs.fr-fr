---
title: Avertissement du compilateur C4577
description: Description et solution de l’avertissement du compilateur C4577.
ms.date: 09/18/2019
f1_keywords:
- C4577
helpviewer_keywords:
- C4577
ms.openlocfilehash: fb9d412196e7764326a397a4bf6e76c8723ac2ae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87196251"
---
# <a name="compiler-warning-level-1-c4577"></a>Avertissement du compilateur (niveau 1) C4577

> 'noexcept’utilisé sans le mode de gestion des exceptions spécifié ; l’arrêt en cas d’exception n’est pas garanti. Spécifier/EHsc

Le compilateur a détecté une **`noexcept`** spécification, mais la gestion des exceptions C++ standard n’a pas été spécifiée. Le compilateur ne prend pas entièrement en charge la gestion des exceptions conformément à la norme C++, sauf si l’option de compilateur [/EHsc](../../build/reference/eh-exception-handling-model.md) est spécifiée. Pour résoudre ce problème, définissez l’option de compilateur **/EHsc** .

Cet avertissement est nouveau dans Visual Studio 2015 et est désactivé par défaut. Pour plus d’informations, consultez [avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
