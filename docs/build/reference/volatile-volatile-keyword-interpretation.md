---
title: /volatile (interprétation de mot clé volatile)
ms.date: 11/04/2016
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
ms.openlocfilehash: 02871622242930d7419fda16f4d106fccb2056f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316637"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (interprétation de mot clé volatile)

Spécifie comment la [volatile](../../cpp/volatile-cpp.md) mot clé doit être interprétée.

## <a name="syntax"></a>Syntaxe

> **/ volatile :**{**iso**|**ms**}

## <a name="arguments"></a>Arguments

**/volatile:ISO**<br/>
Sélectionne strict `volatile` sémantique tel que défini par le langage de la norme ISO C++. Sémantiques acquire/release ne sont pas garanties sur les accès volatiles. Si le compilateur cible ARM, il s’agit de l’interprétation par défaut de `volatile`.

**/volatile:ms**<br/>
Sélectionne l’étendue Microsoft `volatile` sémantiques que vous ajoutez de la mémoire garantie au-delà de la langue de la norme ISO C++ de classement. Sémantiques acquire/release sont garanties sur les accès volatiles. Toutefois, cette option force également au compilateur de générer des barrières de mémoire matérielle, ce qui peuvent ajouter une surcharge significative sur ARM et d’autres architectures d’ordonnancement de mémoire faibles. Si le compilateur cible une plateforme autre qu’ARM, il s’agit d’interprétation par défaut de `volatile`.

## <a name="remarks"></a>Notes

Nous vous recommandons vivement de vous utilisez **/volatile:iso** , ainsi que des primitives de synchronisation explicites et les intrinsèques du compilateur lorsque vous êtes confronté à la mémoire est partagé entre plusieurs threads. Pour plus d’informations, consultez [volatile](../../cpp/volatile-cpp.md).

Si vous déplacez le code existant ou que vous modifiez cette option au milieu d’un projet, il peut être utile d’activer l’avertissement [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) pour identifier les emplacements de code qui sont affectés par la différence de sémantique.

Il existe aucune `#pragma` équivalent pour contrôler cette option.

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>Pour définir le /volatile option du compilateur dans Visual Studio

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Dans le **des options supplémentaires** zone, ajoutez **/volatile:iso** ou **/volatile:ms** , puis **OK** ou **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[volatile](../../cpp/volatile-cpp.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
