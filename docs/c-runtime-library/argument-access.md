---
title: "Accès aux arguments | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.arguments
dev_langs:
- C++
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 66f9ff6dff86bbdff2ec86970a4176f3581316fa
ms.contentlocale: fr-fr
ms.lasthandoff: 03/29/2017

---
# <a name="argument-access"></a>Accès aux arguments
Les macros `va_arg`, `va_end` et `va_start` fournissent l’accès aux arguments de fonction quand le nombre d’arguments est variable. Ces macros sont définies dans STDARG. H pour la compatibilité ANSI C et dans VARARGS. H pour la compatibilité avec UNIX System V.  
  
### <a name="argument-access-macros"></a>Macros d’accès à un argument  
  
|Macro|Utilisation|  
|-----------|-------------------------------|  
|[va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Récupérer un argument dans la liste|  
|[va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Réinitialiser le pointeur|  
|[va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Définir le pointeur au début de la liste d’arguments|  
  
## <a name="see-also"></a>Voir aussi  
 [Routines runtime par catégorie](../c-runtime-library/run-time-routines-by-category.md)
