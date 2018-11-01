---
title: /GL (Optimisation de l'ensemble du programme)
ms.date: 11/04/2016
f1_keywords:
- /gl
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
ms.openlocfilehash: 7e9300c6c851eb013d8304bd90e3ca9aa4b2c022
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640819"
---
# <a name="gl-whole-program-optimization"></a>/GL (Optimisation de l'ensemble du programme)

Active l'optimisation de l'ensemble du programme.

## <a name="syntax"></a>Syntaxe

```
/GL[-]
```

## <a name="remarks"></a>Notes

Optimisation de l’ensemble du programme permet au compilateur d’effectuer des optimisations avec des informations sur tous les modules dans le programme. Sans optimisation de l’ensemble du programme, les optimisations sont effectuées sur une application par module (compiland).

Optimisation de l’ensemble du programme est désactivé par défaut et doit être explicitement activée. Toutefois, il est également possible de désactiver explicitement à l’aide **/GL-**.

Avec les informations sur tous les modules, le compilateur peut :

- Optimiser l’utilisation de registres au-delà des limites de fonction.

- Effectuer un meilleur travail de suivi des modifications apportées aux données globales, ce qui permet une réduction du nombre de charges et de magasins.

- Effectuer un meilleur travail de suivi de l’ensemble possible d’éléments modifiés par un pointeur déréférencé, en réduisant le nombre de charges et de magasins.

- Incorporer une fonction dans un module, même lorsque la fonction est définie dans un autre module.

fichiers .obj produits avec **/GL** ne seront pas disponibles pour des utilitaires d’éditeur de liens, tels que [EDITBIN](../../build/reference/editbin-reference.md) et [DUMPBIN](../../build/reference/dumpbin-reference.md).

Si vous compilez votre programme avec **/GL** et [/c](../../build/reference/c-compile-without-linking.md), vous devez utiliser l’option de l’éditeur de liens /LTCG pour créer le fichier de sortie.

[/ Zi](../../build/reference/z7-zi-zi-debug-information-format.md) ne peut pas être utilisé avec **/GL**

Le format des fichiers produits avec **/GL** dans la version actuelle ne peuvent être lisibles par les versions ultérieures de Visual C++. Vous ne devez pas fournir un fichier .lib composé de fichiers .obj qui ont été générées avec **/GL** , sauf si vous êtes disposé à livrer des copies du fichier .lib pour toutes les versions de Visual C++ que les utilisateurs à utiliser, maintenant et à l’avenir.

fichiers .obj produits avec **/GL** et fichiers d’en-tête précompilés ne doivent pas servir à générer un fichier .lib, sauf si le fichier .lib sera lié sur le même ordinateur que celui qui a généré le **/GL** fichier .obj. Pour plus d’informations à partir du fichier d’en-tête précompilé du fichier .obj est nécessaire au moment de la liaison.

Pour plus d’informations sur les optimisations disponibles et les limitations d’optimisation de l’ensemble du programme, consultez [/LTCG](../../build/reference/ltcg-link-time-code-generation.md).  **/GL** également rend Profiler optimisation guidée n’est disponible ; consultez /LTCG.  Lors de la compilation pour les optimisations guidées profil si vous souhaitez classer les fonctions de vos optimisations guidées par profil, vous devez compiler avec [/Gy](../../build/reference/gy-enable-function-level-linking.md) ou une option de compilateur qui implique/Gy.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Consultez [/LTCG (Link-time Code Generation)](../../build/reference/ltcg-link-time-code-generation.md) pour plus d’informations sur la spécification **/GL** dans l’environnement de développement.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)