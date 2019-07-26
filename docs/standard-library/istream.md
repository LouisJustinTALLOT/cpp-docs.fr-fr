---
title: '&lt;istream&gt;'
ms.date: 11/04/2016
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
helpviewer_keywords:
- istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
ms.openlocfilehash: 0ad27bf849e8d4b9188868b9a29bf423b4cafafa
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458743"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

Définit la classe de modèle basic_istream, qui sert d'intermédiaire pour l'extraction des iostreams, et la classe de modèle basic_iostream, qui sert d'intermédiaire pour les insertions et les extractions. L'en-tête définit également un manipulateur associé. Ce fichier d'en-tête est généralement inclus pour vous par un autre en-tête iostreams ; vous devez rarement l'inclure directement.

## <a name="syntax"></a>Syntaxe

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|Type `basic_iostream` spécialisé sur **char**.|
|[istream](../standard-library/istream-typedefs.md#istream)|Type `basic_istream` spécialisé sur **char**.|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|Type `basic_iostream` spécialisé sur **wchar**.|
|[wistream](../standard-library/istream-typedefs.md#wistream)|Type `basic_istream` spécialisé sur **wchar**.|

### <a name="manipulators"></a>Manipulateurs

|||
|-|-|
|[ws](../standard-library/istream-functions.md#ws)|Ignore l'espace blanc dans le flux.|
|[swap](../standard-library/istream-functions.md#istream_swap)|Échange deux objets de flux.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator>>](../standard-library/istream-operators.md#op_gt_gt)|Extrait des chaînes et des caractères à partir du flux.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|Classe de flux qui peut effectuer à la fois l'entrée et la sortie.|
|[basic_istream](../standard-library/basic-istream-class.md)|La classe de modèle décrit un objet qui contrôle l’extraction d’éléments et d’objets encodés à partir d’une mémoire `Elem`tampon de flux avec des éléments de type, également appelé [char_type](../standard-library/basic-ios-class.md#char_type), dont les `Tr`caractéristiques sont déterminées par la classe, également appelée [traits_type](../standard-library/basic-ios-class.md#traits_type).|

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
