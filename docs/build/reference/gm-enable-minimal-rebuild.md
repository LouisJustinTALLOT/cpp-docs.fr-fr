---
title: /Gm (Activer la régénération minimale)
ms.date: 11/12/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- /FD
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
ms.openlocfilehash: 4a66dda37b84119a4b8bc23f7fc719d50e8786f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292065"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (Activer la régénération minimale)

Obsolète. Permet une régénération minimale, qui détermine si les fichiers sources C++ qui incluent des définitions de classe C++ modifiées (stockées dans des fichiers d'en-tête (.h)) doivent être recompilés.

## <a name="syntax"></a>Syntaxe

```
/Gm
```

## <a name="remarks"></a>Notes

**/GM** est déconseillée. Il peut ne pas déclenche une build pour certains types de modifications de fichier d’en-tête. Vous pouvez supprimer en toute sécurité de cette option à partir de vos projets. Pour améliorer les temps de génération, nous vous recommandons de vous utilisez des en-têtes précompilés et incrémentielle et parallèles options de génération à la place. Pour obtenir la liste des options du compilateur déconseillées, consultez le **Options déconseillées et supprimées du compilateur** section [Options du compilateur classées par catégorie](compiler-options-listed-by-category.md).

Le compilateur stocke des informations sur les dépendances entre les fichiers sources et les définitions de classe dans le fichier .idb du projet au cours de la première compilation. (Informations sur les dépendances indiquent quel fichier source dépend de la définition de classe, et quel fichier .h la définition se trouve dans.) Les compilations suivantes utilisent les informations stockées dans le fichier .idb pour déterminer si un fichier source doit être compilé, même s’il comprend un fichier .h modifié.

> [!NOTE]
> Une régénération minimale s'appuie sur des définitions de classe qui ne changent pas entre les fichiers Include. Les définitions de classe doivent être globales pour un projet (il doit exister une seule définition d'une classe donnée), car les informations sur les dépendances dans le fichier .idb sont créées pour le projet entier. Si vous possédez plusieurs définitions pour une classe dans votre projet, désactivez la régénération minimale.

Étant donné que l’éditeur de liens incrémentielle ne prend pas en charge les métadonnées Windows incluses dans les fichiers .obj à l’aide de la [/ZW (Compilation pour le Windows Runtime)](zw-windows-runtime-compilation.md) option, le **/Gm** option n’est pas compatible avec  **/ZW**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **génération de Code** page de propriétés.

1. Modifier le **activer la régénération minimale** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
