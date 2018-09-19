---
title: Erreur du compilateur C2818 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2818
dev_langs:
- C++
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f692f52477c988c277f60a689dac5ce83a90acb2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112042"
---
# <a name="compiler-error-c2818"></a>Erreur du compilateur C2818

application de surchargé 'operator ->' est récurrente à travers le type 'type'

Une redéfinition de l’opérateur de l’accès de membre de classe contient une récursive `return` instruction. Pour redéfinir le `->` opérateur avec la récurrence, vous devez déplacer la routine récursive à une fonction appelée à partir de l’opérateur de substituer la fonction.