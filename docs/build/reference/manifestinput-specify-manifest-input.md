---
title: /MANIFESTINPUT (Spécifier l'entrée de manifeste)
ms.date: 11/04/2016
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: bf192664a7a2402b06621167d91dff67ce0741a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321356"
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

Cette option ne peut pas être définie directement dans Visual Studio. Au lieu de cela, utilisez le **fichiers manifeste supplémentaires** propriété du projet pour spécifier les fichiers manifeste supplémentaires à inclure. Pour plus d’informations, consultez [entrée et sortie, outil manifeste, propriétés de Configuration, \<Projectname > Property Pages Dialog Box](input-and-output-manifest-tool.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
