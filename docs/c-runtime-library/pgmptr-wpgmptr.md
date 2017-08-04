---
title: _pgmptr, _wpgmptr | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- pgmptr
- _pgmptr
- wpgmptr
- _wpgmptr
dev_langs:
- C++
helpviewer_keywords:
- wpgmptr function
- _wpgmptr function
- _pgmptr function
- pgmptr function
ms.assetid: 4d44b515-0eff-4136-8bc4-684195f218f5
caps.latest.revision: 14
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
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 221d1bd8259d8922695e9060eb8f2ada63d63631
ms.contentlocale: fr-fr
ms.lasthandoff: 05/18/2017

---
# <a name="pgmptr-wpgmptr"></a>_pgmptr, _wpgmptr
Chemin du fichier exécutable. Déconseillé, utilisez [_get_pgmptr](../c-runtime-library/reference/get-pgmptr.md) et [_get_wpgmptr](../c-runtime-library/reference/get-wpgmptr.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
extern char *_pgmptr;  
extern wchar_t *_wpgmptr;  
```  
  
## <a name="remarks"></a>Remarques  
 Lorsqu’un programme est exécuté à partir de l’interpréteur de commandes (Cmd.exe), `_pgmptr` est initialisé automatiquement sur le chemin d’accès complet du fichier exécutable. Par exemple, si Hello.exe figure dans C:\BIN et que C:\BIN est dans le chemin d’accès, `_pgmptr` a la valeur C:\BIN\Hello.exe lorsque vous exécutez :  
  
```  
C> hello   
```  
  
 Lorsqu’un programme n’est pas exécuté à partir de la ligne de commande, `_pgmptr` peut être initialisé au nom du programme (le nom du fichier de base sans l’extension de nom de fichier) ou à un nom de fichier, un chemin d’accès relatif ou un chemin d’accès complet.  
  
 `_wpgmptr` est l’équivalent de caractères larges de `_pgmptr` pour une utilisation avec les programmes qui utilisent `wmain`.  
  
### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique  
  
|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|  
  
## <a name="requirements"></a>Spécifications  
  
|Variable|En-tête requis|  
|--------------|---------------------|  
|`_pgmptr`, `_wpgmptr`|\<stdlib.h>|  
  
## <a name="example"></a>Exemple  
 Le programme suivant montre l'utilisation de `_pgmptr`.  
  
```  
// crt_pgmptr.c  
// compile with: /W3  
// The following program demonstrates the use of _pgmptr.  
//  
#include <stdio.h>  
#include <stdlib.h>  
int main( void )  
{  
   printf("The full path of the executing program is : %Fs\n",   
     _pgmptr); // C4996  
   // Note: _pgmptr is deprecated; use _get_pgmptr instead  
}  
```  
  
 Vous pouvez utiliser `_wpgmptr` en modifiant `%Fs` sur `%S` et `main` sur `wmain`.  
  
## <a name="see-also"></a>Voir aussi  
 [Variables globales](../c-runtime-library/global-variables.md)
