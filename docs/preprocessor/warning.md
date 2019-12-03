---
title: warning (pragma)
ms.date: 08/29/2019
f1_keywords:
- warning_CPP
- vc-pragma.warning
helpviewer_keywords:
- pragmas, warning
- push pragma warning
- pop warning pragma
- warning pragma
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
ms.openlocfilehash: c6c9668f614f932b0a96f30ad3e0395e39ddc400
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683341"
---
# <a name="warning-pragma"></a>warning (pragma)

Active la modification sélective du comportement des messages d'avertissement du compilateur.

## <a name="syntax"></a>Syntaxe

> **avertissement de #pragma (** \
> &nbsp;&nbsp;&nbsp;&nbsp;*Warning-specifier* **:** *Warning-Number-List*\
> &nbsp;&nbsp;&nbsp;&nbsp;[ **;** *Warning-specifier* **:** *Warning-Number-List* ...] **)** \
> **Avertissement #pragma (push** [ **,** *n* ] **)** \
> **AVERTISSEMENT #pragma (POP)**

## <a name="remarks"></a>Notes

Les paramètres spécificateur-avertissement suivants sont disponibles.

|spécificateur-avertissement|Signification|
|------------------------|-------------|
|*1, 2, 3, 4*|Applique le niveau donné du ou des avertissements spécifiés. Active également un avertissement spécifié qui est désactivé par défaut.|
|*default*|Réinitialise le comportement d'avertissement à sa valeur par défaut. Active également un avertissement spécifié qui est désactivé par défaut. L'avertissement est généré à son niveau par défaut, documenté.<br /><br /> Pour plus d’informations, consultez [avertissements du compilateur désactivés par défaut](../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|*désactive*|N’émettez pas le ou les messages d’avertissement spécifiés.|
|*Erreurs*|Signale les avertissements spécifiés comme des erreurs.|
|*once*|Affiche le ou les messages spécifiés une seule fois.|
|*supprimer*|Exécute un push de l'état actuel du pragma sur la pile, désactive l'avertissement spécifié pour la ligne suivante, puis dépile la pile d'avertissement afin que l'état pragma soit réinitialisé.|

L'instruction de code suivante montre qu'un paramètre `warning-number-list` peut contenir plusieurs numéros d'avertissement, et que plusieurs paramètres `warning-specifier` peuvent être spécifiés dans la même directive pragma.

```cpp
#pragma warning( disable : 4507 34; once : 4385; error : 164 )
```

Cette directive est fonctionnellement équivalente au code suivant :

```cpp
// Disable warning messages 4507 and 4034.
#pragma warning( disable : 4507 34 )

// Issue warning 4385 only once.
#pragma warning( once : 4385 )

// Report warning 4164 as an error.
#pragma warning( error : 164 )
```

Le compilateur ajoute 4000 à n'importe quel numéro d'avertissement compris entre 0 et 999.

Pour les numéros d’avertissement dans la plage 4700-4999, qui sont ceux associés à la génération de code, l’état de l’avertissement en vigueur lorsque le compilateur rencontre la définition de fonction est appliqué pour le reste de la fonction. L’utilisation du pragma **Warning** dans la fonction pour modifier l’état d’un nombre d’avertissements supérieur à 4699 ne prend effet qu’après la fin de la fonction. L’exemple suivant montre le positionnement correct des pragmas d' **Avertissement** pour désactiver un message d’avertissement de génération de code, puis pour le restaurer.

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

Notez que dans le corps d’une fonction, le dernier paramètre du pragma **Warning** sera appliqué à la fonction entière.

## <a name="push-and-pop"></a>Push et pop

Le pragma **Warning** prend également en charge la syntaxe suivante, où *n* représente un niveau d’avertissement (1 à 4).

`#pragma warning( push [ , n ] )`

`#pragma warning( pop )`

Le pragma `warning( push )` stocke l’état d’avertissement actuel pour chaque avertissement. Le pragma `warning( push, n )` stocke l’état actuel pour chaque avertissement et définit le niveau d’avertissement global sur *n*.

Le pragma `warning( pop )` dépile le dernier état d’avertissement envoyé sur la pile. Toutes les modifications que vous avez apportées à l’état d’avertissement entre les opérations *Push* et *pop* sont annulées. Considérez cet exemple :

```cpp
#pragma warning( push )
#pragma warning( disable : 4705 )
#pragma warning( disable : 4706 )
#pragma warning( disable : 4707 )
// Some code
#pragma warning( pop )
```

À la fin de ce code, *pop* restaure l’état de chaque avertissement (y compris 4705, 4706 et 4707) à ce qu’il était au début du code.

Lorsque vous écrivez des fichiers d’en-tête, vous pouvez utiliser *Push* et *pop* pour garantir que les modifications de l’état d’avertissement effectuées par un utilisateur n’empêchent pas les en-têtes de se compiler correctement. Utilisez *Push* au début de l’en-tête et *Dépilez* à la fin. Par exemple, si vous avez un en-tête qui ne se compile pas correctement au niveau d’avertissement 4, le code suivant modifie le niveau d’avertissement à 3, puis restaure le niveau d’avertissement d’origine à la fin de l’en-tête.

```cpp
#pragma warning( push, 3 )
// Declarations/definitions
#pragma warning( pop )
```

Pour plus d’informations sur les options du compilateur qui vous aident à supprimer les avertissements, consultez [/fi](../build/reference/fi-name-forced-include-file.md) et [/w](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
