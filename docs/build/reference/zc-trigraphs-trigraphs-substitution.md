---
title: /Zc:, trigrammes (substitution de trigrammes) (C++)
ms.date: 03/06/2018
f1_keywords:
- /Zc
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: 7a20123603030dfe719cd8990018f795df137981
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316000"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:, trigrammes (substitution de trigrammes) (C++)

Lorsque **/Zc : trigraphs** est spécifié, le compilateur remplace une séquence de caractères (trigraphe) à l’aide d’un caractère de ponctuation correspondant.

## <a name="syntax"></a>Syntaxe

> **/Zc:trigraphs**[**-**]

## <a name="remarks"></a>Notes

Un *trigraphe* se compose de deux points d’interrogation consécutifs (« ?? ») suivi d’un troisième caractère unique. La norme du langage C prend en charge des trigraphes pour les fichiers sources qui utilisent un jeu de caractères qui ne contient-elle pas de représentation graphique pour certains caractères de ponctuation. Par exemple, lorsque les trigraphes sont activées, le compilateur remplace le « ?? = « trigraphe en utilisant le caractère « # ». Jusqu'à C ++ 14, trigraphes sont pris en charge, comme dans C. La norme C ++ 17 supprime les trigraphes du langage C++. Dans le code C++, le **/Zc : trigraphs** option du compilateur permet la substitution des séquences de trigraphe par le caractère de ponctuation correspondant. **/Zc:trigraphs-** désactive la substitution de trigrammes.

Le **/Zc : trigraphs** option est désactivée par défaut, et l’option n’est pas affecté lorsque le [/ permissive-](permissive-standards-conformance.md) option est spécifiée.

Pour obtenir la liste des trigraphes de C/C++ et un exemple qui montre comment utiliser des trigraphes, consultez [trigraphes](../../c-language/trigraphs.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier le **des Options supplémentaires** propriété à inclure **/Zc : trigraphs** ou **/Zc:trigraphs-** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)<br/>
[Trigraphes](../../c-language/trigraphs.md)<br/>
