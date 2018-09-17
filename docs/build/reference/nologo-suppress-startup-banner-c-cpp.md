---
title: -nologo (suppression de la bannière de démarrage) (C/C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.SuppressStartupBanner
- VC.Project.VCCLCompilerTool.SuppressStartupBanner
dev_langs:
- C++
helpviewer_keywords:
- -nologo compiler option [C++]
- /nologo compiler option [C++]
- nologo compiler option [C++]
- banners, suppressing startup
ms.assetid: 75930d8b-b11c-4db8-99e5-b52f97da0693
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36f1d1771abb56bd22e8239923fe2e3c15b1588f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711865"
---
# <a name="nologo-suppress-startup-banner-cc"></a>/nologo (Suppression de la bannière de démarrage) (C/C++)

Supprime l’affichage de la bannière de copyright lorsque le compilateur démarre et affiche des messages d’information pendant la compilation.

## <a name="syntax"></a>Syntaxe

```
/nologo
```

## <a name="remarks"></a>Notes

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **général** page de propriétés.

1. Modifier le **supprimer la bannière de démarrage** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SuppressStartupBanner%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)