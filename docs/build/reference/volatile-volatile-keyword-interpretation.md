---
title: -volatile (interprétation de mot clé volatile) | Documents Microsoft
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
ms.openlocfilehash: ccd36c5edaaab8577e5f278b25b51ce69e0633f1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378195"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (interprétation de mot clé volatile)

Spécifie comment la [volatile](../../cpp/volatile-cpp.md) mot clé doit être interprétée.

## <a name="syntax"></a>Syntaxe

> **/ volatile :**{**iso**|**ms**}  

## <a name="arguments"></a>Arguments

**/volatile:ISO**  
Sélectionne strict `volatile` sémantique, comme défini par le langage de la norme ISO C++. Sémantiques acquire/release ne sont pas garanties sur les accès volatiles. Si le compilateur cible ARM, il s’agit de l’interprétation par défaut de `volatile`.

**/volatile:MS**  
Sélectionne l’étendue Microsoft `volatile` sémantique qui l’ajout de mémoire garantie au-delà de la langue de la norme ISO C++ de classement. Sémantiques acquire/release sont garanties sur les accès volatiles. Toutefois, cette option force également au compilateur de générer des barrières de mémoire matérielle, ce qui peuvent ajouter un surcroît de traitement sur ARM et d’autres architectures de classement de mémoire faibles. Si le compilateur cible n’importe quelle plateforme, à l’exception ARM, il s’agit d’interprétation par défaut de `volatile`.

## <a name="remarks"></a>Notes

Nous vous recommandons fortement d’utiliser **/volatile:iso** , ainsi que des primitives de synchronisation explicites et les intrinsèques du compilateur lorsque vous travaillez avec une mémoire qui est partagée entre plusieurs threads. Pour plus d’informations, consultez [volatile](../../cpp/volatile-cpp.md).

Si vous porter du code existant ou que vous modifiez cette option au milieu d’un projet, il peut être utile d’activer l’avertissement [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) pour identifier les emplacements de code qui sont affectés par la différence de sémantique.

Il existe aucune `#pragma` équivalente pour contrôler cette option.

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>Pour définir le /volatile option de compilateur dans Visual Studio

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Dans le **des options supplémentaires** zone, ajoutez **/volatile:iso** ou **/volatile:ms** , puis **OK** ou **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[volatile](../../cpp/volatile-cpp.md)  
[Options du compilateur](../../build/reference/compiler-options.md)  
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)  
