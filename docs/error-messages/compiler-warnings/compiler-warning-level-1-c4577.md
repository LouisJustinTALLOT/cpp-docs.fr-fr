---
title: Avertissement du compilateur C4577
description: Description et solution de l’avertissement du compilateur C4577.
ms.date: 09/18/2019
helpviewer_keywords:
- C4577
ms.openlocfilehash: 637023f4c27f93238fbbd13b4a0e652e6cd958e0
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71241100"
---
# <a name="compiler-warning-level-1-c4577"></a>Avertissement du compilateur (niveau 1) C4577

> 'noexcept’utilisé sans le mode de gestion des exceptions spécifié ; l’arrêt en cas d’exception n’est pas garanti. Spécifier/EHsc

Le compilateur a détecté `noexcept` une spécification, mais C++ la gestion des exceptions standard n’a pas été spécifiée. Le compilateur ne prend pas entièrement en charge la gestion C++ des exceptions conformément à la norme, à moins que l’option de compilateur [/EHsc](../../build/reference/eh-exception-handling-model.md) soit spécifiée. Pour résoudre ce problème, définissez l’option de compilateur **/EHsc** .

Cet avertissement est nouveau dans Visual Studio 2015 et est désactivé par défaut. Pour plus d’informations, consultez [avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
