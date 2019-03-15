---
title: /EXPORT (Exporter une fonction)
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
ms.openlocfilehash: 7c4f4621bbccd4285bcf4eca07d2544d53d14f6c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819850"
---
# <a name="export-exports-a-function"></a>/EXPORT (Exporter une fonction)

Exporte une fonction par nom ou ordinal ou données, à partir de votre programme.

## <a name="syntax"></a>Syntaxe

> **/ EXPORT :**<em>nom d’entrée</em>[**,\@**<em>ordinale</em>[**, NONAME**]] [**, données**]

## <a name="remarks"></a>Notes

Le **/EXPORT** option spécifie un fonction ou élément de données à exporter à partir de votre programme afin que les autres programmes peuvent appeler la fonction ou utiliser les données. Exportations sont généralement définies dans une DLL.

Le *nom d’entrée* est le nom de la fonction ou élément de données tel qu’il doit être utilisé par le programme appelant. *ordinal* spécifie un index dans la table d’exportation dans la plage comprise entre 1 et 65 535, si vous ne spécifiez pas *ordinale*, assigne un. Le **NONAME** mot clé exporte la fonction uniquement comme ordinal, sans un *nom d’entrée*.

Le **données** mot clé spécifie que l’élément exporté est un élément de données. L’élément de données dans le programme client doit être déclaré à l’aide de **extern __declspec (dllimport)**.

Il existe quatre méthodes pour l’exportation d’une définition, répertoriées dans l’ordre d’utilisation recommandé :

1. [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) dans le code source

1. Un [exportations](exports.md) instruction dans un fichier .def

1. Une spécification /EXPORT dans une commande LINK

1. Un [commentaire](../../preprocessor/comment-c-cpp.md) directive dans le code source, sous la forme `#pragma comment(linker, "/export: definition ")`.

Toutes ces méthodes peuvent être utilisées dans le même programme. Quand LINK génère un programme contenant des exportations, il crée également une bibliothèque d’importation, sauf si un fichier .exp est utilisé dans la build.

LINK utilise les formes décorées des identificateurs. Le compilateur décore un identificateur lorsqu’il crée le fichier .obj. Si *nom d’entrée* est spécifiée pour l’éditeur de liens dans son non décoré forment (tel qu’il apparaît dans le code source), lien tente de correspondre au nom. Si elle ne peut pas trouver une correspondance unique, LINK émet un message d’erreur. Utilisez le [DUMPBIN](dumpbin-reference.md) outil pour obtenir le [nom décoré](decorated-names.md) forme d’un identificateur lorsque vous devez spécifier à l’éditeur de liens.

> [!NOTE]
> Ne spécifiez pas la forme décorée d’identificateurs en langage C qui sont déclarés `__cdecl` ou `__stdcall`.

Si vous devez exporter un nom non décoré de fonction et avez exportations différents en fonction de la configuration de build (par exemple, dans les versions 32 bits ou 64 bits), vous pouvez utiliser différents fichiers DEF pour chaque configuration. (Les directives du préprocesseur conditionnelles ne sont pas autorisés dans les fichiers DEF.) Comme alternative, vous pouvez utiliser un `#pragma comment` directive avant une déclaration de fonction, comme indiqué ici, où `PlainFuncName` est le nom non décoré, et `_PlainFuncName@4` est le nom décoré de la fonction :

```cpp
#pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
BOOL CALLBACK PlainFuncName( Things * lpParams)
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Entrez l’option dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
