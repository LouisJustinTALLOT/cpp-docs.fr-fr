---
title: errno, constantes
ms.date: 09/17/2018
f1_keywords:
- ENOEXEC
- ENOMEM
- E2BIG
- STRUNCATE
- ENOENT
- EMFILE
- EBADF
- EDEADLOCK
- EXDEV
- EILSEQ
- EINVAL
- EDOM
- EACCES
- ERANGE
- ENOSPC
- EAGAIN
- EEXIST
- ECHILD
helpviewer_keywords:
- ENOEXEC constant
- EBADF constant
- EAGAIN constant
- EINVAL constant
- ENOENT constant
- errno constants
- E2BIG constant
- EMFILE constant
- EDEADLOCK constant
- ENOSPC constant
- EDOM constant
- ENOMEM constant
- EACCES constant
- EEXIST constant
- STRUNCATE constant
- ERANGE constant
- ECHILD constant
- EXDEV constant
- EILSEQ constant
ms.assetid: 47089258-d5a5-4cd8-b193-223894dea0cf
ms.openlocfilehash: c7c623b81d626b3d653dbd731521ffe2649671ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645599"
---
# <a name="errno-constants"></a>errno, constantes

## <a name="syntax"></a>Syntaxe

```

#include <errno.h>
```

## <a name="remarks"></a>Notes

Les valeurs **errno** sont des constantes affectées à [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) lorsque différentes conditions d'erreur se produisent.

ERRNO.H contient les définitions des valeurs **errno**. Toutefois, toutes les définitions contenues dans ERRNO.H ne sont pas utilisées dans les systèmes d'exploitation Windows 32 bits. Certaines valeurs dans ERRNO.H sont présentes pour assurer la compatibilité avec la famille UNIX de systèmes d'exploitation.

Les valeurs **errno** dans un système d'exploitation Windows 32 bits sont un sous-ensemble des valeurs pour **errno** dans les systèmes XENIX. Par conséquent, la valeur **errno** n'est pas nécessairement identique au code d'erreur réel retourné par un appel système à partir des systèmes d'exploitation Windows. Pour accéder au code d'erreur réel du système d'exploitation, utilisez la variable [_doserrno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), qui contient cette valeur.

Les valeurs **errno** suivantes sont prises en charge :

|Constante|Description|
|-|-|
|**ECHILD**|Aucun processus généré.|
|**EAGAIN**|Aucun autre processus. Une tentative de création d'un processus a échoué, car aucun autre emplacement de processus n'est disponible, la mémoire est insuffisante ou le niveau d'imbrication maximal a été atteint.|
|**E2BIG**|Liste d’arguments trop longue.|
|**EACCES**|Autorisation refusée. Le paramètre d'autorisation du fichier n'autorise pas l'accès spécifié. Cette erreur indique une tentative d'accès à un fichier (ou, dans certains cas, un répertoire) d'une manière incompatible avec les attributs du fichier.<br/><br/>Par exemple, l'erreur peut se produire lors d'une tentative de lecture d'un fichier qui n'est pas ouvert, d'ouverture d'un fichier en lecture seule existant pour l'écriture ou d'ouverture d'un répertoire au lieu d'un fichier. Dans les versions 3.0 et ultérieures du système d'exploitation MS-DOS, **EACCES** peut également indiquer une violation de verrouillage ou de partage.<br/><br/>L'erreur peut également se produire lors d'une tentative d'attribution d'un nouveau nom à un fichier ou à un répertoire, ou de suppression d'un répertoire existant.|
|**EBADF**|Numéro de fichier erroné. Il existe deux raisons possibles : 1) Le descripteur de fichier spécifié n'est pas une valeur valide ou ne fait pas référence à un fichier ouvert. 2) Une tentative a été effectuée pour écrire dans un fichier ou un périphérique ouvert pour l'accès en lecture seule.|
|**EDEADLOCK**|Un interblocage des ressources se produirait. L’argument d’une fonction mathématique ne se trouve pas dans le domaine de la fonction.|
|**EDOM**|Argument mathématique.|
|**EEXIST**|Les fichiers existent. Une tentative a été effectuée pour créer un fichier existant. Par exemple, les indicateurs **_O_CREAT** et **_O_EXCL** sont spécifiés dans un appel **_open**, mais le fichier nommé existe déjà.|
|**EILSEQ**|Séquence non conforme d'octets (par exemple, dans une chaîne MBCS).|
|**EINVAL**|Argument non valide. Une valeur non valide a été spécifiée pour l’un des arguments d’une fonction. Par exemple, la valeur fournie pour l'origine lors du positionnement d'un pointeur de fichier (au moyen d'un appel à **fseek**) est avant le début du fichier.|
|**EMFILE**|Trop de fichiers ouverts. Aucun autre descripteur de fichiers n'est disponible, et aucun autre fichier ne peut être ouvert.|
|**ENOENT**|Aucun fichier ou répertoire de ce type. Le fichier ou le répertoire spécifié n'existe pas ou est introuvable. Ce message peut apparaître lorsqu’un fichier spécifié n’existe pas ou un composant d’un chemin d’accès ne spécifie pas un répertoire existant.|
|**ENOEXEC**|Erreur de format exec. Une tentative a été effectuée pour exécuter un fichier qui n'est pas exécutable ou qui a un format de fichier exécutable non valide.|
|**ENOMEM**|Mémoire insuffisante. La mémoire disponible est insuffisante pour l'opérateur tenté. Par exemple, ce message peut apparaître lorsque la mémoire disponible est insuffisante pour exécuter un processus enfant, ou lorsque la demande d'allocation dans un appel **_getcwd** ne peut pas être satisfaite.|
|**ENOSPC**|Aucun espace libre sur le périphérique. Aucun autre espace pour l'écriture n'est disponible sur le périphérique (par exemple, si le disque est plein).|
|**ERANGE**|Résultat trop volumineux. Un argument d’une fonction mathématique est trop volumineux, provoquant ainsi la perte partielle ou totale de crédibilité du résultat. Cette erreur peut également se produire dans d'autres fonctions lorsqu'un argument est plus grand que prévu (par exemple, lorsque l'argument *buffer* de **_getcwd** est plus long que prévu).|
|**EXDEV**|Lien entre les périphériques. Une tentative a été effectuée pour déplacer un fichier vers un autre périphérique (à l'aide de la fonction **rename**).|
|**STRUNCATE**|Une copie ou une concaténation de chaîne a provoqué une chaîne tronquée. Consultez [_TRUNCATE](../c-runtime-library/truncate.md).

Les valeurs suivantes sont prises en charge pour la compatibilité avec Posix. Ce sont les valeurs requises sur les systèmes non Posix.

```C
#define E2BIG /* argument list too long */
#define EACCES /* permission denied */
#define EADDRINUSE /* address in use */
#define EADDRNOTAVAIL /* address not available */
#define EAFNOSUPPORT /* address family not supported */
#define EAGAIN /* resource unavailable try again */
#define EALREADY /* connection already in progress */
#define EBADF /* bad file descriptor */
#define EBADMSG /* bad message */
#define EBUSY /* device or resource busy */
#define ECANCELED /* operation canceled */
#define ECHILD /* no child process */
#define ECONNABORTED /* connection aborted */
#define ECONNREFUSED /* connection refused */
#define ECONNRESET /* connection reset */
#define EDEADLK /* resource deadlock would occur */
#define EDESTADDRREQ /* destination address required */
#define EDOM /* argument out of domain */
#define EEXIST /* file exists */
#define EFAULT /* bad address */
#define EFBIG /* file too large */
#define EHOSTUNREACH /* host unreachable */
#define EIDRM /* identifier removed */
#define EILSEQ /* illegal byte sequence */
#define EINPROGRESS /* operation in progress */
#define EINTR /* interrupted */
#define EINVAL /* invalid argument */
#define EIO /* io error */
#define EISCONN /* already connected */
#define EISDIR /* is a directory */
#define ELOOP /* too many synbolic link levels */
#define EMFILE /* too many files open */
#define EMLINK /* too many links */
#define EMSGSIZE /* message size */
#define ENAMETOOLONG /* filename too long */
#define ENETDOWN /* network down */
#define ENETRESET /* network reset */
#define ENETUNREACH /* network unreachable */
#define ENFILE /* too many files open in system */
#define ENOBUFS /* no buffer space */
#define ENODATA /* no message available */
#define ENODEV /* no such device */
#define ENOENT /* no such file or directory */
#define ENOEXEC /* executable format error */
#define ENOLCK /* no lock available */
#define ENOLINK /* no link */
#define ENOMEM /* not enough memory */
#define ENOMSG /* no message */
#define ENOPROTOOPT /* no protocol option */
#define ENOSPC /* no space on device */
#define ENOSR /* no stream resources */
#define ENOSTR /* not a stream */
#define ENOSYS /* function not supported */
#define ENOTCONN /* not connected */
#define ENOTDIR /* not a directory */
#define ENOTEMPTY /* directory not empty */
#define ENOTRECOVERABLE /* state not recoverable */
#define ENOTSOCK /* not a socket */
#define ENOTSUP /* not supported */
#define ENOTTY /* inappropriate io control operation */
#define ENXIO /* no such device or address */
#define EOPNOTSUPP /* operation not supported */
#define EOTHER /* other */
#define EOVERFLOW /* value too large */
#define EOWNERDEAD /* owner dead */
#define EPERM /* operation not permitted */
#define EPIPE /* broken pipe */
#define EPROTO /* protocol error */
#define EPROTONOSUPPORT /* protocol not supported */
#define EPROTOTYPE /* wrong protocol type */
#define ERANGE /* result out of range */
#define EROFS /* read only file system */
#define ESPIPE /* invalid seek */
#define ESRCH /* no such process */
#define ETIME /* stream timeout */
#define ETIMEDOUT /* timed out */
#define ETXTBSY /* text file busy */
#define EWOULDBLOCK /* operation would block */
#define EXDEV /* cross device link */
```

## <a name="see-also"></a>Voir aussi

[Constantes globales](../c-runtime-library/global-constants.md)