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
ms.openlocfilehash: 8e9675a673462c8eaab94d29a3ae36a4786737b7
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687857"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

Définit le modèle de classe basic_istream, qui sert d’intermédiaire pour les extractions de iostreams et le modèle de classe basic_iostream, qui sert d’intermédiaire pour les insertions et les extractions. L'en-tête définit également un manipulateur associé. Ce fichier d'en-tête est généralement inclus pour vous par un autre en-tête iostreams ; vous devez rarement l'inclure directement.

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

|opérateur|Description|
|-|-|
|[operator>>](../standard-library/istream-operators.md#op_gt_gt)|Extrait des chaînes et des caractères à partir du flux.|

### <a name="classes"></a>Classes

|Class|Description|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|Classe de flux qui peut effectuer à la fois l'entrée et la sortie.|
|[basic_istream](../standard-library/basic-istream-class.md)|Le modèle de classe décrit un objet qui contrôle l’extraction d’éléments et d’objets encodés à partir d’une mémoire tampon de flux avec des éléments de type `Elem`, également connus sous le nom de [char_type](../standard-library/basic-ios-class.md#char_type), dont les caractéristiques sont déterminées par la classe `Tr`, également appelée [ traits_type](../standard-library/basic-ios-class.md#traits_type).|

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
