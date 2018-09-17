---
title: -volatile (interprétation de mot clé volatile) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
dev_langs:
- C++
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4204d602d1390bf30080a800174426513faf0467
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723630"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (interprétation de mot clé volatile)

Spécifie comment la [volatile](../../cpp/volatile-cpp.md) mot clé doit être interprétée.

## <a name="syntax"></a>Syntaxe

> **/ volatile :**{**iso**|**ms**}

## <a name="arguments"></a>Arguments

**/volatile:ISO**<br/>
Sélectionne strict `volatile` sémantique tel que défini par le langage de la norme ISO C++. Sémantiques acquire/release ne sont pas garanties sur les accès volatiles. Si le compilateur cible ARM, il s’agit de l’interprétation par défaut de `volatile`.

**/volatile:MS**<br/>
Sélectionne l’étendue Microsoft `volatile` sémantiques que vous ajoutez de la mémoire garantie au-delà de la langue de la norme ISO C++ de classement. Sémantiques acquire/release sont garanties sur les accès volatiles. Toutefois, cette option force également au compilateur de générer des barrières de mémoire matérielle, ce qui peuvent ajouter une surcharge significative sur ARM et d’autres architectures d’ordonnancement de mémoire faibles. Si le compilateur cible une plateforme autre qu’ARM, il s’agit d’interprétation par défaut de `volatile`.

## <a name="remarks"></a>Notes

Nous vous recommandons vivement de vous utilisez **/volatile:iso** , ainsi que des primitives de synchronisation explicites et les intrinsèques du compilateur lorsque vous êtes confronté à la mémoire est partagé entre plusieurs threads. Pour plus d’informations, consultez [volatile](../../cpp/volatile-cpp.md).

Si vous déplacez le code existant ou que vous modifiez cette option au milieu d’un projet, il peut être utile d’activer l’avertissement [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) pour identifier les emplacements de code qui sont affectés par la différence de sémantique.

Il existe aucune `#pragma` équivalent pour contrôler cette option.

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>Pour définir le /volatile option du compilateur dans Visual Studio

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Dans le **des options supplémentaires** zone, ajoutez **/volatile:iso** ou **/volatile:ms** , puis **OK** ou **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[volatile](../../cpp/volatile-cpp.md)<br/>
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
