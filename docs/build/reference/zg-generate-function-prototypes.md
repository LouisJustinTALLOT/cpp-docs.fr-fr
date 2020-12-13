---
description: En savoir plus sur:/ZG (générer des prototypes de fonction)
title: /Zg (Générer les prototypes de fonction)
ms.date: 11/04/2016
f1_keywords:
- /zg
helpviewer_keywords:
- Zg compiler option [C++]
- /Zg compiler option [C++]
- function prototypes, generate function prototypes compiler option
- -Zg compiler option [C++]
- generate function prototypes compiler option
ms.assetid: c8df1b46-24ff-46f2-8356-e0a144b21dd2
ms.openlocfilehash: ee0bed48f15acae867d344a60a6d42f3b17c7e85
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178873"
---
# <a name="zg-generate-function-prototypes"></a>/Zg (Générer les prototypes de fonction)

Supprimé. Crée un prototype de fonction pour chaque fonction définie dans le fichier source, mais ne compile pas le fichier source.

## <a name="syntax"></a>Syntaxe

```
/Zg
```

## <a name="remarks"></a>Notes

Cette option du compilateur n’est plus disponible. Elle a été supprimée dans Visual Studio 2015. Cette page est conservée pour les utilisateurs des versions antérieures de Visual Studio.

Le prototype de fonction comprend le type de retour de fonction et une liste de types d’arguments. La liste de types d’arguments est créée à partir des types des paramètres formels de la fonction. Les prototypes de fonctions déjà présents dans le fichier source sont ignorés.

La liste des prototypes est écrite dans la sortie standard. Cette liste peut vous aider à vérifier que les arguments réels et les paramètres formels d’une fonction sont compatibles. Vous pouvez enregistrer la liste en redirigeant la sortie standard vers un fichier. Vous pouvez ensuite utiliser **#include** pour ajouter la liste des prototypes de fonctions dans votre fichier source. Cela permet au compilateur d’effectuer une vérification des types d’arguments.

Si vous utilisez l’option **/Zg** et que votre programme contient des paramètres formels avec les types struct, enum ou union (ou qu’il contient des pointeurs vers ces types), la déclaration de chaque type struct, enum ou union doit être accompagnée d’une balise (le nom). Dans l’exemple suivant, le nom de la balise est `MyStruct`.

```C
// Zg_compiler_option.c
// compile with: /Zg
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```

L’option **/ZG** a été déconseillée dans visual Studio 2005 et a été supprimée dans visual studio 2015. Le compilateur MSVC a supprimé la prise en charge de l’ancien code de style C. Pour obtenir la liste des options du compilateur déconseillées, consultez **Options du compilateur déconseillées et supprimées** dans [Options du compilateur classées par catégorie](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
