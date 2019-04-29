---
title: Types fondamentaux (C++/CX)
ms.date: 01/22/2017
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
ms.openlocfilehash: 2bd5be01b868fd3086c2064edfd4ca343db425be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301449"
---
# <a name="fundamental-types-ccx"></a>Types fondamentaux (C++/CX)

Outre les types intégrés C++ standard, C++ / c++ / CX prend en charge le système de type défini par l’architecture de Windows Runtime en fournissant des typedefs pour le Runtime Windows fondamentaux des types qui correspondent aux types C++ standard... C++ / c++ / CX implémente booléennes, de caractère et les types numériques fondamentaux. Ces typedefs sont définis dans l’espace de noms `default` qui ne doit jamais être spécifié explicitement. En outre, C++ / c++ / CX fournit des wrappers et des implémentations concrètes pour certains types Windows Runtime et les interfaces.

## <a name="boolean-and-character-types"></a>Types booléens et de caractère

Le tableau suivant répertorie les types intégrés booléens et de caractère, et leurs équivalents C++ standard.

|Espace de noms|C++ / c++ / nom CX|Définition|Nom C++ standard|Plage de valeurs|
|---------------|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|Plateforme|Booléen|Valeur booléenne de 8 bits.|bool|**true** (différent de zéro) et **false** (zéro)|
|default|char16|Valeur non numérique 16 bits qui représente un point de code Unicode (UTF-16).|wchar_t<br /><br /> - ou -<br /><br /> L’c’|(Spécifié par la norme Unicode)|

## <a name="numeric-types"></a>Types numériques

Le tableau suivant répertorie les types numériques intégrés. Les types numériques sont déclarés dans l’espace de noms `default` et sont des typedefs pour le type intégré C++ correspondant. Pas tous les types intégrés de C++ (longs, par exemple) sont pris en charge dans le Runtime de Windows. Pour des raisons de clarté, nous vous recommandons d’utiliser C++ / c++ / nom CX.

|C++ / c++ / nom CX|Définition|Nom C++ standard|Plage de valeurs|
|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|int8|Valeur numérique signée 8 bits.|signed char|-128 à 127|
|uint8|Valeur numérique non signée 8 bits.|unsigned char|De 0 à 255|
|int16|Entier signé 16 bits.|short|-32 768 et 32 767|
|uint16|Entier non signé 16 bits.|unsigned short|De 0 à 65 535|
|int32|Entier signé 32 bits.|int|2,147,483,648 et 2 147 483 647|
|uint32|Entier 32 bits non signé.|unsigned int|De 0 à 4 294 967 295|
|int64|Entier signé 64 bits.|long long  -or- __int64|-9,223,372,036,854, 775,808 à 9,223,372,036,854,775,807|
|uint64|Entier 64 bits non signé.|unsigned long long  -or- unsigned __int64|De 0 à 18 446 744 073 709 551 615|
|float32|Nombre à virgule flottante IEEE 754 32 bits.|float|3.4E +/- 38 (7 chiffres)|
|float64|Nombre à virgule flottante IEEE 754 64 bits.|double|1.7E +/- 308 (15 chiffres)|

## <a name="windows-runtime-types"></a>Types de Runtime Windows

Le tableau suivant répertorie certains types supplémentaires qui sont définis par l’architecture de Windows Runtime et sont intégrés dans C++ / c++ / CX. Object et String sont des types référence. Tous les autres sont des types valeur. Tous ces types sont déclarés dans l’espace de noms `Platform` . Pour obtenir une liste complète, consultez [Platform namespace](../cppcx/platform-namespace-c-cx.md).

|Nom|Définition|
|----------|----------------|
|Object|Représente n’importe quel type Windows Runtime.|
|Chaîne|Série de caractères représentant du texte.|
|Rect|Ensemble de quatre nombres à virgule flottante représentant l’emplacement et la taille d’un rectangle.|
|SizeT|Paire ordonnée de nombres à virgule flottante qui spécifient la hauteur et la largeur.|
|Point|Paire ordonnée de coordonnées x et y à virgule flottante qui définissent un point dans un plan à deux dimensions.|
|GUID|Valeur non numérique 128 bits utilisée comme identificateur unique.|
|UIntPtr|(Uniquement réservé à un usage interne.) Valeur non signée 64 bits utilisée comme pointeur.|
|IntPtr|(Uniquement réservé à un usage interne.)  Valeur signée 64 bits utilisée comme pointeur.|

## <a name="see-also"></a>Voir aussi

[Système de type](../cppcx/type-system-c-cx.md)
