---
description: En savoir plus sur:/c (compiler sans liaison)
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
ms.openlocfilehash: b9dd692dd99cddf63015fe26e37dc54841816f7f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179367"
---
# <a name="c-compile-without-linking"></a>/c (Compiler sans liaison)

Empêche l’appel automatique à LINK.

## <a name="syntax"></a>Syntaxe

```
/c
```

## <a name="remarks"></a>Notes

La compilation avec **/c** crée uniquement des fichiers. obj. Vous devez appeler explicitement LINK avec les fichiers et options appropriés pour effectuer la phase de liaison de la Build.

Tout projet interne créé dans l’environnement de développement utilise l’option **/c** par défaut.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

- Cette option n’est pas disponible dans l’environnement de développement.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Pour définir cette option du compilateur par programmation, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileOnly%2A>.

## <a name="example"></a>Exemple

La ligne de commande suivante crée les fichiers objets FIRST. objet SECOND. obj. Le troisième. obj est ignoré.

```
CL /c FIRST.C SECOND.C THIRD.OBJ
```

Pour créer un fichier exécutable, vous devez appeler LINK :

```
LINK firsti.obj second.obj third.obj /OUT:filename.exe
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
