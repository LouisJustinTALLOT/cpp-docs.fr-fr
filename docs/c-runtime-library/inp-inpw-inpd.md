---
title: _inp, _inpw, _inpd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _inp
- _inpw
- _inpd
apilocation:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- inpd
- _inp
- _inpw
- _inpd
dev_langs:
- C++
helpviewer_keywords:
- inp function
- inpw function
- ports, I/O routines
- inpd function
- _inp function
- _inpd function
- I/O [CRT], port
- _inpw function
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a24996fbf2aea97581038bed28297416541ce9da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389847"
---
# <a name="inp-inpw-inpd"></a>_inp, _inpw, _inpd
Prend en entrée sur un port un octet (`_inp`), un mot (`_inpw`), ou un mot double (`_inpd`).  
  
> [!IMPORTANT]
>  Ces fonctions sont obsolètes. Depuis Visual Studio 2015, elles ne sont pas disponibles dans la bibliothèque CRT.  
  
> [!IMPORTANT]
>  Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _inp(   
   unsigned short port   
);  
unsigned short _inpw(   
   unsigned short port   
);  
unsigned long _inpd(   
   unsigned short port   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `port`  
 Numéro du port d’E/S.  
  
## <a name="return-value"></a>Valeur de retour  
 Les fonctions retournent l’octet, le mot ou le mot double lu à partir du `port`. Aucun retour d'erreur.  
  
## <a name="remarks"></a>Notes  
 Les fonctions `_inp`, `_inpw`et `_inpd` lisent respectivement un octet, un mot et un mot double sur le port d’entrée spécifié. La valeur d’entrée peut être tout entier court non signé dans la plage 0 - 65 535.  
  
 Étant donné que ces fonctions lisent directement à partir d’un port d’E/S, elles ne peuvent pas être utilisées dans le code utilisateur.  
  
## <a name="requirements"></a>Configuration requise  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|`_inp`|\<conio.h>|  
|`_inpw`|\<conio.h>|  
|`_inpd`|\<conio.h>|  
  
 Pour plus d'informations sur la compatibilité, voir [Compatibilité](../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliothèques  
 Toutes les versions des [bibliothèques Runtime C](../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Voir aussi  
 [E/S de console et de port](../c-runtime-library/console-and-port-i-o.md)   
 [_outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)