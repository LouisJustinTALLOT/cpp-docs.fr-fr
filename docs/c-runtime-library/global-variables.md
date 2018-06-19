---
title: Variables globales | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.variables
dev_langs:
- C++
helpviewer_keywords:
- global variables
- variables, global
- global variables, Microsoft run-time library
ms.assetid: 01d1551c-2f0c-4f72-935c-6442caccf84f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2da3dd07c7088bee4be750b764b4a467bfebeae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392037"
---
# <a name="global-variables"></a>Variables globales
La bibliothèque Runtime C Microsoft fournit les variables ou macros globales suivantes. Plusieurs d'entre elles sont déconseillées au profit de versions fonctionnelles plus sûres, que nous vous recommandons d'utiliser à la place des variables globales.  
  
|Variable|Description|  
|--------------|-----------------|  
|[__argc, \__argv, \__wargv](../c-runtime-library/argc-argv-wargv.md)|Contient les arguments de ligne de commande.|  
|[_daylight, _dstbias, _timezone et _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)|Obsolète. Utilisez plutôt `_get_daylight`, `_get_dstbias`, `_get_timezone` et `_get_tzname`.<br /><br /> Prend en compte l'heure locale ; utilisé dans certaines fonctions de date et heure.|  
|[errno, _doserrno, _sys_errlist et _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)|Obsolète. Utilisez plutôt `_get_errno`, `_set_errno`, `_get_doserrno`, `_set_doserrno`, `perror` et `strerror`.<br /><br /> Stocke les codes d'erreur et les informations associées.|  
|[_environ, _wenviron](../c-runtime-library/environ-wenviron.md)|Obsolète. Utilisez plutôt `getenv_s`, `_wgetenv_s`, `_dupenv_s`, `_wdupenv_s`, `_putenv_s` et `_wputenv_s`.<br /><br /> Pointeurs vers des tableaux de pointeurs désignant des chaînes d'environnement de processus ; initialisés au démarrage.|  
|[_fmode](../c-runtime-library/fmode.md)|Obsolète. Utilisez plutôt `_get_fmode` ou `_set_fmode`.<br /><br /> Définit le mode de traduction de fichier par défaut.|  
|[_iob](../c-runtime-library/iob.md)|Tableau de structures de contrôle d'E/S pour la console, les fichiers et les appareils.|  
|[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)|Contient des informations utilisées par les fonctions de classification des caractères.|  
|[_pgmptr, _wpgmptr](../c-runtime-library/pgmptr-wpgmptr.md)|Obsolète. Utilisez plutôt `_get_pgmptr` ou `_get_wpgmptr`.<br /><br /> Initialisées au démarrage du programme sur le chemin d’accès complet ou relatif du programme, le nom complet du programme ou le nom du programme sans son extension de nom de fichier, selon la façon dont le programme a été appelé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence sur les bibliothèques Runtime C](../c-runtime-library/c-run-time-library-reference.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)   
 [__argc, \__argv, \__wargv](../c-runtime-library/argc-argv-wargv.md)   
 [_get_daylight](../c-runtime-library/reference/get-daylight.md)   
 [_get_dstbias](../c-runtime-library/reference/get-dstbias.md)   
 [_get_timezone](../c-runtime-library/reference/get-timezone.md)   
 [_get_tzname](../c-runtime-library/reference/get-tzname.md)   
 [perror](../c-runtime-library/reference/perror-wperror.md)   
 [strerror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)   
 [_get_doserrno](../c-runtime-library/reference/get-doserrno.md)   
 [_set_doserrno](../c-runtime-library/reference/set-doserrno.md)   
 [_get_errno](../c-runtime-library/reference/get-errno.md)   
 [_set_errno](../c-runtime-library/reference/set-errno.md)   
 [_dupenv_s, _wdupenv_s](../c-runtime-library/reference/dupenv-s-wdupenv-s.md)   
 [getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)   
 [getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)   
 [_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)   
 [_get_fmode](../c-runtime-library/reference/get-fmode.md)   
 [_set_fmode](../c-runtime-library/reference/set-fmode.md)