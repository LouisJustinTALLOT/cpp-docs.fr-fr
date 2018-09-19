---
title: Champs de bits C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69411a727c3f590e9a45a46ecb4ea2eb0eab05c8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029466"
---
# <a name="c-bit-fields"></a>Champs de bits C++

Les classes et les structures peuvent contenir des membres qui occupent moins d'espace de stockage qu'un type intégral. Ces membres sont spécifiés en tant que champs de bits. La syntaxe pour le champ de bits *déclarateur de membre* spécification suit :

## <a name="syntax"></a>Syntaxe

*déclarateur* **:** *expression constante*

## <a name="remarks"></a>Notes

(Facultatif) *déclarateur* est le nom par lequel le membre est accessible dans le programme. Il doit s'agir d'un type intégral (y compris les types énumérés). Le *expression constante* Spécifie le nombre de bits que le membre occupe dans la structure. Les champs de bits anonymes, autrement dit les membres de champ de bits sans identificateur, peuvent être utilisés pour le remplissage.

> [!NOTE]
> Un champ de bits sans nom de la largeur 0 force l’alignement du champ de bits suivant à la suivante **type** limite, où **type** est le type du membre.

L'exemple suivant déclare une structure qui contient des champs de bits :

```cpp
// bit_fields1.cpp
// compile with: /LD
struct Date {
   unsigned short nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned short nMonthDay : 6;    // 0..31  (6 bits)
   unsigned short nMonth    : 5;    // 0..12  (5 bits)
   unsigned short nYear     : 8;    // 0..100 (8 bits)
};
```

La disposition de mémoire conceptuelle d'un objet de type `Date` est illustrée dans la figure suivante.

![Disposition de mémoire d’un objet date](../cpp/media/vc38uq1.png "vc38UQ1") mise en mémoire d’objet Date

Notez que `nYear` est de 8 bits et provoquerait un dépassement de la limite de mot du type déclaré, **non signé** **court**. Par conséquent, il est lancé au début d’un nouveau **non signé** **court**. Il n'est pas nécessaire que tous les champs de bits tiennent dans un objet du type sous-jacent ; de nouvelles unités de stockage sont allouées en fonction du nombre de bits demandé dans la déclaration.

**Section spécifique à Microsoft**

Le classement des données déclarées comme champs de bits s'étend du bit faible au bit de poids fort, comme illustré dans la figure ci-dessus.

**FIN de la section spécifique à Microsoft**

Si la déclaration d'une structure inclut un champ sans nom de longueur 0, comme indiqué dans l'exemple suivant,

```cpp
// bit_fields2.cpp
// compile with: /LD
struct Date {
   unsigned nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned nMonthDay : 6;    // 0..31  (6 bits)
   unsigned           : 0;    // Force alignment to next boundary.
   unsigned nMonth    : 5;    // 0..12  (5 bits)
   unsigned nYear     : 8;    // 0..100 (8 bits)
};
```

puis la disposition de mémoire se présente comme dans l’illustration suivante :

![Disposition d’un objet Date avec zéro&#45;champ de bits de longueur](../cpp/media/vc38uq2.png "vc38UQ2") disposition d’objet de Date avec un champ de bits de longueur nulle

Le type sous-jacent d’un champ de bits doit être un type intégral, comme décrit dans [Types fondamentaux](../cpp/fundamental-types-cpp.md).

Si l’initialiseur pour une référence de type `const T&` est une lvalue qui fait référence à un champ de bits de type `T`, la référence n’est pas directement liée au champ de bits. Au lieu de cela, la référence est liée à une table temporaire initialisée pour contenir la valeur du champ de bits.

## <a name="restrictions-on-bit-fields"></a>Restrictions sur les champs de bits

La liste suivante détaille les opérations erronées sur les champs de bits :

- Prise de l'adresse d'un champ de bits.

- L’initialisation non -**const** référence avec un champ de bits.

## <a name="see-also"></a>Voir aussi

[Classes et structs](../cpp/classes-and-structs-cpp.md)