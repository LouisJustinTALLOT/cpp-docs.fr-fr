---
title: Avertissement des outils Éditeur de liens LNK4286
ms.date: 04/15/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: 43ed18808ba5ce632dd7dc7095f7bc30e4497ec9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59674225"
---
# <a name="linker-tools-warning-lnk4286"></a>Avertissement des outils Éditeur de liens LNK4286

> symbole '*symbole*'définie dans'*filename_1.obj*'est importé par'*filename_2.obj*'

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) a été spécifiée pour *symbole* même si le symbole est défini dans le fichier objet *filename_1.obj* dans la même image. Supprimer le `__declspec(dllimport)` modificateur pour résoudre cet avertissement.

## <a name="remarks"></a>Notes

Avertissement LNK4286 est une version plus générale de [avertissement d’outils de l’éditeur de liens LNK4217](linker-tools-warning-lnk4217.md). L’éditeur de liens génère l’avertissement LNK4286 lorsqu’il peut indiquer quel fichier de l’objet référencé le symbole, mais pas la fonction.

Pour résoudre LNK4286, supprimez le `__declspec(dllimport)` modificateur de déclaration à partir de la déclaration anticipée de *symbole* référencé dans *filename_2.obj*.

Bien que le code final généré se comporte correctement, le code généré pour appeler une fonction importée est moins efficace que l’appel de la fonction directement. Cet avertissement n’apparaît pas quand vous compilez à l’aide de la [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) option.

Pour plus d’informations sur Importer et exporter des déclarations de données, consultez [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="see-also"></a>Voir aussi

[Outils de l’éditeur de liens LNK4049 d’avertissement](linker-tools-warning-lnk4049.md) \
[Outils de l’éditeur de liens LNK4217 d’avertissement](linker-tools-warning-lnk4217.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)