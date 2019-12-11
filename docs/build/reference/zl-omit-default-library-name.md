---
title: /Zl (Omettre le nom de la bibliothèque par défaut)
ms.date: 11/04/2016
f1_keywords:
- /zi
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
ms.openlocfilehash: 1bcb90dbf071253dc0561845e3bd713dc42d5aef
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988553"
---
# <a name="zl-omit-default-library-name"></a>/Zl (Omettre le nom de la bibliothèque par défaut)

Omet le nom de la bibliothèque Runtime C par défaut du fichier. obj. Par défaut, le compilateur place le nom de la bibliothèque dans le fichier .obj afin de diriger l’éditeur de liens vers la bibliothèque appropriée.

## <a name="syntax"></a>Syntaxe

```
/Zl
```

## <a name="remarks"></a>Notes

Pour plus d’informations sur la bibliothèque par défaut, consultez [utiliser la bibliothèque Runtime](md-mt-ld-use-run-time-library.md).

Vous pouvez utiliser **/zl** pour compiler les fichiers. obj que vous envisagez de placer dans une bibliothèque. Bien que l’omission du nom de la bibliothèque n’enregistre qu’une petite quantité d’espace pour un seul fichier. obj, l’espace total enregistré est significatif dans une bibliothèque qui contient de nombreux modules objet.

Cette option est une option avancée. La définition de cette option supprime la prise en charge de la bibliothèque Runtime C qui peut être requise par votre application, provoquant des erreurs au moment de la liaison si votre application dépend de cette prise en charge. Si vous utilisez cette option, vous devez fournir les composants requis d’une autre façon.

Utilisez [/NODEFAULTLIB (ignorer les bibliothèques)](nodefaultlib-ignore-libraries.md). pour indiquer à l’éditeur de liens d’ignorer les références de bibliothèque dans tous les fichiers. obj.

Pour plus d’informations, consultez [Fonctionnalités de la bibliothèque CRT](../../c-runtime-library/crt-library-features.md).

Lors de la compilation avec **/zl**, `_VC_NODEFAULTLIB` est défini.  Par exemple :

```cpp
// vc_nodefaultlib.cpp
// compile with: /Zl
void Test() {
   #ifdef _VC_NODEFAULTLIB
      int i;
   #endif

   int i;   // C2086
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **avancé** .

1. Modifiez la propriété **omettre les noms de bibliothèque par défaut** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
