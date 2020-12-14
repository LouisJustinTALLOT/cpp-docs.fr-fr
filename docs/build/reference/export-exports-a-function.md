---
description: En savoir plus sur:/EXPORT (exporte une fonction)
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
ms.openlocfilehash: a52ea79d0569d31c26eabd06d51ef58a10567119
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200804"
---
# <a name="export-exports-a-function"></a>/EXPORT (Exporter une fonction)

Exporte une fonction par nom ou ordinal, ou données, à partir de votre programme.

## <a name="syntax"></a>Syntaxe

> **/Export :**<em>entryname</em>[**, \@**<em>ordinal</em>[**, NoName**]] [**, Data**]

## <a name="remarks"></a>Notes

L’option **/Export** spécifie une fonction ou un élément de données à exporter à partir de votre programme afin que d’autres programmes puissent appeler la fonction ou utiliser les données. Les exportations sont généralement définies dans une DLL.

L’argument *entryname* est le nom de la fonction ou de l’élément de données tel qu’il doit être utilisé par le programme appelant. *ordinal* spécifie un index dans la table d’exportations de la plage comprise entre 1 et 65 535 ; Si vous ne spécifiez pas d' *ordinal*, Link affecte un. Le mot clé **NoName** exporte la fonction uniquement en tant qu’ordinal, sans *entryname*.

Le mot clé **Data** spécifie que l’élément exporté est un élément de données. L’élément de données dans le programme client doit être déclaré à l’aide de **extern __declspec (dllimport)**.

Il existe quatre méthodes pour exporter une définition, répertoriées dans l’ordre d’utilisation recommandé :

1. [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) dans le code source

1. Une instruction [exports](exports.md) dans un fichier. def

1. Une spécification /EXPORT dans une commande LINK

1. Directive de [Commentaire](../../preprocessor/comment-c-cpp.md) dans le code source, sous la forme `#pragma comment(linker, "/export: definition ")` .

Toutes ces méthodes peuvent être utilisées dans le même programme. Quand LINK génère un programme qui contient des exportations, il crée également une bibliothèque d’importation, à moins qu’un fichier. exp ne soit utilisé dans la Build.

LINK utilise des formes décorées d’identificateurs. Le compilateur décore un identificateur lorsqu’il crée le fichier. obj. Si l’argument *entryname* est spécifié à l’éditeur de liens dans sa forme non décorée (tel qu’il apparaît dans le code source), Link tente de faire correspondre le nom. S’il ne peut pas trouver une correspondance unique, LINK émet un message d’erreur. Utilisez l’outil [DUMPBIN](dumpbin-reference.md) pour récupérer la forme de [nom décoré](decorated-names.md) d’un identificateur lorsque vous devez le spécifier à l’éditeur de liens.

> [!NOTE]
> Ne spécifiez pas la forme décorée des identificateurs C qui sont déclarés **`__cdecl`** ou **`__stdcall`** .

Si vous devez exporter un nom de fonction non décoré et avoir des exportations différentes en fonction de la configuration de build (par exemple, dans les builds 32 bits ou 64 bits), vous pouvez utiliser différents fichiers DEF pour chaque configuration. (Les directives conditionnelles du préprocesseur ne sont pas autorisées dans les fichiers DEF.) Vous pouvez également utiliser une `#pragma comment` directive avant une déclaration de fonction comme indiqué ici, où `PlainFuncName` est le nom non décoré et `_PlainFuncName@4` est le nom décoré de la fonction :

```cpp
#pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
BOOL CALLBACK PlainFuncName( Things * lpParams)
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande de l’éditeur de liens **Propriétés de configuration**  >    >   .

1. Entrez l’option dans la zone **options supplémentaires** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
