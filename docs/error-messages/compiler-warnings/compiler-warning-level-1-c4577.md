---
title: Avertissement du compilateur C4577
description: Description et solution de l’avertissement du compilateur C4577.
ms.date: 09/18/2019
f1_keywords:
- C4577
helpviewer_keywords:
- C4577
ms.openlocfilehash: e29e47b2a268d86f7f6a280b79a1604fe6eff8a4
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810558"
---
# <a name="compiler-warning-level-1-c4577"></a>Avertissement du compilateur (niveau 1) C4577

> 'noexcept’utilisé sans le mode de gestion des exceptions spécifié ; l’arrêt en cas d’exception n’est pas garanti. Spécifier/EHsc

Le compilateur a détecté une spécification `noexcept`, mais C++ la gestion des exceptions standard n’a pas été spécifiée. Le compilateur ne prend pas entièrement en charge la gestion C++ des exceptions conformément à la norme, à moins que l’option de compilateur [/EHsc](../../build/reference/eh-exception-handling-model.md) soit spécifiée. Pour résoudre ce problème, définissez l’option de compilateur **/EHsc** .

Cet avertissement est nouveau dans Visual Studio 2015 et est désactivé par défaut. Pour plus d’informations, consultez [avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
