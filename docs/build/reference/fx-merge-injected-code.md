---
title: /Fx (Fusionner le code injecté)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExpandAttributedSource
- /Fx
- VC.Project.VCCLCompilerTool.ExpandAttributedSource
helpviewer_keywords:
- Fx compiler option [C++]
- -Fx compiler option [C++]
- injected code
- merging injected code
- /Fx compiler option [C++]
ms.assetid: 14f0e301-3bab-45a3-bbdf-e7ce66f20560
ms.openlocfilehash: f1a266eee4edc524fbbe49bdef31a8235f62bd3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292300"
---
# <a name="fx-merge-injected-code"></a>/Fx (Fusionner le code injecté)

Produit une copie de chaque fichier source avec le code injecté fusionné dans la source.

## <a name="syntax"></a>Syntaxe

```
/Fx
```

## <a name="remarks"></a>Notes

Pour distinguer un fichier source fusionné d’un fichier source d’origine, **/Fx** ajoute une extension .mrg entre le nom de fichier et l’extension de fichier. Par exemple, un fichier nommé MyCode.cpp contenant du code avec attributs et généré avec **/Fx** crée un fichier nommé MyCode.mrg.cpp contenant le code suivant :

```
//+++ Start Injected Code
[no_injected_text(true)];      // Suppress injected text, it has
                               // already been injected
#pragma warning(disable: 4543) // Suppress warnings about skipping
                               // injected text
#pragma warning(disable: 4199) // Suppress warnings from attribute
                               // providers
//--- End Injected Code
```

Dans un fichier .mrg, le code injecté en raison d’un attribut est délimité comme suit :

```
//+++ Start Injected Code
...
//--- End Injected Code
```

L’attribut [no_injected_text](../../windows/no-injected-text.md) attribut est incorporé dans un fichier .mrg, ce qui permet la compilation du fichier .mrg sans réinjection de texte.

Notez bien que le fichier source .mrg est destiné à être une représentation sous forme de code source injecté par le compilateur. Le fichier .mrg ne peut pas être compilé ou s’exécuter exactement comme le fichier source d’origine.

Les macros ne sont pas développées dans le fichier .mrg.

Si votre programme inclut un fichier d’en-tête qui utilise du code injecté, **/Fx** génère un fichier .mrg.h pour cet en-tête. **/Fx** ne fusionne pas les fichiers include qui n’utilisent pas de code injecté.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés des **Fichiers de sortie** .

1. Modifiez la propriété **Développement de la source avec attributs** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExpandAttributedSource%2A>.

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](output-file-f-options.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
