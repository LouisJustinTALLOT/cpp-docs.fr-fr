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
ms.openlocfilehash: 0808f66c4d4c4e99b3038ea18a1f71f4ebaca89a
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446180"
---
# <a name="zw-windows-runtime-compilation"></a>/ZW (compilation Windows Runtime)

Compile le code pour prendre en charge de Microsoft source C++ extensions du composant C++/CX pour la création d’applications de plateforme universelle Windows (UWP).

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
