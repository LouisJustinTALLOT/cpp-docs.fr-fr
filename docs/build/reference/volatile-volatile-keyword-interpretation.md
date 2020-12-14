---
description: En savoir plus sur:/volatile (interprétation de mot clé volatile)
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
ms.openlocfilehash: e75a9932cff59748cf75b89a3a85e89130de84f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259212"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (interprétation de mot clé volatile)

Spécifie comment le mot clé [volatile](../../cpp/volatile-cpp.md) doit être interprété.

## <a name="syntax"></a>Syntaxe

> **/volatile :**{**ISO** | **MS**}

## <a name="arguments"></a>Arguments

**/volatile : ISO**<br/>
Sélectionne **`volatile`** la sémantique stricte telle que définie par le langage C++ ISO. Les sémantiques Acquire/Release ne sont pas garanties sur les accès volatiles. Si le compilateur cible ARM, il s’agit de l’interprétation par défaut de **`volatile`** .

**/volatile : ms**<br/>
Sélectionne **`volatile`** la sémantique étendue Microsoft, qui ajoute des garanties d’ordonnancement de mémoire au-delà du langage C++ standard ISO. Les sémantiques d’acquisition/libération sont garanties sur les accès volatiles. Toutefois, cette option force également le compilateur à générer des barrières de mémoire matérielle, ce qui peut ajouter une surcharge importante sur ARM et d’autres architectures de classement de mémoire faible. Si le compilateur cible une plateforme à l’exception de ARM, il s’agit de l’interprétation par défaut de **`volatile`** .

## <a name="remarks"></a>Notes

Nous vous recommandons vivement d’utiliser **/volatile : ISO** avec les primitives de synchronisation explicites et les intrinsèques du compilateur lorsque vous travaillez avec de la mémoire partagée par plusieurs threads. Pour plus d’informations, consultez [volatile](../../cpp/volatile-cpp.md).

Si vous portez du code existant ou modifiez cette option au milieu d’un projet, il peut être utile d’activer les [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) d’avertissement pour identifier les emplacements de code qui sont affectés par la différence de sémantique.

Il n’existe aucun `#pragma` équivalent pour contrôler cette option.

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>Pour définir l’option de compilateur/volatile dans Visual Studio

1. Ouvrez la boîte de dialogue **pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >   .

1. Dans la zone **options supplémentaires** , ajoutez **/volatile : ISO** ou **/volatile : ms** , puis choisissez **OK** ou **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[volatile](../../cpp/volatile-cpp.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
