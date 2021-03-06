---
description: En savoir plus sur les constantes de validation sur disque
title: Commit-To-Disk, constantes
ms.date: 11/04/2016
f1_keywords:
- vc.constants
helpviewer_keywords:
- commit-to-disk constants
ms.assetid: 0b903b23-b4fa-431e-a937-51d95f695ecf
ms.openlocfilehash: 416729f4b3b7bfdfdcb0ba11193f6c2a52691e6e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322642"
---
# <a name="commit-to-disk-constants"></a>Commit-To-Disk, constantes

**Spécifique à Microsoft**

## <a name="syntax"></a>Syntaxe

```
#include <stdio.h>
```

## <a name="remarks"></a>Notes

Ces constantes spécifiques à Microsoft spécifient si la mémoire tampon associée au fichier ouvert est vidée dans les mémoires tampons du système d'exploitation ou sur le disque. Le mode est inclus dans la chaîne qui spécifie le type d'accès en lecture/écriture (**"r"**, **"w"**, **"a"**, **"r+"**, **"w+"**, **"a+"**).

Les modes de validation sur disque sont les suivants :

- **c**

   Écrit le contenu non écrit de la mémoire tampon spécifiée sur le disque. Cette fonctionnalité de validation sur disque se produit uniquement lors des appels explicites à la fonction [fflush](../c-runtime-library/reference/fflush.md) ou [_flushall](../c-runtime-library/reference/flushall.md). Ce mode est utile lors de l'utilisation de données sensibles. Par exemple, si votre programme prend fin après un appel à `fflush` ou à `_flushall`, vous pouvez être certain que vos données ont atteint les mémoires tampons du système d'exploitation. Toutefois, à moins qu'un fichier soit ouvert avec l'option **c**, les données peuvent ne jamais être écrites sur le disque si le système d'exploitation s'arrête également.

- **n**

   Écrit le contenu non écrit de la mémoire tampon spécifiée dans les mémoires tampons du système d'exploitation. Le système d'exploitation peut mettre en cache les données et déterminer un délai optimal pour écrire sur le disque. Dans de nombreuses conditions, ce comportement convient à un comportement efficace du programme. Toutefois, si la conservation des données est critique (par exemple, des transactions bancaires ou des informations de billet d’avion), utilisez l’option **c**. Le mode **n** est l’option par défaut.

> [!NOTE]
> Les options **c** et **n** ne font pas partie de la norme ANSI pour `fopen`, mais sont des extensions Microsoft : ne les utilisez pas quand la portabilité ANSI est souhaitée.

## <a name="using-the-commit-to-disk-feature-with-existing-code"></a>Utilisation de la fonctionnalité de validation sur disque avec le code existant

Par défaut, les appels aux fonctions [fflush](../c-runtime-library/reference/fflush.md) ou [_flushall](../c-runtime-library/reference/flushall.md) de la bibliothèque écrivent les données dans les mémoires tampons gérées par le système d'exploitation. Le système d'exploitation détermine le délai optimal pour écrire réellement les données sur le disque. La fonctionnalité de validation sur disque de la bibliothèque runtime garantit que les données critiques sont écrites directement sur le disque plutôt que dans les mémoires tampons du système d'exploitation. Vous pouvez fournir cette fonctionnalité à un programme existant sans le réécrire en liant ses fichiers objets avec COMMODE.OBJ.

Dans le fichier exécutable résultant, les appels à `fflush` écrivent le contenu de la mémoire tampon directement sur le disque, et les appels à `_flushall` écrivent le contenu de toutes les mémoires tampons sur le disque. Ces deux fonctions sont les seules affectées par COMMODE.OBJ.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[E/S de flux](../c-runtime-library/stream-i-o.md)<br/>
[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
