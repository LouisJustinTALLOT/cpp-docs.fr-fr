---
title: Erreur irrécupérable C1853 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1853
dev_langs:
- C++
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 016e5bbf064643ddff0f63c5e16a967ed914f3e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044949"
---
# <a name="fatal-error-c1853"></a>Erreur irrécupérable C1853

> «*filename*« fichier d’en-tête précompilé est d’une version précédente du compilateur, ou l’en-tête précompilé est en C++ et vous l’utilisez C (ou inversement)

Causes possibles :

- L’en-tête précompilé a été compilé avec une version précédente du compilateur. Essayez de recompiler l’en-tête avec le compilateur actuel.

- L’en-tête précompilé est en C++ et vous l’utilisez de réessayez C. recompiler l’en-tête pour une utilisation avec C en spécifiant un de le [TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) options du compilateur, ou en remplaçant le suffixe du fichier source par « c ». Pour plus d’informations, consultez [deux possibilités pour précompiler le Code](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code).