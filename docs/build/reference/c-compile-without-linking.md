---
title: /c (Compiler sans liaison)
ms.date: 11/04/2016
f1_keywords:
- /c
helpviewer_keywords:
- suppress link
- cl.exe compiler, compiling without linking
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
ms.openlocfilehash: bfe351daf43b913f10df74b1059ba98f7d5d657b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294848"
---
# <a name="c-compile-without-linking"></a>/c (Compiler sans liaison)

Empêche l’appel automatique de lien.

## <a name="syntax"></a>Syntaxe

```
/c
```

## <a name="remarks"></a>Notes

Compilation avec **/c** crée des fichiers .obj uniquement. Vous devez appeler explicitement lien avec les fichiers appropriés et les options permettant d’effectuer la phase de liaison de la build.

Tout projet interne créé dans l’environnement de développement utilise le **/c** option par défaut.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

- Cette option n’est pas disponible dans l’environnement de développement.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Pour définir cette option du compilateur par programmation, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileOnly%2A>.

## <a name="example"></a>Exemple

La ligne de commande suivante crée les fichiers objets FIRST.obj et SECOND.obj. THIRD.obj est ignoré.

```
CL /c FIRST.C SECOND.C THIRD.OBJ
```

Pour créer un fichier exécutable, vous devez appeler le lien :

```
LINK firsti.obj second.obj third.obj /OUT:filename.exe
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
