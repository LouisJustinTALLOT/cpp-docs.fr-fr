---
title: -Fd (nom de fichier de base de données) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /FD
- VC.Project.VCCLWCECompilerTool.ProgramDataBaseFileName
- VC.Project.VCCLCompilerTool.ProgramDataBaseFileName
dev_langs:
- C++
helpviewer_keywords:
- /FD compiler option [C++]
- program database file name [C++]
- -FD compiler option [C++]
- PDB files, creating
- program database compiler option [C++]
- .pdb files, creating
- FD compiler option [C++]
ms.assetid: 3977a9ed-f0ac-45df-bf06-01cedd2ba85a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07ab9f1d9c5c611b8da8b19860fe9e0c05351d75
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375621"
---
# <a name="fd-program-database-file-name"></a>/Fd (Nom de fichier PDB)
Spécifie un nom de fichier pour le fichier de base de données (PDB) de programme créé par [/Z7, / Zi, /ZI (Format des informations de débogage)](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Fdpathname  
```  
  
## <a name="remarks"></a>Notes  
 Sans **/Fd**, par défaut est le nom de fichier PDB VC*x*0.pdb, où *x* est la version principale de Visual C++ en cours d’utilisation.  
  
 Si vous spécifiez un nom de chemin d’accès qui n’inclut pas un nom de fichier (le chemin d’accès se termine par une barre oblique inverse), le compilateur crée un fichier .pdb nommé VC*x*pdb 0 dans le répertoire spécifié.  
  
 Si vous spécifiez un nom de fichier qui n’inclut pas une extension, le compilateur utilise .pdb en tant que l’extension.  
  
 Cette option nomme également le fichier d’état (.idb) utilisé pour la régénération minimale et la compilation incrémentielle.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur la page de propriétés des **Fichiers de sortie** .  
  
4.  Modifier la **nom de fichier de base de données de programme** propriété.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>.  
  
## <a name="example"></a>Exemple  
 Cette ligne de commande crée un fichier .pdb nommé PROG.pdb et un fichier .idb nommé PROG.idb :  
  
```  
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier de sortie (/ F) Options](../../build/reference/output-file-f-options.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [Spécification du nom de chemin](../../build/reference/specifying-the-pathname.md)