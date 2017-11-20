---
title: __crtLCMapStringW | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __crtLCMapStringW
apilocation:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords: __crtLCMapStringW
dev_langs: C++
helpviewer_keywords: __crtLCMapStringW
ms.assetid: 45b4ac0e-438c-4fa3-b4d1-34195f4467d9
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 88af917cb86826cc4615948f7a5d2e53e888bad5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="crtlcmapstringw"></a>__crtLCMapStringW
Mappe une chaîne de caractères à une autre en effectuant une transformation dépendante des paramètres régionaux spécifiés. Cette fonction peut aussi être utilisée pour générer une clé de tri pour la chaîne d’entrée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
int __crtLCMapStringW(  
   LCID    Locale,  
   DWORD   dwMapFlags,  
   LPCWSTR lpSrcStr,  
   int     cchSrc,  
   LPWSTR  lpDestStr,  
   int     cchDest)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Locale`  
 Identificateur de paramètres régionaux. Les paramètres régionaux fournissent un contexte pour le mappage de chaînes ou la génération de clés de tri. Une application peut utiliser la macro `MAKELCID` pour créer un identificateur de paramètres régionaux.  
  
 `dwMapFlags`  
 Type de transformation à utiliser pendant le mappage de chaînes ou la génération de clés de tri.  
  
 `lpSrcStr`  
 Pointeur vers une chaîne source que la fonction mappe ou utilise pour la génération de clés de tri. Ce paramètre est censé être une chaîne de type Unicode.  
  
 `cchSrc`  
 Taille en caractères de la chaîne pointée par le paramètre `lpSrcStr` . Ce nombre peut ou non inclure le terminateur NULL.  
  
 La valeur -1 de `cchSrc` indique que la chaîne pointée par `lpSrcStr` se termine par un caractère Null. Si c’est le cas et si cette fonction est utilisée dans son mode mappage de chaîne, la fonction calcule la longueur proprement dite de la chaîne et termine la chaîne mappée stockée dans `*lpDestStr`par un caractère null.  
  
 `lpDestStr`  
 Pointeur long désignant une mémoire tampon dans laquelle la fonction stocke la chaîne mappée ou la clé de tri.  
  
 `cchDest`  
 Taille en caractères de la mémoire tampon pointée par `lpDestStr`.  
  
## <a name="return-value"></a>Valeur de retour  
 Si la valeur de `cchDest` est différente de zéro, le nombre de caractères (ou d’octets si `LCMAP_SORTKEY` est spécifié) écrits dans la mémoire tampon indique que l’opération a réussi. Ce nombre inclut l’espace destiné à accueillir un terminateur NULL.  
  
 Si la valeur de `cchDest` est égale à zéro, la taille de la mémoire tampon en caractères (ou en octets si `LCMAP_SORTKEY` est spécifié) nécessaire pour recevoir la chaîne traduite ou la clé de tri indique que l’opération a réussi. Cette taille inclut de l’espace destiné à accueillir un terminateur NULL.  
  
 La valeur zéro indique l’échec de l’opération. Pour obtenir des informations plus complètes sur les erreurs, appelez la fonction `GetLastError` .  
  
## <a name="remarks"></a>Remarques  
 Si `cchSrc` est supérieure à zéro et que `lpSrcStr` est une chaîne qui se termine par un caractère null, `__crtLCMapStringW` affecte à `cchSrc` la longueur de la chaîne. `__crtLCMapStringW` appelle ensuite la version de chaîne étendue (Unicode) de la fonction `LCMapString` avec les paramètres spécifiés. Pour plus d’informations sur les paramètres et la valeur de retour de cette fonction, consultez la fonction `LCMapString` dans [MSDN Library](http://go.microsoft.com/fwlink/?linkID=150542).  
  
## <a name="requirements"></a>Spécifications  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|__crtLCMapStringW|awint.h|