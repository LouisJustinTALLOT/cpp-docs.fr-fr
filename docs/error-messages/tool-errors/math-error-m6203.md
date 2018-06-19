---
title: Erreur mathématique M6203 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6203
dev_langs:
- C++
helpviewer_keywords:
- M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7660284f9e5e69b53f3289eaa1aa424944bbecb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319310"
---
# <a name="math-error-m6203"></a>Erreur mathématique M6203
'fonction' : erreur _OVERFLOW  
  
 Le résultat de la fonction donnée était trop grand pour être représentée.  
  
 Cette erreur appelle la `_matherr` fonction avec le type d’erreur, le nom de fonction et ses arguments. Vous pouvez réécrire la `_matherr` afin de personnaliser la gestion de certaines erreurs mathématiques à virgule flottante d’exécution.