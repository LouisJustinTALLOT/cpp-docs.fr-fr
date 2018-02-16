---
title: fegetround, fesetround2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- fegetround
- fesetround
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fegetround
- fesetround
- fenv/fegetround
- fenv/fesetround
dev_langs:
- C++
helpviewer_keywords:
- fegetround function
- fesetround function
ms.assetid: 596af00b-be2f-4f57-b2f5-460485f9ff0b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bf50371c781a5ade76f3f35de8fc760331d72a20
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="fegetround-fesetround"></a>fegetround, fesetround
Obtient ou définit le mode d’arrondi à virgule flottante actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int fegetround(void);  
  
int fesetround(  
   int round_mode  
);   
```  
  
#### <a name="parameters"></a>Paramètres  
 `round_mode`  
 Mode d’arrondi à définir, comme l’une des macros d’arrondi à virgule flottante. Si la valeur n’est pas égale à l’une des macros d’arrondi à virgule flottante, le mode d’arrondi n’est pas modifié.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, `fegetround` retourne le mode d’arrondi comme l’une des valeurs de macros d’arrondi à virgule flottante. Une valeur négative est retournée s’il est impossible de déterminer le mode d’arrondi actuel.  
  
 En cas de réussite, `fesetround` retourne la valeur 0. Sinon, une valeur non nulle est retournée.  
  
## <a name="remarks"></a>Notes  
 Les opérations à virgule flottante peuvent utiliser l’un des différents modes d’arrondi. Ils contrôlent la direction dans laquelle les résultats des opérations à virgule flottante sont arrondis lors du stockage des résultats. Voici les noms et les comportements des macros d’arrondi à virgule flottante définies dans \<fenv.h> :  
  
|Macro|Description|  
|-----------|-----------------|  
|FE_DOWNWARD|Arrondi à l’infini négatif.|  
|FE_TONEAREST|Arrondi au plus proche.|  
|FE_TOWARDZERO|Arrondi à zéro.|  
|FE_UPWARD|Arrondi à l’infini positif.|  
  
 Le comportement par défaut de FE_TONEAREST consiste à arrondir les résultats à mi-chemin entre les valeurs représentables vers la valeur la plus proche avec un bit de poids faible pair (0).  
  
 Le mode d’arrondi actuel affecte ces opérations :  
  
-   Conversions de chaînes.  
  
-   Résultats des opérateurs arithmétiques à virgule flottante en dehors des expressions constantes.  
  
-   Fonctions d’arrondi de bibliothèque, comme `rint` et `nearbyint`.  
  
-   Valeurs de retour des fonctions mathématiques de bibliothèque standard.  
  
 Le mode d’arrondi actuel n’affecte pas ces opérations :  
  
-   Fonctions de bibliothèque `trunc`, `ceil`, `floor`et `lround` .  
  
-   Casts et conversions implicites entre des valeurs à virgule flottante et entières, toujours arrondies à zéro.  
  
-   Résultats des opérateurs arithmétiques à virgule flottante dans des expressions constantes, toujours arrondis à la valeur la plus proche.  
  
 Pour utiliser ces fonctions, vous devez désactiver les optimisations à virgule flottante qui peuvent empêcher l’accès à l’aide de la directive `#pragma fenv_access(on)` avant l’appel. Pour plus d’informations, consultez [fenv_access](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Configuration requise  
  
|Fonction|En-tête C|En-tête C++|  
|--------------|--------------|------------------|  
|`fegetround`,                `fesetround`|\<fenv.h>|\<cfenv>|  
  
 Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence alphabétique des fonctions](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [nearbyint, nearbyintf, nearbyintl](../../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)   
 [rint, rintf, rintl](../../c-runtime-library/reference/rint-rintf-rintl.md)   
 [lrint, lrintf, lrintl, llrint, llrintf, llrintl](../../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)