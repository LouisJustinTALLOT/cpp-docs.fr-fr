---
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
ms.openlocfilehash: 1b2dd1ca4768cef8eed93436c959a7d02bcbfd82
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415693"
---
# <a name="zg-generate-function-prototypes"></a>/Zg (Générer les prototypes de fonction)

Supprimé. Crée un prototype de fonction pour chaque fonction définie dans le fichier source, mais ne compile pas le fichier source.

## <a name="syntax"></a>Syntaxe

```
/Zg
```

## <a name="remarks"></a>Notes

Cette option du compilateur n’est plus disponible. Elle a été supprimée dans Visual C++ 2015. Cette page est destinée aux utilisateurs de versions antérieures de Visual C++.

Le prototype de fonction comprend le type de retour de fonction et une liste de types d’arguments. La liste de types d’arguments est créée à partir des types des paramètres formels de la fonction. Les prototypes de fonctions déjà présents dans le fichier source sont ignorés.

La liste des prototypes est écrite dans la sortie standard. Cette liste peut vous aider à vérifier que les arguments réels et les paramètres formels d’une fonction sont compatibles. Vous pouvez enregistrer la liste en redirigeant la sortie standard vers un fichier. Vous pouvez ensuite utiliser **#include** pour ajouter la liste des prototypes de fonctions dans votre fichier source. Cela permet au compilateur d’effectuer une vérification des types d’arguments.

Si vous utilisez l’option **/Zg** et que votre programme contient des paramètres formels avec les types struct, enum ou union (ou qu’il contient des pointeurs vers ces types), la déclaration de chaque type struct, enum ou union doit être accompagnée d’une balise (le nom). Dans l’exemple suivant, le nom de la balise est `MyStruct`.

```C
// Zg_compiler_option.c
// compile with: /Zg
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```

Le **/Zg** option a été déconseillée dans Visual Studio 2005 et a été supprimée dans Visual Studio 2015. Le compilateur Visual C++ a supprimé la prise en charge pour le code plus anciens, de style C. Pour obtenir la liste des options du compilateur déconseillées, consultez **Options déconseillées et supprimées du compilateur** dans [Options du compilateur classées par catégorie](../../build/reference/compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
