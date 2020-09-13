---
title: '/experimental : préprocesseur (activer le mode de conformité de préprocesseur)'
description: 'Utilisez l’option du compilateur de préprocesseur/experimental : pour activer la prise en charge expérimentale du compilateur pour un préprocesseur conforme au standard.'
ms.date: 09/10/2020
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: 9a98289434e7154d2ec8b8753d990876a8218acf
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042093"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>`/experimental:preprocessor` (Activer le mode de conformité de préprocesseur)

Cette option est obsolète à compter de Visual Studio 2019 version 16,5, remplacée par l' [`/Zc:preprocessor`](zc-preprocessor.md) option du compilateur. **`/experimental:preprocessor`** active un préprocesseur expérimental basé sur des jetons qui est plus conforme aux normes C++ 11, y compris les fonctionnalités du préprocesseur C99. Pour plus d’informations, consultez [vue d’ensemble du nouveau préprocesseur MSVC](../../preprocessor/preprocessor-experimental-overview.md).

## <a name="syntax"></a>Syntaxe

> **`/experimental:preprocessor`**\[**`-`**]

## <a name="remarks"></a>Remarques

Utilisez l' **`/experimental:preprocessor`** option du compilateur pour activer le préprocesseur conforme expérimental. Vous pouvez utiliser **`/experimental:preprocessor-`** l’option pour spécifier explicitement le préprocesseur traditionnel.

L' **`/experimental:preprocessor`** option est disponible à partir de Visual Studio 2017 version 15,8. À compter de Visual Studio 2019 version 16,5, le nouveau préprocesseur est terminé et est disponible sous l' [`/Zc:preprocessor`](zc-preprocessor.md) option du compilateur.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Modifiez la propriété **options supplémentaires** pour inclure *`/experimental:preprocessor`* , puis cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)
