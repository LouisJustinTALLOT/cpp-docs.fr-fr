---
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
ms.openlocfilehash: 73295866004fd506fd5f06ff25c048d14b821016
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59424038"
---
# <a name="zw-windows-runtime-compilation"></a>/ZW (compilation Windows Runtime)

Compile le code pour prendre en charge les extensions du composant C++ de Visual C++ / source c++ / CX pour la création d’applications de plateforme universelle Windows (UWP).

Lorsque vous utilisez **/ZW** pour compiler, spécifiez toujours **/EHsc** également.

## <a name="syntax"></a>Syntaxe

```cpp
/ZW /EHsc
/ZW:nostdlib /EHsc
```

## <a name="arguments"></a>Arguments

**nostdlib**<br/>
Indique que Platform.winmd, Windows.Foundation.winmd et les autres fichiers de métadonnées Windows par défaut (.winmd) ne sont pas inclus automatiquement dans la compilation. Au lieu de cela, vous devez utiliser le [/FU (nom du #using fichier)](fu-name-forced-hash-using-file.md) option du compilateur pour spécifier explicitement les fichiers de métadonnées Windows.

## <a name="remarks"></a>Notes

Lorsque vous spécifiez le **/ZW** option, le compilateur prend en charge ces fonctionnalités :

- Fichiers de métadonnées requis, espaces de noms, types de données et les fonctions dont votre application a besoin pour s’exécutent dans le Windows Runtime.

- Le comptage de références d’objets Windows Runtime et automatique l’abandon d’un objet lorsque son décompte de références atteint zéro.

Étant donné que l’éditeur de liens incrémentielle ne prend pas en charge les métadonnées Windows incluses dans les fichiers .obj à l’aide de la **/ZW** option déconseillées [/Gm (activer la régénération minimale)](gm-enable-minimal-rebuild.md) option n’est pas compatible avec **/ZW**.

Pour plus d’informations, consultez [référence du langage Visual C++](../../cppcx/visual-c-language-reference-c-cx.md).

## <a name="requirements"></a>Configuration requise

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
