---
title: Erreur irrécupérable RC1102 du compilateur de ressources | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1102
dev_langs:
- C++
helpviewer_keywords:
- RC1102
ms.assetid: bd2091f8-ef5e-4151-a8d6-98043e9422b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2be0a62b08b361f1cfa423fa3999a440e2fe4709
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073180"
---
# <a name="resource-compiler-fatal-error-rc1102"></a>Erreur irrécupérable RC1102 du compilateur de ressources 

Erreur interne : trop d’arguments pour RCPP

Trop d’arguments passés au préprocesseur du compilateur de ressources. Réduire le nombre de symboles définis avec les symboles définissent (/ d) option en les définissant dans votre source. Cette erreur peut également être provoquée par spécification de trop nombreuses incluent des chemins de recherche de fichier à l’aide de l’option de chemin de recherche Include (/ i).