---
title: "cpow, cpowf, cpowl | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "cpow"
  - "cpowf"
  - "cpowl"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-math-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "cpow"
  - "cpowf"
  - "cpowl"
  - "complex/cpow"
  - "complex/cpowf"
  - "complex/copwl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "cpow (fonction)"
  - "cpowf (fonction)"
  - "complexe/cpowl (fonction)"
ms.assetid: 83fe2187-22b7-4295-ab16-4d77abdbb80b
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# cpow, cpowf, cpowl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Récupère la valeur d’un nombre élevé à la puissance spécifiée, où la base et exposant sont des nombres complexes. Cette fonction a une branche de coupe pour l’exposant l’axe réel négatif.  
  
## Syntaxe  
  
```  
_Dcomplex cpow(   
   _Dcomplex x, _Dcomplex y   
);  
_Fcomplex cpow(   
   _Fcomplex x, _Fcomplex y   
);  // C++ only  
_Lcomplex cpow(   
   _Lcomplex x, _Lcomplex y   
);  // C++ only  
_Fcomplex cpowf(   
   _Fcomplex x, _Fcomplex y   
);  
_Lcomplex cpowl(   
   _Lcomplex x, _Lcomplex y   
);  
```  
  
#### Paramètres  
 `x`  
 La base.  
  
 `y`  
 L’exposant.  
  
## Valeur de retour  
 La valeur de `x` à la puissance de `y` avec une branche de coupe pour `x` l’axe réel négatif.  
  
## Notes  
 C\+\+ autorisant la surcharge, vous pouvez appeler des surcharges de `cpow` qui acceptent et retournent des valeurs `_Fcomplex` et `_Lcomplex`. Dans un programme C, `cpow` accepte et retourne toujours un `_Dcomplex` valeur.  
  
## Configuration requise  
  
|Routine|En\-tête C|En\-tête C\+\+|  
|-------------|----------------|--------------------|  
|`cpow`, `cpowf`, `cpowl`|\<complex.h\>|\< ccomplex \>|  
  
 Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md) dans l'introduction.  
  
## Voir aussi  
 [Référence alphabétique des fonctions](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cexp, cexpf, cexpl](../../c-runtime-library/reference/cexp-cexpf-cexpl.md)   
 [clog10, clog10f, clog10l](../../c-runtime-library/reference/clog10-clog10f-clog10l.md)   
 [CLOG, clogf, clogl](../../c-runtime-library/reference/clog-clogf-clogl.md)