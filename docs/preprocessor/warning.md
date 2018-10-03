---
title: avertissement | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- warning_CPP
- vc-pragma.warning
dev_langs:
- C++
helpviewer_keywords:
- pragmas, warning
- push pragma warning
- pop warning pragma
- warning pragma
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 90cb11a6e6ab0c088c0b2425856d61556e76564c
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234630"
---
# <a name="warning-pragma"></a>Warning (pragma)
Active la modification sélective du comportement des messages d'avertissement du compilateur.

## <a name="syntax"></a>Syntaxe

```
#pragma warning(
    warning-specifier : warning-number-list [; warning-specifier : warning-number-list...] )
#pragma warning( push[ ,n ] )
#pragma warning( pop )
```

## <a name="remarks"></a>Notes

Les paramètres spécificateur-avertissement suivants sont disponibles.

|spécificateur-avertissement|Signification|
|------------------------|-------------|
|*1, 2, 3, 4*|Applique le niveau donné du ou des avertissements spécifiés. Cela active également un avertissement spécifié qui est désactivé par défaut.|
|*default*|Réinitialise le comportement d'avertissement à sa valeur par défaut. Cela active également un avertissement spécifié qui est désactivé par défaut. L'avertissement est généré à son niveau par défaut, documenté.<br /><br /> Pour plus d’informations, consultez [avertissements du compilateur désactivés par défaut](../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|*disable*|Ne publie pas le ou les messages d'avertissement spécifiés.|
|*Erreur*|Signale les avertissements spécifiés comme des erreurs.|
|*once*|Affiche le ou les messages spécifiés une seule fois.|
|*supprimer*|Exécute un push de l'état actuel du pragma sur la pile, désactive l'avertissement spécifié pour la ligne suivante, puis dépile la pile d'avertissement afin que l'état pragma soit réinitialisé.|

L'instruction de code suivante montre qu'un paramètre `warning-number-list` peut contenir plusieurs numéros d'avertissement, et que plusieurs paramètres `warning-specifier` peuvent être spécifiés dans la même directive pragma.

```cpp
#pragma warning( disable : 4507 34; once : 4385; error : 164 )
```

Cela équivaut fonctionnellement au code suivant.

```cpp
// Disable warning messages 4507 and 4034.
#pragma warning( disable : 4507 34 )

// Issue warning 4385 only once.
#pragma warning( once : 4385 )

// Report warning 4164 as an error.
#pragma warning( error : 164 )
```

Le compilateur ajoute 4000 à n'importe quel numéro d'avertissement compris entre 0 et 999.

Pour les numéros d'avertissement dans la plage 4700-4999 qui sont associés à la génération du code, l'état d'avertissement en vigueur lorsque le compilateur rencontre l'accolade ouvrante d'une fonction est appliquée pour le reste de la fonction. À l’aide de la **avertissement** pragma dans la fonction pour modifier l’état d’un avertissement qui a un nombre supérieur à 4699 entre en vigueur uniquement après la fin de la fonction. L’exemple suivant montre le positionnement correct de **avertissement** pragmas pour désactiver un message d’avertissement de génération de code, puis de le restaurer.

```cpp
// pragma_warning.cpp
// compile with: /W1
#pragma warning(disable:4700)
void Test() {
   int x;
   int y = x;   // no C4700 here
   #pragma warning(default:4700)   // C4700 enabled after Test ends
}

int main() {
   int x;
   int y = x;   // C4700
}
```

Notez que, tout au long d’une fonction, le corps, le dernier paramètre de la **avertissement** pragma sera appliquée à la fonction entière.

## <a name="push-and-pop"></a>Push et pop

Le **avertissement** pragma prend également en charge la syntaxe suivante, où *n* représente un niveau d’avertissement (1 à 4).

`#pragma warning( push [ , n ] )`

`#pragma warning( pop )`

Le pragma `warning( push )` stocke l’état d’avertissement actuel pour chaque avertissement. Le pragma `warning( push, n )` stocke l’état actuel pour chaque avertissement et définit le niveau d’avertissement global sur *n*.

Le pragma `warning( pop )` POP le dernier état d’avertissement est placé sur la pile. Toutes les modifications que vous avez apportées à l’état d’avertissement entre *push* et *pop* sont annulées. Considérez cet exemple :

```cpp
#pragma warning( push )
#pragma warning( disable : 4705 )
#pragma warning( disable : 4706 )
#pragma warning( disable : 4707 )
// Some code
#pragma warning( pop )
```

À la fin de ce code, *pop* restaure l’état de chaque avertissement (inclut 4705, 4706 et 4707) à ce qu’il était au début du code.

Lorsque vous écrivez des fichiers d’en-tête, vous pouvez utiliser *push* et *pop* afin de garantir que les modifications d’état d’avertissement apportées par un utilisateur n’empêchent pas les en-têtes de se compiler correctement. Utilisez *push* au début de l’en-tête et *pop* à la fin. Par exemple, si vous avez un en-tête qui ne se compile pas correctement au niveau de l'avertissement 4, le code suivant remplace le niveau d'avertissement par 3, puis restaure le niveau d'avertissement d'origine à la fin de l'en-tête.

```cpp
#pragma warning( push, 3 )
// Declarations/definitions
#pragma warning( pop )
```

Pour plus d’informations sur les options qui vous aident à suppriment de compilateur des avertissements, consultez [/FI](../build/reference/fi-name-forced-include-file.md) et [/w](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)