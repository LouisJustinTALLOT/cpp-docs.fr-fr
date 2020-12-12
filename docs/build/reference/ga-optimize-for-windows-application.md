---
description: En savoir plus sur:/GA (optimiser pour une application Windows)
title: /GA (Optimiser pour une application Windows)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication
- /ga
helpviewer_keywords:
- /GA compiler option [C++]
- GA compiler option [C++]
- -GA compiler option [C++]
- Optimize for Windows compiler options
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
ms.openlocfilehash: f9d65dce26e80b585abc4d67e2eef55f10cb365b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191977"
---
# <a name="ga-optimize-for-windows-application"></a>/GA (Optimiser pour une application Windows)

Permet d’obtenir un code plus efficace pour un fichier. exe pour l’accès aux variables de stockage local des threads (TLS).

## <a name="syntax"></a>Syntaxe

```
/GA
```

## <a name="remarks"></a>Notes

**/GA** accélère l’accès aux données déclarées avec [__declspec (thread)](../../cpp/declspec.md) dans un programme Windows. Lorsque cette option est définie, la macro [__tls_index](/windows/win32/ProcThread/thread-local-storage) est supposée être 0.

L’utilisation de **/GA** pour une dll peut entraîner une génération de code incorrecte.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
