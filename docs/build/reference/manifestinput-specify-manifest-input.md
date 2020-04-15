---
title: /MANIFESTINPUT (Spécifier l'entrée de manifeste)
ms.date: 07/24/2019
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: d7c8351c915f5666ada9939df686c81c86ab89ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337511"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Spécifier l'entrée de manifeste)

Spécifie un fichier d’entrée manifeste à inclure dans le manifeste qui est intégré dans l’image.

## <a name="syntax"></a>Syntaxe

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>Paramètres

*Fichier*<br/>
Le fichier manifeste à inclure dans le manifeste intégré.

## <a name="remarks"></a>Notes

**L’option /MANIFESTINPUT** spécifie le chemin d’un fichier d’entrée à utiliser pour créer le manifeste intégré dans une image exécutable. Si vous disposez de plusieurs fichiers d’entrée manifestes, utilisez le commutateur plusieurs fois, une fois pour chaque fichier d’entrée. Les fichiers d’entrée manifestes sont fusionnés pour créer le manifeste intégré. Cette option nécessite l’option **/MANIFEST:EMBED.**

Cette option ne peut pas être définie directement dans Visual Studio. Utilisez plutôt la propriété **Additional Manifest Files** du projet pour spécifier d’autres fichiers manifestes à inclure. Pour plus d’informations, voir [Les pages de propriété de Manifest Tool](manifest-tool-property-pages.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
