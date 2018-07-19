---
title: '&lt;istream&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
dev_langs:
- C++
helpviewer_keywords:
- istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7000bd30e34836466e9f662f9b6b0dd8f2ecde4c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956552"
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
|[iostream](../standard-library/istream-typedefs.md#iostream)|Un type `basic_iostream` spécialisé sur **char**.|
|[istream](../standard-library/istream-typedefs.md#istream)|Un type `basic_istream` spécialisé sur **char**.|
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
|[basic_istream](../standard-library/basic-istream-class.md)|La classe de modèle décrit un objet qui contrôle l’extraction d’éléments et objets encodés à partir d’une mémoire tampon de flux avec des éléments de type `Elem`, également appelé [char_type](../standard-library/basic-ios-class.md#char_type), dont les caractéristiques sont déterminées par la classe `Tr`, également appelé [traits_type](../standard-library/basic-ios-class.md#traits_type).|

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programmation](../standard-library/iostream-programming.md)<br/>
[iostreams, conventions](../standard-library/iostreams-conventions.md)<br/>
