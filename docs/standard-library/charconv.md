---
title: '&lt;charconv&gt;'
ms.date: 07/22/2020
f1_keywords:
- <charconv>
helpviewer_keywords:
- charconv header
ms.openlocfilehash: c9dfb8e18a8f7fd367ec4f6b52b1a0af74b3f939
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507714"
---
# <a name="ltcharconvgt"></a>&lt;charconv&gt;

Convertissez rapidement une séquence de caractères en une valeur entière ou à virgule flottante, et inversement.
L’une des façons d’utiliser cette bibliothèque est d’écrire et d’aller-retour des valeurs à virgule flottante dans des fichiers JSON et texte.

Les fonctions de conversion sont optimisées pour les performances et prennent également en charge le comportement des allers-retours les plus courts. Le comportement d’aller-retour le plus court signifie que lorsqu’un nombre est converti en caractères, seule une précision suffisante est écrite pour permettre la récupération du nombre d’origine lors de la conversion de ces caractères en virgule flottante. Aucune autre fonction CRT ou STL n’offre cette fonctionnalité.

Voici quelques-uns des avantages de l’utilisation de la `<charconv>` bibliothèque :

- La séquence de caractères représentant une valeur numérique n’a pas besoin d’être terminée par un caractère null. De même, lorsqu’un nombre est converti en caractères, le résultat n’est pas terminé par le caractère null.
- Les fonctions de conversion n’allouent pas de mémoire. Vous êtes propriétaire de la mémoire tampon dans tous les cas.
- Les fonctions de conversion ne lèvent pas d’exception. Elles retournent une structure qui contient des informations sur les erreurs.
- Les conversions ne sont pas sensibles au mode d’arrondi du Runtime.
- Les conversions ne prennent pas en charge les paramètres régionaux. Ils impriment et analysent toujours les points décimaux comme'. 'jamais comme', 'pour les paramètres régionaux qui utilisent des virgules.

## <a name="requirements"></a>Configuration requise

**En-tête :**\<charconv>

**Espace de noms :** std

/std : c++ 17, ou version ultérieure, est requis.

## <a name="members"></a>Membres

### <a name="types"></a>Types

| Type | Description |
|-|:-|
| [chars_format](chars-format-class.md) | Spécifie le type de mise en forme, par exemple scientifique, Hex, etc. |
| [from_chars_result](from-chars-result-structure.md) | Contient le résultat d’une `from_chars` conversion. |
| [to_chars_result](to-chars-result-structure.md) | Contient le résultat d’une `to_chars` conversion. |

### <a name="functions"></a>Fonctions

| Fonction | Description |
|-|:-|
| [from_chars](charconv-functions.md#from_chars) | Convertit des caractères en entier, float ou double. |
| [to_chars](charconv-functions.md#to_chars)| Convertit un entier, un float ou un double en caractères. |

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](cpp-standard-library-header-files.md)
