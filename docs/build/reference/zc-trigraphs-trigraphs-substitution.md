---
title: /Zc:, trigrammes (substitution de trigrammes) (C++)
ms.date: 03/06/2018
f1_keywords:
- /Zc:trigraphs
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: 0e4c98e09551d39e3ff7978767b21f1d2c5bb318
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438649"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:, trigrammes (substitution de trigrammes) (C++)

Quand **/Zc : trigraphes** est spécifié, le compilateur remplace une séquence de caractères trigraphes à l’aide d’un caractère de ponctuation correspondant.

## <a name="syntax"></a>Syntaxe

> **/Zc : trigraphes**[ **-** ]

## <a name="remarks"></a>Notes

Un *trigraphe* se compose de deux points d’interrogation consécutifs («  ?? ») suivis d’un troisième caractère unique. La norme du langage C prend en charge les trigraphes pour les fichiers sources qui utilisent un jeu de caractères qui ne contient pas de représentations graphiques pratiques pour certains caractères de ponctuation. Par exemple, lorsque les trigraphes sont activés, le compilateur remplace le « ?? = "trigraphe à l’aide du caractère' # '. En C++ 14, les trigraphes sont pris en charge comme en C. La norme C++ 17 supprime les C++ trigraphes du langage. Dans C++ le code, l’option de compilateur **/Zc : trigraphes** permet la substitution des séquences de trigraphes par le caractère de ponctuation correspondant. **/Zc : trigraphes-** désactive la substitution de trigraphes.

L’option **/Zc : trigraphes** est désactivée par défaut, et l’option n’est pas affectée quand l’option [/permissive-](permissive-standards-conformance.md) est spécifiée.

Pour obtenir la liste des CC++ /trigraphes, ainsi qu’un exemple qui montre comment utiliser les trigraphes, consultez [trigraphes](../../c-language/trigraphs.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration** > **C/C++**  > **Ligne de commande**.

1. Modifiez la propriété **options supplémentaires** pour inclure **/Zc : trigraphes** ou **/Zc : trigraphes-** , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)<br/>
[Trigraphes](../../c-language/trigraphs.md)<br/>
