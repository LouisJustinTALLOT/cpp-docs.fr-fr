---
title: "Fonctions obsol&#232;tes | Microsoft Docs"
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
f1_keywords: 
  - "is_wctype"
  - "_loaddll"
  - "_unloaddll"
  - "_getdllprocaddr"
  - "_seterrormode"
  - "_beep"
  - "_sleep"
  - "_getsystime"
  - "corecrt_wctype/is_wctype"
  - "process/_loaddll"
  - "process/_unloaddll"
  - "process/_getdllprocaddr"
  - "stdlib/_seterrormode"
  - "stdlib/_beep"
  - "stdlib/_sleep"
  - "time/_getsystime"
  - "time/_setsystime"
dev_langs: 
  - "C"
  - "C++"
ms.assetid: 8e14c2d4-1481-4240-8586-47eb43db02b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Fonctions obsol&#232;tes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Certaines fonctions de la bibliothèque sont obsolètes et ont des équivalents plus récents. Nous vous recommandons d’utiliser les versions mises à jour. D’autres fonctions obsolètes ont été supprimées du CRT. Cette rubrique répertorie les fonctions déconseillées comme obsolètes et celles qui ont été supprimées d’une version particulière de Visual Studio.  
  
## Déconseillées comme obsolètes dans Visual Studio 2015  
  
|Fonction obsolète|Alternative|  
|-----------------------|-----------------|  
|`is_wctype`|[iswctype](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|  
|`_loaddll`|[LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187), [LoadLibraryEx](http://go.microsoft.com/fwlink/p/?LinkID=236091) ou [LoadPackagedLibrary](https://msdn.microsoft.com/library/windows/desktop/hh447159\(v=vs.85\).aspx)|  
|`_unloaddll`|[FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188)|  
|`_getdllprocaddr`|[GetProcAddress](../build/getprocaddress.md)|  
|`_seterrormode`|[SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkID=255242)|  
|`_beep`|[Beep](https://msdn.microsoft.com/library/windows/desktop/ms679277\(v=vs.85\).aspx)|  
|`_sleep`|[Sleep](https://msdn.microsoft.com/library/windows/desktop/ms686298\(v=vs.85\).aspx)|  
|`_getsystime`|[GetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724338\(v=vs.85\).aspx)|  
|`_setsystime`|[SetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724936\(v=vs.85\).aspx)|  
  
## Supprimées du CRT dans Visual Studio 2015  
  
|Fonction obsolète|Alternative|  
|-----------------------|-----------------|  
|[\_cgets, \_cgetws](../c-runtime-library/cgets-cgetws.md)|[\_cgets\_s, \_cgetws\_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|  
|[gets, \_getws](../c-runtime-library/gets-getws.md)|[gets\_s, \_getws\_s](../c-runtime-library/reference/gets-s-getws-s.md)|  
|[\_get\_output\_format](../c-runtime-library/get-output-format.md)|None|  
|[\_heapadd](../c-runtime-library/heapadd.md)|None|  
|[\_heapset](../c-runtime-library/heapset.md)|None|  
|[inp, inpw](../c-runtime-library/inp-inpw.md)|None|  
|[\_inp, \_inpw, \_inpd](../c-runtime-library/inp-inpw-inpd.md)|None|  
|[outp, outpw](../c-runtime-library/outp-outpw.md)|None|  
|[\_outp, \_outpw, \_outpd](../c-runtime-library/outp-outpw-outpd.md)|None|  
|[\_set\_output\_format](../c-runtime-library/set-output-format.md)|Aucun|  
  
## Supprimées du CRT dans les versions antérieures de Visual Studio  
 [\_lock](../c-runtime-library/lock.md)  
  
 [\_unlock](../c-runtime-library/unlock.md)