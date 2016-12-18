---
title: "acos, acosf, acosl | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "acosf"
  - "acos"
  - "acosl"
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
  - "acos"
  - "acosl"
  - "acosf"
  - "math/acosf"
  - "math/acosl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "acos (fonction)"
  - "acosf (fonction)"
  - "acosl (fonction)"
  - "arccosine (fonction)"
  - "fonctions trigonométriques"
ms.assetid: 00b89c48-8faf-4824-aa95-fa4349a4975d
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# acos, acosf, acosl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcule le arccosinus.  
  
## Syntaxe  
  
```  
double acos(   
   double x   
);  
float acos(  
   float x   
);   // C++ only  
long double acos(  
   long double x  
);   // C++ only  
float acosf(  
   float x   
);  
long double acosl(  
   long double x  
);  
```  
  
#### Paramètres  
 `x`  
 Valeur entre – 1 et 1, pour laquelle le arccosinus doit être calculé \(le cosinus inverse\).  
  
## Valeur de retour  
 La fonction `acos` retourne l'arccosinus de `x` dans la plage 0 à π radians.  
  
 Par défaut, si `x` est inférieur à 1 ou supérieur à 1, `acos` retourne un indéfini.  
  
|Entrée|Exception SEH|Exception Matherr|  
|------------|-------------------|-----------------------|  
|± ∞|`INVALID`|`_DOMAIN`|  
|± QNAN,IND|aucun|`_DOMAIN`|  
|&#124;x&#124;\>1|`INVALID`|`_DOMAIN`|  
  
## Notes  
 Comme C\+\+ permet la surcharge, vous pouvez appeler les surcharges de `acos` qui acceptent et retournent des valeurs de type `float` et `long double`.  Dans un programme C, `acos` prend et retourne toujours `double`.  
  
## Configuration requise  
  
|Routine|En\-tête requis|En\-têtes facultatifs|  
|-------------|---------------------|---------------------------|  
|`acos`, `acosf`, `acosl`|\<math.h\>|\<errno.h\>|  
  
## Exemple  
 Ce programme invite l'utilisateur à entrer une valeur dans la plage \-1 à 1.  Valeurs d'entrée en dehors de cette plage produisent des messages d'erreur `_DOMAIN`.  Si une valeur valide est entrée, le programme imprime l'arc sinus et le cosinus de cette valeur.  
  
```  
// crt_asincos.c  
// arguments: 0  
  
#include <math.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main( int ac, char* av[] )  
{  
    double  x,  
            y;  
    errno_t err;   
  
    // argument checking  
    if (ac != 2)  
    {  
        fprintf_s( stderr, "Usage: %s <number between -1 and 1>\n",  
                   av[0]);  
        return 1;  
    }  
  
    // Convert argument into a double value  
    if ((err = sscanf_s( av[1], "%lf", &x )) != 1)  
    {  
        fprintf_s( stderr, "Error converting argument into ",  
                   "double value.\n");  
        return 1;  
    }  
  
    // Arcsine of X  
    y = asin( x );  
    printf_s( "Arcsine of %f = %f\n", x, y );  
  
    // Arccosine of X  
    y = acos( x );  
    printf_s( "Arccosine of %f = %f\n", x, y );  
}  
```  
  
  **Arcsinus de 0,000000 \= 0,000000**  
**Cosinus de 0,000000 \= 1,570796**   
## Équivalent .NET Framework  
 [System::Math::Acos](https://msdn.microsoft.com/en-us/library/system.math.acos.aspx)  
  
## Voir aussi  
 [Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)   
 [asin, asinf, asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan, atanf, atanl, atan2, atan2f, atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos, cosf, cosl, cosh, coshf, coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [\_matherr](../../c-runtime-library/reference/matherr.md)   
 [sin, sinf, sinl, sinh, sinhf, sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)