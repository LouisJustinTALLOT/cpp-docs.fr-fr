---
title: Avertissement LNK4286 des outils de l’éditeur de liens
ms.date: 04/09/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: f4ab9104c68534eaf1278a6cacb91623c24a237b
ms.sourcegitcommit: 0ad3f4517e64900a2702dd3d366586f9e2bce2c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477632"
---
# <a name="linker-tools-warning-lnk4286"></a>Avertissement LNK4286 des outils de l’éditeur de liens

> symbole '*symbole*'définie dans'*filename_1.obj*'est importé par'*filename_2.obj*'

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) a été spécifiée pour *symbole* même si le symbole est défini dans le fichier objet *filename_1.obj* dans la même image. Supprimer le `__declspec(dllimport)` modificateur pour résoudre cet avertissement.

## <a name="remarks"></a>Notes

Avertissement LNK4286 est une version plus générale de [avertissement d’outils de l’éditeur de liens LNK4217](linker-tools-warning-lnk4217.md). L’éditeur de liens génère l’avertissement LNK4286 lorsqu’il peut indiquer quel fichier de l’objet référencé le symbole, mais pas la fonction.

Pour résoudre LNK4286, supprimez le `__declspec(dllimport)` modificateur de déclaration à partir de la déclaration anticipée de *symbole* référencé dans *filename_2.obj*.

Bien que le code final généré se comporte correctement, le code généré pour appeler une fonction importée est moins efficace que l’appel de la fonction directement. Cet avertissement n’apparaît pas quand vous compilez à l’aide de la [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) option.

Pour plus d’informations sur Importer et exporter des déclarations de données, consultez [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="see-also"></a>Voir aussi

[Outils de l’éditeur de liens LNK4049 d’avertissement](linker-tools-warning-lnk4049.md) \
[Avertissement LNK4286 des outils de l’éditeur de liens](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)