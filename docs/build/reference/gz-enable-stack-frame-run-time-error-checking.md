---
title: -GZ (activer la pile des vérifications des erreurs d’exécution Frame) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gz
dev_langs:
- C++
helpviewer_keywords:
- -GZ compiler option [C++]
- release-build errors
- /GZ compiler option [C++]
- GZ compiler option [C++]
- debug builds, catch release-build errors
ms.assetid: b3efeeff-d5e3-4057-91c9-f6fc73d0270c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f13824064b7c7dcdb75524a22b14a4d90942918
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707217"
---
# <a name="gz-enable-stack-frame-run-time-error-checking"></a>/GZ (Activer les vérifications des erreurs au moment de l'exécution pour le frame de pile)

Effectue les mêmes opérations que le [/RTC (vérifications des erreurs au moment de l’exécution)](../../build/reference/rtc-run-time-error-checks.md) option. Obsolète.

## <a name="syntax"></a>Syntaxe

```
/GZ
```

## <a name="remarks"></a>Notes

**/GZ** doit uniquement être utilisée dans un code ([/Od (désactiver (débogage))](../../build/reference/od-disable-debug.md)) générer.

**/GZ** est déconseillée depuis Visual Studio 2005 ; utiliser [/RTC (vérifications des erreurs au moment de l’exécution)](../../build/reference/rtc-run-time-error-checks.md) à la place. Pour obtenir la liste des options du compilateur déconseillées, consultez **Options déconseillées et supprimées du compilateur** dans [Options du compilateur classées par catégorie](../../build/reference/compiler-options-listed-by-category.md).

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