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
ms.openlocfilehash: 37399bb50f195c683b52eea4c8fadf8679d62852
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233091"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

Définit le modèle de classe basic_istream, qui sert d’intermédiaire pour les extractions de iostreams, et le modèle de classe basic_iostream, qui sert d’intermédiaire pour les insertions et les extractions. L'en-tête définit également un manipulateur associé. Ce fichier d'en-tête est généralement inclus pour vous par un autre en-tête iostreams ; vous devez rarement l'inclure directement.

## <a name="syntax"></a>Syntaxe

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|Type `basic_iostream` spécialisé sur **`char`** .|
|[IStream](../standard-library/istream-typedefs.md#istream)|Type `basic_istream` spécialisé sur **`char`** .|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|Type `basic_iostream` spécialisé sur **wchar**.|
|[wistream](../standard-library/istream-typedefs.md#wistream)|Type `basic_istream` spécialisé sur **wchar**.|

### <a name="manipulators"></a>Manipulateurs

|||
|-|-|
|[Web](../standard-library/istream-functions.md#ws)|Ignore l'espace blanc dans le flux.|
|[swap](../standard-library/istream-functions.md#istream_swap)|Échange deux objets de flux.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[>>d’opérateur](../standard-library/istream-operators.md#op_gt_gt)|Extrait des chaînes et des caractères à partir du flux.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|Classe de flux qui peut effectuer à la fois l'entrée et la sortie.|
|[basic_istream](../standard-library/basic-istream-class.md)|Le modèle de classe décrit un objet qui contrôle l’extraction d’éléments et d’objets encodés à partir d’une mémoire tampon de flux avec des éléments de type `Elem` , également appelés [char_type](../standard-library/basic-ios-class.md#char_type), dont les caractéristiques sont déterminées par la classe `Tr` , également appelée [traits_type](../standard-library/basic-ios-class.md#traits_type).|

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
