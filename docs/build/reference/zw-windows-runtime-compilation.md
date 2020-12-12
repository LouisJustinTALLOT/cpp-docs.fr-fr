---
description: En savoir plus sur:/ZW (compilation Windows Runtime)
title: /ZW (compilation Windows Runtime)
ms.date: 04/08/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.CompileAsWinRT
- /zw
helpviewer_keywords:
- /ZW
- -ZW compiler option
- /ZW compiler option
- -ZW
- Windows Runtime compiler option
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
ms.openlocfilehash: b2c39cdfb3f1d22d12c8d07b1e844c550a7a0e3a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273915"
---
# <a name="zw-windows-runtime-compilation"></a>/ZW (compilation Windows Runtime)

Compile le code source pour prendre en charge les extensions de composant Microsoft C++/CX C++ pour la création d’applications plateforme Windows universelle (UWP).

Quand vous utilisez **/ZW** pour compiler, spécifiez toujours **/EHsc** également.

## <a name="syntax"></a>Syntaxe

```cpp
/ZW /EHsc
/ZW:nostdlib /EHsc
```

## <a name="arguments"></a>Arguments

**nostdlib**<br/>
Indique que Platform.winmd, Windows.Foundation.winmd et les autres fichiers de métadonnées Windows par défaut (.winmd) ne sont pas inclus automatiquement dans la compilation. Au lieu de cela, vous devez utiliser l’option de compilateur [/Fu (Name forced #using file)](fu-name-forced-hash-using-file.md) pour spécifier explicitement les fichiers de métadonnées Windows.

## <a name="remarks"></a>Notes

Lorsque vous spécifiez l’option **/ZW** , le compilateur prend en charge les fonctionnalités suivantes :

- Les fichiers de métadonnées requis, les espaces de noms, les types de données et les fonctions nécessaires à l’exécution de votre application dans le Windows Runtime.

- Le décompte de références automatiques des objets Windows Runtime et l’abandon automatique d’un objet quand son décompte de références atteint zéro.

Étant donné que l’éditeur de liens incrémentiel ne prend pas en charge les métadonnées Windows incluses dans les fichiers. obj à l’aide de l’option **/ZW** , l’option [/GM de l’option/GM (activer la régénération minimale)](gm-enable-minimal-rebuild.md) est incompatible avec **/ZW**.

Pour plus d’informations, consultez [Référence du langage Visual C++](../../cppcx/visual-c-language-reference-c-cx.md).

## <a name="requirements"></a>Spécifications

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
