---
title: Erreur irrécupérable C1211 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1211
dev_langs:
- C++
helpviewer_keywords:
- C1211
ms.assetid: df0ca70d-ec6e-4400-926a-b877e2599978
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 444d2bc25c2eddd5ea9a0170272bd3e71b61f94f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018523"
---
# <a name="fatal-error-c1211"></a>Erreur irrécupérable C1211

L'attribut personnalisé TypeForwardedTo n'est pas pris en charge par la version installée du runtime

L’erreur C1211 se produit quand vous avez un compilateur pour la version actuelle, mais un Common Language Runtime d’une version précédente.

Certaines fonctionnalités du compilateur risquent de ne pas fonctionner sur une version précédente du runtime.

Pour résoudre l’erreur C1211, installez le common language runtime fourni avec le compilateur que vous utilisez.

Pour plus d’informations, consultez [transfert de Type (C++ / c++ / CLI)](../../windows/type-forwarding-cpp-cli.md).