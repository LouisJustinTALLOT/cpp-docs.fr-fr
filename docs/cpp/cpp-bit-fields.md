---
description: 'En savoir plus sur : champs de bits C++'
title: Champs de bits C++
ms.date: 11/19/2018
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
ms.openlocfilehash: 3cf1eb3e3beb0da69a4c148a48e7c68e23804d1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344586"
---
# <a name="c-bit-fields"></a>Champs de bits C++

Les classes et les structures peuvent contenir des membres qui occupent moins d'espace de stockage qu'un type intégral. Ces membres sont spécifiés en tant que champs de bits. La syntaxe de la spécification du *déclarateur* de champ de bits est la suivante :

## <a name="syntax"></a>Syntaxe

*déclarateur* **:** *constant-expression*

## <a name="remarks"></a>Notes

Le *déclarateur* (facultatif) est le nom par lequel le membre est accessible dans le programme. Il doit s'agir d'un type intégral (y compris les types énumérés). L' *expression constante* spécifie le nombre de bits que le membre occupe dans la structure. Les champs de bits anonymes, autrement dit les membres de champ de bits sans identificateur, peuvent être utilisés pour le remplissage.

> [!NOTE]
> Un champ de bits sans nom de largeur 0 force l’alignement du champ de bits suivant sur la limite de **type** suivante, où **type** est le type du membre.

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

![Graphique Disposition en mémoire d'un objet date](../cpp/media/vc38uq1.png "Graphique Disposition en mémoire d'un objet date") <br/>
Disposition de la mémoire d'un objet Date

Notez que `nYear` est de 8 bits de long et déborderait la limite de mot du type déclaré, **`unsigned short`** . Par conséquent, il est lancé au début d’un nouveau **`unsigned short`** . Il n'est pas nécessaire que tous les champs de bits tiennent dans un objet du type sous-jacent ; de nouvelles unités de stockage sont allouées en fonction du nombre de bits demandé dans la déclaration.

**Spécifique à Microsoft**

Le classement des données déclarées comme champs de bits s'étend du bit faible au bit de poids fort, comme illustré dans la figure ci-dessus.

**FIN spécifique à Microsoft**

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

la disposition de la mémoire est ensuite illustrée dans la figure suivante :

![Disposition d’un objet date avec un champ de bits de longueur&#45;zéro](../cpp/media/vc38uq2.png "Disposition d’un objet date avec un champ de bits de longueur&#45;zéro") <br/>
Disposition d'un objet Date avec un champ de bits de longueur 0

Le type sous-jacent d’un champ de bits doit être un type intégral, comme décrit dans [types intégrés](../cpp/fundamental-types-cpp.md).

Si l’initialiseur d’une référence de type `const T&` est une lvalue qui fait référence à un champ de bits de type `T` , la référence n’est pas liée directement au champ de bits. Au lieu de cela, la référence est liée à un temporaire initialisé pour contenir la valeur du champ de bits.

## <a name="restrictions-on-bit-fields"></a>Restrictions sur les champs de bits

La liste suivante détaille les opérations erronées sur les champs de bits :

- Prise de l'adresse d'un champ de bits.

- Initialisation d’une non- **`const`** référence avec un champ de bits.

## <a name="see-also"></a>Voir aussi

[Classes et structs](../cpp/classes-and-structs-cpp.md)
