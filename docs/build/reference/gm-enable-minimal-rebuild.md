---
title: /Gm (Activer la régénération minimale)
ms.date: 11/12/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
ms.openlocfilehash: 9b928f3add0a2ec10257bf63fe61a824336c19b8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439643"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (Activer la régénération minimale)

Action déconseillée. Permet une régénération minimale, qui détermine si les fichiers sources C++ qui incluent des définitions de classe C++ modifiées (stockées dans des fichiers d'en-tête (.h)) doivent être recompilés.

## <a name="syntax"></a>Syntaxe

```
/Gm
```

## <a name="remarks"></a>Notes

**/GM** est déconseillé. Il se peut qu’il ne déclenche pas de build pour certains types de modifications de fichier d’en-tête. Vous pouvez supprimer cette option en toute sécurité de vos projets. Pour améliorer les temps de génération, nous vous recommandons d’utiliser à la place des en-têtes précompilés et des options de génération incrémentielle et parallèle. Pour obtenir la liste des options du compilateur déconseillées, consultez la section **Options du compilateur déconseillées et supprimées** dans [Options du compilateur classées par catégorie](compiler-options-listed-by-category.md).

Le compilateur stocke des informations sur les dépendances entre les fichiers sources et les définitions de classe dans le fichier .idb du projet au cours de la première compilation. (Les informations sur les dépendances indiquent quel fichier source est dépendant de quelle définition de classe, et dans quel fichier .h la définition se trouve.) Les compilations suivantes utilisent les informations stockées dans le fichier .idb pour déterminer si un fichier source a besoin d'être compilé, même s'il inclut un fichier .h modifié.

> [!NOTE]
> Une régénération minimale s'appuie sur des définitions de classe qui ne changent pas entre les fichiers Include. Les définitions de classe doivent être globales pour un projet (il doit exister une seule définition d'une classe donnée), car les informations sur les dépendances dans le fichier .idb sont créées pour le projet entier. Si vous possédez plusieurs définitions pour une classe dans votre projet, désactivez la régénération minimale.

Étant donné que l’éditeur de liens incrémentiel ne prend pas en charge les métadonnées Windows incluses dans les fichiers. obj à l’aide de l’option [/ZW (Windows Runtime Compilation)](zw-windows-runtime-compilation.md) , l’option **/GM** est incompatible avec **/ZW**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez les **Propriétés de configuration** > page de propriétés de **génération de code** **C/C++**  > .

1. Modifiez la propriété **activer la régénération minimale** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
