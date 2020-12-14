---
description: En savoir plus sur:/GL (optimisation de l’ensemble du programme)
title: /GL (Optimisation de l'ensemble du programme)
ms.date: 11/04/2016
f1_keywords:
- /gl
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
ms.openlocfilehash: ad42eaeeacf897686831c9b415aa62026b5644f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200193"
---
# <a name="gl-whole-program-optimization"></a>/GL (Optimisation de l'ensemble du programme)

Active l'optimisation de l'ensemble du programme.

## <a name="syntax"></a>Syntaxe

```
/GL[-]
```

## <a name="remarks"></a>Notes

L’optimisation de l’ensemble du programme permet au compilateur d’effectuer des optimisations avec des informations sur tous les modules du programme. Sans l’optimisation de l’ensemble du programme, les optimisations sont effectuées sur une base par module (compiland).

L’optimisation de l’ensemble du programme est désactivée par défaut et doit être explicitement activée. Toutefois, il est également possible de le désactiver explicitement avec **/GL-**.

Avec les informations de tous les modules, le compilateur peut :

- Optimisez l’utilisation des registres à travers les limites des fonctions.

- Améliorez le suivi des modifications apportées aux données globales, ce qui permet de réduire le nombre de charges et de magasins.

- Améliorez le suivi de l’ensemble d’éléments possibles modifié par un déréférencement de pointeur, réduisant ainsi le nombre de charges et de magasins.

- Inline une fonction dans un module même lorsque la fonction est définie dans un autre module.

les fichiers. obj produits avec **/GL** ne seront pas disponibles pour ces utilitaires de l’éditeur de liens comme [EDITBIN](editbin-reference.md) et [DUMPBIN](dumpbin-reference.md).

Si vous compilez votre programme avec **/GL** et [/c](c-compile-without-linking.md), vous devez utiliser l’option de l’éditeur de liens/LTCG pour créer le fichier de sortie.

[/Zi](z7-zi-zi-debug-information-format.md) ne peut pas être utilisé avec **/GL**

Le format des fichiers générés avec **/GL** dans la version actuelle n’est peut-être pas lisible par les versions ultérieures de Visual C++. Vous ne devez pas envoyer un fichier. lib constitué de fichiers. obj générés avec **/GL** , à moins que vous ne souhaitiez expédier des copies du fichier. lib pour toutes les versions de Visual C++ que vos utilisateurs vous attendent à utiliser, maintenant et à l’avenir.

les fichiers. obj produits avec **/GL** et les fichiers d’en-tête précompilés ne doivent pas être utilisés pour générer un fichier. lib, sauf si le fichier. lib est lié sur le même ordinateur qui a produit le fichier **/GL** . obj. Les informations du fichier d’en-tête précompilé du fichier. obj seront nécessaires au moment de la liaison.

Pour plus d’informations sur les optimisations disponibles avec et sur les limitations de l’optimisation de l’ensemble du programme, consultez [/LTCG](ltcg-link-time-code-generation.md).  **/GL** rend également disponible l’optimisation guidée par profil ; voir/LTCG.  Lors de la compilation des optimisations guidées par profil et si vous souhaitez classer les fonctions à partir de vos optimisations guidées par profil, vous devez compiler avec [/Gy](gy-enable-function-level-linking.md) ou une option du compilateur qui implique/Gy.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Pour plus d’informations sur la spécification de **/GL** dans l’environnement de développement [, consultez/LTCG (génération de code durant l’édition de liens)](ltcg-link-time-code-generation.md) .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
