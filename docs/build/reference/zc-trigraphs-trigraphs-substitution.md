---
title: /Zc:, trigrammes (substitution de trigrammes) (C++)
description: Option du compilateur Microsoft C++ qui contrôle la prise en charge de la conformité pour les trigraphes.
ms.date: 07/25/2020
f1_keywords:
- /Zc:trigraphs
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: e24f3d2f0064c3acc04b4c3774f47f6e442d5ddd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211851"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>`/Zc:trigraphs`(Substitution de trigraphes)

Lorsque **`/Zc:trigraphs`** est spécifié, le compilateur remplace une séquence de caractères trigraphes par un caractère de ponctuation correspondant.

## <a name="syntax"></a>Syntaxe

> **`/Zc:trigraphs`**[**`-`**]

## <a name="remarks"></a>Notes

Un *trigraphe* se compose de deux points d’interrogation consécutifs ( **`??`** ) suivis d’un troisième caractère unique. La norme du langage C prend en charge les trigraphes pour les fichiers sources qui utilisent un jeu de caractères qui ne contient pas de représentations graphiques pratiques pour certains caractères de ponctuation. Par exemple, lorsque les trigraphes sont activés, le compilateur remplace le **`??=`** trigraphe à l’aide du **`#`** caractère. En C++ 14, les trigraphes sont pris en charge comme en C. La norme C++ 17 supprime les trigraphes du langage C++. Dans le code C++, l' **`/Zc:trigraphs`** option de compilateur active la substitution des séquences de trigraphes par le caractère de ponctuation correspondant. **`/Zc:trigraphs-`** désactive la substitution de trigraphe.

L' **`/Zc:trigraphs`** option est désactivée par défaut, et l’option n’est pas affectée lorsque l' [`/permissive-`](permissive-standards-conformance.md) option est spécifiée.

Pour obtenir la liste des trigraphes C/C++ et un exemple qui montre comment utiliser les trigraphes, consultez [trigraphes](../../c-language/trigraphs.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Modifiez la propriété **options supplémentaires** pour inclure **`/Zc:trigraphs`** ou **`/Zc:trigraphs-`** , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[`/Zc`Conformité](zc-conformance.md)<br/>
[Trigraphes](../../c-language/trigraphs.md)
