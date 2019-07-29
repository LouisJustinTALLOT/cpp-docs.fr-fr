---
title: /MANIFESTINPUT (Spécifier l'entrée de manifeste)
ms.date: 07/24/2019
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: 7b7bd54f98003d9158276fcf75fd61ffb5348585
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606464"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Spécifier l'entrée de manifeste)

Spécifie un fichier d’entrée de manifeste à inclure dans le manifeste incorporé dans l’image.

## <a name="syntax"></a>Syntaxe

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>Paramètres

*filename*<br/>
Fichier manifeste à inclure dans le manifeste incorporé.

## <a name="remarks"></a>Notes

L’option **/MANIFESTINPUT** spécifie le chemin d’accès d’un fichier d’entrée à utiliser pour créer le manifeste incorporé dans une image exécutable. Si vous avez plusieurs fichiers d’entrée de manifeste, utilisez le commutateur plusieurs fois, une fois pour chaque fichier d’entrée. Les fichiers d’entrée du manifeste sont fusionnés pour créer le manifeste incorporé. Cette option requiert l’option **/Manifest: embed** .

Cette option ne peut pas être définie directement dans Visual Studio. Utilisez plutôt la propriété **fichiers manifeste supplémentaires** du projet pour spécifier des fichiers manifeste supplémentaires à inclure. Pour plus d’informations, consultez les pages de propriétés de l' [outil manifeste](manifest-tool-property-pages.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
