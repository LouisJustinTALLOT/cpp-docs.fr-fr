---
title: Constantes de mode de traduction
ms.date: 11/04/2016
f1_keywords:
- _O_BINARY
- _O_TEXT
- _O_RAW
helpviewer_keywords:
- O_BINARY constant
- O_TEXT constant
- O_RAW constant
- _O_TEXT constant
- _O_RAW constant
- translation constants
- _O_BINARY constant
- translation, constants
- translation, modes
- translation modes (file I/O)
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
ms.openlocfilehash: 25588758e682409bad0a6cb2723304275f00c25e
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519722"
---
# <a name="translation-mode-constants"></a>Constantes de mode de traduction

## <a name="syntax"></a>Syntaxe

```

#include <fcntl.h>
```

## <a name="remarks"></a>Notes

Les constantes manifestes `_O_BINARY` et `_O_TEXT` déterminent le mode de traduction des fichiers (`_open` et `_sopen`) ou le mode de traduction des flux (`_setmode`).

Les valeurs autorisées sont :

|||
|-|-|
`_O_TEXT`  | Ouvre un fichier en mode texte (traduit). Les combinaisons retour chariot/saut de ligne sont traduites en un seul saut de ligne en entrée. Les caractères de saut de ligne sont traduits en combinaisons retour chariot/saut de ligne en sortie. De même, Ctrl+Z est interprété comme un caractère de fin de fichier en entrée. Dans les fichiers ouverts en lecture ou en lecture/écriture, `fopen` recherche un Ctrl+Z à la fin du fichier et le supprime, si possible. En effet, l’utilisation des fonctions `fseek` et `ftell` pour se déplacer dans un fichier qui se termine par un Ctrl+Z peut provoquer un comportement incorrect de `fseek` vers la fin du fichier.
`_O_BINARY`  | Ouvre un fichier en mode binaire (non traduit). Les traductions ci-dessus sont supprimées.
`_O_RAW`  | Comme pour `_O_BINARY`. Prise en charge pour la compatibilité C 2.0.

Pour plus d’informations, consultez [E/S de fichier en mode texte et binaire](../c-runtime-library/text-and-binary-mode-file-i-o.md) et [Traduction des fichiers](../c-runtime-library/file-translation-constants.md).

## <a name="see-also"></a>Voir aussi

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_pipe](../c-runtime-library/reference/pipe.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_setmode](../c-runtime-library/reference/setmode.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)