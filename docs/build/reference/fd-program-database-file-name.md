---
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
ms.openlocfilehash: c686de7dc9c9c20c404240db558d2ff66078ceb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292729"
---
# <a name="fd-program-database-file-name"></a>/Fd (Nom de fichier PDB)

Spécifie un nom de fichier pour le fichier de base de données (PDB) programme créé par [/Z7, / Zi, /ZI (Format des informations de débogage)](z7-zi-zi-debug-information-format.md).

## <a name="syntax"></a>Syntaxe

```
/Fdpathname
```

## <a name="remarks"></a>Notes

Sans **/Fd**, par défaut est le nom du fichier PDB VC*x*0.pdb, où *x* est la version principale de Visual C++ en cours d’utilisation.

Si vous spécifiez un nom de chemin d’accès qui n’inclut pas un nom de fichier (le chemin d’accès se termine par une barre oblique inverse), le compilateur crée un fichier .pdb nommé VC*x*0.pdb dans le répertoire spécifié.

Si vous spécifiez un nom de fichier qui n’inclut pas une extension, le compilateur utilise .pdb en tant que l’extension.

Cette option nomme également le fichier d’état (.idb) utilisé pour la régénération minimale et la compilation incrémentielle.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés des **Fichiers de sortie** .

1. Modifier le **nom de fichier de base de données de programme** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>.

## <a name="example"></a>Exemple

Cette ligne de commande crée un fichier .pdb nommé PROG.pdb et un fichier .idb nommé PROG.idb :

```
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP
```

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](output-file-f-options.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Spécification du nom de chemin](specifying-the-pathname.md)
