---
description: En savoir plus sur:/FD (nom du fichier de base de données du programme)
title: /Fd (Nom de fichier PDB)
ms.date: 11/04/2016
f1_keywords:
- /FD
- VC.Project.VCCLWCECompilerTool.ProgramDataBaseFileName
- VC.Project.VCCLCompilerTool.ProgramDataBaseFileName
helpviewer_keywords:
- /FD compiler option [C++]
- program database file name [C++]
- -FD compiler option [C++]
- PDB files, creating
- program database compiler option [C++]
- .pdb files, creating
- FD compiler option [C++]
ms.assetid: 3977a9ed-f0ac-45df-bf06-01cedd2ba85a
ms.openlocfilehash: 3990cdd6c560dfdeaef7078a29e965831c2a9504
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200661"
---
# <a name="fd-program-database-file-name"></a>/Fd (Nom de fichier PDB)

Spécifie un nom de fichier pour le fichier de base de données du programme (PDB) créé par [/Z7,/Zi,/ZI (format des informations de débogage)](z7-zi-zi-debug-information-format.md).

## <a name="syntax"></a>Syntaxe

```
/Fdpathname
```

## <a name="remarks"></a>Notes

Sans **/FD**, le nom du fichier PDB est par défaut VC *x* 0. pdb, où *x* est la version principale de Visual C++ en cours d’utilisation.

Si vous spécifiez un nom de chemin d’accès qui n’inclut pas de nom de fichier (le chemin d’accès se termine par une barre oblique inverse), le compilateur crée un fichier. PDB nommé VC *x* 0. pdb dans le répertoire spécifié.

Si vous spécifiez un nom de fichier qui n’inclut pas d’extension, le compilateur utilise. pdb comme extension.

Cette option nomme également le fichier d’État (. IDB) utilisé pour la régénération minimale et la compilation incrémentielle.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés des **Fichiers de sortie** .

1. Modifiez la propriété **nom du fichier de base de données du programme** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>.

## <a name="example"></a>Exemple

Cette ligne de commande crée un fichier. PDB nommé PROG. pdb et un fichier. IDB nommé PROG. IDB :

```
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP
```

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](output-file-f-options.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Spécification du chemin d’accès](specifying-the-pathname.md)
