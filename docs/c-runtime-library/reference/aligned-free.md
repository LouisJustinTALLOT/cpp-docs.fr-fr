---
title: _aligned_free | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _aligned_free
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- aligned_free
- _aligned_free
dev_langs:
- C++
helpviewer_keywords:
- _aligned_free function
- aligned_free function
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 30b37b6424b02ffb4eab6f1d90d03d7b2a3154b2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="alignedfree"></a>_aligned_free
Libère un bloc de mémoire qui a été alloué avec [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) ou [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _aligned_free (  
   void *memblock  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `memblock`  
 Pointeur vers le bloc de mémoire qui a été retourné à la fonction `_aligned_malloc` ou `_aligned_offset_malloc`.  
  
## <a name="remarks"></a>Notes  
 `_aligned_free` est marqué `__declspec(noalias)`, ce qui signifie que la fonction ne peut pas modifier les variables globales. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md).  
  
 Cette fonction ne valide pas son paramètre, contrairement à d’autres fonctions CRT _aligned. Si `memblock` est un pointeur `NULL`, cette fonction n’effectue aucune action. Elle ne modifie pas `errno` et elle n’appelle pas le gestionnaire de paramètres non valides. Si une erreur se produit dans la fonction en raison de la non-utilisation de fonctions _aligned au préalable pour allouer le bloc de mémoire ou qu’une erreur d’alignement de mémoire se produit en raison d’un désastre imprévu, la fonction génère un rapport de débogage à partir des [macros _RPT, _RPTF, _RPTW, _RPTFW](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md).  
  
## <a name="requirements"></a>Configuration requise  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|`_aligned_free`|\<malloc.h>|  
  
## <a name="example"></a>Exemple  
 Pour plus d’informations, consultez [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Alignement des données](../../c-runtime-library/data-alignment.md)