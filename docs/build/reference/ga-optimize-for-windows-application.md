---
title: -GA (optimiser pour une Application de Windows) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication
- /ga
dev_langs:
- C++
helpviewer_keywords:
- /GA compiler option [C++]
- GA compiler option [C++]
- -GA compiler option [C++]
- Optimize for Windows compiler options
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ef8aaf1e2b3f1dd75f7ca2669aaf09f3d121a98
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710058"
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

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)