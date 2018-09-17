---
title: -c (compiler sans liaison) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /c
dev_langs:
- C++
helpviewer_keywords:
- suppress link
- cl.exe compiler, compiling without linking
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de6fe291bde8652b772c7091c1919836f88960fd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710344"
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

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)