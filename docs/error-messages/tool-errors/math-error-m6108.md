---
title: Erreur mathématique M6108 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6108
dev_langs:
- C++
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4dfeca48aa04ebfbc097649e5c25253166c50dad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325849"
---
# <a name="math-error-m6108"></a>Erreur mathématique M6108
racine carrée  
  
 L’opérande d’une opération de la racine carrée est négative.  
  
 Programme se termine par le code de sortie 136.  
  
> [!NOTE]
>  Le `sqrt` fonction dans la bibliothèque Runtime C et la fonction intrinsèque FORTRAN **SQRT** ne génèrent pas cette erreur. C `sqrt` fonction vérifie l’argument avant d’effectuer l’opération et retourne une valeur d’erreur si l’opérande est négatif. Le FORTRAN **SQRT** fonction génère l’erreur de domaine [M6201](../../error-messages/tool-errors/math-error-m6201.md) au lieu de cette erreur.