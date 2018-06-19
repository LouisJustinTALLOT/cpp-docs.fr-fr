---
title: Avertissement du compilateur C4962 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4962
dev_langs:
- C++
helpviewer_keywords:
- C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74878342e153a78c6149ae3b177eff8c49e4a261
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272098"
---
# <a name="compiler-warning-c4962"></a>Avertissement du compilateur C4962
'fonction' : les optimisations guidées par profil sont désactivées, car elles génèrent des incohérences au niveau des données de profil  
  
 Une fonction n’a pas été compilée avec /LTCG:PGO, car les données de décompte (profil) pour la fonction n’étaient pas fiables. Réexécutez le profilage pour régénérer le fichier .pgc qui contient les données de profil non fiables pour cette fonction.  
  
 Cet avertissement est désactivé par défaut. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).