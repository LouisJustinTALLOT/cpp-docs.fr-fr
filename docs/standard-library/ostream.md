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
ms.openlocfilehash: 8de66718dab10b5c95e8c1ab7fd0bd17e9b4ee5e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448169"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

Définit la classe de modèle [basic_ostream](../standard-library/basic-ostream-class.md), qui sert d’intermédiaire pour les insertions des iostreams. L'en-tête définit également plusieurs manipulateurs associés. Cet en-tête est généralement inclus pour vous par l’un des autres en-têtes iostream. Vous devez rarement l'inclure directement.)

## <a name="syntax"></a>Syntaxe

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|Crée un type à `basic_ostream` partir de qui est spécialisé sur `char_traits` **char** et spécialisé sur **char**.|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|Crée un type à `basic_ostream` partir de qui est spécialisé sur `char_traits` **wchar_t** et spécialisé sur **wchar_t**.|

### <a name="manipulators"></a>Manipulateurs

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|Met fin à une ligne et vide la mémoire tampon.|
|[ends](../standard-library/ostream-functions.md#ends)|Met fin à une chaîne.|
|[flush](../standard-library/ostream-functions.md#flush)|Vide la mémoire tampon.|
|[swap](../standard-library/ostream-functions.md#swap)|Échange les valeurs du paramètre d'objet `basic_ostream` de gauche avec celles du paramètre d'objet `basic_ostream` de droite.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator<<](../standard-library/ostream-operators.md#op_lt_lt)|Écrit différents types dans le flux.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|La classe de modèle décrit un objet qui contrôle l'insertion d'éléments et d'objets encodés dans une mémoire tampon de flux.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
