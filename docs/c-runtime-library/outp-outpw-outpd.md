---
title: _outp, _outpw, _outpd | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _outpd
- _outp
- _outpw
apilocation:
- msvcrt.dll
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _outpw
- _outpd
- _outp
- outpd
dev_langs:
- C++
helpviewer_keywords:
- outpw function
- words
- _outpd function
- outpd function
- outp function
- ports, writing bytes at
- bytes, writing to ports
- words, writing to ports
- double words
- double words, writing to ports
- _outpw function
- _outp function
ms.assetid: c200fe22-41f6-46fd-b0be-ebb805b35181
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 85cc0953b92df0b26583f9c9028498beb3e1271f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="outp-outpw-outpd"></a>_outp, _outpw, _outpd
Produit sur un port un octet (`_outp`), un mot (`_outpw`), ou un mot double (`_outpd`).  
  
> [!IMPORTANT]
>  Ces fonctions sont obsolètes. Depuis Visual Studio 2015, elles ne sont pas disponibles dans la bibliothèque CRT.  
  
> [!IMPORTANT]
>  Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      int _outp(  
unsigned short port,  
int databyte   
);  
unsigned short _outpw(  
unsigned short port,  
unsigned short dataword   
);  
unsigned long _outpd(  
unsigned short port,  
unsigned long dataword   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *port*  
 Numéro de port.  
  
 *databyte, dataword*  
 Valeurs de sortie.  
  
## <a name="return-value"></a>Valeur de retour  
 Les fonctions retournent la sortie des données. Aucun retour d'erreur.  
  
## <a name="remarks"></a>Notes  
 Les fonctions `_outp`, `_outpw`et `_outpd` écrivent respectivement un octet, un mot et un mot double sur le port de sortie spécifié. L’argument *port* peut être un entier non signé dans la plage 0-65 535, *databyte* peut être un entier dans la plage 0-255 et *dataword* peut être respectivement toute valeur de la plage d’un entier, un entier court non signé et un entier long non signé.  
  
 Étant donné que ces fonctions écrivent directement vers un port d’E/S, elles ne peuvent pas être utilisées dans le code utilisateur. Pour plus d’informations sur l’utilisation des ports d’E/S dans ces systèmes d’exploitation, recherchez « Communications série dans Win32 » sur MSDN.  
  
## <a name="requirements"></a>Configuration requise  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|`_outp`|\<conio.h>|  
|`_outpw`|\<conio.h>|  
|`_outpd`|\<conio.h>|  
  
 Pour plus d'informations sur la compatibilité, voir [Compatibilité](../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliothèques  
 Toutes les versions des [bibliothèques Runtime C](../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Voir aussi  
 [E/S de console et de port](../c-runtime-library/console-and-port-i-o.md)   
 [_inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)