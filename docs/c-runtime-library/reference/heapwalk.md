---
title: _heapwalk | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _heapwalk
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- heapwalk
- _heapwalk
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], heap-related problems
- heapwalk function
- _heapwalk function
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab80252b599d0a6d7a50e3b113824adc8d8d9926
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="heapwalk"></a>_heapwalk

Parcourt le tas et retourne des informations sur l’entrée suivante.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime, sauf dans les builds de débogage. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _heapwalk( _HEAPINFO *entryinfo );
```

### <a name="parameters"></a>Paramètres

*entryinfo*<br/>
Mémoire tampon destinée à contenir les informations relatives au tas.

## <a name="return-value"></a>Valeur de retour

**_heapwalk** renvoie un des constantes manifestes entières suivantes définies dans Malloc.h.

|Valeur de retour|Signification|
|-|-|
|**_HEAPBADBEGIN**| Informations d’en-tête initiales non valides ou introuvables.|
|**_HEAPBADNODE**| Tas endommagé ou nœud incorrect trouvé.|
|**_HEAPBADPTR**| Le **_pentry** champ le **_HEAPINFO** structure ne contient pas un pointeur valide dans le tas ou *entryinfo* est un pointeur null.|
|**_HEAPEND**| Fin du tas atteinte avec succès.|
|**_HEAPEMPTY**| Tas non initialisé.|
|**_HEAPOK**| Aucune erreur jusqu'à présent ; *entryinfo* est mis à jour avec des informations sur l’entrée suivante du tas.|

En outre, si une erreur se produit, **_heapwalk** définit **errno** à **ENOSYS**.

## <a name="remarks"></a>Notes

Le **_heapwalk** fonction permet de déboguer les problèmes liés au tas de programmes. La fonction Guide à travers le tas, en parcourant une entrée par l’appel et retourne un pointeur vers une structure de type **_HEAPINFO** qui contient des informations sur l’entrée suivante du tas. Le **_HEAPINFO** type, définie dans Malloc.h, contient les éléments suivants.

|Champ|Signification|
|-|-|
|`int *_pentry`|Pointeur vers une entrée du tas.|
|`size_t _size`|Taille de l’entrée du tas.|
|`int _useflag`|Indicateur qui indique si l’entrée du tas est en cours d’utilisation.|

Un appel à **_heapwalk** qui retourne **_HEAPOK** stocke la taille de l’entrée dans le **_size** champ et définit les **_useflag** soit au champ **_FREEENTRY** ou **_USEDENTRY** (les deux sont des constantes définies dans Malloc.h). Pour obtenir ces informations sur la première entrée dans le tas, passez **_heapwalk** un pointeur vers un **_HEAPINFO** structure dont **_pentry** membre est **NULL** . Si le système d’exploitation ne prend pas en charge **_heapwalk**(par exemple, Windows 98), la fonction retourne **_HEAPEND** et définit **errno** à **ENOSYS**.

Cette fonction valide son paramètre. Si *entryinfo* est un pointeur null, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne **_HEAPBADPTR**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_heapwalk**|\<malloc.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_heapwalk.c

// This program "walks" the heap, starting
// at the beginning (_pentry = NULL). It prints out each
// heap entry's use, location, and size. It also prints
// out information about the overall state of the heap as
// soon as _heapwalk returns a value other than _HEAPOK
// or if the loop has iterated 100 times.

#include <stdio.h>
#include <malloc.h>

void heapdump(void);

int main(void)
{
    char *buffer;

    heapdump();
    if((buffer = (char *)malloc(59)) != NULL)
    {
        heapdump();
        free(buffer);
    }
    heapdump();
}

void heapdump(void)
{
    _HEAPINFO hinfo;
    int heapstatus;
    int numLoops;
    hinfo._pentry = NULL;
    numLoops = 0;
    while((heapstatus = _heapwalk(&hinfo)) == _HEAPOK &&
          numLoops < 100)
    {
        printf("%8s block at %Fp of size %4.4X\n",
               (hinfo._useflag == _USEDENTRY ? "USED" : "FREE"),
               hinfo._pentry, hinfo._size);
        numLoops++;
    }

    switch(heapstatus)
    {
    case _HEAPEMPTY:
        printf("OK - empty heap\n");
        break;
    case _HEAPEND:
        printf("OK - end of heap\n");
        break;
    case _HEAPBADPTR:
        printf("ERROR - bad pointer to heap\n");
        break;
    case _HEAPBADBEGIN:
        printf("ERROR - bad start of heap\n");
        break;
    case _HEAPBADNODE:
        printf("ERROR - bad node in heap\n");
        break;
    }
}
```

```Output
    USED block at 00310650 of size 0100
    USED block at 00310758 of size 0800
    USED block at 00310F60 of size 0080
    FREE block at 00310FF0 of size 0398
    USED block at 00311390 of size 000D
    USED block at 003113A8 of size 00B4
    USED block at 00311468 of size 0034
    USED block at 003114A8 of size 0039
...
    USED block at 00312228 of size 0010
    USED block at 00312240 of size 1000
    FREE block at 00313250 of size 1DB0
OK - end of heap
```

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapchk](heapchk.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
