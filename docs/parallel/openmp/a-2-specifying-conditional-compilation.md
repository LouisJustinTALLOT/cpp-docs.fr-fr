---
title: A.2 spécifiant la Compilation conditionnelle | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d54245a2df2f38bed2674a3bb3923f8212d35459
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690593"
---
# <a name="a2---specifying-conditional-compilation"></a>A.2   Spécification de compilation conditionnelle
Les exemples suivants illustrent l’utilisation de la compilation conditionnelle à l’aide de la macro OpenMP `_OPENMP` ([Section 2.2](../../parallel/openmp/2-2-conditional-compilation.md) page 8). Avec la compilation de OpenMP, le `_OPENMP` macro est définie.  
  
```  
# ifdef _OPENMP   
    printf_s("Compiled by an OpenMP-compliant implementation.\n");  
# endif  
```  
  
 L’opérateur de préprocesseur défini permet plusieurs macros à tester dans une seule directive.  
  
```  
# if defined(_OPENMP) && defined(VERBOSE)  
    printf_s("Compiled by an OpenMP-compliant implementation.\n");  
# endif  
```