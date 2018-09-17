---
title: -Zl (omettre le nom de la bibliothèque par défaut) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /zi
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
dev_langs:
- C++
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f09abebb8fc142bbe2390f61d790a5885c9aebe
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707315"
---
# <a name="zl-omit-default-library-name"></a>/Zl (Omettre le nom de la bibliothèque par défaut)

Omet le nom de bibliothèque runtime C par défaut à partir du fichier .obj. Par défaut, le compilateur place le nom de la bibliothèque dans le fichier .obj afin de diriger l’éditeur de liens vers la bibliothèque appropriée.

## <a name="syntax"></a>Syntaxe

```
/Zl
```

## <a name="remarks"></a>Notes

Pour plus d’informations sur la bibliothèque par défaut, consultez [utilisez Run-Time Library](../../build/reference/md-mt-ld-use-run-time-library.md).

Vous pouvez utiliser **/Zl** pour compiler les fichiers .obj vous envisagez de placer dans une bibliothèque. Bien qu’en omettant le nom de la bibliothèque enregistre uniquement une petite quantité d’espace pour un seul fichier .obj, l’espace total économisé est significatif dans une bibliothèque qui contient de nombreux modules objet.

Cette option est une option avancée. Cette option supprime certains prise en charge de bibliothèque Runtime C qui peut être requis par votre application, ce qui entraîne des erreurs du moment de la liaison si votre application dépend de cette prise en charge. Si vous utilisez cette option, vous devez fournir les composants requis par d’autres moyens.

Utilisez [/NODEFAULTLIB (ignorer les bibliothèques)](../../build/reference/nodefaultlib-ignore-libraries.md). pour diriger l’éditeur de liens pour ignorer les références de bibliothèque dans tous les fichiers .obj.

Pour plus d’informations, consultez [Fonctionnalités de la bibliothèque CRT](../../c-runtime-library/crt-library-features.md).

Lors de la compilation avec **/Zl**, `_VC_NODEFAULTLIB` est défini.  Exemple :

```
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

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **avancé** page de propriétés.

1. Modifier le **omettre les noms de bibliothèque par défaut** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)