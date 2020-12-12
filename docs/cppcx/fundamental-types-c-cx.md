---
description: 'En savoir plus sur : types fondamentaux (C++/CX)'
title: Types fondamentaux (C++/CX)
ms.date: 01/22/2017
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
ms.openlocfilehash: 40e0a849d0b838f53ddaea26c8993dcfe625ed5d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321003"
---
# <a name="fundamental-types-ccx"></a>Types fondamentaux (C++/CX)

En plus des types intégrés C++ standard, C++/CX prend en charge le système de type défini par l’architecture Windows Runtime en fournissant des typedefs pour les types fondamentaux Windows Runtime qui correspondent aux types C++ standard. C++/CX implémente les types fondamentaux booléens, caractère et numérique. Ces typedefs sont définis dans l’espace de noms `default` qui ne doit jamais être spécifié explicitement. En outre, C++/CX fournit des wrappers et des implémentations concrètes pour certains types et interfaces Windows Runtime.

## <a name="boolean-and-character-types"></a>Types booléens et de caractère

Le tableau suivant répertorie les types intégrés booléens et de caractère, et leurs équivalents C++ standard.

|Espace de noms|Nom de/CX C++|Définition|Nom C++ standard|Plage de valeurs|
|---------------|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|Plateforme|Boolean|Valeur booléenne de 8 bits.|bool|**`true`** (différent de zéro) et **`false`** (zéro)|
|default|char16|Valeur non numérique 16 bits qui représente un point de code Unicode (UTF-16).|wchar_t<br /><br /> -ou-<br /><br /> L’c’|(Spécifié par la norme Unicode)|

## <a name="numeric-types"></a>Types valeurs numériques

Le tableau suivant répertorie les types numériques intégrés. Les types numériques sont déclarés dans l’espace de noms `default` et sont des typedefs pour le type intégré C++ correspondant. Tous les types intégrés C++ (long, par exemple) ne sont pas pris en charge dans le Windows Runtime. Pour des fins de cohérence et de clarté, nous vous recommandons d’utiliser le nom C++/CX.

|Nom de/CX C++|Définition|Nom C++ standard|Plage de valeurs|
|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|int8|Valeur numérique signée 8 bits.|signed char|-128 à 127|
|uint8|Valeur numérique non signée 8 bits.|unsigned char|De 0 à 255|
|int16|Entier signé 16 bits.|short|-32 768 à 32 767|
|uint16|Entier non signé 16 bits.|unsigned short|De 0 à 65 535|
|int32|Entier signé 32 bits.|int|-2 147 483 648 à 2 147 483 647|
|uint32|Entier non signé 32 bits.|nombre entier non signé|De 0 à 4 294 967 295|
|int64|Entier signé 64 bits.|long-ou-__int64|-9 223 372 036 854, 775 808 à 9 223 372 036 854 775 807|
|uint64|Entier 64 bits non signé.|unsigned long-or-unsigned long __int64|De 0 à 18 446 744 073 709 551 615|
|float32|Nombre à virgule flottante IEEE 754 32 bits.|float|3.4E +/- 38 (7 chiffres)|
|float64|Nombre à virgule flottante IEEE 754 64 bits.|double|1.7E +/- 308 (15 chiffres)|

## <a name="windows-runtime-types"></a>Types de Windows Runtime

Le tableau suivant répertorie certains types supplémentaires qui sont définis par l’architecture Windows Runtime et qui sont intégrés à C++/CX. Object et String sont des types référence. Tous les autres sont des types valeur. Tous ces types sont déclarés dans l’espace de noms `Platform` . Pour obtenir une liste complète, consultez [Platform namespace](../cppcx/platform-namespace-c-cx.md).

|Nom|Définition|
|----------|----------------|
|Object|Représente tout type de Windows Runtime.|
|Chaîne|Série de caractères représentant du texte.|
|Rect|Ensemble de quatre nombres à virgule flottante représentant l’emplacement et la taille d’un rectangle.|
|SizeT|Paire ordonnée de nombres à virgule flottante qui spécifient la hauteur et la largeur.|
|Point|Paire ordonnée de coordonnées x et y à virgule flottante qui définissent un point dans un plan à deux dimensions.|
|Guid|Valeur non numérique 128 bits utilisée comme identificateur unique.|
|UIntPtr|(À usage interne uniquement.) Valeur 64 bits non signée qui est utilisée comme pointeur.|
|IntPtr|(À usage interne uniquement.)  Valeur 64 bits signée qui est utilisée comme pointeur.|

## <a name="see-also"></a>Voir aussi

[Système de types](../cppcx/type-system-c-cx.md)
