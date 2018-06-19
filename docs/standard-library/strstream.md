---
title: '&lt;strstream&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <strstream>
dev_langs:
- C++
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 882248ab4f9ed692aa36bac5873251867b2fff54
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856633"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

Définit plusieurs classes qui prennent en charge les opérations iostreams sur les séquences stockées dans un tableau d'objets `char` alloué. Ces séquences sont facilement converties vers et à partir de chaînes C.

## <a name="syntax"></a>Syntaxe

```cpp
#include <strstream>

```

## <a name="remarks"></a>Notes

Les objets de type `strstream` fonctionnent avec `char` *, qui sont des chaînes C. Utilisez [\<sstream>](../standard-library/sstream.md) pour les objets de type [basic_string](../standard-library/basic-string-class.md).

> [!NOTE]
> Les classes de \<strstream > sont déconseillés. Envisagez d’utiliser les classes de \<sstream > à la place.

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[strstreambuf, classe](../standard-library/strstreambuf-class.md)|Cette classe décrit une mémoire tampon de flux qui contrôle la transmission d'éléments vers et à partir d'une séquence d'éléments stockée dans un objet de tableau `char`.|
|[istrstream, classe](../standard-library/istrstream-class.md)|La classe décrit un objet qui contrôle l’extraction d’éléments et d’objets encodés à partir d’une mémoire tampon de flux de classe [strstreambuf](../standard-library/strstreambuf-class.md).|
|[ostrstream, classe](../standard-library/ostrstream-class.md)|La classe décrit un objet qui contrôle l’insertion d’éléments et d’objets encodés dans une mémoire tampon de flux de classe [strstreambuf](../standard-library/strstreambuf-class.md).|
|[strstream, classe](../standard-library/strstream-class.md)|La classe décrit un objet qui contrôle l’insertion et l’extraction d’éléments et d’objets encodés à l’aide d’une mémoire tampon de flux de classe [strstreambuf](../standard-library/strstreambuf-class.md).|

## <a name="see-also"></a>Voir aussi

[\<strstream>](../standard-library/strstream.md)<br/>
[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programmation](../standard-library/iostream-programming.md)<br/>
[iostreams, conventions](../standard-library/iostreams-conventions.md)<br/>
