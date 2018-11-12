---
title: /MANIFESTINPUT (Spécifier l'entrée de manifeste)
ms.date: 11/04/2016
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: 30e0d4b71943dec8e0efe9112caf7cdf57f66809
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442690"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Spécifier l'entrée de manifeste)

Spécifie un fichier d’entrée manifest à inclure dans le manifeste est incorporé dans l’image.

## <a name="syntax"></a>Syntaxe

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>Paramètres

*filename*<br/>
Le fichier manifeste à inclure dans le manifeste incorporé.

## <a name="remarks"></a>Notes

Le **/MANIFESTINPUT** option spécifie le chemin d’accès de fichier d’entrée à utiliser pour créer le manifeste incorporé dans une image exécutable. Si vous avez manifeste plusieurs fichiers d’entrée, utilisez le commutateur plusieurs fois : une fois pour chaque fichier d’entrée. Les fichiers d’entrée manifestes sont fusionnés pour créer le manifeste incorporé. Cette option nécessite la **de manifeste : incorporer** option.

Cette option ne peut pas être définie directement dans Visual Studio. Au lieu de cela, utilisez le **fichiers manifeste supplémentaires** propriété du projet pour spécifier les fichiers manifeste supplémentaires à inclure. Pour plus d’informations, consultez [entrée et sortie, outil manifeste, propriétés de Configuration, \<Projectname > Property Pages Dialog Box](../../ide/input-and-output-manifest-tool.md).

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)