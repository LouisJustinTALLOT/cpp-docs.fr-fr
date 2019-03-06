---
title: /Fo (Nom de fichier objet)
ms.date: 11/04/2016
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
ms.openlocfilehash: bcb0f96eba277b65e3478843ca0e1666f9c404aa
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418358"
---
# <a name="fo-object-file-name"></a>/Fo (Nom de fichier objet)

Spécifie un nom de fichier objet (.obj) ou un répertoire à utiliser à la place de la valeur par défaut.

## <a name="syntax"></a>Syntaxe

```
/Fopathname
```

## <a name="remarks"></a>Notes

Si vous n’utilisez pas cette option, le fichier objet utilise le nom de base du fichier source et l’extension .obj. Vous pouvez utiliser n’importe quel nom et l’extension que vous souhaitez, mais la convention recommandée consiste à utiliser. obj.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés des **Fichiers de sortie** .

1. Modifier le **nom de fichier objet** propriété.  Dans l’environnement de développement, le fichier objet doit avoir une extension de. obj.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.

## <a name="example"></a>Exemple

La ligne de commande suivante crée un fichier objet nommé THIS.obj dans un répertoire existant, \OBJECT, sur le lecteur B.

```
CL /FoB:\OBJECT\ THIS.C
```

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](../../build/reference/output-file-f-options.md)<br/>
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[Spécification du nom de chemin](../../build/reference/specifying-the-pathname.md)
