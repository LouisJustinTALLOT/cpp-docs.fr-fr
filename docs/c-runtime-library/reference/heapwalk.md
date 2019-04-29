---
title: _heapwalk
ms.date: 11/04/2016
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
helpviewer_keywords:
- debugging [CRT], heap-related problems
- heapwalk function
- _heapwalk function
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
ms.openlocfilehash: cc2a49d9032746cc6c82c9dc401fc96baabbe2e1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331686"
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

**_heapwalk** retourne une des constantes manifestes entières suivantes définies dans Malloc.h.

|Valeur de retour|Signification|
|-|-|
|**_HEAPBADBEGIN**| Informations d’en-tête initiales non valides ou introuvables.|
|**_HEAPBADNODE**| Tas endommagé ou nœud incorrect trouvé.|
|**_HEAPBADPTR**| Le **_pentry** champ la **_HEAPINFO** structure ne contient pas un pointeur valide vers le tas ou *entryinfo* est un pointeur null.|
|**_HEAPEND**| Fin du tas atteinte avec succès.|
|**_HEAPEMPTY**| Tas non initialisé.|
|**_HEAPOK**| Aucune erreur jusqu'à présent ; *entryinfo* est mis à jour avec des informations sur l’entrée suivante du tas.|

En outre, si une erreur se produit, **_heapwalk** définit **errno** à **ENOSYS**.

## <a name="remarks"></a>Notes

Le **_heapwalk** fonction permet de déboguer les problèmes liés au tas dans les programmes. La fonction parcourt le tas, en raison d’une entrée par appel et retourne un pointeur vers une structure de type **_HEAPINFO** qui contient des informations sur l’entrée suivante du tas. Le **_HEAPINFO** type, défini dans Malloc.h, contient les éléments suivants.

|Champ|Signification|
|-|-|
|`int *_pentry`|Pointeur vers une entrée du tas.|
|`size_t _size`|Taille de l’entrée du tas.|
|`int _useflag`|Indicateur qui indique si l’entrée du tas est en cours d’utilisation.|

Un appel à **_heapwalk** qui retourne **_HEAPOK** stocke la taille de l’entrée dans le **_Taille** champ et définit le **_useflag** champ soit **_FREEENTRY** ou **_USEDENTRY** (les deux sont des constantes définies dans Malloc.h). Pour obtenir ces informations sur la première entrée dans le tas, passez **_heapwalk** un pointeur vers un **_HEAPINFO** dont la propriété **_pentry** membre est **NULL** . Si le système d’exploitation ne prend pas en charge **_heapwalk**(par exemple, Windows 98), la fonction retourne **_HEAPEND** et définit **errno** à **ENOSYS**.

Cette fonction valide son paramètre. Si *entryinfo* est un pointeur null, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne **_HEAPBADPTR**.

## <a name="requirements"></a>Configuration requise

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
