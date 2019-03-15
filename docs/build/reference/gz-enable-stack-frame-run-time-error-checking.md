---
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
ms.openlocfilehash: 3e6ffce487cc8183e45f3a911e7060ea22b28216
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810495"
---
# <a name="gz-enable-stack-frame-run-time-error-checking"></a>/GZ (Activer les vérifications des erreurs au moment de l'exécution pour le frame de pile)

Effectue les mêmes opérations que le [/RTC (vérifications des erreurs au moment de l’exécution)](rtc-run-time-error-checks.md) option. Obsolète.

## <a name="syntax"></a>Syntaxe

```
/GZ
```

## <a name="remarks"></a>Notes

**/GZ** doit uniquement être utilisée dans un code ([/Od (désactiver (débogage))](od-disable-debug.md)) générer.

**/GZ** est déconseillée depuis Visual Studio 2005 ; utiliser [/RTC (vérifications des erreurs au moment de l’exécution)](rtc-run-time-error-checks.md) à la place. Pour obtenir la liste des options du compilateur déconseillées, consultez **Options déconseillées et supprimées du compilateur** dans [Options du compilateur classées par catégorie](compiler-options-listed-by-category.md).

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
