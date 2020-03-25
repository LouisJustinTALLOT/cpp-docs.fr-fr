---
title: Avertissement des outils Éditeur de liens LNK4286
ms.date: 04/15/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: d0205ba065f6e410383c38a0f1c2eaa0da55fe93
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173866"
---
# <a name="linker-tools-warning-lnk4286"></a>Avertissement des outils Éditeur de liens LNK4286

> le symbole'*symbol*'défini dans'*filename_1. obj*'est importé par'*filename_2. obj*'

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) a été spécifié pour *symbol* même si le symbole est défini dans le fichier objet *filename_1. obj* dans la même image. Supprimez le modificateur `__declspec(dllimport)` pour résoudre cet avertissement.

## <a name="remarks"></a>Notes

AVERTISSEMENT LNK4286 est une version plus générale du [LNK4217 d’avertissement des outils Éditeur de liens](linker-tools-warning-lnk4217.md). L’éditeur de liens génère un avertissement LNK4286 lorsqu’il peut déterminer quel fichier objet a référencé le symbole, mais pas quelle fonction.

Pour résoudre LNK4286, supprimez le modificateur de déclaration `__declspec(dllimport)` de la déclaration anticipée du *symbole* référencé dans *filename_2. obj*.

Bien que le code généré final se comporte correctement, le code généré pour appeler une fonction importée est moins efficace que l’appel direct de la fonction. Cet avertissement n’apparaît pas quand vous compilez à l’aide de l’option [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) .

Pour plus d’informations sur les déclarations d’importation et d’exportation de données, consultez [dllexport, DllImport](../../cpp/dllexport-dllimport.md).

## <a name="see-also"></a>Voir aussi

[Avertissement des outils Éditeur de liens LNK4049](linker-tools-warning-lnk4049.md) \
[Avertissement des outils Éditeur de liens LNK4217](linker-tools-warning-lnk4217.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
