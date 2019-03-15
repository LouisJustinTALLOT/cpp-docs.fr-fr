---
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
ms.openlocfilehash: a5eb6a10f3c4833ecc3e9d9c8451894788ebd938
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817380"
---
# <a name="ga-optimize-for-windows-application"></a>/GA (Optimiser pour une application Windows)

Génère du code plus efficace pour un fichier .exe pour accéder aux variables de stockage local des threads (TLS).

## <a name="syntax"></a>Syntaxe

```
/GA
```

## <a name="remarks"></a>Notes

**/GA** accélère l’accès aux données déclarées avec [__declspec (thread)](../../cpp/declspec.md) dans un programme basé sur Windows. Lorsque cette option est définie, le [__tls_index a la valeur](/windows/desktop/ProcThread/thread-local-storage) macro est censée pour avoir la valeur 0.

À l’aide de **/GA** pour une DLL peut entraîner la génération de code incorrecte.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
