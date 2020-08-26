---
title: '&lt;ostream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
ms.openlocfilehash: ffcb6c7b2f95b0b62659f6080c9ed0d1f111237c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846392"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

Définit le modèle de classe [basic_ostream](../standard-library/basic-ostream-class.md), qui sert d’intermédiaire pour les insertions du iostreams. L'en-tête définit également plusieurs manipulateurs associés. Cet en-tête est généralement inclus pour vous par l’un des autres en-têtes iostream. Vous devez rarement l'inclure directement.)

## <a name="syntax"></a>Syntaxe

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|Crée un type à partir de `basic_ostream` qui est spécialisé sur **`char`** et `char_traits` spécialisé sur **`char`** .|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|Crée un type à partir de `basic_ostream` qui est spécialisé sur **`wchar_t`** et `char_traits` spécialisé sur **`wchar_t`** .|

### <a name="manipulators"></a>Manipulateurs

|Nom|Description|
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|Met fin à une ligne et vide la mémoire tampon.|
|[fins](../standard-library/ostream-functions.md#ends)|Met fin à une chaîne.|
|[postconsommation](../standard-library/ostream-functions.md#flush)|Vide la mémoire tampon.|
|[swap](../standard-library/ostream-functions.md#swap)|Échange les valeurs du paramètre d'objet `basic_ostream` de gauche avec celles du paramètre d'objet `basic_ostream` de droite.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[<<d’opérateur ](../standard-library/ostream-operators.md#op_lt_lt)|Écrit différents types dans le flux.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|Le modèle de classe décrit un objet qui contrôle l’insertion d’éléments et d’objets encodés dans une mémoire tampon de flux.|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
