---
description: En savoir plus sur:/GZ (activer le frame de pile Run-Time la vérification des erreurs)
title: /GZ (Activer les vérifications des erreurs au moment de l'exécution pour le frame de pile)
ms.date: 11/04/2016
f1_keywords:
- /gz
helpviewer_keywords:
- -GZ compiler option [C++]
- release-build errors
- /GZ compiler option [C++]
- GZ compiler option [C++]
- debug builds, catch release-build errors
ms.assetid: b3efeeff-d5e3-4057-91c9-f6fc73d0270c
ms.openlocfilehash: 0b0936037c265bf57413c458ffc0a831184cb074
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191691"
---
# <a name="gz-enable-stack-frame-run-time-error-checking"></a>/GZ (Activer les vérifications des erreurs au moment de l'exécution pour le frame de pile)

Effectue les mêmes opérations que l’option [/RTC (vérifications des erreurs au moment de l’exécution)](rtc-run-time-error-checks.md) . Action déconseillée.

## <a name="syntax"></a>Syntaxe

```
/GZ
```

## <a name="remarks"></a>Notes

**/Gz** est uniquement destiné à une utilisation dans une build non optimisée ([/OD (Disable (Debug)](od-disable-debug.md))).

**/Gz** est déconseillé depuis Visual Studio 2005 ; Utilisez [à la place/RTC (vérifications des erreurs au moment de l’exécution)](rtc-run-time-error-checks.md) . Pour obtenir la liste des options du compilateur déconseillées, consultez **Options du compilateur déconseillées et supprimées** dans [Options du compilateur classées par catégorie](compiler-options-listed-by-category.md).

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
