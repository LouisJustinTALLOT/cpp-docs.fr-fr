---
title: errno, _doserrno, _sys_errlist, and _sys_nerr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _errno
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _sys_errlist
- errno
- _sys_nerr
- _doserrno
dev_langs:
- C++
helpviewer_keywords:
- error codes, printing
- sys_errlist global variable
- doserrno global variable
- errno global variable
- _doserrno global variable
- _sys_errlist global variable
- _sys_nerr global variable
- sys_nerr global variable
ms.assetid: adbec641-6d91-4e19-8398-9a34046bd369
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b17abb975ea9f3212d4bd6171bcd2bffb78e483c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392417"
---
# <a name="errno-doserrno-syserrlist-and-sysnerr"></a>errno, _doserrno, _sys_errlist et _sys_nerr
Macros globales qui contiennent des codes d'erreur définis pendant l'exécution du programme et équivalents chaîne des codes d'erreur pour l'affichage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#define errno   (*_errno())  
#define _doserrno   (*__doserrno())  
#define _sys_errlist (__sys_errlist())  
#define _sys_nerr (*__sys_nerr())  
```  
  
## <a name="remarks"></a>Notes  
 Les éléments `errno` et `_doserrno` sont définis à 0 par l'exécution lors du démarrage du programme. L'élément `errno` est déclenché en cas d'erreur lors d'un appel au niveau système. Comme `errno` contient la valeur du dernier appel qui le définit, cette valeur peut être modifiée par les appels suivants. Les appels de la bibliothèque Runtime qui déclenchent `errno` en cas d'erreur ne suppriment pas `errno` en cas de réussite. Supprimez toujours `errno` en appelant `_set_errno(0)` juste avant un appel qui peut le déclencher, puis vérifiez-le immédiatement après celui-ci.  
  
 En cas d'erreur, l'élément `errno` n'est pas nécessairement défini à la même valeur que le code d'erreur retourné par un appel système. En ce qui concerne les opérations d'E/S, `_doserrno` stocke les équivalents en codes d'erreur des codes `errno` du système d'exploitation. Pour la plupart des opérations autres que d'E/S, la valeur `_doserrno` n'est pas définie.  
  
 Chaque valeur `errno` est associée à un message d'erreur dans `_sys_errlist` qui peut être imprimé en utilisant l'une des fonctions [perror](../c-runtime-library/reference/perror-wperror.md), ou stocké dans une chaîne à l'aide de l'une des fonctions [strerror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md) ou [strerror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md). Les fonctions `perror` et `strerror` utilisent le tableau `_sys_errlist` et `_sys_nerr`, le nombre d'éléments dans `_sys_errlist`, pour traiter les informations relatives aux erreurs. Un accès direct à `_sys_errlist` et `_sys_nerr` est déconseillé pour des raisons de sécurité du code. Nous vous recommandons d'utiliser les versions fonctionnelles plus sécurisées, au lieu des macros globales, comme indiqué ici :  
  
|Macro globale|Équivalents fonctionnels|  
|------------------|----------------------------|  
|`_doserrno`|[_get_doserrno](../c-runtime-library/reference/get-doserrno.md), [_set_doserrno](../c-runtime-library/reference/set-doserrno.md)|  
|`errno`|[_get_errno](../c-runtime-library/reference/get-errno.md), [_set_errno](../c-runtime-library/reference/set-errno.md)|  
|`_sys_errlist`, `_sys_nerr`|[strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)|  
  
 Les routines mathématiques des bibliothèques définissent `errno` en appelant [_matherr](../c-runtime-library/reference/matherr.md). Pour gérer des erreurs mathématiques différemment, écrivez votre propre routine selon la description de la référence `_matherr`, puis appelez-la `_matherr`.  
  
 Toutes les valeurs `errno` du tableau suivant sont des constantes prédéfinies dans \<errno.h> et compatibles avec UNIX. Seuls `ERANGE`, `EILSEQ`, et `EDOM` sont spécifiés dans la norme ISO C99.  
  
|Constante|Message d'erreur système|Value|  
|--------------|--------------------------|-----------|  
|`EPERM`|Opération non autorisée|1|  
|`ENOENT`|Aucun fichier ou répertoire de ce type|2|  
|`ESRCH`|Aucun de ces processus|3|  
|`EINTR`|Fonction interrompue|4|  
|`EIO`|Erreur d'E/S|5|  
|`ENXIO`|Aucun périphérique ou adresse de ce type|6|  
|`E2BIG`|Liste d'arguments trop longue|7|  
|`ENOEXEC`|Erreur de format exec|8|  
|`EBADF`|Numéro de fichier erroné|9|  
|`ECHILD`|Aucun processus généré|10|  
|`EAGAIN`|Plus de processus disponibles ou mémoire insuffisante ou niveau maximal d'imbrication atteint|11|  
|`ENOMEM`|Mémoire insuffisante|12|  
|`EACCES`|Autorisation refusée|13|  
|`EFAULT`|Adresse incorrecte|14|  
|`EBUSY`|Périphérique ou ressource occupé|16|  
|`EEXIST`|Le fichier existe|17|  
|`EXDEV`|Lien multi-périphériques|18|  
|`ENODEV`|Aucun périphérique de ce type|19|  
|`ENOTDIR`|Pas un répertoire|20|  
|`EISDIR`|Est un répertoire|21|  
|`EINVAL`|Argument non valide|22|  
|`ENFILE`|Trop de fichiers ouverts dans le système|23|  
|`EMFILE`|Trop de fichiers ouverts|24|  
|`ENOTTY`|Opération de contrôle d'E/S incorrecte|25|  
|`EFBIG`|Fichier trop grand|27|  
|`ENOSPC`|Aucun espace libre sur le périphérique|28|  
|`ESPIPE`|Recherche non valide|29|  
|`EROFS`|Système de fichiers en lecture seule|30|  
|`EMLINK`|Trop de liens|31|  
|`EPIPE`|Canal rompu|32|  
|`EDOM`|Argument mathématique|33|  
|`ERANGE`|Résultat trop volumineux|34|  
|`EDEADLK`|Un blocage des ressources se produirait|36|  
|`EDEADLOCK`|Identique à EDEADLK pour assurer la compatibilité avec les versions antérieures de Microsoft C|36|  
|`ENAMETOOLONG`|Nom de fichier trop long|38|  
|`ENOLCK`|Pas de verrous disponibles|39|  
|`ENOSYS`|Fonction non prise en charge|40|  
|`ENOTEMPTY`|Répertoire non vide|41|  
|`EILSEQ`|Séquence d'octets non conforme|42|  
|`STRUNCATE`|La chaîne a été tronquée|80|  
  
## <a name="requirements"></a>Configuration requise  
  
|Macro globale|En-tête requis|En-tête facultatif|  
|------------------|---------------------|---------------------|  
|`errno`|\<errno.h> ou \<stdlib.h>, \<cerrno> ou \<cstdlib> (C++)||  
|`_doserrno`, `_sys_errlist`, `_sys_nerr`|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h>, \<cerrno> (C++)|  
  
 Les macros `_doserrno`, `_sys_errlist` et `_sys_nerr` sont des extensions Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Variables globales](../c-runtime-library/global-variables.md)   
 [errno, constantes](../c-runtime-library/errno-constants.md)   
 [perror, _wperror](../c-runtime-library/reference/perror-wperror.md)   
 [strerror, _strerror, _wcserror, \__wcserror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)   
 [strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)   
 [_get_doserrno](../c-runtime-library/reference/get-doserrno.md)   
 [_set_doserrno](../c-runtime-library/reference/set-doserrno.md)   
 [_get_errno](../c-runtime-library/reference/get-errno.md)   
 [_set_errno](../c-runtime-library/reference/set-errno.md)