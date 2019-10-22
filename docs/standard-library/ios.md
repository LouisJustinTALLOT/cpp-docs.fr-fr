---
title: '&lt;ios&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ios>
- ios/std::<ios>
helpviewer_keywords:
- ios header
ms.assetid: d3d4c161-2f37-4f04-93cc-0a2a89984a9c
ms.openlocfilehash: a322e517a4adb51879fc2a60f6c08f6561276de9
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689509"
---
# <a name="ltiosgt"></a>&lt;ios&gt;

Définit plusieurs types et fonctions de base pour l'opération d'iostreams. Cet en-tête est généralement inclus pour vous par un autre en-tête iostream ; vous l'incluez rarement directement.

## <a name="requirements"></a>spécifications

**En-tête**: \<ios >

**Espace de noms :** std

> [!NOTE]
> La bibliothèque de > \<ios utilise l’instruction `#include <iosfwd>`.

## <a name="remarks"></a>Notes

Un grand nombre de fonctions sont des manipulateurs. Un manipulateur déclaré dans \<ios> modifie les valeurs stockées dans son objet d’argument de classe [ios_base](../standard-library/ios-base-class.md). D’autres manipulateurs effectuent des actions sur des flux contrôlés par des objets d’un type dérivé de cette classe, comme une spécialisation de l’un des modèles de classe [basic_istream](../standard-library/basic-istream-class.md) ou [basic_ostream](../standard-library/basic-ostream-class.md). Par exemple, [noskipws](../standard-library/ios-functions.md#noskipws)(**Str**) efface l’indicateur de format `ios_base::skipws` dans l' `str` d’objet, qui peut être de l’un de ces types.

Vous pouvez également appeler un manipulateur en l'insérant dans un flux de sortie ou en l'extrayant d'un flux d'entrée, grâce à des opérations d'insertion et d'extraction spéciales fournies pour les classes dérivées de `ios_base`. Exemple :

```cpp
istr>> noskipws;
```

appelle [noskipws](../standard-library/ios-functions.md#noskipws)(**istr**).

## <a name="members"></a>Membres

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[ios](../standard-library/ios-typedefs.md#ios)|Prend en charge la classe ios de l'ancienne bibliothèque iostream.|
|[streamoff](../standard-library/ios-typedefs.md#streamoff)|Prend en charge les opérations internes.|
|[streampos](../standard-library/ios-typedefs.md#streampos)|Contient la position actuelle du pointeur de mémoire tampon ou du pointeur de fichier.|
|[streamsize](../standard-library/ios-typedefs.md#streamsize)|Spécifie la taille du flux.|
|[wios](../standard-library/ios-typedefs.md#wios)|Prend en charge la classe wios de l'ancienne bibliothèque iostream.|
|[wstreampos](../standard-library/ios-typedefs.md#wstreampos)|Contient la position actuelle du pointeur de mémoire tampon ou du pointeur de fichier.|

### <a name="manipulators"></a>Manipulateurs

|||
|-|-|
|[boolalpha](../standard-library/ios-functions.md#boolalpha)|Indique que les variables de type [bool](../cpp/bool-cpp.md) apparaissent comme **true** ou **false** dans le flux.|
|[dec](../standard-library/ios-functions.md#dec)|Indique que les variables de type entier sont affichées en notation de base 10.|
|[defaultfloat](../standard-library/ios-functions.md#ios_defaultfloat)|Configure les indicateurs d'un objet `ios_base` pour utiliser un format d'affichage par défaut pour les valeurs de type float.|
|[fixed](../standard-library/ios-functions.md#fixed)|Indique qu'un nombre à virgule flottante est affiché en notation décimale fixe.|
|[hex](../standard-library/ios-functions.md#hex)|Indique que les variables de type entier sont affichées en notation de base 16.|
|[hexfloat](../standard-library/ios-functions.md#hexfloat)|
|[internal](../standard-library/ios-functions.md#internal)|Aligne à gauche le signe d'un nombre et aligne à droite le nombre.|
|[left](../standard-library/ios-functions.md#left)|Fait en sorte que le texte qui n'est pas aussi large que la largeur de sortie apparaisse dans le flux aligné avec la marge de gauche.|
|[noboolalpha](../standard-library/ios-functions.md#noboolalpha)|Indique que les variables de type [bool](../cpp/bool-cpp.md) apparaissent comme 1 ou 0 dans le flux.|
|[noshowbase](../standard-library/ios-functions.md#noshowbase)|Désactive l'indication de la base de notation dans laquelle un nombre est affiché.|
|[noshowpoint](../standard-library/ios-functions.md#noshowpoint)|Affiche uniquement la partie entière des nombres à virgule flottante dont la partie fractionnaire est égale à zéro.|
|[noshowpos](../standard-library/ios-functions.md#noshowpos)|Fait en sorte que les nombres positifs ne soient pas signés explicitement.|
|[noskipws](../standard-library/ios-functions.md#noskipws)|Fait en sorte que les espaces soient lus par le flux d'entrée.|
|[nounitbuf](../standard-library/ios-functions.md#nounitbuf)|Fait en sorte que la sortie soit mise en mémoire tampon et traitée quand la mémoire tampon est pleine.|
|[nouppercase](../standard-library/ios-functions.md#nouppercase)|Spécifie que les chiffres hexadécimaux et l'exposant en notation scientifique apparaissent en minuscules.|
|[oct](../standard-library/ios-functions.md#oct)|Indique que les variables de type entier sont affichées en notation de base 8.|
|[right](../standard-library/ios-functions.md#right)|Fait en sorte que le texte qui n'est pas aussi large que la largeur de sortie apparaisse dans le flux aligné avec la marge de droite.|
|[scientific](../standard-library/ios-functions.md#scientific)|Fait en sorte que les nombres à virgule flottante soient affichés à l'aide de la notation scientifique.|
|[showbase](../standard-library/ios-functions.md#showbase)|Indique la base de notation dans laquelle un nombre est affiché.|
|[showpoint](../standard-library/ios-functions.md#showpoint)|Affiche la partie entière d'un nombre à virgule flottante et les chiffres à droite de la virgule décimale même quand la partie fractionnaire est égale à zéro.|
|[showpos](../standard-library/ios-functions.md#showpos)|Fait en sorte que les nombres positifs soient signés explicitement.|
|[skipws](../standard-library/ios-functions.md#skipws)|Fait en sorte que les espaces ne soient pas lus par le flux d'entrée.|
|[unitbuf](../standard-library/ios-functions.md#unitbuf)|Fait en sorte que la sortie soit traitée quand la mémoire tampon n'est pas vide.|
|[uppercase](../standard-library/ios-functions.md#uppercase)|Spécifie que les chiffres hexadécimaux et l'exposant en notation scientifique apparaissent en majuscules.|

### <a name="error-reporting"></a>Rapport d’erreurs

|||
|-|-|
|[io_errc](../standard-library/ios-functions.md#io_errc)||
|[is_error_code_enum](../standard-library/ios-functions.md#is_error_code_enum)||
|[iostream_category](../standard-library/ios-functions.md#iostream_category)||
|[make_error_code](../standard-library/ios-functions.md#make_error_code)||
|[make_error_condition](../standard-library/ios-functions.md#make_error_condition)||

### <a name="classes"></a>Classes

|||
|-|-|
|[basic_ios](../standard-library/basic-ios-class.md)|Le modèle de classe décrit les fonctions membres et de stockage communes aux flux d’entrée (de classe de modèle [basic_istream](../standard-library/basic-istream-class.md)) et les flux de sortie (de classe de modèle [basic_ostream](../standard-library/basic-ostream-class.md)) qui dépendent des paramètres du modèle.|
|[fpos](../standard-library/fpos-class.md)|Le modèle de classe décrit un objet qui peut stocker toutes les informations nécessaires à la restauration d’un indicateur de position de fichier arbitraire dans n’importe quel flux.|
|[ios_base](../standard-library/ios-base-class.md)|La classe décrit les fonctions membres et de stockage communes aux flux d'entrée et de sortie qui ne dépendent pas des paramètres du modèle.|

## <a name="see-also"></a>Voir aussi

[Référence de fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
