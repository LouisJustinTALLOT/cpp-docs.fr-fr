---
description: En savoir plus sur:/nologo (supprimer la bannière de démarrage) (C/C++)
title: /nologo (Suppression de la bannière de démarrage) (C/C++)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.SuppressStartupBanner
- VC.Project.VCCLCompilerTool.SuppressStartupBanner
helpviewer_keywords:
- -nologo compiler option [C++]
- /nologo compiler option [C++]
- nologo compiler option [C++]
- banners, suppressing startup
ms.assetid: 75930d8b-b11c-4db8-99e5-b52f97da0693
ms.openlocfilehash: a924eaf18a772b9495e1a493855fd72e9b79dd83
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196605"
---
# <a name="nologo-suppress-startup-banner-cc"></a>/nologo (Suppression de la bannière de démarrage) (C/C++)

Supprime l’affichage de la bannière de Copyright au démarrage du compilateur et l’affichage des messages d’information pendant la compilation.

## <a name="syntax"></a>Syntaxe

```
/nologo
```

## <a name="remarks"></a>Notes

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **général** .

1. Modifiez la propriété **Supprimer la bannière de démarrage** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SuppressStartupBanner%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
