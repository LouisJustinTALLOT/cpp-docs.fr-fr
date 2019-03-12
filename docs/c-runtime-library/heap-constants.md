---
title: Constantes de tas
ms.date: 11/04/2016
f1_keywords:
- _HEAPBADPTR
- _HEAPEMPTY
- _HEAPBADBEGIN
- _HEAPOK
- _HEAPBADNODE
- _HEAPEND
helpviewer_keywords:
- _HEAPOK constants
- _HEAPEND constants
- HEAPBADBEGIN constants
- _HEAPBADNODE constants
- HEAPBADNODE constants
- HEAPBADPTR constants
- _HEAPEMPTY constants
- HEAPEND constants
- HEAPOK constants
- HEAPEMPTY constants
- _HEAPBADBEGIN constants
- _HEAPBADPTR constants
- heap constants
ms.assetid: 3f751bb9-2dc4-486f-b5f5-9061c96d3754
ms.openlocfilehash: 44c7a280ebffd0073f1dfb3a0a3cbdbd2efee0fb
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745371"
---
# <a name="heap-constants"></a>Constantes de tas

## <a name="syntax"></a>Syntaxe

```
#include <malloc.h>
```

## <a name="remarks"></a>Remarques

Ces constantes donnent la valeur de retour indiquant l’état du tas.

|Constante|Signification|
|--------------|-------------|
|`_HEAPBADBEGIN`|Les informations d’en-tête initiales sont introuvables ou ne sont pas valides.|
|`_HEAPBADNODE`|Un nœud incorrect a été trouvé, ou un segment de mémoire est endommagé.|
|`_HEAPBADPTR`|Le champ **_pentry** de la structure **_HEAPINFO** ne contient pas de pointeur valide dans le tas (routine `_heapwalk` uniquement).|
|`_HEAPEMPTY`|Le tas n’a pas été initialisé.|
|`_HEAPEND`|Fin du segment de mémoire atteinte avec succès (routine `_heapwalk` uniquement).|
|`_HEAPOK`|Le tas est cohérent (routines `_heapset` et `_heapchk` uniquement). Aucune erreur jusqu'à présent ; la structure **_HEAPINFO** contient des informations sur l’entrée suivante (routine `_heapwalk` uniquement).|

## <a name="see-also"></a>Voir aussi

[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
