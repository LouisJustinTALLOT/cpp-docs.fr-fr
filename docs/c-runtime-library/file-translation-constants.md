---
title: Constantes de translation de fichier
ms.date: 11/04/2016
f1_keywords:
- c.constants.file
helpviewer_keywords:
- translation constants
- file translation [C++], constants
- translation, file translation constants
- translation, constants
- constants [C++], file translation mode
- file translation [C++]
ms.assetid: 49b13bf3-442e-4d19-878b-bd1029fa666a
ms.openlocfilehash: d98a74c820023ac8684f54413c0e81c58eba7b0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443288"
---
# <a name="file-translation-constants"></a>Constantes de translation de fichier

## <a name="syntax"></a>Syntaxe

```
#include <stdio.h>
```

## <a name="remarks"></a>Notes

Ces constantes spécifient le mode de translation (**« b »** ou **« t »**). Le mode est inclus dans la chaîne qui spécifie le type d'accès (**"r"**, **"w"**, **"a"**, **"r+"**, **"w+"**, **"a+"**).

Les modes de translation sont les suivants :

- **t**

   Ouvre en mode texte (traduit). Dans ce mode, les combinaisons retour chariot-saut de ligne sont traduites en flux d'une ligne (saut de ligne) en entrée, et les caractères de saut de ligne sont traduits en combinaisons retour chariot/saut de en sortie. De même, Ctrl+Z est interprété comme un caractère de fin de fichier en entrée. Dans les fichiers ouverts en lecture ou lecture/écriture, `fopen` recherche un Ctrl+Z à la fin du fichier et le supprime, si possible. En effet, l’utilisation des fonctions `fseek` et `ftell` pour se déplacer dans un fichier qui se termine par un Ctrl+Z peut provoquer un comportement incorrect de `fseek` vers la fin du fichier.

   > [!NOTE]
   > L’option **t** ne fait pas partie de la norme ANSI pour `fopen` et `freopen`. Il s’agit d’une extension Microsoft qui ne doit pas être utilisée là où la portabilité ANSI est souhaitée.

- **b**

   Ouvre en mode binaire (non traduit). Les traductions ci-dessus sont supprimées.

Si **t** ou **b** n'est pas spécifié dans *mode*, le mode de traduction est défini par la variable de mode par défaut [_fmode](../c-runtime-library/fmode.md). Pour plus d’informations sur l’utilisation des modes texte et binaire, consultez [E/S de fichier en mode texte et binaire](../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="see-also"></a>Voir aussi

[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)