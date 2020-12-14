---
description: 'En savoir plus sur : variables globales'
title: Variables globales
ms.date: 11/04/2016
f1_keywords:
- c.variables
helpviewer_keywords:
- global variables
- variables, global
- global variables, Microsoft run-time library
ms.assetid: 01d1551c-2f0c-4f72-935c-6442caccf84f
ms.openlocfilehash: 8029f058b39cb2e069c83279b361b79f3c8f5515
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229884"
---
# <a name="global-variables"></a>Variables globales

La bibliothèque Runtime C Microsoft fournit les variables ou macros globales suivantes. Plusieurs d'entre elles sont déconseillées au profit de versions fonctionnelles plus sûres, que nous vous recommandons d'utiliser à la place des variables globales.

|Variable|Description|
|--------------|-----------------|
|[__argc, \_ _argv \_ _wargv](../c-runtime-library/argc-argv-wargv.md)|Contient les arguments de ligne de commande.|
|[_daylight, _dstbias, _timezone, et _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)|Action déconseillée. Utilisez plutôt `_get_daylight`, `_get_dstbias`, `_get_timezone` et `_get_tzname`.<br /><br /> Prend en compte l'heure locale ; utilisé dans certaines fonctions de date et heure.|
|[errno, _doserrno, _sys_errlist et _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)|Action déconseillée. Utilisez plutôt `_get_errno`, `_set_errno`, `_get_doserrno`, `_set_doserrno`, `perror` et `strerror`.<br /><br /> Stocke les codes d'erreur et les informations associées.|
|[_environ, _wenviron](../c-runtime-library/environ-wenviron.md)|Action déconseillée. Utilisez plutôt `getenv_s`, `_wgetenv_s`, `_dupenv_s`, `_wdupenv_s`, `_putenv_s` et `_wputenv_s`.<br /><br /> Pointeurs vers des tableaux de pointeurs désignant des chaînes d'environnement de processus ; initialisés au démarrage.|
|[_fmode](../c-runtime-library/fmode.md)|Action déconseillée. Utilisez plutôt `_get_fmode` ou `_set_fmode`.<br /><br /> Définit le mode de traduction de fichier par défaut.|
|[_iob](../c-runtime-library/iob.md)|Tableau de structures de contrôle d'E/S pour la console, les fichiers et les appareils.|
|[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)|Contient des informations utilisées par les fonctions de classification des caractères.|
|[_pgmptr, _wpgmptr](../c-runtime-library/pgmptr-wpgmptr.md)|Action déconseillée. Utilisez plutôt `_get_pgmptr` ou `_get_wpgmptr`.<br /><br /> Initialisées au démarrage du programme sur le chemin d’accès complet ou relatif du programme, le nom complet du programme ou le nom du programme sans son extension de nom de fichier, selon la façon dont le programme a été appelé.|

## <a name="see-also"></a>Voir aussi

[Référence de la bibliothèque de Run-Time C](../c-runtime-library/c-run-time-library-reference.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)<br/>
[__argc, \_ _argv \_ _wargv](../c-runtime-library/argc-argv-wargv.md)<br/>
[_get_daylight](../c-runtime-library/reference/get-daylight.md)<br/>
[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)<br/>
[_get_timezone](../c-runtime-library/reference/get-timezone.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)<br/>
[perror](../c-runtime-library/reference/perror-wperror.md)<br/>
[strerror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)<br/>
[_get_doserrno](../c-runtime-library/reference/get-doserrno.md)<br/>
[_set_doserrno](../c-runtime-library/reference/set-doserrno.md)<br/>
[_get_errno](../c-runtime-library/reference/get-errno.md)<br/>
[_set_errno](../c-runtime-library/reference/set-errno.md)<br/>
[_dupenv_s, _wdupenv_s](../c-runtime-library/reference/dupenv-s-wdupenv-s.md)<br/>
[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)<br/>
[getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)<br/>
[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)<br/>
[_get_fmode](../c-runtime-library/reference/get-fmode.md)<br/>
[_set_fmode](../c-runtime-library/reference/set-fmode.md)
